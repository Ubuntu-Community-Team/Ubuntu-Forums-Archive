---
title: "Help Stuck Atheros 5006 EGS Problems  NOOB"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-03-15
So i've been trying to figure out this thing all day, gone through as many posts as i can find and I am still stuck...but have made progress...kinda.  At first i couldn't get anything to even show up in Network Manager, but now at least the wireless card is there so i fee like i am making progress

Here is the lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)


Here is the iwconfig:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:16:E6:3D:01:41   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Also, under the properties..I am not totally sure what to put under the "ESSID" ...my router name?

Running 6.10 Edgy with the restricted generic kernal

Please help!

---

### Post by SactoBob on 2007-03-15
You look like you should be up and running to me.  Do you have a connection to your router?  Have you tried internet?

After having recently done this, I like the easy solution of using the network-manager-gnome applet from the repository.  After you install it and reboot, you have a signal bar at the top of the screen.  If you click it, the program shoes available networks and walks you through connection much like that other OS would.

---

### Post by ssc351 on 2007-03-15
No I do not have a connection to the router and no i can't get on the internet.  I do have network-gnome installed through synaptic but I don't get any "bars" up by where they should be.  Am i missing something?

---

### Post by ssc351 on 2007-03-15
bump

---

### Post by SactoBob on 2007-03-15
If you have network-**manager**-gnome (you said network-gnome) installed, then you should have an icon at the upper right of your screen in 6.10 where you can manage your connections.

Also, with your Atheros chip, have you enabled all repositories in Synaptic, and do you show a restricted modules package with the madwifi drivers installed?

---

### Post by ssc351 on 2007-03-15
Yes I do have network-manager-gnome  installed and yes the madwifi does show up under the restricted modules 2.6.17-11-generic.

I still do not have the bars showing up with the network manager gnome...maybe that is my problem?  How do I know if all the repositories are there/installed/enabled?  What am I looking for?

---

### Post by ssc351 on 2007-03-16
help!

---

### Post by ssc351 on 2007-03-16
quick update, not sure if this helps or not..but when I hit alt-f2 to open up apps, network manager and network-manager-gnome DO NOT appear. Not sure if this means anything.

---

