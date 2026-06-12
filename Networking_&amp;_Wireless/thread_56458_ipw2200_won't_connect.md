---
title: "ipw2200 won't connect"
date: 2005-08-12
forum: Networking &amp; Wireless
---

### Post by tehsyco on 2005-08-12
I just got the driver for my network card compiled (ipw2200) for my dell inspiron 6000. I think it's having an issue actually adding the .ko to my system to use it though. What can I type to add/make sure it's added? (Seems like modprobe is not working.)

Thanks,
Jordan

---

### Post by ape on 2005-08-12
`lsmod | grep ipw2200` should do the trick to show you if the module is in fact loaded. You can also cat /proc/modules and grep for ipw2200 if you need to.

---

### Post by luca_linux on 2005-08-12
You'd better update the driver. Just follow this HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by tehsyco on 2005-08-12
This is what came up:

ipw2200 - 159368 - 0
firmware_class - 9728 - 1 ipw2200
ieee80211 - 26596 - 1 ipw2200
ieee80211_crypt - 5960 - 2 ipw2200,ieee80211

If this is the case and it IS loaded, any idea why it won't connect? When I do sudo dhclient eth1 I get this:

sit0: unknown hardware address type 776
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 with different intervals
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dmesg | grep ipw returns this:
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection


Any idea why it won't connect?

Thanks,
Jordan


EDIT: I forgot to mention my router is a 2wire Homeportal, I used to run freebsd with it and there were a few issues but it did work, so I'm not sure if that would affect this or not.

---

### Post by tehsyco on 2005-08-12
I switched my network thing to eth1 in the top-right corner (it was on eth0) and it looks to be sending/receiving but I'm still not online...

It says in the status box:

Status: Receiving (switches to idle every other second)

Activity:
Received: 318 Packets (121.6 Kb)
Sent: 35 packets (30.5 Kb)

Signal Strength: 88%

EDIT: On my homeportal, it's listing the computer as gateway.2wire.net (my localhost) but it's saying it's inactive.

---

### Post by tehsyco on 2005-08-12
I just got an error on dmesg grep ipw:

Firmware error detected. Restarting.

I'll try to install another version now.

---

### Post by tehsyco on 2005-08-12
I really don't understand this. The network is set up perfectly, it says its sending and receiving packets with practically no errors, but yet I'm STILL not connected.

EDIT: My homeportal says that it's connected, but yet something's not working...
      
   Ethernet: 1 Device(s) 
 
   Phoneline: 0 Device(s)  
 
   Wireless: 1 Device(s) 
 

Here's my iwconfig:

eth1 IEEE 802.11b ESSID:"DSLNetwork"
        Mode: Managed Frequency: 2.462 GHz Access Point: 00:0D:72:87:21:B9
        Bit Rate: 11 Mb/s Tx-Power=20 dBm
        RTS thr:off Fragment thr:off
        Encryption key:<key> Security mode:open
        Power Management: off
        Link Quality=58/100 Signal level=-64 dBm Noise level=-85 dBm
        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries:0 Invalid misc:2 Missed beacon:5

Here's ifconfig:

eth1 Link encap: Ethernet HWaddr 00:13:CE:23:8#:FD
        inet6 addr: fe80::213:ceff:fe23:83fd/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:721 errors:0 dropped:2 overruns:0 frame:0
        TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:81817 (79.8 KiB) TX bytes:44652 (43.6 KiB)
        Interrupt: 17 Base address:0x8000 Memory:dfdfd000-dfdfdfff

---

### Post by arthur_kalm on 2005-08-12
Hi everyone,

I am having a similar problem on my HP nc4200. Here is the information I can gather:

When I reboot and the Network Interfaces starts up I get the following message:

*ipw2200: failed to send WEP_KEY command*

lsmod | grep ipw2200 said:

[I]arthur@kubuntu:~/downloads$ lsmod | grep ipw2200
ipw2200               162568  0
firmware_class          9728  1 ipw2200
ieee80211              44548  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211[/I]

