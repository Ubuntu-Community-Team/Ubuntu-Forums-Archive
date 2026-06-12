---
title: "Is dial-up broadband possible in Ubuntu? Does it even exist?"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by fredbaluga on 2006-08-12
At university my (Windows) computer plugged in via ethernet to the holes in the wall and all i had to do was enable the LAN network connection to gain access to the internet.
Back at home, my parents' (Windows) computer connects to broadband via a usb modem which requires a dial-up (i presume the software for this is provided by the ISP - Wanadoo).

I have become increasingly annoyed by windows, especially having each installed program adding various processes, which i have to re-disable each time they update.
Seeing as there was nothing really tying me to windows i tried Ubuntu and liked it a lot (workspaces - genius!).

I'm unable to get any sort of access to the internet with my modem (D-Link DSL 300T) using the advice in the manual or their website; and the phone support line doesnt open until monday.
Is it possible to connect to the internet on Ubuntu with this setup? Or shall I wait until i'm back at university accomodation?

I'm new to linux, but eager to learn, and any respond will be appreciated. Even if it is to tell me to just give up and go back.

---

### Post by az on 2006-08-12
Unfortunately, the pppoe protocol is too uncommon for there to be a friendly way to use it yet.  You must run 

sudo pppoeconf

from the command line and enter your connection information to use your ADSL modem.

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

I beleive that the connection is started upon boot once it is configured that way.

---

### Post by fredbaluga on 2006-08-12
thanks for the quick reply

pppoeconf output:
	Sorry, I scanned 1 interface, but the Access
	Concentrator of your provider did not respond. Please
	check your network and modem cables. Another reason
	for the scan failure may also be another running pppoe
	process which controls the modem.

---

### Post by az on 2006-08-12
> **fredbaluga said:**
> thanks for the quick reply

pppoeconf output:
	Sorry, I scanned 1 interface, but the Access
	Concentrator of your provider did not respond. Please
	check your network and modem cables. Another reason
	for the scan failure may also be another running pppoe
	process which controls the modem.

Are you using the correct cable (crossover or patch?)

---

### Post by fredbaluga on 2006-08-12
it's all set up the advised way. i've tried the the cables that came in the box, and some i had lying around.

i can ping it:
	--- 192.168.1.1 ping statistics ---
	8 packets transmitted, 8 received, 0% packet loss, time 6999ms
	rtt min/avg/max/mdev = 0.619/0.652/0.751/0.039 ms

but i cant ping google or anything:
	--- 64.233.189.104 ping statistics ---
	8 packets transmitted, 0 received, +8 errors, 100% packet loss, time 6999ms

also, typing [http://192.168.1.1](http://192.168.1.1) (the modem IP) which in Windows takes me to a graphical interface, never connects in Ubuntu

---

### Post by drtvasudevan on 2006-08-12
do i understand that you are 
1.using a laptop
2. using ubuntu and acessing net from university and also from home.
then the network settings will be different.
you must create  an additional location by going to the network settings system >admin>networking

---

### Post by fredbaluga on 2006-08-12
argh, sorry, did not make my self clear
1. im using a desktop pc
2. i installed ubuntu since coming home from university i've only had the time to mount my partitions (i only mention it because i didn't need a modem then, i just used the one cable to connect the ethernet ports my room and my computer)

i'm assuming creating a dial up connection will be harder than accessing an already existing network

related forum posts have asked for the outputs of various commands, so i'll add them now to save time in case they're needed
```
cat /etc/network/interfaces output:
	auto lo
	iface lo inet loopback

	auto eth0
	iface eth0 inet dhcp

	auto eth1
	iface eth1 inet dhcp

	auto eth2
	iface eth2 inet dhcp

	auto ath0
	iface ath0 inet dhcp

	auto wlan0
	iface wlan0 inet dhcp


	iface dsl-provider inet ppp
	provider dsl-provider

	# added by pppoeconf
	auto modconf
	    iface modconf inet manual

	    pre-up /sbin/ifconfig modconf up # line maintained by pppoeconf

cat /etc/resolv.conf output:
	nameserver 192.168.1.1

route -n output:
	Kernel IP routing table
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
	0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

ifconfig output:
	eth0    Link encap:Ethernet  HWaddr 00:13:8F:48:7F:AF
		inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
		inet6 addr: fe80::213:8fff:fe48:7faf/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:465 errors:154 dropped:0 overruns:0 frame:154
		TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000
		RX bytes:140074 (136.7 KiB)  TX bytes:95015 (92.7 KiB)
		Interrupt:58 Base address:0xdead

	lo	Link encap:Local Loopback
		inet addr:127.0.0.1  Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING  MTU:16436  Metric:1
		RX packets:15 errors:0 dropped:0 overruns:0 frame:0
		TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0
		RX bytes:1996 (1.9 KiB)  TX bytes:1996 (1.9 KiB)
```