### Post by sstakes1 on 2007-03-16
There are somethings you must do to get NetworkManager to work. Try this excellent [[COLOR="DarkRed"]howto[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=341357&highlight=3945+wireless") It primarily involves delegating all control to network interface management to the network manager.

HTH

---

### Post by SactoBob on 2007-03-17
Is this a usb wireless card?   It looks like these are not yet supported with madwifi?
[http://doc.gwos.org/index.php/MadwifiDriver](http://doc.gwos.org/index.php/MadwifiDriver)

Wireless can be a headache - one that can repeat when you upgrade.
I go with a wireless bridge to get rid of all the headaches.  For $60, the bridge takes care of all the wireless chores and provides you with 4 standard ethernet outlets.

As far as your computer knows, it is connected to a wire.  [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)
But it is not a real portable solution of you are on the go a lot.  I use an Atheros with madwifi for that.

---

### Post by godvalve on 2007-03-17
Hey guy....
   I'm banging my head against this same problem at the moment. dmesg on my machine returns:

:~$ dmesg 
....
[17179590.956000] wifi%: unable to attach hardware: 'Hardware revision not supported' (Hal status 13)
....


I just bought this laptop and I'm thinking that our Atheros cards aren't supported by the 2.6.11.17 restricted-modules.

Anyone have thoughts on this?:confused:

---

### Post by SactoBob on 2007-03-17
Yes, that error message seems pretty clear - the card is not supported by madwifi.
HAL is the "Hardware Abstraction Level".
It's a long story, but the HAL is non-open-source object module that was put in there because of FCC requirements that certain parameters of the wireless chip could not be user modified.  That ensures that the chip cannot be operated outside of FCC regulations for things like power, channel etc.

Anyhow, that is not really relevant to you.  What is relevant is that your card is not supported by the HAL, so you are out of luck with madwifi.  You could try the ndiswrapper method.

In my own long story of trying to get wireless working in Linux, I have become a big fan of wireless bridges.  For $60 you can get four wired outlets with a wireless bridge, and it it works great and is very handy.  [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)

It gives you the luxury of having a surefire connection that will work from your wireless with Linux, and the luxury of time to get your original card working since you now have a connection.

---

### Post by godvalve on 2007-03-17
Sweet!

Thx for the tip.  :popcorn:

---

### Post by ssc351 on 2007-03-17
THats really annoying...oh well...will it be fixing/changed with Fiesty?  Are there any Atheros cards that are Mini PCI Express that work with Edgy?  

Anyone recommended a certain card instead of an Atheros?

---

### Post by SactoBob on 2007-03-17
You can check with [www.netgate.com](www.netgate.com).  The local Linux User Group referred me there.  They understand open source and will talk to you if you call.  They have a bunch of cards that work (I am using one now).  If you get one, make sure that it supports WPA if that is important to you.  Some of their cards do not.

Think of it this way - you are saving a lot with a free and superior OS.

If you don't need high portability, you get better performance and avoid drivers entirely with something like the Buffalo Ethernet Connector, which works great and is available for $60 from Newegg.  Check out this link.

[http://www.linuxquestions.org/questions/showthread.php?t=536898](http://www.linuxquestions.org/questions/showthread.php?t=536898)

Bob

---

### Post by ssc351 on 2007-03-26
Ok I am convinced this thing has got to work...It looks like the thing should be working but who knows....again here is the lspci:

dell640m@dell640m-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)


Is that bottom line a problem with the Atheros..."unknown device"?

Here is the iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:16:E6:3D:01:41   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:90  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Here is the ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          inet6 addr: fe80::216:e6ff:fe3d:141/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:13138 (12.8 KiB)

ath0:avah Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          inet addr:169.254.3.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:15:C5:6F:27:4C  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6f:274c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13097558 (12.4 MiB)  TX bytes:657906 (642.4 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1824 (1.7 KiB)  TX bytes:1824 (1.7 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E6-3D-01-41-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:2030
          TX packets:503 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:31016 (30.2 KiB)  TX bytes:39858 (38.9 KiB)
          Interrupt:17 


I think I am using Network Manager correctly. I simply left click on the icon and go to create new wireless network, then type in "linksys" for the name of my router, correct?  My router is set-up as "linksys" without any encryption.  I cannot connect to it nor get on the internet, obviously.  

Any help!!!!! I am so frustrated!!!

---

### Post by j0sh0 on 2007-03-27
Hi,
I rekcon if you've got ath0 appearing in iwconfig and ifconfig then you're already half way there! You're one of the luck ones!

Try this from the command line:

sudo ifconfig wifi0 down
sudo iwconfig ath0 essid [your wireless ssid] channel [router's channel] key [your WEP key]
sudo iwpriv ath0 authmode 2

you need to make sure the channel your router is broadcasting on matches the channel (frequency) iwconfig is set for. Check the router's setup page for this.
Also, with atheros-based cards (the one I've had success with, anyway), you need to ensure authmode is set to 2 (for a restriced/shared network, anyhow)

Let me know how you go!

---

### Post by ssc351 on 2007-03-27
Still not working...do I need to go back into network manager and type in all the info again?  Also, before i followed the last post, none of the wireless configurations would save. Meaning I would need to retype them in every time.  Not sure if that means anything... Here is everything with the changes:

dell640m@dell640m-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
dell640m@dell640m-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:4031 (3.9 KiB)

ath0:avah Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          inet addr:169.254.3.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:15:C5:6F:27:4C  
          inet addr:192.168.1.116  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6f:274c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:383579 (374.5 KiB)  TX bytes:50321 (49.1 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E6-3D-01-41-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:7670
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5539 (5.4 KiB)  TX bytes:15647 (15.2 KiB)
          Interrupt:17 

dell640m@dell640m-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:16:E6:3D:01:41   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:21  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ssc351 on 2007-03-27
sorry that last one was after a restart...here it is without a restart:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SAMAX"  Nickname:""
          Mode:Master  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:46  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dell640m@dell640m-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
dell640m@dell640m-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:4031 (3.9 KiB)

ath0:avah Link encap:Ethernet  HWaddr 00:16:E6:3D:01:41  
          inet addr:169.254.3.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:15:C5:6F:27:4C  
          inet addr:192.168.1.116  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6f:274c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1315989 (1.2 MiB)  TX bytes:255612 (249.6 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by ssc351 on 2007-03-27
bump

---

### Post by SactoBob on 2007-03-27
Did you check madwifi.org?
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Somebody reports success with a more recent version of HAL, but failure with the earlier version.
just search that page or "egs" and you will see the entry.  {Edit 3/28/07- Sorry, this page has now changed, and you can only search now by manufacturer} 


I don't know what version of HAL is shipped with Ubuntu, or resides in the repositories, but somebody reports success with madwifi using this chip.

BTW, you can eliminate some of that extraneous info on lspci by piping to grep
lspci | grep Atheros

---

### Post by j0sh0 on 2007-03-28
sc351,
I've not had any experience with gnome_network_manager, only using the terminal/command line. I don't think you've got HAL issues, however the appropriate output from dmesg would tell you this. 
Have you had your wireless working before, like in windows or anything? You really need to make sure your iwconfig settings match your router settings (what encryption are you using, if any?)?

---

### Post by SactoBob on 2007-03-28
> I don't think you've got HAL issues, however the appropriate output from dmesg would tell you this. 

Did I miss something?  I didn't see the OP say anything about dmesg.  I did see Godvalve report a dmesg error concerning HAL with the same chip:

> [17179590.956000] wifi%: unable to attach hardware: 'Hardware revision not supported' (Hal status 13)

Unfortunately, the madwifi link I reported above takes you to a "new and improved" page where the devices are broken down by manufacturer, so you can no longer just search for the chip - sorry.  But the report I saw on the old "big" compatibility page said that that the OS was unable recognize a card with the same chip before the latest HAL update, and that the HAL version that came with his recent version of Linux did not work, which sounds sort of what like Godvalve reported, and may relate to the message that the OP gets out of lspci.
> 
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

It would at least be worth looking at the compatibility charts at madwifi IMO, and making sure you have the very latest version of HAL.  That chip is reported to work with madwifi, but only with the latest version of HAL.

---

### Post by ssc351 on 2007-03-28
To answer a couple of questions...yes it does work in windows and yes i did check the madwifi website and it is compatible...this card is actually labeled as a gigabyte GN-W10GT.

Should I try to reinstall the madwifi driver?

Should I uninstall everything with the wireless card and start over?

I have no idea how to do either so someone would have to walk me through step by step.

---

### Post by SactoBob on 2007-03-28
Here is what the compatibility page has to say about your gigabyte GN-W10GT card:

> Chipset:	I believe AR5005GS, XR, 108Mbps,a/b/g
Interface:	Mini PCI Express
Notes:	Works great with Network-Manager in Ubuntu with latest MadWifi snapshot
Notes:	Is this actually a WI01GT? If so it should be AR5006EGS, XR, 108Mbps, b/g
Notes:	Works from HAL version 0.9.18 onward. **This card was not detected with HAL 0.9.17.2** (which happens to be the version found in madwifi-ng-0.9.2.1 in Gentoo portage as of Feb. '07). Gentoo users should install from the tarball provided here until portage is updated.
September/October 2006

Unless this entry is wrong, your card should "just work" if you have HAL 9.18 or greater.  When you boot up, it should be active.  Have you installed the latest version of madwifi and HAL?

If you have installed a current version, and your card is not working, you should report it to madwifi.org.  The line from lspci which states that the Atheros is an unknown device indicates that you have not installed a current version of HAL as per above, or else the entry in madwifi compatibility list is wrong.

---

### Post by ssc351 on 2007-03-28
I downloaded and installed the latest HAL version...but I have no idea what I may have done or screwed up before that when i was messing around.  Can I uninstall whatever I have on there now and start over with the latest HAL?  

If that is what I need to do, can someone walk me through the whole process so i don't get screwed up worse that I already am.

If I do it correctly and its still a problem I will let madwifi know...but at this point I am not conifident to say its a bug and not a "user error" :)

---

### Post by ssc351 on 2007-03-29
bump

---

### Post by ssc351 on 2007-03-29
So I followed this page: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)  and I used 0.9.3 so it "should work" so either I have a bug or I am screwing something up but the outputs are still the same.  Also, if it is a bug, how do I report it?

---

### Post by SactoBob on 2007-03-29
Did each step of the HowTo yield the expected results?

Did you check [http://madwifi.org/wiki/UserDocs/Troubleshooting](http://madwifi.org/wiki/UserDocs/Troubleshooting) to troubleshoot the problem?
Did you confirm that you successfully installed the new version? (the way to check the version is on that troubleshooting page)  My suspicion is that you did not successfully install the new version if lspci | grep Atheros still reports an unknown device.  If madwifi does not recognize your Atheros card, there is not much point proceeding beyond that point.

It is hard to say much when you report that it doesn't work without specifics except that your outputs are the same.  If you made an error, it will be hard to say where without the results of each step in that fairly long First Time Howto.

Since the card is reported to work with madwifi, I would doubt that there is a bug, but maybe.  It would seem more likely that you made an error, or that there is something unusual about your equipment that is causing the problem.

You might try posting at linuxquestions.org since 2Gnu there, who hangs out in the Wireless Networking sub-forum, is a real expert with Atheros chipset cards.  I am just a guy that got his Atheros card working very easily.  Atheros cards are reputed to be the easiest to set up in Linux, which is why I bought mine, but 2Gnu would probably be able to help.

BTW, if you are tired of this hassle, it is not hard to buy a wireless solution.  But I admire your determination, and the Atheros card should work.

---

### Post by SactoBob on 2007-03-30
Somebody else was having a problem with the new Atheros chip, and was kindly referred to a "howto" by one of our folks using Ubuntu.
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

---

### Post by ssc351 on 2007-03-31
Bob,

I tried going through that How to:

I can't install the restricted module 2.6.17-11-386, i get an error in synaptic reading, "linux-restricted-modules-2.6.17-10-386:
 Depends: linux-image-2.6.17-10-386  but it is not installable"  I assume it is because I have a 686 kernal (2.6.20-13-generic)?

Should I try using the using the same version number but for x86_64 generic?

Also, I did try just using the restricted module version number 2.6.20..13.10 and then following the how to but I get the same result.

Any ideas?  By the way, thanks for all the help.

---

### Post by ssc351 on 2007-04-01
Update here is what happened when I looked up the version( cat /proc/net/wireless)

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 21
  ath0: 0004    0.  161.  161.      33      0      0      0      0        0


What does status 0004 mean?

---

### Post by ssc351 on 2007-04-02
another thing to add...when i do a iwlist scan i get:

ath0 no scan results....


so I don't get an error...its like fiesty is seeing the card and everything is working but it can't find the networks ...am I screwing something else up somewhere else?

Can someone please help me finish this!

---

### Post by godvalve on 2007-04-02
> **SactoBob said:**
> Somebody else was having a problem with the new Atheros chip, and was kindly referred to a "howto" by one of our folks using Ubuntu.
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)


Wow! Thx for the heads-up on this howto!  [-o<


Alas... it didn't work for me.

---

### Post by ssc351 on 2007-04-03
Ok after doing a little more looking around, I found on the madwifi site that some pci express cards you need to cover up the Rf kill pin.  Which is pin 13.  The symptons sound the same on my adapter so I tried putting in all the rf kill lines but that didn't solve it.  So next it must be the pin itself.  however, this is a mini pci express card.  Is it the same pin?  Do I need to cover up more than one?  Anyone??? Anyone???

---

### Post by ssc351 on 2007-04-04
Alright come on guys, i can't believe I am the only one with this problem.  I am getting really frustrated and I'm almost to the point where I am just going to buy another wireless card, but this one works really well with windows so i assume once it does work with linux it will be great.  

I am pretty sure after all the reading and forums, everything is installed correctly.  Like I said in a previous post, the wireless led is not on.  I added the rfkill=0 line in but it still will not turn on.

HELP!

---

### Post by ssc351 on 2007-04-05
Alright! Finally fixed here is the link I followed to it...for anyone else...

you have to use ndiswrapper with this card, not madwifi!

[http://ubuntuforums.org/showthread.php?t=394581&highlight=net5211](http://ubuntuforums.org/showthread.php?t=394581&highlight=net5211)

---

### Post by godvalve on 2007-04-12
Wow! Feisty Fawn (7.4 Beta) takes care of all these issues instantly. Everything works on install. I have network support out of the box.

---

### Post by specv on 2007-04-13
> **ssc351 said:**
> Alright! Finally fixed here is the link I followed to it...for anyone else...

you have to use ndiswrapper with this card, not madwifi!

[http://ubuntuforums.org/showthread.php?t=394581&highlight=net5211](http://ubuntuforums.org/showthread.php?t=394581&highlight=net5211)

the only problem with ndiswrapper you will lost master mode. I intended to do pen testing and this card seemed like the best choice

---

