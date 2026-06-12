---
title: "New - confused - user"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by ESL on 2007-02-12
Hi all.

Just installed Ubuntu 6.10 onto my IBM T41 and I am utterly confused with wireless settings. 

As far as I know, the built-in chipset is the Cisco Aironet version. But I can't see how to get it enabled. I'm not even sure how to see if it is actually recognised or not. I'm not sure if this set-u....upported "out of the box" as it were, but I'm quite prepared for some "under the hood" stuff. :) 

I'm quite used to setting up wireless when running XP-SP2 and know all my router settings etc. I'm using WPA-PSK (TKIP) and my router does not broadcast an SSID.

I don't mind lerning what to do, but this is my first ever experience with Linux let alone Ubuntu - and I can't even figure out where to start. I'm using a separate XP PC to access this forum, so I can work in parallel.

Hope some kind soul can lead me through this.

Cheers
George

---

### Post by dannyboy79 on 2007-02-12
go to a terminal and type in lspci -v. this will tell us the chipset info for your hardware. also please post the output from the following commands.

sudo ifconfig

also, I would suggest turning off wpa until you at least get your card connected to your access point. on a quick note, have you tried to go to the aka start menu, under system, admin, then go to networking? it'll ask you for an admin password. Ubuntu uses sudo, which is basically temporary root privalages. so when it asks you for the admin password, it want's your password you created for your user. this way you never have to relogin under root as this can be dangerious. you just always login as yourself and you sudo for admin stuff. once in networking, do you see any interfaces? maybe wlan0, or eth0, or ath0? if so, try to "activate it" does it activate? if so, go and try firefox, does firefox work? if so, you're done. next you can work on the wpa which is done with the wpa_suppliment driver I believe which I haven't bothered using. I just use WEP as I know no one around me is gonna try to get on my network. plus the more the encryption, the slower the wireless  network.

---