---

### Post by drtvasudevan on 2006-08-12
> **fredbaluga said:**
> argh, sorry, did not make my self clear
1. im using a desktop pc
2. i installed ubuntu since coming home from university i've only had the time to mount my partitions (i only mention it because i didn't need a modem then, i just used the one cable to connect the ethernet ports my room and my computer)

i'm assuming creating a dial up connection will be harder than accessing an already existing network 



    * To configure dialup 

```
sudo pppconfig
```

    * To connect dialup 

```
sudo pon provider_name
```
of course you dont type "provider name" .your own providers name

    * To disconnect dialup 

```
sudo poff
```
ooops!
i saw dial up and assumed....
usb modems are a real pain i hear.
sorry i have no answer.:oops:

---

### Post by fredbaluga on 2006-08-12
ok....i went through pppconfig
as primary nameserver i put the modem's ip (192.168.1.1)
the followed instructions as set here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

it didnt see a modem and gave me a list of choices ttyS etc blah
In the networking section of system --> admin my ethernet is recognised but modem is not. is this right? as the modem is plugged into the ethernet port im not sure if it would come up here. if i try to edit the modem section the 'ok' button greys out. do i have to mount my modem or other similar process?

---

### Post by drtvasudevan on 2006-08-12
see [http://www.ubuntuforums.org/showthread.php?t=109451](http://www.ubuntuforums.org/showthread.php?t=109451)

---

### Post by fredbaluga on 2006-08-12
thanks very much. i saw this already yesterday but it made no sense to me. 
now it does. im quite glad im picking it up. . . 

. . anyway i followed the advice given there of changing
```
iface eth0 inet dhcp
```to
```
iface eth0 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   gateway 192.168.1.1
```

and i had the same no route thing
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

so i added one, but now it says
```
Destination     Gateway            Genmask         Flags Metric   Ref    Use Iface
192.168.1.0     0.0.0.0             255.255.255.0   U     0      0      0    eth0
0.0.0.0            192.168.1.1      0.0.0.0             UG   0      0      0    eth0
```
presumably i want to merge the two lines it one (tell me if im wrong)
how would i go about doing this?

also, unlike the other guy, i still cannot access the modems web interface



argh . . . tired
please keep helping if you can. it seems im very close [-o<
i'll be eternally greatful if a awake tomorrow and find an answer

---

### Post by drtvasudevan on 2006-08-13
> **fredbaluga said:**
> 
it didnt see a modem and gave me a list of choices ttyS etc blah
In the networking section of system --> admin my ethernet is recognised but modem is not. is this right? as the modem is plugged into the ethernet port im not sure if it would come up here. if i try to edit the modem section the 'ok' button greys out. do i have to mount my modem or other similar process?

no you dont see the modem.
only the eth0 through which you are connecting to the wide area network outside. that is you become a part of a wide network.
no need to mount modem or anything.

of course you must be able to communicate to it with 198.164.1.1 in url box. you would in adsl modem but this is usb. i dont know about usb.

---

### Post by drtvasudevan on 2006-08-13
[QUOTE=fredbaluga;1373095]thanks very much. i saw this already yesterday but it made no sense to me. 
now it does. im quite glad im picking it up. . . 

. . anyway i followed the advice given there of changing
```
iface eth0 inet dhcp
```to
```
iface eth0 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   gateway 192.168.1.1
```

/QUOTE]

these are same as mine except the added line
```
dns-nameservers 192.168.1.1
```

so do a
```
gksu gedit /etc/network/interfaces
```
and add that line.
i too shall  pray!

---

### Post by fredbaluga on 2006-08-13
cheers that helped.
ifcong no longer shows errors on the RX / TX packets thing

i can even access the web interface on the modem but it doesnt even try to connect after i put all the data in.
i cannot successfully ping anything other than the modem

i seem to be in the same position as this guy [http://www.ubuntuforums.org/showthread.php?t=109451](http://www.ubuntuforums.org/showthread.php?t=109451)
so i followed the add route advice
```
sudo route add default gw 192.168.1.1 dev eth0
```
meaning im left with a route -n of
```
Destination     Gateway            Genmask         Flags Metric   Ref    Use Iface
192.168.1.0     0.0.0.0             255.255.255.0   U     0      0      0    eth0
0.0.0.0            192.168.1.1      0.0.0.0              UG   0      0      0    eth0
```
clutching at straws, im thinking that i need to change it to this
```
Destination     Gateway            Genmask         Flags Metric   Ref    Use Iface
192.168.1.0    192.168.1.1       255.255.255.0   U     0      0      0    eth0
```
if so, how would i do this?
if not, any ideas? i'm stumped


my modem is not usb btw

---

### Post by fredbaluga on 2006-08-13
also, the broadband in my house isn't an instant access affair.

to get broadband access on my parents computer, opening a browser  brings up a connection interface (similar to
the old-school days of 56k) which dials 0 and connects instantly (taking a few seconds to register the name/password).

presumably if broadband is coming down the pipes then i can access it similar to accessing internet via lan,
and this is just wanadoo's way of keeping everyting similar to help their call center operators.

again, if this isnt the case, point it out

---

### Post by drtvasudevan on 2006-08-13
> **fredbaluga said:**
> cheers that helped.

clutching at straws, im thinking that i need to change it to this
```
Destination     Gateway            Genmask         Flags Metric   Ref    Use Iface
192.168.1.0    192.168.1.1       255.255.255.0   U     0      0      0    eth0
```
if so, how would i do this?
if not, any ideas? i'm stumped
your set up is now just like mine. i dont think it shd be changed.
try pinging 
ping 82.211.81.186
ping [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by fredbaluga on 2006-08-13
no joy. 100% errors pinging anything other than the modem itself.
thanks all for helping me to get to the modem graphical interface though, it's a start at least.

unless anyone has any better ideas i'm going to phone the d-link people tomorrow about setting up the modem for wanadoo and all their associated perculiarities.

---

### Post by drtvasudevan on 2006-08-13
> **fredbaluga said:**
> also, the broadband in my house isn't an instant access affair.

to get broadband access on my parents computer, opening a browser  brings up a connection interface ..
presumably if broadband is coming down the pipes then i can access it similar to accessing internet via lan,
....
again, if this isnt the case, point it out

i am afraid i was under a total erroneous assumption.](*,) 
why are you not trying to connect with the usb modem that already is there?
if the dialer config is there in the modem it may work.
or if the ISP has given an installtion cd look for a linux driver in it (remote chances):roll: 
trying to connect a dial up modem setup network from a LAN port to my mind looks impossible.:-k 
try with usb modem.

---

### Post by fredbaluga on 2006-08-13
there is only one usb modem in the house and my parents would not be best pleased if i took it from their computer to allow mine to get online. 
but i'll give it a bash anyway, see what happens (godammit i came to ubuntu so i wouldn't need to steal things).

wanadoo are now owned by orange, who, despite claiming to be at the forefront of modern technology do not have an email address
(the monthly email statement my dad gets from them is from a no-reply email and they list a postal address as their contact information).

the word 'linux' finds 0 results on their entire website ('help section included).
seriously, these people are a joke.

i'll try the wanadoo install cd with the usb modem.

---

### Post by drtvasudevan on 2006-08-13
usb is simple enough to unplug and plug back.
it is hot plug in too so no potential problems unless both the pcs want to be online simultaneously.
i wonder how the connections have been setup if you want both the modem and lan port to connect.
perhaps it is possible to make a home network and share the connection.

---

