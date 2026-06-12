---
title: "internet problems"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by cryo4.rm on 2007-07-03
PLEASE HELP ME ----- 

over the weekend my laptop has stopped connecting to the net.

FEiSTY 7.04 
Usually use a CABLE into ETH0, since i've had the computer it has just WORKED with no confic necessary

think ive screwed my setting dabbling with some WLAN manager coz all of a sudden my cable isnt giving me anything. (and never sorted wlan either)

 I CAN PING MY MODEM.... but not external sites. (modem - internet is working coz this computers on it) 

 ifconfig eth0 gives me

eth0 Link encap:Ethernet HWaddr 00:11:2F:5B:AB:95 
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:2fff:fe5b:ab95/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:932 errors:0 dropped:0 overruns:0 frame:0
TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:68391 (66.7 KiB) TX bytes:17800 (17.3 KiB)
Interrupt:17

 -----------------------
 ( i lifted these from another post but are identical save the addresses)

 have tried etc/init.d/networking restart

 have tried pppoeconfig
 (said the access concentrator of my provider does not respond.. )

----------------------------------------------------

 when i open  >settings>network tools, network device is set to LOOPBACK INTERFACE, i can change this to ETH0 but it has no effect and when i open up the window a second time it has reverted back to LO ...
 


 please... can someone give me a hint as to where to start to diagnose the problem...

 ::::::::::::::::::: THANK::: LISTENING ATTENTLY::::

---

### Post by scrooge_74 on 2007-07-03
options that come to mind

reboot cable modem (if that what you have)

disable your cards and reboot, then reenable them

other way is to go to /etc/network/interfaces

and check things look like this 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

then reboot

or do a network restart

---

