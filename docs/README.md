# Development

We need to build the image, bring it up, and make a self signed certificate [ref](https://github.com/msis/docker-compose-nginx-gogs)

```
docker build -t vanessa/gogs
```

Set the password to what you want, you will need to input this later into the web interface


```
export POSTGRES_USER=gogs 
export POSTGRES_PASSWORD=gogs 
docker-compose up -d
```

Then create a self signed certificate

```
docker exec -it (gitserver) bash
cd /data/gogs/conf/
/app/gogs/gogs cert -ca=true -duration=8760h0m0s -host=0.0.0.0
exit
docker-compose restart
```

You can then go to 127.0.0.1 in your browser. It probably will tell you it's not secure and you need to add an exception, do that for now and enter the information about your database.
