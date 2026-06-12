---
title: "problem installing network card"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by jurojin on 2010-02-01
hey people,

I 've just installed ubuntu 9.10 and everything is working fine - it just takes ages to boot, but that's another topic -  but the networkcard is not working. so maybe somebody can give me a hint what is wrong. My card is a

D-Link DGE-528T with a r8169 Gigabit chipset

dmesg | grep Ethernet:
[    1.995148] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

lspci says:
...
00:09.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
...

so it seems the system finds the card, but i ran ip link, and
...
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
link/ether ff:ff:ff:ff:ff:ff brd ff:ff:ff:ff:ff:ff

well, the address seems to be ff:ff:ff:ff:ff:ff which cannot be right. I did an ifconfig -a , having the same result

ifconfig -a
...
eth0 Link encap:Ethernet Hardware Adresse ff:ff:ff:ff:ff:ff
       BROADCAST MULTICAST MTU:1500 Metrik:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       Kollisionen:0 Sendewarteschlangenlänge: 1000
       RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
       Interrupt:16 Basisadressse:0x8000

(yes, my system langugae is german)

well i guess there is something wrong with the address so just to give you more info, i did aswell:

cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

... and ... 
cat /etc/modules
lp
r8169

... and changed it to ...
/etc/modules
lp
mii

but that does not work. i have the moduls r8169 and mii in the lsmod result:
...
r8168    32064 0
mii          5212 1 r8169
....


I have an ASUS A8V Deluxe motherboard and no other cards in the pci slots, just the networkcard. 

windows is running fine on this machine, Ram is and networkcard are brandnew - just bought it today cause i thought my other one was broken, having the same problems.

so, please, please help me :)

thanx

best 
j

---

### Post by samantha_ on 2010-02-01
[http://art.ubuntuforums.org/showthread.php?t=1203330](http://art.ubuntuforums.org/showthread.php?t=1203330)

setting the bitrate to 10mb/s should fix it

---

