---
title: "ubuntu internet connection sucks"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by fouadk on 2007-09-22
hi everyone...

my problem is that i can not make my pppoe connection to work on ubuntu....

the way things work in windows is that i have no router or anything at all, all i have is a RJ-45 cable that i plug into an ethernet card and i create a new connection in windows xp and provide the username and password and Service name and ACname and that is all...no DNS , no nothing....

i tried to use the roaring penguin and installed it and modified the file /etc/ppp/pppoe.conf and added there the Service name and ACname since the wizard installer doesnt provide that capability but i still have no internet connection even though when i run the command sudo pppoe-start , it says "Connected"

i can not ping a website...all i can ping is my self.... ping 127.0.0.1

what is the problem ??? ubuntu without internet connection worth nothing....
how can i make the pppoe connection works once and for all ???

please help 

thanks in advance

---

### Post by Sturmeh on 2007-09-22
This might help:
[http://ubuntuforums.org/showthread.php?t=554357&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=554357&highlight=pppoe)

Try giving the search function a whirl.

---

### Post by fouadk on 2007-09-22
it seems i found it 

i use roaring penguin

edit /etc/ppp/pppoe.conf 

find DNSTYPE put it to SERVER so in /etc/ppp/pppoe.conf find the DNSTYPE and set it to DNSTYPE = SERVER



hope it works....it did work for me after putting the username and servicename and acname

---

### Post by deroldj on 2007-09-22
try: As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

---

