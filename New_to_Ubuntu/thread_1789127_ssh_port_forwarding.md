---
title: "ssh port forwarding"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by node2network on 2011-06-23
I'm not good at English.

I'm trying to port forwarding on ssh. My network is below.

my pc        -> 172.20.0.50/20
ssh server01 -> 172.16.0.10/20
ssh server02 -> 172.16.0.20/20,192.168.0.20/24
windows machine 192.168.0.30/24

My pc can only connect ssh server01 with port 22.
I want to access windows machine by using ssh port forwarding.
My typed command is below.

On my pc:

$ ssh -L10000:172.16.0.20:10010 hoge@172.16.0.10

On ssh server01

$ ssh -L10010:192.168.0.30:3389 hoge@172.16.0.20

I thought that I can connect windows machine with accessing localhost:10000 on my pc. But I cannot. Why?

---

### Post by CharlesA on 2011-06-23
They are on totally different networks.

Can you ping the machine at 192.168.0.30 from either server?

---

### Post by node2network on 2011-06-23
I can only ping the machine at 192.168.0.30 from ssh server02.

server02 and windows machine belong to the same network.
server01 and server02 belong to the same network

---

### Post by CharlesA on 2011-06-23
Are you able to ssh directly to server02?

ssh -L10000:192.168.0.30:3389 hoge@172.16.0.20

---

### Post by node2network on 2011-06-23
I can't ssh directly to server02. server02 can only accept ssh from server01.

---

### Post by CharlesA on 2011-06-23
You could try this to rule out port forwarding issues:

One session (server01:22):

```
ssh -L 2222:172.16.0.20:22 user@server01
```

New session (localhost:2222):

```
ssh -L 10000:192.168.0.30:3389 user@server02
```

Then connect via rdp to localhost:10000

---

### Post by node2network on 2011-06-23
oh! thank you! I can!

---

### Post by CharlesA on 2011-06-23
> **node2network said:**
> oh! thank you! I can!
Outstanding. It might be a bit of a pain to do it that way, but I think that might be only way to get it working since the machines are on two different networks.

You can mark the thread as solved from the thread tools menu at the top. :)

---