### Post by sumgi on 2007-02-12
Read [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

Also tail your system logs.

tail -f /var/log/messages

More good [links]("http://www.ubuntuforums.org/showthread.php?t=232059").

---

### Post by ESL on 2007-02-12
Thanks for taking the time to reply;

lspci -v seems to confirm that it is a Cisco AIRONET Wireless 802.11b. Don't know if the rest of the stuff is useful.

ifconfig output is as follows:

```

[FONT="Courier New"]eth0     Link encap:Ethernet  HWaddr  00:11:25:82:DC:3A
           UP BROADCAST MULTICAST   MTU:1500   METRIC:1
           RX packets:0  errors:0  dropped:0  overruns :  frame:0
           TX packets:0  errors:0  dropped:0  overruns :  frame:0
           collisions:0  txqueuelen:1000
           RX bytes:0  (0.0 b)    TX Bytes:0  (0.0 b)
           Base address:0x8400  Memory;c0220000-c0240000

lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  METRIC:1
           RX packets:18  errors:0  dropped:0  overruns :  frame:0
           TX packets:18  errors:0  dropped:0  overruns :  frame:0
           collisions:0  txqueuelen:
           RX bytes:1284  (1.2 KiB)  TX bytes:1284  (1.2 KiB)[/FONT]

```

As for the other stuff, In networking I can see:

[LIST]
[*]Wireless connection (wifi0)
[*]Wireless connection (eth1)
[*]Wired Connection
[*]Modem connection
[/LIST]

I have tried activating wifi0 and it seems to activate OK, but I have no connection with Firefox. Now, I know that all I have entred is the SSID and left DCHP set. So I also know I have not entered any WPA-PSK stuff so I'm guessing this is needed somewhere, but don't know where or where to get it.

My main "server" PC which has the router wired to it, also provides wireless access to 2 other XP PCs and I have two other wireless access points broadcasting near my vicinity, so turning off WPA long term is not an option except for testing.

But I would be happy to hear from you on what I have said so far.

I'm starting to think its basically all working, but the WPA bits are missing - am I on the right track?

Cheers.
George

---

### Post by ESL on 2007-02-12
Hmmm...

Still confused. Changed my router to "no security" from WPA-PSK and enabled wifi0 and eth1, but still no connecttion.

Tried loading Network Manager to see if it helps, but was informed it can't be installed on my PC (i386) .

Found some threads that seem relevant, but I don't have a clue how to do most of the stuff that's being asked of me. Guess I'm just a Linux dummie right now :confused: 

I'll have to come back tomorrow when I have had more sleep and a little less ubuntu...

:( :( :(

---

### Post by dannyboy79 on 2007-02-12
ok, well you didn't post the results I asked for from lspci -v so how do expect me to help you??? i needed to see that so I can find out if you have more than 1 interface for connecting to the internet, like eth0, eth1, and wifi0. you can't have more than 1 interface at a time since you are using dhcp you'll confuss the hell out of you computer! you need to now post the output from your /etc/network/interfaces file so I can it. please again, post the output of lspci -v. you are on the right track. you need to install wpa_suppliment or whatever it's called. this will allow you to configure your wpa security. you really need to read sumgi's first link that he posted and then use this to setup wpa. [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa)

good luck. like I said though, you need to turn off security just to make sure you can connect to your ap first, then after you do, turn wpa back on on your router and then folow the guide to install wpa on your laptop, you can do it just follow the first link and then the link I gave you. everything is there for you.

---

### Post by ESL on 2007-02-13
Ok, I missed a bit out - I'm sorry if it was really relevant. But coming to this forum for help was about the 100th thing I had tried in the run-up to trying to make Wifi work, and in a way - it was the last thing I wanted to do, because I just knew I would end up being asked to do things that I just did not understand and look even more foolish when I didn't know how.

I can't do anything today because I have other commitments, so it's going to be tomorrow evening (14th) before I can have another look at this and attempt to understand what is going on, or which bit of which manual I have not read yet.

Thanks for all your links, tips and pointers so far - I mean that sincerely. I can see I have a lot more learning to do before I have any chance of making this work.

---

### Post by dannyboy79 on 2007-02-13
well I have to tell you, if you come here for help than don't worry about thinking that you're going to look foolish if you don't know how to do something. that's the whole point you came here in the first place. So, if you want help, then help us help you. we don't know what you've already tried, we don't know your experience. we just know what we need to know in order to troublehsoot the issue and if you don't provide us with that, than we can't help ya. So, no one is gonna insult you for not knowing something, linux doesn't just come over night. I have been on it since march 2006 and I just learned yesterday how to shutdown my system using the command line. my point is, is that there is so much to learn you just have to start where you're having problems and you'll learn so much in just trying to solve the first issue. so when you come back, just post what we ask for if you'd like out help. if you don't know how to provide us with what we want, tell us that and we can tell you how. or use gogle to look thru some linux for beginers websites. for example: I read the beginners course here, [http://www.linux.org/lessons/](http://www.linux.org/lessons/)
and then you can go frmo there but it at least helps you understand things when people rattle off things when they are trying to help ya. good luck

---

### Post by ESL on 2007-02-13
Thanks for the comments. 

I'll have a good go at this again tomorrow evening (UK time) and see if I can't get some sense of order into things.

I did have a rash moment a few hours ago when I started thinking that things were so much easier under XP....






But the moment soon passed. :lolflag: 

As Arnie is fond of saying, "I'll be back..."

Cheers

---

### Post by ESL on 2007-02-14
OK - back again and I started with the Network trouble shooting guide and just got horribly confused - so I thought it sensible to go right back to your first response. (incidentally, normal wired Ethernet via the router is OK, as that is how I am connected right now. So - here goes:

The outputs from lspci -v and sudo ifconfig, as you requested.

george@George-T41:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: IBM Unknown device 0529
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: IBM Unknown device 052e
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
        I/O behind bridge: 00004000-00008fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1860 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: IBM Unknown device 052d
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Unknown device 0537
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: IBM Unknown device 0524
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0530
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: e8000000-e9fff000 (prefetchable)
        Memory window 1: c2000000-c3fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: ea000000-ebfff000 (prefetchable)
        Memory window 1: c4000000-c5fff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
        Subsystem: IBM PRO/1000 MT Mobile Connection
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0220000 (32-bit, non-prefetchable) [size=128K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 8400 [size=64]
        [virtual] Expansion ROM at ec200000 [disabled] [size=64K]
        Capabilities: <access denied>

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
        Subsystem: AIRONET Wireless Communications Unknown device 5000
        Flags: bus master, fast devsel, latency 64, IRQ 11
        I/O ports at 8000 [size=256]
        Memory at c0214000 (32-bit, non-prefetchable) [size=16K]
        Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
        [virtual] Expansion ROM at ec000000 [disabled] [size=2M]
        Capabilities: <access denied>

george@George-T41:~$ 
george@George-T41:~$ 
george@George-T41:~$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44228 (43.1 KiB)  TX bytes:44228 (43.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9B-8C-BD-15-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:38 dropped:0 overruns:0 frame:38
          TX packets:25 errors:25 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:5082 (4.9 KiB)
          Interrupt:11 Base address:0x8000 

george@George-T41:~$ 

Thanks for still being with me.

---

### Post by ESL on 2007-02-14
Whoa there...........


Suddenly started working.  :) 

Now I just have to backtrack and try to understand what I did :confused: 

Then it's time to have a go at WPA-PSK.

Thanks so far Dannyboy - something you said back there or asked me to do, must have triggered a neuron in the old grey matter somewhere.

You are a :KS

---

### Post by jml on 2007-02-14
ESL, welcome to Ubuntu!

I noticed that your Aironet card is an 802.11b card.  Out of the box, 802.11b cards do not usually support WPA-PSK encryption.  That support was built into the 802.11g specification.  Did this card connect with WPA in Windows? 

I'm  glad to hear its connecting, that tells me that you got all of the hardware and baseline configuration issues solved.  You might want to utilize WEP encryption in place of WPA, I know its not as secure, but it is supported by both your card and Ubuntu out of the box.

If you feel you must use WPA, you might want to do what I did.  I have an old IBM ThinkPad R40e.  I blacklisted the internal card (instructions can be found by searching the forum for the term blacklist.) I bought a PCMCIA wireless card that used the Atheros chip set, (NetGear WG511T, no version listed.) Then I downloaded two applications via Synaptic, network-manager and network-manager-gnome.  This set of two applications supports connecting to multiple networks and gives you a GUI to configure wpa_supplicant.  That's the application required to set up WPA encryption in Linux.

Good luck, and again, welcome to Linux.

Joe

---

### Post by ESL on 2007-02-14
Hi Joe, many thanks for your observations and support.

I have been looking around the WPA-PSK stuff and I am just getting increasingly confused. But also  a little worried about using an open connection, so might want to try WEP until I have learned enough to make WPA-PSK work.

I have the wpa_supplicant loaded and have more or less figured out what commands I need to start it. Using wpa_supplicant help command, I think i need to execute:

wpa_supplicant -Dairo -ieth1 -c/etc/wpa_supplicant.conf

But I'm not sure at all where the conf file should be placed or how to create it, or exactly what to put in it?

Also, I'm not sure how to make sure it starts automatically  all the time (i.e. after a hibernate).

Ive had a look in the examples given but my head is spinning a bit right now, so could really do with a pointer or two.

I'm planning the following:

Connect with DHCP
SSID "Speedtouch477161"
Security WEP
Type 64 bit Alphanumeric.

I don't know if you need anything else, but I may be able to figure it out.
Unless you have some better advice - which would be greatly appreciated.

:confused:

PS: Missed part of your post there Joe: YES, I have this same Laptop working under XP-SP2 and WPA-PSK (TKIP) works just fine.

---

### Post by ESL on 2007-02-15
:) 

Well, got it all sorted on WEP with 128bit hex key, so that will have to do for me.

Hopefully someone will find a way of making WPA-PSK a little easier to install and configure at some later date. My main problem at the moment seems to be that the Network-Manager app refuses to install on my machine, something to do with not wanting to install on an i386 architecture PC.  s'funny, I thought they all were.... :confused: 

Thanks to all that commented here, you did help me a lot.

Now - onward to see if this Ubuntu thing is REALLY for me, or is it back to XP.

Things still to sort out:
[LIST]
[*]iPod linking
[*]MS Pocket PC Syncing
[/LIST]

Neither of these I think I can actually achieve - all I've read so far, is that these are a nightmare

---

