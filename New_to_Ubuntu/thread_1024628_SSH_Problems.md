---
title: "SSH Problems"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Napandee on 2008-12-29
Hello!

I've placed this in the beginner section since I'm not that good with it just yet :)

Now to my problem,

I'm trying to setup a ssh port forward from one server to another, this has worked just a day or two ago but now I can't get it back up.

This is my command: ssh -fNg -L 8006:127.0.0.1:3307 root@somehost
I get the password question from the remote host but then I get this: bind: Address already in use.

Ive checked my SSH tunnels with:ps -ef | grep ssh command but all connections are just my ssh remote login and the ssh tunnel I've just setup. 

And when I try and telnet 127.0.0.1 8006 I just get connection refused closed.

Help would be good since I don't seem to find anything googling that helps me :)

---

### Post by stephanvaningen on 2008-12-29
You can get more connection information with
```
netstat
```

---

