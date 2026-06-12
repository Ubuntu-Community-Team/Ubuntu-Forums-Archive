---
title: "Won't save IPv4 settings"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by bigboy7foru on 2009-09-29
So every time i shut down the machine and restart it the settings are all gone!!
 
Is there a file that i need to edit or creat that will keep them there??
 
Any and all help Appreciated
Aaron

---

### Post by Iowan on 2009-09-29
Where/how are you setting them?

---

### Post by cariboo on 2009-09-29
+1 to Iowan, what version of Ubuntu are you using?

---

### Post by doas777 on 2009-09-29
if you are using intrepid or jaunty and network manager to set your config, I found that to get it to save a static ip, I had to delete the "auto eth0" card in network manager, and readd it. you can find your mac/hwaddr with ```
ifconfig
```with luck your settings will save.

---

### Post by nandemonai on 2009-09-29
> **doas777 said:**
> if you are using intrepid or jaunty and network manager to set your config, I found that to get it to save a static ip, I had to delete the "auto eth0" card in network manager, and readd it. you can find your mac/hwaddr with ```
ifconfig
```with luck your settings will save.

+1

This is a known bug in Intrepid. Jaunty fixed the issue for me though.

---

### Post by doas777 on 2009-09-29
> **nandemonai said:**
> +1

This is a known bug in Intrepid. Jaunty fixed the issue for me though.

it's quite possible that i'm still doing it out of habit. lol

have fun

---

### Post by bigboy7foru on 2009-09-30
Well I go in to the System>Preferences>Network Configuration and manually put in the eth2 settings
 
IP, Netmask, gateway, DNS, and Search Domains
Also it is an Static IP 
 
There is only a Eth1, Eth2, Br0, and a Lo
 
Eth0 was deleted a while back
 
 
Is there any other info you guys need?

---

### Post by Iowan on 2009-09-30
Under Jaunty, I usually use the Network Manager applet to add/edit connections. Seems like it was a bit tricky to get it to enter some data (I don't remember if I needed to TAB, click, or ENTER).
Do you actually have multiple interfaces - eth1 and eth2? (My laptop uses eth1 for it's wireless) Did you create the bridge (Br0)?

---

### Post by bigboy7foru on 2009-10-05
> **Iowan said:**
> Under Jaunty, I usually use the Network Manager applet to add/edit connections. Seems like it was a bit tricky to get it to enter some data (I don't remember if I needed to TAB, click, or ENTER).
Do you actually have multiple interfaces - eth1 and eth2? (My laptop uses eth1 for it's wireless) Did you create the bridge (Br0)?
 
 
Yes we have a LAN(eth1) and WAN(eth2) connection and the br0 is the bridge we created
 
im running the 8.10 version8.10Intrepid Ibex8.10Intrepid Ibex Intrepid Ibex
 
i tried using Jaunty but the openVPN wouldn't work
 
 
Thanks
Aaron

---

### Post by vaibhav123 on 2010-05-28
i am facing the same problem.....i manually entered te ip address through system>prefrences>network config> auto eth0 >ipv4 settings....

i have to enter them every time i restart.....

---

