---
title: "[SOLVED] Need help installing ndiswrapper and setting up network"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by rednano12 on 2008-12-14
Installed ubuntu today. Dual booting with winXP. This message is being sent from the winXP partition. I heard that ndiswrapper was the only way to install my network card as it does not have Linux drivers. :( I have a Airlink PCI Adapter #AWLH3028. I got a fatal error thing and don't know how to download the source. Tortoise SVN isn't working for me. I set up fstab to be able to browse the windows partition from ubuntu. 

Please help me!

---

### Post by squeabs on 2008-12-14
In the repositories (Applications-Add/Remove) search for "ndis". Make sure all available software is selected. Once you check that, it should download and install a graphical interface for connecting to wireless networks.
Once it installs, you should be able to fire it up. You'll also need to get the driver for your wireless card. The best place to find that is the manufacturer's website. Then you may need to install "wine" via the same Add/Remove process. Some wireless card drivers come as a .exe file. Once wine is installed, the driver software should run in wine.
What I did (may not work for everyone) is, once the driver software installs, grab the actual driver file (the .inf or .ini) or such and copy/paste it to the ubuntu desktop. Then run ndis. When it asks for a driver file, simply point it to the desktop file you just pasted. After that installs, you should be set for wireless.
That how I got it working anyway.

---

### Post by rednano12 on 2008-12-15
I did that, but I could not connect to the network. My driver is an inf file. I set ndiswrapper gui to find my file. I did that, but I do not know how to search for wireless networks from here. I tried doing it from terminal, and got some fatal error. Searching in the wiki told me that I needed to compile from source which I have no idea how to do. Please help!

---

### Post by squeabs on 2008-12-15
Go to System-Admin-Network. A Network Settings window should pop up. From there, you want to "unlock" via the button at the bottom right. Doing that will allow you to administer the network settings.
Select wireless networks, then properties. As of now, roaming is enabled. To input the information yourself, click to disable roaming mode. Now all that's left is to input your wireless settings and hopefully it will connect for you once this is done.
I've included some screenshots for a visual. Good luck.
EDIT: You'll need to know what type of security your wireless networks has (WEP, WPA, etc.)

---

### Post by Michael.Godawski on 2008-12-15
hi rednano12, 

let's have a closer look at your current network status (see if ndiswrapper set up correctly)

Open up the terminal 
applications > accessories > terminal
and run these commands
```
sudo lshw -C network
iwconfig
```

Post the output here if possible.

What squeabs suggests is correct.:p Report back when you hit the wall.

---

### Post by rednano12 on 2008-12-15
Thank you very much! Going to go try the new suggestions! :guitar:

Here are the outputs
 *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:10:18:07:1b:b9
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:2
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 02
       serial: 00:07:e9:6a:de:43
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:10:18:07:1b:b9
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:2
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 02
       serial: 00:07:e9:6a:de:43
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

I think that I did something wrong. :(

---

### Post by squeabs on 2008-12-15
On your last posted screenshot, did you try clicking the "unlock" button? After you do that, you should be able to select the wired network selection. Then you can disable roaming mode and input your own network data.

---

### Post by rednano12 on 2008-12-16
But I need a wireless connection! If I unlock, there are no options for wireless.

---

### Post by squeabs on 2008-12-16
Okay, I see what you mean. That's a little odd. I don't know if it'll help, but maybe you installed the wrong driver. When you installed it via ndis, did it say "hardware present"? If not, I believe this is your wireless card copied from your terminal output: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller. If you type that in google, putting "driver" at the end of it, you may get your correct driver. 
I wish I could provide more help, but I'm fairly new to ubuntu myself.
Also, if you right click the two computers on the top panel, is "wireless enabled" checked?

---

### Post by starcannon on 2008-12-16
Try ndiswrapper again, it seems that googling that wifi card brought back a lot of people with trouble, the solution was almost always ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by rednano12 on 2008-12-17
I did some searching too... I found a modified driver and instructions to only use the Win98 drivers. Neither worked. :(

---

### Post by squeabs on 2008-12-19
This thread might be helpful.
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by rednano12 on 2008-12-26
[SOLVED]

Thank you all for your help. I solved the problem by upgrading to 8.10. WiFi works, but I have a new problem which will be posted in a new thread.

Thanks again!

EDIT: How do I change the thread title? How do I lock the thread?

---

