---
title: "[SOLVED] two computers running ubuntu on the same network..."
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by loso on 2007-04-29
I want them to see each other, but at the moment they don't.  How do I change that?
Both computers are running feisty desktop 7.04, and both are connected to the same router.
I'm sure this is a silly question :S

---

### Post by denver on 2007-04-29
First, find out the IP address of each computer

```
ifconfig
```

and you should get a listing of the network cards on your computer. Do this on both computers and see if they are in the same networh. If you router is handing out IP's via DHCP the should be. Usualy the IP address is something simmilar to 192.168.0.1 . Try pinging one another to see if there is some comunication between them.

```
ping 192.168.0.X
```

( where X is the last digit of the others machine's IP). If all is well then you can install samba or some other file sharing service on your computer. I belive there is an application that easely does this in GNOME. System-->Administration-->Shared Folders.

Hope This helps...good luck!

---

### Post by loso on 2007-04-29
it worked!!  Thanks :)

---

