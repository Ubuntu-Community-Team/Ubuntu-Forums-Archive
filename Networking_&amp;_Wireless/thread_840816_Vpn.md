---
title: "Vpn?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by mankatron2008 on 2008-06-25
hi,

i'm a relative new user to ubuntu and have only used it as a virtual machine until this evening. after a bit of fun, i got wireless working and my next goal is to be able to VPN into work. despite following the various guides, i am unable to connect - i am 99% sure that i have set it up correctly but alas, after prompting me for login details (that are correct, as i'm using them on a vista laptop) there is nothing. nada. 

i've looked at debug and messages, there is nothing there - it looks as if no connection attempt is being made. my router logs only show attempts to connect that originate from my laptop as opposed to this machine.

i have refuse EAP, refuse CHAP ticked and use peer DNS/peer DNS through tunnel unticked. 

any help greatly appreciated.

---

### Post by niyonk on 2008-06-25
What VPN client are you using because Kvpnc works fine for me.
Its easy for me, i just have to import a .pcf file.
I am not sure about your case. :(

---

### Post by mankatron2008 on 2008-06-25
i'm just using the networkmanager tool...

---

### Post by niyonk on 2008-06-25
I highly recommend Kvpnc, 
I do not know about the network manager tool.
Probably the software would do most of the dirty work for 'ya :-D
PEACE!!

---

### Post by kriot on 2008-06-26
be sure to install vpnc then install kvpnc. I just set this up myself today and it works great. with kvpnc you can import .pcf files which makes things nice and simple.

I think the command is something like

#sudo apt-get install vpnc

I installed kvpnc from the add/remove programs app in ubuntu but it cant be much different from the command above.

Good luck.

KC

---

### Post by mankatron2008 on 2008-06-26
thanks for those, installed kvpnc and it's a nice little tool - i'm at work now so can't paste the log but i was getting an MS CHAP authentication error iirc.

would this suggest that i'm trying to connect using the wrong credentials? 

refuse CHAP is enabled, didn't get time to test with it disabled this morning...

if i can get VPN working, i pretty much have no reason aside from the odd game to use XP :)

---

