---
title: "wired network connection help"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by jeretraca on 2008-04-07
Hello Friends
I have resently moved to Ubuntu and installed version 7.1.0 in my machine
with no problem WHEN I boot the system there the problems begin

Obuntu tells me

The panel encountered a problem while loadin
"OAFIID:GNOME_FastUserSwitch Applet
Do you want to delete the applet from your configuration 
since i dont know what it is and what it does i usually say No

Next the wired network in the Nework manager 
I open network make sure it is not roaming 

no problem put in the static ip address very good now I put in the network cable nothing happens

when i ping dns on the terminal it is visible and available


i tried ifconfig eth0 with following result

Link encap:Ethernet Hwaddr 00:31:8F:6E:39
Inet Addr 195.202.83.69  Beaust:195.202.83.95 mask 255.255.255.224
UP BROADCAST Running MuLTICAST MTU:1500 METRIC 1
Rx packets:270 errors:0 Dropped:0 overruns:0 frame:583
TX packets:143 errors:0 dropped:0 overruns:0 carrier0
collisions :0 txquelen:1000
RXbytes:23774(23.2kb)  Txbytes:14022(13.6kb)
interrupt:18 base Adress:0xd400

then i try

ifup eth0 result failed to open stefile /var/run/network/ifstate : permission Denied

the same answer when I try 
if down eth0

one more thing about the local area network in order for mackintosh or windows machines to run on the network their network adapters must be configured to run at 10mbps full duplex is there a provision for that in ubuntu as this often solves the network problem on mackintosh vista or or windows xp machines

Please assist me on thisl

---

### Post by equity on 2008-04-07
first, to change something on your hardware configuration you have to do it as superuser by typing "sudo" prior any command to have the right to do it.

So, let's start:
kill the network manager that you do not need by typing:
**killall nm-applet**

then type:
[B]sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth0 <the internal IP you want to have> netmask <netmask> up
sudo route add default gw <default gateway>
sudo dhclient eth0[/B]

and post the output if it does not work.

---

