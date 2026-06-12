---
title: "Possible to run server and client on same machine"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by Hannon565 on 2010-11-04
Been doing alot client server programming in college and only place at the moment is college so am just wonder with ubuntu 10.10 using terminal window can you run a client and server off the same machine. We are doing daytime and Http client and servers.

I know probable the wrong forum to post this in but wasnt sure where to post it.

Cheers for any help

---

### Post by stlsaint on 2010-11-04
I wouldnt see why not. Depending on what applications your using you may have to set client to look to localhost for resources but other than that it should go smoothly. I would suggest running something like openvz on the server machine (if its a server) so you can run multiple containers and test client and servers together.

---

### Post by Hannon565 on 2010-11-04
I was thinking of just running the server and client on the local host 127.0.0.1 but wasnt sure if would work

---

### Post by HermanAB on 2010-11-04
Here you go:
$ ssh user@localhost

---

### Post by Hannon565 on 2010-11-04
Cheers

---

