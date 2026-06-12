---
title: "Keep losing file share"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by fregas on 2009-08-25
I have recently upgraded my ubuntu to the latest version 9.04.  I use it as a samba file server.  Now I keep losing access to my share.  Periodically the other computers won't be able to access it.  But if i come in and hit a web page or something I can get on the internet and the other computers can again hit the share.    I've checked my sleep settings and i have it set to never sleep.  Anyone know what the problem could be?

---

### Post by cariboo on 2009-08-26
Check your ip address there may be a conflict. Two of the computers on your network may have the same ip address.

---

### Post by fregas on 2009-08-26
Should I assign a static IP in ubuntu?

---

### Post by desperado665 on 2009-08-26
I also suffered from the same disconnect issues with samba. I have hence found a better share solution. If your other pc's are also Ubuntu, try ssh. It works much better than samba.

Once you install ssh on all the pc's
```
sudo apt-get install openssh
```

Go to Places>Connect to server

Then change server type to ssh, input IP address of the PC you want to connect to.

---

### Post by fregas on 2009-08-27
i thought of that, but I do have a couple of windows computers.  Is there a good SSH / drive mounting client for windoze?

---

### Post by aktiwers on 2009-08-27
> **fregas said:**
> i thought of that, but I do have a couple of windows computers.  Is there a good SSH / drive mounting client for windoze?
[http://hartvig.de/2008/mounting-your-ssh-shares-in-microsoft-windows/](http://hartvig.de/2008/mounting-your-ssh-shares-in-microsoft-windows/)

---

