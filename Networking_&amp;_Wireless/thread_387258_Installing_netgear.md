---
title: "Installing netgear"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by sloshman9 on 2007-03-18
Hello. I am trying to install NETGEAR WG121 onto ubuntu, but I am not getting anywhere.

Can anybody out there help me?

---

### Post by Kobalt on 2007-03-18
Lets try this one. Open up a Terminal and type this command line 
```
gksudo gedit /etc/modprobe.d/blacklist
```
Add the following two lines at the end of the file
> blacklist islsm
blacklist islsm_usb
Finally save & close, and reboot. 
It will blacklist the wrong drivers present in the kernel that are conflicting to get your hardware to work.
After that you should be able to configure your network directly from System > Admin. > Network.

---

### Post by GringoMatt on 2007-03-28
I have the same problem. I had it working great under Edgy but upgraded to Feisty and the usb adapter no longer works. It doesn't even show up anymore if I run iwconfig.
The drivers are blacklisted still but it makes no difference. Any ideas?

Incidentally if you are actually trying to get this working using the Edgy version there is a full guide in the community docs on how to do so, however that does not solve my problem in Feisty.

cheers

Matt

---

### Post by GringoMjA on 2007-04-10
The Feisty problem has gone away with some updates and is now working well.

cheers

Matt

---

