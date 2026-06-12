---
title: "Huawei CDMA Modem not working in ubuntu 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dalfish on 2009-11-02
Dear All


I have recently upgraded to karmic from jaunty 
I have two internet connection 
The one with autoeth is working fine

I have huwawei  Ec325 cdma USB MODEM Both these connection worked fine in Ubuntu 9.04

I cannot edit the network connection i have given the root password after that the following message is there 


ERROR initialising editor Insufficient previleges 

So i cannot use my Huawei CDMA USB modem supplied by BSNL india

How to activate the network connection to browse the internet 

Please help 


regards 


dalfish

---

### Post by suyog on 2009-11-07
This is known bug, you need to workaround to connect.
1) when you plugin your huawei modem, go in my computer , eject cd drive, sd storage which show up for huawei.
2)install gnome-ppp which is dialer. configure it and dial.

Check following link and my comments for reference.

[http://platonic.techfiz.info/2009/10/26/reliance-netconnect-and-ubuntu-9-10](http://platonic.techfiz.info/2009/10/26/reliance-netconnect-and-ubuntu-9-10)

---

### Post by suyog on 2010-01-04
Hey now its working straight from Network Manager. Give a try.

---

### Post by Marselinus Denny on 2010-03-19
Hi. I just managed internet connection with my Sentar ST661 CDMA 1x modem with WVDIAL utility because my Network-Connection Manager doesn't work at all. Unfortunately, since Ubuntu 9.04, Ubuntu had removed this utility from its core, so you must install its dependencies manually using Debian Package Manager, but its won't be difficult.:p

Just follow this instructions:
[http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910/](http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910/)

Just note, if you can see your IP address, DNS server, etc. It means you are succeed. I spent a lot of time to find out why my WVDIAL didn't give me any confirmations if i succeed or not. The Network Manager also didn't show any signs of successful connections :!:
 So, just open your browser and surf. And if you had managed a connection, your terminal should similar to this:

CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Mar 20 19:19:29 2010
--> Pid of pppd: 1672
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> local  IP address 10.1.50.246
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> remote IP address 10.1.63.9
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> primary   DNS address 202.134.1.10
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> secondary DNS address 222.124.198.150
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;

forgive me if my English bad, i'm not come from English spoken country

---

### Post by andrewhudsen on 2010-04-30
dear all


i am new in ubuntu.now i am working with ubuntu 9.10 i could not install and use bsnl huawei ec325 nic usb cdma data modem.I also do not get any ubuntu supporting driver software from bsnl.So i cannot use my Huawei CDMA USB modem supplied by BSNL india

How to activate the network connection to browse the internet 

Please help 


regards

andrewhudsen

---

### Post by Nisal on 2010-04-30
its CDMA o hsdpa ?

---

### Post by andrewhudsen on 2010-04-30
dear all

i am new in ubuntu . i installed ubuntu 9.10.now audio & video are not working .it is showing that need plug in.currently i have no internet connection.so i wont be able to connect system to internet and downlode automatically.will it be possile to dowlode plug-in of all software as a file and install it from pen drive / cd.If so plz send me link of all plug-in 



plase help me

with regards 

andrewhudsn

---

### Post by suyog on 2010-05-01
> **andrewhudsen said:**
> dear all


i am new in ubuntu.now i am working with ubuntu 9.10 i could not install and use bsnl huawei ec325 nic usb cdma data modem.I also do not get any ubuntu supporting driver software from bsnl.So i cannot use my Huawei CDMA USB modem supplied by BSNL india

How to activate the network connection to browse the internet 

Please help 


regards

andrewhudsen
Use this link if you are having some issues with USB modems in Ubuntu
It really helped me.
[http://hardik.in/2010/03/20/ubuntu-9-10-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-of-the-box/](http://hardik.in/2010/03/20/ubuntu-9-10-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-of-the-box/)

---

