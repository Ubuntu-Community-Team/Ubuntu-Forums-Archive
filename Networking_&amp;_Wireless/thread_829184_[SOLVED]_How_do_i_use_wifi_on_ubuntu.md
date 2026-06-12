---
title: "[SOLVED] How do i use wifi on ubuntu?"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by dirtydaman on 2008-06-14
I just got ubuntu and i think i might have made a mistake by doing so sadly :( my wifi isnt working i tried going to network setting but there is no option to search for available networks i dont know how to use manual so please help i dont have any internet for the laptop i installed ubuntu on. I tried using manual but it didnt work and the network icon disappeared from the top right of the desktop. And i have ubuntu version 8.04

---

### Post by ZootHornRollo on 2008-06-14
have you checked that your wifi device is compatible with linux?

if found this website useful when building my pc [http://www.linux-drivers.org/](http://www.linux-drivers.org/)

you could try searching your make/model of card on the ubuntu forum and see if anyone has had problems/success in getting it to work.

---

### Post by dirtydaman on 2008-06-14
> **ZootHornRollo said:**
> have you checked that your wifi device is compatible with linux?

if found this website useful when building my pc [http://www.linux-drivers.org/](http://www.linux-drivers.org/)

you could try searching your make/model of card on the ubuntu forum and see if anyone has had problems/success in getting it to work.

Can yo please do it for me? I don't understand anything about the website. Thanks.

My model/make is Linksys Router. Thanks for your help.

---

### Post by issih on 2008-06-14
Your router is irrelevant.

We need to know what hardware your computer uses

Open a terminal on the laptop ("Applications->Accessories->Terminal)

Then enter:
```
sudo lshw -C network
```

Then post the output here, that should tell us what hardware your laptop uses.

Next enter:

```
ifconfig -a
```

and post the result here.

Finally, could you tell me if you have a an option for "enable wireless" present in the right click menu of the networking icon sitting in the notification area.

if the icon is still missing, it will probably come back by restarting X (ctrl+alt+backspace) or you can run nm-applet in a terminal.

---

### Post by dirtydaman on 2008-06-14
Open a terminal on the laptop ("Applications->Accessories->Terminal)

Then enter:
```
sudo lshw -C network
```

 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:f6:89:d0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:74:98:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Next enter:

```
ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:f6:89:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92100 (89.9 KB)  TX bytes:92100 (89.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:74:98:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-74-98-E9-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Tomatz on 2008-06-14
Have you tried a simple **left click** on the network icon in the systray (top right).

I thought the broadcom BCM4318 worked out of the box. I may be wrong?

---

### Post by Tomatz on 2008-06-14
This thread should get you up and running:

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)


Just remember that when you buy a laptop, the manufactures install the drivers for your hardware. This is not a problem with Linux rather the problem is with the lack of support for Linux coming from hardware vendors. ;)

---

### Post by dirtydaman on 2008-06-14
> **Tomatz said:**
> Have you tried a simple **left click** on the network icon in the systray (top right).

I thought the broadcom BCM4318 worked out of the box. I may be wrong?

I already tried that.. but thanks for helping..

---

### Post by Tomatz on 2008-06-14
Check out the link i posted above. There is a howto that will get your wilan (wireless adaptor) working.

---

### Post by dirtydaman on 2008-06-14
I have version 8.04 not 6.06... I'm confused:confused:

---

### Post by Tomatz on 2008-06-14
> **dirtydaman said:**
> I have version 8.04 not 6.06... I'm confused:confused:

It should still work, all the requirements are the same ;)


Go for it.

---

### Post by dirtydaman on 2008-06-14
the steps are too confusing and besides how am i supposed to download the drivers without internet ? omg ubuntu is being a pain in the as*

---

### Post by Tomatz on 2008-06-14
> **dirtydaman said:**
> the steps are too confusing and besides how am i supposed to download the drivers without internet ? omg ubuntu is being a pain in the as*

You will need to use an ethernet cable.

For almost any piece of hardware you will need a driver weather on windows. *NIX, OSX etc. Don't rant it will get us nowhere ;)

Connect your laptop via ethernet and follow the steps.

If you get any problems just PM me.

---

### Post by dirtydaman on 2008-06-14
srry i just got really pissed and mad cuz my friend told me this was supposed to be amazing but i cant even get on the internet even with ethernet thats the problem i cant get on the internet any way possible with that laptop :(

---

### Post by dirtydaman on 2008-06-14
can u like tell me ur AIM or something so u can help me step by step please cuz that would be great :D

---

### Post by Tomatz on 2008-06-15
[COLOR="Lime"][/COLOR]> **dirtydaman said:**
> can u like tell me ur AIM or something so u can help me step by step please cuz that would be great :D

Nah its fine ;)

Ubuntu autodetects 90% of hardware but some (due to lack of manifacturer support etc), you will need to tinker with to get it to work.

**[COLOR="#00ff00"]Step 1[/COLOR]**

**R click** on the following links and **"save as"**

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) 

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

[B]
[COLOR="#00ff00"]Step 2[/COLOR][/B]

**R click** and **save as**, the following links:

[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip) *[COLOR="Red"](unzip this when downloaded)[/COLOR]*

[http://www.fjall.org/d505/wlan/bcmwl5.inf](http://www.fjall.org/d505/wlan/bcmwl5.inf)
[B]
[COLOR="#00ff00"]Step 3[/COLOR][/B]

_Put ALL the files you downloaded onto a flash drive_

**[COLOR="#00ff00"]Step 4[/COLOR] **

Now go to your ubuntu box, switch it on (if needed) and put the flash drive in the usb port. Then copy all the files from the flash drive onto the desktop.

**[COLOR="#00ff00"]Step 5[/COLOR]**

Double click the **ndiswrapper-common** file that should be on your desktop and install it. Then do the same with the **ndiswrapper-utils** file. 

**[COLOR="#00ff00"]Step 6[/COLOR]**

Now open a **terminal** *(applications, accesories)* and copy and paste the following:

```
sudo gedit /etc/modprobe.d/blacklist
```

Press enter and a text (config) file will open.** Scroll to the bottom of the file and type:**

```
blacklist bcm43xx
```

**Save** the file then **reboot**
[B]
[COLOR="#00ff00"]Step 7[/COLOR][/B]

Once your box has rebooted, open a terminal and type:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

Then in the same terminal type:

```
sudo ndiswrapper -m
```

**Now reboot** (again :P)
[B]
[COLOR="#00ff00"]Step 8[/COLOR][/B]
[B]
L click on the network icon in the systray to connect to wifi networks!!![/B]


Hope that fixes your problem :)

---

### Post by ugm6hr on 2008-06-15
@Tomatz:
Ubuntu 8.04 uses the b43-pci-bridge driver (see his lshw), not bcm43xx, so I suspect that would need to be blacklisted to.

However, the b43 driver is supposed to work - so it may be easier to use it than go down the ndiswrapper route.

@dirtydaman:
The simplest way to get wifi working would be to use System->Administration-> Hardware Drivers and enable the Broadcom firmware.
This should then work (possibly after a reboot).

However, to do this, you need to be connected with ethernet cable.  It would be worthwhile getting that working anyway.  It is unusual to be unable to use a cable ethernet (and yourLAN card is supported).

Try booting with the cable plugged into the router, and give output from:
```
ifconfig
route -n
```

---

### Post by rage-against-windows on 2008-06-15
Dont know if this is how its "spose" to work, but all I did was Install wifi-radar picked my connection out of the list of many in my area then hit connect and its worked ever since automatically. Oh yeah in the system/network settings under wireless settings I also found my connection after selecting it in wifi-radar and changed configuration to automatic config (dhcp). Works without fail every single day for the last 3 months.

---

### Post by Tomatz on 2008-06-15
> **ugm6hr said:**
> @Tomatz:
Ubuntu 8.04 uses the b43-pci-bridge driver (see his lshw), not bcm43xx, so I suspect that would need to be blacklisted to.

However, the b43 driver is supposed to work - so it may be easier to use it than go down the ndiswrapper route.

@dirtydaman:
The simplest way to get wifi working would be to use System->Administration-> Hardware Drivers and enable the Broadcom firmware.
This should then work (possibly after a reboot).

However, to do this, you need to be connected with ethernet cable.  It would be worthwhile getting that working anyway.  It is unusual to be unable to use a cable ethernet (and yourLAN card is supported).

Try booting with the cable plugged into the router, and give output from:
```
ifconfig
route -n
```


Ahhh i didn't consider that (but it says to blacklist in my howto) :)

Obviously if you can get your ethernet working that would be the easier/better option as it will automatically set up your wilan card.

If you cant then you could always fall back to my howto.

:popcorn: to ugm6hr for pointing that out.

---

### Post by dirtydaman on 2008-06-15
thanks for ur help guys but google helps all :D talking to u guys on wifi right now lol ;) now i just need to figure out how to get animation effects to work :confused: lol

---

### Post by Tomatz on 2008-06-16
> **dirtydaman said:**
> thanks for ur help guys but google helps all :D talking to u guys on wifi right now lol ;) now i just need to figure out how to get animation effects to work :confused: lol

Run the restricted drivers manager, Then reboot and in a terminal type:

```
sudo apt-get install compizconfig-settings-manager
```

Then in a terminal type:
```

ccsm
```


:)

---

