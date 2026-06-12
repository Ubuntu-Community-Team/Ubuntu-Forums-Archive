---
title: "My network not working?"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by f1do on 2006-12-11
i juz install ubuntu-6.10-server on my PC...

I type lspci...
.....
....Ethernet COntroller: Accton Technology Corporation SMC2-1211TX
....Ethernet COntroller: Intel Coporation 8280BA/BAM/CA/CAM Ethernet COntroller

I set dhcp to my eth0, and static to my eth1...

But my network is still not working?

Can anyone help??

---

### Post by scrooge_74 on 2006-12-11
I assume that eth0 connects to the internet and eth1 is for your LAN.  You have to give more info on what are you planning to do, what other equipments you have.

---

### Post by f1do on 2006-12-11
> **scrooge_74 said:**
> I assume that eth0 connects to the internet and eth1 is for your LAN.  You have to give more info on what are you planning to do, what other equipments you have.

What kind of info you need to know? i kind of new to ubuntu...?

I need to connect to the LAN, as well as connect to the internet...but it seems i can't connect to both...
Even if i tried using a cross-cable to another computer, i can't ping to each other... 
Is it because of the driver problems ?

---

### Post by scrooge_74 on 2006-12-12
You have to first configure a few things.  

If you are going to use your computer with to nics has a router then your first card is going to use DHCP so your ISP will assign automatically and IP for it to connect.  Your second nic is your internal LAN so you have to provide an static IP, submask and everything. 

Then you other PC has to be in the same submask and IP range as your second nic, and also you have to tell this second pc that its gateway to the internet is the IP of your second nic.

This is not so much Linux stuff is more networking stuff.

After you make all this you can use your firewall program to configure so your internal LAN can be better protected.  To the outside world you will only give one IP address the other machine will be hidden behind your first PC

---