and dmesg said:

[I]arthur@kubuntu:~/downloads$ dmesg | grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: failed to send WEP_KEY command[/I]

Thank you for any help you can provide!

---

### Post by tehsyco on 2005-08-12
Now 'iwlist scan' says that eth0 doesn't support scanning. This is a nightmare.

Arthur, can you paste output from ifconfig/iwconfig?

---

### Post by arthur_kalm on 2005-08-14
[I]arthur@kubuntu:~/downloads$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0E:35:F3:4E:B3
          inet addr:192.168.128.7  Bcast:192.168.128.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:28 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14375 (14.0 KiB)  TX bytes:348 (348.0 b)
          Interrupt:21 Base address:0xa000 Memory:d0400000-d0400fff

arthur@kubuntu:~/downloads$ iwconfig eth0
eth0      IEEE 802.11b  ESSID:"NEBO"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:06:25:54:70:56
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:1[/I]


Remember I have the latest driver and fireware.

---

### Post by arthur_kalm on 2005-08-14
Wow, this is really bad...

I've installed SuSE and even though the Intel 2200 is suppose to work out of the box it does not! Ahhhh! And now sound and 3d acceleration don't work out of the box with SuSE (they did with Ubuntu). I have an HP nc4200. Man, linux is great for the desktop but getting it on this laptop has been a _pain in the ass_

 ](*,)  ](*,)  ](*,) 

If anyone has _any_ advice on how to get this bloody Intel 2200 card working it would be highly appreciated. I really don't want to have to use Windows on this laptop :( 

PS. I will be switching back to Ubuntu shortly.

---

### Post by drwoland on 2005-08-15
yah i think i have the exact same issue.

---

### Post by arthur_kalm on 2005-08-15
drwoland do you also have an HP nc4200?

I am considering going out and buying another wireless card that works better with linux. I'll post back if that works...

---

### Post by drwoland on 2005-08-15
[QUOTE=arthur_kalm]drwoland do you also have an HP nc4200?

I am considering going out and buying another wireless card that works better with linux. I'll post back if that works...[/QUOTE]

I'm on a brand new IBM T43 :\ I'm sure we'll figure it out eventually.

---

### Post by declain on 2005-09-07
I just picked up a Sony Vaio VGN-T150.  Got ubuntu loaded successfully, but the wireless won't connect.  I followed the how to and updated my drivers to the newest drivers.  Won't let me activate eth1.  

Anyone figure out how to get this working if the How To doesn't?

Thanks
Steve

---

### Post by mlomker on 2005-09-07
My ipw2200 did not work out of the box, either but I did get it working.  

You'll need build-essential and the headers for your running kernel.

In a terminal window:

```

su
apt-get install build-essential
apt-get install linux-headers-$(uname -r)

```

Then:

```

updatedb
locate ipw2200 | more
locate ieee80211 | more

```

Delete the files that these two search find.  **rm filename** to delete a file and **rm -fr /whatever/dir** to delete a *carefully* selected directory.  Run the process a second time to make sure that they are all gone.

