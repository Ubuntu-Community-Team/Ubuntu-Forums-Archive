---
title: "Setting up a pppoe connection with wireless"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by rajit.dasgupta on 2010-12-18
I am running ubuntu on a dell inspiron mini 10 netbook. I have a bsnl broadband connection to which i connect using a username and password (on windows, with my older laptop) with a wi-fi enabled router. 
Connection is ok when i'm wired [i've set up a dsl connection which works fine]. however this doesnt work when I try to connect via wireless, although i can see that it can detect my router [i've loaded all the wireless drivers].
Is there something i'm missing out?

---

### Post by fly-by-night on 2010-12-18
A couple of suggestions and questions:

1. What version of Ubuntu are you using.

2. Do you have DHCP "on" on the router.  Or do you need to manually configure IP details. If everything is auto, try manually specifying SSID, Password, IP etc - Preferences/Network_Connections/Wireless (in Gnome).

3. Did you reboot or restart_networking after the changes you made (drivers, setting changes etc).

---

### Post by rajit.dasgupta on 2010-12-18
1. I'm using Maverick. [10.10] Its a netbook version.

2. Dhcp is on. The IP and everything are detected automatically. I don't think i have an SSID for my router. On windows I normally connect using a usrname and password.

3. Yup I restarted after my installations. Still no luck.

I have to set up a vpn connection on ubuntu to connect the same way, right?

---

### Post by dineshs on 2010-12-21
Method-I
[http://ubuntuforums.org/showthread.php?p=9857165#post9857165](http://ubuntuforums.org/showthread.php?p=9857165#post9857165)
Method-II(simple method)
Configure your modem in PPPoE mode so that the connection will be always ON(no need of dialler)
ref modem configuration for multiuse in [http://www.calcutta.bsnl.co.in/dataoneinstall/menu.html](http://www.calcutta.bsnl.co.in/dataoneinstall/menu.html)
Q1)What is the model name of your modem?
Q2)Are you using VPN?

---

### Post by rajit.dasgupta on 2010-12-24
Followed the instructions for multi-user. However I still have to dial-up to access the internet.
What am I doing wrong?

My router is Nokia siemens sl2_141.

I tried creating a vpn...but every time i try to connect it says that the vpn service failed to start.

Also, on Ubuntu, I can detect my router just fine on wireless, but I can't connect to it.

The wired connection is working though [via dsl].

---

### Post by nikhilbhardwaj on 2010-12-25
hi rajit,
i have a bsnl router too and i've gotten around by automatically setting it to connect to the internet, this way you don't need pppoe in either windows or linux.

to achieve this here's what i did,
goto 192.168.1.1 which should be the web ui for your router
now go to internet connection under the configuration tab.

there will be a connection with the VPI/VCI values 0/35, either delete it or change the VCI value for that connection for me that was bridge_0_32.

now add a new internet connection with the following settings
Configure ATM PVC
VPI:0
VCI:32
Service Category:UBR with PCR
Peak Cell Rate : 8000

Configure Connection Type
Encapsulation Type:PPPoE LLC/SNAP
Encapsulation Mode:Bridged

in the
Configure Broadband User Name and Password section
enter your username typically your phone no and the password
be sure to set
Session established by:	Always On

after this is done reboot your router,
now you should be able to connect to the internet without dialing both for wired and wireless connections.

hope this helps
you can ask for any clarifications if you wish

---

