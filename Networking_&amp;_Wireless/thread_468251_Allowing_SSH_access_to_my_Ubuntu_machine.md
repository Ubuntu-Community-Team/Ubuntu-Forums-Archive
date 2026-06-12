---
title: "Allowing SSH access to my Ubuntu machine"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by bsdrocker on 2007-06-08
I want to allow ssh access to my ubuntu machine so I can manage it from other workstations accross my network. When I try it gives me an error. I'm assuming there is some kind of firewall I need to open port 22 on.

My install is VERY Vanilla so far - not much tweaking yet.

Thanks,

BSDRocker

---

### Post by Mr. C. on 2007-06-08
Yes, port 22 to the server needs to be open.

What is the error ?

MrC

---

### Post by bsdrocker on 2007-06-08
Its an error on SecureCRT - here it is;

The remote system refused the connection.

How do I go about opening that port?

Cheers,

BSDRocker

---

### Post by Mr. C. on 2007-06-08
Are you sure the ssh server is running and configured to listen on port 22 ?

What's the output of :

```
netstat -ln --tcp | grep 22
```

MrC

---

### Post by daschmidty on 2007-06-08
Also you said you have a vanilla install..did you install the ssh server?

```
sudo apt-get install openssh-server
```

---

### Post by bsdrocker on 2007-06-08
...I feel stupid - I didn't have openssh-server installed. I guess I'm assumed it did it by default on install. Well you know what happens when you assume - you make an *** oUt of you and ME!

Cheers and thanks for the help!

-BSDRocker

---

### Post by daschmidty on 2007-06-08
yeah that got me for a long time too..it install the client package but not the server..go figure...i guess for security reasons

---

