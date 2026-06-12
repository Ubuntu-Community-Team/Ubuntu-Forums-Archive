---
title: "Don't know how to install madwifi"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by mojdk on 2008-08-22
Hi.

I just installed a partition of linux for the very first time in my life. I have no experience with linux what so ever. So I installed ubuntu, but now i want to connect to my wifi so I can get on the internet. I've just googled a little, and i found out that "madwifi" might be the best solution. But my problem is that i don't know even how to install it. I have tried this guide [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#InstallingMadWifi](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#InstallingMadWifi) but still can't figure it out. 
Could someone please help me? :)

My wifi adapter is a d-link DWA-547

//mojdk

---

### Post by livestockPimp on 2008-08-22
Ok,
have you done everything this guide says?
have you untar the source, done the "make", ect and install the drivers?

if so, what is the output of "ifconfig -a"

also what is the output of "lsmod"

Thanks

---

### Post by mojdk on 2008-08-22
Well i did untar it. And did not understand a thing of the rest you wrote :D Sorry..

---

### Post by livestockPimp on 2008-08-22
Ok, after you untar it you are meant to go into the dir and type "make" and then "make install".

this will compile the ath_pci module.

have you completed these steps?

were there any errors during these steps?

if these steps appeared to work then type "lsmod"
at the command prompt and post the output here.
Also post the output of "ifconfig -a"

---

