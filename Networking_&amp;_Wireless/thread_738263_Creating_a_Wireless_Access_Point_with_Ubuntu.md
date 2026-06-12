---
title: "Creating a Wireless Access Point with Ubuntu"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by shuoink on 2008-03-28
Ok so here's my situation. I've got a good laptop (2.2ghz, 1gb ram, etc...) with a dead-ish video card. No matter what screen resolution I choose, I can only see the top-half of the screen for some reason ( this is not a linux problem, as it does this even when the computer is booting up and such). The vga port doesn't seem to be working at all.

Anyway, the computer already has a working installation of ubuntu 7.10 on it. I managed to set it up so that I could get around the display problem by configuring remote desktop and then logging into it via vncviewer.

The laptop is a MSI MS-1029 ( [http://www.msicomputer.com/NB/product_spec.asp?model=MS-1029](http://www.msicomputer.com/NB/product_spec.asp?model=MS-1029) ) with a MS-6855B wireless card ( [http://www.msicomputer.com/product/p_spec.asp?model=MP54GBT2](http://www.msicomputer.com/product/p_spec.asp?model=MP54GBT2) ).

What I want to do is use this laptop as a wireless access point. I have tried unsuccessfully to create an ad-hoc network that my other laptops could connect to.

Any ideas? How can I get this system working as a wireless access point?

---

### Post by dstew on 2008-03-28
[Here is a community document]("https://help.ubuntu.com/community/Router") that tells how to do that. Your wireless card needs to be able to function in "Master" mode.

About your half-screen, is the LCD bad, or maybe you just lost a lamp? On my Mac Studio Display, it went half-dark, and the problem was the inverter board for the lamps. I put in a new inverter, and it was all good.

EDIT: Checked the specs on that card, it can operate in "infrastructure" mode, which is the same as master mode, so you should be able to set it up as an access point.

---

### Post by shuoink on 2008-03-28
I think the LCD is fine because if I connect an external monitor to the vga port, I can't get any display on that at all.

I saw the infrastructure mode and wasn't sure what that was. It's good to know that it is the same as master mode. Thanks!

... now I just gotta figure out how to do it. I'll read the document you posted and see if that works for me. I've been googling this for days and have not seen the document you listed so I hope it works.

---

### Post by shuoink on 2008-03-28
OK, so I got as far as step 4.5 and this is the output I get when restarting networking:

```
spudly@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 10451
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:d3:af:0e:83
Sending on   LPF/eth0/00:13:d3:af:0e:83
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.213.1 port 67
RTNETLINK answers: No such process
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:d3:af:0e:83
Sending on   LPF/eth0/00:13:d3:af:0e:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.213.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.213.1
bound to 192.168.213.199 -- renewal in 1464 seconds.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
                                                                         [ OK ]

```

Despite the errors in the output above, I went ahead and tried to connect to the new access point using my other laptop. It doesn't show up on my list of available networks so I chose "connect to other wireless network." I entered the name and chose "None" for wireless security (because I did not configure a WEP key). Upon connecting it said I needed to put in a password. Since I didn't setup a password, I'm not sure what password it needs. 

Any hints?

Incidentally, if I did configure a WEP key ( i would like to but did not for initial simplicity), what type of key is it? The choices i have when connecting are:
WEP 128-bit passphrase
WEP 64-bit/128-bit hex
WEP 64-bit/128-bit ascii

Also, how will I configure DHCP and DNS? It seems that part of the wiki is not written yet.

---

### Post by dstew on 2008-03-29
Going back to the start, you do have the required DSL connection through a wire to a DSL mode, and you have a wireless adapter that is working, correct? Post the output of```
ifconfig
iwconfig
```
It looks like eth0 (presumably your wired connection to the DSL modem) is OK, but wlan0 is not defined. I see another interface in your output wmaster0 that is apparently not supported by a driver.

As far as the WEP key, the document has code to generate a 128-bit hex key.

Also, post the output of```
cat /etc/network/interfaces
```

---

### Post by shuoink on 2008-03-29
Here's the info you requested. I actually think the problem is that my wireless card supports master mode, but the driver I am using does not.

when i run "sudo iwconfig wlan0 mode master", i get the following error:
```
Error for wireless request "Set Mode" (8B06) :
   SET failed on device wlan0 ; Invalid argument.
```
and the mode of wlan0 stays at "managed"

I am using a wireless card with the RT2500 chipset. I found two solutions to this, both of which I haven't been able to figure out.
#1 Asus has a driver for their WL-107g card that supports RT2500 chipset cards in master mode
#2 There's a Rt2x00 project that supports legacy drivers for RT2500 (without master mode) and if you get the latest branch from GIT and apply a patch (which i can't find) and then compile it yourself, you can get it working in master mode.

Both of the solutions require you to compile the code yourself and neither have a clear set of instructions that I could find. (Actually the first has instructions but they appear to be flawed).

Anyway here's the output from ifconfig, iwconfig and /etc/network/interfaces

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:D3:AF:0E:83  
          inet addr:192.168.213.199  Bcast:192.168.213.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:feaf:e83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62946496 errors:352 dropped:0 overruns:0 frame:0
          TX packets:62874031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:176179 txqueuelen:1000 
          RX bytes:733025479 (699.0 MB)  TX bytes:3424085230 (3.1 GB)
          Interrupt:20 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1608 (1.5 KB)  TX bytes:1608 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:74:26:BB  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-74-26-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"shuoink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/network/interfaces:
```
# Set up the local loopback interface 
auto lo
iface lo inet loopback

# Set up the external interface
auto eth0
iface eth0 inet dhcp

# Set up the internal wireless network
auto wlan0
iface wlan0 inet static
    wireless-mode master
    wireless-essid shuoink
    wireless-channel 1
    wireless-key d376f9f6b193d57f10cb1fefa4
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255

```

---

### Post by dstew on 2008-03-30
Yes, I think you are right that the driver is not setting the mode to master. It is possible that you need to capitalize Master, which is the way it is in the iwconfig man page, but I am not sure. Slim chance, but worth a try. But otherwise, if you are right, you will have to hunt for a driver that can set that mode. And, since what you are doing is unusual, it will be hard to find on-line examples. But, you seem to have the spirit of experimentation, so good luck, and post back on what you find out.

---

### Post by shuoink on 2008-04-01
I've given up on using ubuntu for this for now. I managed to get XP installed on the laptop (not easy, trust me) and the wireless card's bundled software had an option that automatically set it up for Access Point mode. Once XP was installed, I had the access point up and running within 10 mins.

I love ubuntu, but I really with manufacturers would develop fully-functional drivers for it. Hopefully in the near future these manufacturers will catch that vision so I don't have to waste my time attempting the nearly-impossible.

Don't worry, I still use ubuntu on my normal laptop.

My advice to anyone attempting this a RT2500 chipset is to give it up, because it's not going to work unless you can find and install some drivers that supports master mode.

---

### Post by kevdog on 2008-04-01
What drivers are you using for your rt2500 card?  The built in drivers or the serial monkey drivers?  I thought the serial monkey drivers supported master mode but I'm not certain.  Perhaps checking out the serial monkey website will give more info:


Correction only the newer version of the drivers the rt2x00 support master mode.  These drivers are part of hardy's kernel.  So you might want to update to hardy's developing kernel, or just install the beta hardy installation.
[http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS](http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS)

---

### Post by shuoink on 2008-04-02
kevdog - You're right, the RT2x00 drivers do support master mode, but only if:
1. You download the entire source code using GIT
2. You apply a patch written by some guy (all the links I found to the patch returned 404 errors by the way)
3. You compile it yourself

The documentation on the website is extremely lacking, so I personally was not able to figure it out. They expect you to use the forum, but every thread I found that looked like it might be helpful ended with someone telling the thread starter that they should keep searching the forum because the question was already answered. I never found the answer to any of my questions in the forum.

Before I got XP installed, I still had the default drivers that came with gutsy.

If it works in hardy, then I'm glad. With my dead video card situation, I'm not about to change a working system.

---

### Post by shuoink on 2008-04-02
Oh and just a quick note. the RT2x00 legacy drivers that come precompiled for you, do NOT support master mode.

---