Download [the driver](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download), [the firmware](http://ipw2200.sourceforge.net/firmware.php?i_agree_to_the_license=yes&f=ipw2200-fw-2.3.tgz), and the [ieee80211 drivers.](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.0.3.tgz?download) 

Untar the downloaded files.

```

tar zxvf filename

``` 

Install the ieee drivers first, then the ipw2200, and then copy the firmware files.  The process for the first two is to execute **make** in the directory and then **make install**.  

Copy the firmware files to the hotplug directory.
```

cp *.fw /usr/lib/hotplug/firmware

```

When you reboot it should all work, assuming you already have the ipw2200 listed in your /etc/modules file.

---

### Post by mlomker on 2005-09-07
[QUOTE=declain]Anyone figure out how to get this working if the How To doesn't?
[/QUOTE]

You need to be more specific.  What do you get from the following commands?

iwconfig
ifconfig
route -n
dmesg | grep ipw2200

---

### Post by declain on 2005-09-08
I'll remove all the drivers and try loading again and then I'll provide the info you requested.  

Thanks!
Steve

---

### Post by shimp999 on 2005-09-13
I have a Toshiba M45-355 which comes with a Marvell 10/100 ethernet built in and the Intell 2200BG wireless--both do not work out of box and the drivers are either nonexistant or not working.  Since I have no means of downloading anything on my laptop, where can I download the build-essential (not sure what all is included in this package) files and kernel headers manually so I can transfer them to my laptop via flash disk?

Thanks

---

### Post by declain on 2005-09-13
[QUOTE=shimp999]I have a Toshiba M45-355 which comes with a Marvell 10/100 ethernet built in and the Intell 2200BG wireless--both do not work out of box and the drivers are either nonexistant or not working.  Since I have no means of downloading anything on my laptop, where can I download the build-essential (not sure what all is included in this package) files and kernel headers manually so I can transfer them to my laptop via flash disk?

Thanks[/QUOTE]


Try: [http://www.apt-get.org/](http://www.apt-get.org/)

---

### Post by shimp999 on 2005-09-13
[QUOTE=declain]Try: [http://www.apt-get.org/](http://www.apt-get.org/)[/QUOTE]


Thanks...
But i'm trying to figure out where I can look up what exactly comes with "build-essential".  I think it includes gcc, make, but after that, I can't recall.  Also, i'm looking for where I can manually download the ubuntu deb files for whatever I need.

---

### Post by arthur_kalm on 2005-09-13
IT WORKS!!   :grin:  :grin: 

OK so here is how I did it. I installed everything from the howto: [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200)

Then I attempted to connect to the network at my university which gave out a WEP as a string. For some reason I wasn't getting an IP address. I finally decided to try the hex version of the string and it worked right away!

PS. Wrote this up on wireless  :grin:

---

### Post by FishFoot on 2005-09-18
[QUOTE=mlomker]You need to be more specific.  What do you get from the following commands?

iwconfig
ifconfig
route -n
dmesg | grep ipw2200[/QUOTE]


Hey mlonker,

You lead me to this thread from another place and I followed your guide here.  I'm still having the same problem though.  Everything looks like it is setup correctly but I can't get anything to work...

Here's the output from various utilities (and the ones you listed above). 

Can you think of anything else that might help?

I'm on the verge of a re-installation because I'm pretty sure that this sort-of worked out of the box.  I'd bet I've screwed something up but I'm not entirely sure what it is... I also don't know where to look for problems.

Anyway, here's that output

```

dmesg | grep ieee
-----------------
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, 1.0.3
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>


dmesg | grep ipw
-----------------
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

lspci
--------
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)


lsmod | grep ipw
--------
ipw2200               162568  0 
firmware_class          9728  1 ipw2200
ieee80211              44548  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211


iwconfig
--------------
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"beer"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig 
---------------
eth0      Link encap:Ethernet  HWaddr 00:03:25:1C:7B:D3  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe1c:7bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2123914 (2.0 MiB)  TX bytes:511903 (499.9 KiB)
          Interrupt:10 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:7B:CF:14  
          inet6 addr: fe80::20e:35ff:fe7b:cf14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:64070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5830 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x6000 Memory:e0200000-e0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:577980 (564.4 KiB)  TX bytes:577980 (564.4 KiB)

route -n
------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0




sudo ifup eth1
--------------------
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:7b:cf:14
Sending on   LPF/eth1/00:0e:35:7b:cf:14
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


``` 

Please note, I've checked the MAC addresses against the HWaddresses listed in ifconfig output and they do match.  eth1 is my wifi card (ipw2200).

Thanks
FishFoot

---

### Post by mlomker on 2005-09-18
> 
Please note, I've checked the MAC addresses against the HWaddresses listed in ifconfig output and they do match.

The tell-tale sign here is that iwconfig is showing itself as unassociated.  I bet that you have encryption enabled on your access point but something is misconfigured in your setup.

Try disabling encryption and make your access point 'open' as a test.

---

### Post by FishFoot on 2005-09-18
[QUOTE=mlomker]The tell-tale sign here is that iwconfig is showing itself as unassociated.  I bet that you have encryption enabled on your access point but something is misconfigured in your setup.

Try disabling encryption and make your access point 'open' as a test.[/QUOTE]

I can tell you for sure that I have no encryption on the router.  My other machine (also running Ubuntu) is connected to the network.  Its using a USB WiFi card (netgear wg111) with no encryption enabled.  No problems there.

GOOD NEWS THOUGH!!!

I changed the ssid, unchecked the "this device is configured" option and committed the changes.  I changed the ssid back, reconfigured the settings on the network settings gui tool and now the card is working!!!!  First I tried with the static IP, then with DHCP and it is working.  SWEET!!!

I'm not really sure what is different but... hell who cares!!!

I'm going to try the WEP route now.  I'll let you know how it goes.

Thanks for the help so far, I think the end MAY be in sight.  People like you make this thing happen

FishFoot.

---

### Post by FishFoot on 2005-09-18
[QUOTE=FishFoot]I can tell you for sure that I have no encryption on the router.  My other machine (also running Ubuntu) is connected to the network.  Its using a USB WiFi card (netgear wg111) with no encryption enabled.  No problems there.

GOOD NEWS THOUGH!!!

I changed the ssid, unchecked the "this device is configured" option and committed the changes.  I changed the ssid back, reconfigured the settings on the network settings gui tool and now the card is working!!!!  First I tried with the static IP, then with DHCP and it is working.  SWEET!!!

I'm not really sure what is different but... hell who cares!!!

I'm going to try the WEP route now.  I'll let you know how it goes.

Thanks for the help so far, I think the end MAY be in sight.  People like you make this thing happen

FishFoot.[/QUOTE]

I can't believe it... WEP Is working too.  This is so odd.  I swear I've done nothing different since when I posted that config output.  Well... I rebooted into windows at my parent's house and then I came home and booted in Ubuntu and... viola.

---

### Post by mlomker on 2005-09-18
[QUOTE=FishFoot] I rebooted into windows at my parent's house and then I came home and booted in Ubuntu and... viola.[/QUOTE]

I'm glad to hear it!  I had a few frustrations with my laptop when I first got it as well--sometimes the wireless button would be on and sometimes off for no apparent reason.  It stopped doing that after the first day.  Who knows sometimes.   :-?

---

### Post by FishFoot on 2005-09-19
[QUOTE=mlomker]I'm glad to hear it!  I had a few frustrations with my laptop when I first got it as well--sometimes the wireless button would be on and sometimes off for no apparent reason.  It stopped doing that after the first day.  Who knows sometimes.   :-?[/QUOTE]


Seriously!!!

I just got the WPA working on 2 different routers.  I'm pretty sure this is all working.  One point that wasn't clear to me:

wpa_supplicant needs to be running BEFORE you bring up your WiFi card.  I read that in [luca's post](http://ubuntuforums.org/showthread.php?t=26623) .  I wasn't sure how to use the Network Settings GUI to actually bring the card online.  You know, connect it to the network.  Well basically it needs to be treated as if it were an open network.  By that I mean, you don't need to configure the WEP key, just leave it blank.  Then if you need a static IP it can be setup right there.  I found that checking that static first makes clear that your troubles aren't DHCP related.  I'd try that before allowing DHCP to take over.

All in all not too bad.  It took time and presistance but its up and running now, so no looking back.... I hope.

mlomker, thank you for your patience and guidance.  I would have lost faith if not for your help.

Luca, thanks for the guide... if your eyes end up here. :-)

Thanks,
FishFoot

---

