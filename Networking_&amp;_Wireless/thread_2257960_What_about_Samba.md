---
title: "What about Samba?"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by exsencon on 2014-12-23
I installed the new Ubuntu 14.10, it was allright, a bit slower than my old Ubuntu 10.10 I must say. Wireless was a problem but finally solved. (Dell Inspiron Laptop 1501,HDD120GB, RAM 2GB).
I wanted to connect it to my WINXP desktop via samba and I can read and write from Ubuntu to the windows without problems but to get Ubuntu to show up on my Win desktop, well... I really can only do it as root (meaning sudo su) and then I get the samba24 or something like that and that works untill I reboot of course,then I have to do it all over again.
Now,I know samba has always problems connecting both ways, so my question is: is there an easy way to get Ubuntu-Windows AND Windows-Ubuntu? Just between 2 PC's, It can't be that hard I would think but in my 6 years with linux it has always given me a hard time.

---

### Post by r.stiltskin on 2014-12-23
Shouldn't be too hard to set up:

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html]("https://help.ubuntu.com/lts/serverguide/samba-fileserver.html")

(That page comes from the Ubuntu 14.04 documentation but it should work the same in 14.10.)

---

### Post by exsencon on 2014-12-24
Tried it as you said and it works! 
Thanks a lot r.stiltskin!.
We can consider this thread closed.

---

### Post by exsencon on 2014-12-27
well, maybe I was a little bit too fast. Though it is working allright i still have to go into a terminal on every boot and do
sudo restart smbd
sudo restart nmbd
otherwise I can't get to my Ubuntu stuff in my WinXp desktop, getting something like: Permission denied or somthing like that.
Now when I do those two lines it is OK but I have to do them on every boot.

---

