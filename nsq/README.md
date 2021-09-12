## NSQ

### Register a new host at `/etc/hosts`.
```shell
127.0.0.1       nsqd nsqlookupd
```

### Create topic
```shell
curl -X POST http://127.0.0.1:4151/topic/create?topic=product_updated
```

### Publish a message
```shell
curl -d "{\"id\":1,\"is_deleted\":true}" http://127.0.0.1:4151/pub?topic=product_updated
```

### Consume message
```shell
nsq_tail -lookupd-http-address=127.0.0.1:4161 -topic=product_updated -channel=local
```