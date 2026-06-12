---
title: "HOWTO: Get RTL8187B (ID: 8197) Working. Step by Step"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-05-12
[color=blue]There is now native support for this wireless card in the kernel 2.6.27 which is in Ubuntu 8.10[/color]

This driver is somewhat buggy. When running at 54MB/s it works fine for about 2-5 minutes and then connections start to time out.

To temporally fix this, put this command in your /etc/rc.local file.

```
gksu gedit /etc/rc.local
```
and put this **BEFORE** the exit 0,
```
iwconfig wlan0 rate 5.5M fixed
```

This will run at startup.
Having a bit rate of 5.5M will temporally fix the timeouts and quality. The errors may still occur but not as much.

___________________________________

**Ubuntu 8.04 & Ubuntu 7.10**

There are 2 ways of getting it to work. The native way or Ndiswrapper way.

**Native:**
Look here. It explains everything

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) 

(You want to download the Compact Wireless Old)


**Ndiswrapper:**

This is mainly for the ID of 8197 but can be used for all the RTL8187B. Checking 'lsusb' will give you the ID number of your wireless card.

**1. Install Ndiswrapper**
With no Internet:
First put in your Ubuntu CD when logged in.
Then go, System > Admin > Software Soruces > Tick the cd box at the bottom.
In Synpatic Package Manager (System > Admin >) and locate reload button. Press that, wait a bit. Will give errors saying cannot download etc, Don't worry about that. Then follow the With Internet' bit because your using your CD as 'The Internet'

With Internet:
Go to Add/Remove and search for Windows Wireless Drivers
Install it.
Thats Ndiswrapper Installed.


**2. Install the Driver**
Go to System > Administration > Windows Wireless Drivers > Install New Driver > Locate the driver > Install.
It should say:

Hardware Present: Yes

Now, in Network Manager, you should see wireless access points.

*If you cannot connect with WEP, remove Network Manager and Install Wifi-Radar

Hope this worked for you...and if you have any problems, please post in here.

Also, for a alternative way, check here: [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

Thanks,
Tom

---

### Post by icdelg on 2008-05-12
Heh...
I modified the win98 driver as you instructed but when i try to install it it still says hardware is not present.

Also, I checked out my /etc/rc.local file and all its says is:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

What am I doing wrong? :confused:

---

### Post by Tom--d on 2008-05-12
Can you please post the out come of:
```
lsusb
```
and
```
lspci
```

My /etc/rc.local file looks like: 
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig wlan1 up
dhclient -r wlan1
iwconfig wlan1 mode Managed
iwconfig wlan1 essid "router name"
iwconfig wlan1 key MY_WEP_KEY open
dhclient wlan1

exit 0
```

---

### Post by icdelg on 2008-05-12
lsusb

Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 

lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Tom--d on 2008-05-13
Sorry for a late reply, I went bed.

You have the same card as me. 

First thing you need to do is get the driver to recognize the wireless card.

Use this attached file (its the driver) and extract and use that.. see if that worked. :\

---

### Post by icdelg on 2008-05-13
No luck...

It doesn't make any sense. Do you think there could be a problem with my version of ndiswrapper or that the modified version of the RTL8187b driver I installed from this website [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/") is causing problems?

---

### Post by Tom--d on 2008-05-14
Yes... that might be it. As the modified driver is very buggy it might mess things up.

Uninstall it. I do not know how to do that so you might need to ask on the forums. 

After that, uninstall ndiswrapper, insatll it again and try again. 

As you have the same wireless card as me. It should be the same. It should work.

---

### Post by icdelg on 2008-05-14
I reinstalled hardy as well as ndiswrapper and still no luck. My rc.local file still looks the same too.

---

### Post by Tom--d on 2008-05-15
You shoudln't touch the rc.local file yet. That is needed when you have the wireless card working. 

I do not knon why it doing this :\
It works on mine and I have the same card as you.

I really don't know why :(

Email Realtek and ask for a driver for that ID. I got one but didn't work for me. (it is a windows driver made for ndiswrapper and for the ID of 8197) 

I would attach it but I do not have it anymore :(

---

### Post by icdelg on 2008-05-15
I'll email realtek for the drivers. I'll post again when I recieve and install them. Thanks for all the help anyway! :)

---

### Post by Tom--d on 2008-05-16
Thats ok :)

You will have to wait a week. (thats how long it took me :() 

If its possible, could you attach the driver from Realtek in a post?

Thanks,
Tom

---

### Post by Tom--d on 2008-06-07
I can confirm that no encryption and pass phrase works with network manager.

For me, I have WEP encryption. For some reason, it doesn't work properly.

---

### Post by Brown_ on 2008-06-13
Hi y'all.
When I saw that thread name i thought my problems with wireless driver's gone, but unfortunately it's wrong... Following that tutorial you made, I did the same you did, and we've got the same wireless card(rtl8187, id 8197).
Every things was going well till the part "net8187b
Hardware Present: Yes" after that in Network Manager, i supposed to see wireless access points, but there's only "Wired Connection" and "Point to Point Connection" no Wireless access point.Once back I installed the rtl8187-jadamns-modified-driver and after all i could see the available networks list, but i couldn't make the internet work at all, only the list shows up...
Any idea what's goin' on ?
Ps.: Gezzes...That the only one driver left to ubuntu works fine...

Thanks in advance

---

### Post by Tom--d on 2008-06-13
Reboot and see if ity works then.

---

### Post by Brown_ on 2008-06-13
The entire proccess i did connected on a wired connection, should i disconnect before install ? or it doesn't matter !?

---

### Post by Tom--d on 2008-06-13
It shouldn't affect anything but to be on the save side, yes.

Also, make sure your wireless switch is ON (thats if you have one) while installing the driver

---

### Post by Brown_ on 2008-06-13
Hey Tom.
Thanks for the replies. I still didnt make it work, did every thing again, even reinstall ubuntu, but didn't make any diference, after install the Wireless Manager keeps the same(Wired connection and Point 2 point connection)
There are some results:

mateus@mateus-laptop:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
mateus@mateus-laptop:~$ lspc
lspci     lspcmcia  
mateus@mateus-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

mateus@mateus-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

- What should i try next !?
\Cheers

---

### Post by Tom--d on 2008-06-14
Right, 
Do you have ndiswrapper installed. And ndisgtk (GUI of Ndiswrapper)

Then get the driver on my second post. Extract it, keep it in the folder!
Go to, System > Admin > Windows Wireless Drivers

Install Driver, locate the .inf file. (the .sys file must be in there as well!)

Then, it should, like mine, say 'Hardware Present = Yes' If yes. The driver is installed, properly!

Then do. in terminal,
```
sudo ifconfig wlan0 down
sudo ifconfig wlan up
```

Then after, do this.

```
wlist scan
```

then post the outcomes!

:)

---

### Post by Petawa on 2008-06-15
I have the same wifi card as well. I followed the tutorial, and I was able to see "net8187b Hardware Present: Yes" from Windows Wireless Drivers.  However, when I try to "ifconfig wlan0 up" or anything else wlan0, it says that wlan0 cannot be found. Indeed, Network Manager does not see a wireless card either.

I can get internet using the included rtl8187 drivers. However, it is very unstable.  It will always show 4 or 5 bars in network manager, but the internet tends to stop working after 2 or 3 minutes, and I have to rmmod/modprobe rtl8187 to get it back for another 2 to 3 minutes. I've seen many posts about this problem on this forum, but none have a solution beyond installing ndiswrapper, hence why I followed this tutorial.

I added rtl8187 to blacklist before I followed this tutorial.  As I mentioned, even though it says the hardware is present, I can't do anything with wlan0, since it doesn't think its there.  I "modprobe ndiswrapper", no change.  I "modprobe rtl8187", and immediately wlan0 appears and it connects (though its unstable).  I "rmmod rtl8187" and wlan0 disappears again.

I've tried restarting many times.  I always have no internet at all upon boot, and I can never see wlan0 until I resort to using the default unstable drivers.

Can anyone figure out why the hardware is detected but wlan0 won't appear when using ndiswrapper?

---

### Post by Tom--d on 2008-06-15
> **Petawa said:**
> I have the same wifi card as well. I followed the tutorial, and I was able to see "net8187b Hardware Present: Yes" from Windows Wireless Drivers.  However, when I try to "ifconfig wlan0 up" or anything else wlan0, it says that wlan0 cannot be found. Indeed, Network Manager does not see a wireless card either.

I can get internet using the included rtl8187 drivers. However, it is very unstable.  It will always show 4 or 5 bars in network manager, but the internet tends to stop working after 2 or 3 minutes, and I have to rmmod/modprobe rtl8187 to get it back for another 2 to 3 minutes. I've seen many posts about this problem on this forum, but none have a solution beyond installing ndiswrapper, hence why I followed this tutorial.

I added rtl8187 to blacklist before I followed this tutorial.  As I mentioned, even though it says the hardware is present, I can't do anything with wlan0, since it doesn't think its there.  I "modprobe ndiswrapper", no change.  I "modprobe rtl8187", and immediately wlan0 appears and it connects (though its unstable).  I "rmmod rtl8187" and wlan0 disappears again.

I've tried restarting many times.  I always have no internet at all upon boot, and I can never see wlan0 until I resort to using the default unstable drivers.

Can anyone figure out why the hardware is detected but wlan0 won't appear when using ndiswrapper?

Weird :\
I'm using the wireless card now and its fine.

ok, now in terminal type, iwconfig

post the output. With the ndiswrapper drivers installed etc.

---

### Post by Petawa on 2008-06-15
When the internet's working (using rtl8187):
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:F7:AC:1A:B6
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=49/64  Signal level=25/65
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I know my signal quality's kind of low, I'm connecting through the ceiling to to apartment above mine (with their knowledge).

After it stops working on rtl8187:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:F7:AC:1A:B6
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=49/64  Signal level=23/65
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

After rmmod rtl8187, modprobe ndiswrapper (and either with or without "/etc/init.d/networking restart", doesn't make a difference:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

And just for good measure, "ndiswrapper -l" when rtl8187 is disabled:
```
net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

```

The signal strength with rtl8187 is wildly varying..I'm sure its in part my not-so-great signal, but Vista on the same machine never has a problem.  Hence why I'm doing ndiswrapper in the first place.

---

### Post by Tom--d on 2008-06-15
Ah I see the problem!

Your wireless card has the ID of 8187 (mine is 8197, makes A LOT of difference)

Thats an easy one.

Use this driver attached to the post and see what happens.

---

### Post by Petawa on 2008-06-15
Exact same messages, no change. It shows hardware detected with the new driver as well, but all iwconfig has to say is
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

---

### Post by Tom--d on 2008-06-15
I do not understand :S

It should work!
As the driver i gave is the Windows 98 driver for that card. (the driver for my card is modified of win98)

mm...
post the outcome of lspci and lsusb and ifconifg

also, post the outcome uname -r


edi: reinstall ndiswrapper

---

### Post by Petawa on 2008-06-15
ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:1a:92:8c:01:04
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:1a:92:8c:05:6e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lsusb
```

Bus 007 Device 007: ID 04a9:1097 Canon, Inc.
Bus 007 Device 006: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 007 Device 005: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 007 Device 002: ID 0424:2502 Standard Microsystems Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 06a3:8021 Saitek PLC
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1532:0009
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

lspci```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

```

trying the reinstall now...

---

### Post by Tom--d on 2008-06-15
Also, please post the outcome of uname -r

---

### Post by Petawa on 2008-06-15
Reinstall didn't change anything, 
uname -r
2.6.24-16-generic

BTW, thanks for trying to help

---

### Post by Tom--d on 2008-06-15
No problem. 

Well. I cant get my head around it.

You are using the same kernel as me, same driver.. but it will not work for you :(
mm..

download the drivers from here:

[http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8187B-Driver-6106302082007-WHQL.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8187B-Driver-6106302082007-WHQL.shtml)

and try them all. Dont do Vista, they dont work. nor 64bit


Ahhh.. important, are you on 32bit (x86) or 64bit?

---

### Post by Petawa on 2008-06-15
32 bit
I have to do some homework now (I didn't realize how long I've spent!! Having to rmmod/modprobe or restart into Vista to post a reply or see yours each time is time consuming!)
I'll definitely try the other drivers next weekend if I don't get any time before, and maybe even during the week someone will come up with a solution to why the default rtl8187 are so flaky, since there's a lot of people having that problem too.

Thanks again for the help so far!

---

### Post by Tom--d on 2008-06-15
Thats ok :)
Also, drop a email to Realtek, you may get drivers :D

I did :D but perfer the Win98 modified driver.

---

### Post by lotacus on 2008-06-16
This is all good and dandy IF you want to use ndiswrapper.

I managed to find source code for the drivers somewhere, cannot remember where though. Well, I'm pretty sure they are source, or maybe reverse engeneered drivers, in either case, it seems like they installed fine after compiling them. in the consol if I issue the command to bring up the wirless status, it will see the ssids etc, and when I go to the networking icon in top right, it will see the ssid's available, but without the signal strength. My network uses wpa2 which doesn't seem to be supported by linux or very sketchy support at that (what a shame), but here's a hitch, when I connect using WEP, it will freeze ubuntu. Hmm.. Sorry, i'm at work right now so I can't give a lot of details, but when i get home, i'll post the entire process I go through to compile etc, and i'll post the drivers source as well, and hopefully a dev will download them and take a look, and hopefully be able to clean it up and make it work almost 100% with ubuntu and have it as an update.

---

### Post by Tom--d on 2008-06-16
> **lotacus said:**
> This is all good and dandy IF you want to use ndiswrapper.

I managed to find source code for the drivers somewhere, cannot remember where though. Well, I'm pretty sure they are source, or maybe reverse engeneered drivers, in either case, it seems like they installed fine after compiling them. in the consol if I issue the command to bring up the wirless status, it will see the ssids etc, and when I go to the networking icon in top right, it will see the ssid's available, but without the signal strength. My network uses wpa2 which doesn't seem to be supported by linux or very sketchy support at that (what a shame), but here's a hitch, when I connect using WEP, it will freeze ubuntu. Hmm.. Sorry, i'm at work right now so I can't give a lot of details, but when i get home, i'll post the entire process I go through to compile etc, and i'll post the drivers source as well, and hopefully a dev will download them and take a look, and hopefully be able to clean it up and make it work almost 100% with ubuntu and have it as an update.


That is due to the drivers fault. Not Ubuntu.
WPA has to be supported by the drivers and the card.

I think I know how drivers you are on about and I've tried them, they are very very buggy and crashed my system.
Ndiswrapper, on the other hand, doesnt crash my system and with the driver im using, i can have all types of encryption :D

---

### Post by mbarvian on 2008-06-18
Thanks for this easy tutorial! I'll give this a try as soon as I can!:guitar:

---

### Post by alchemist0 on 2008-06-21
YES!! YEAAAAAHHHH!!!!! MAN I CANT EVEN DESCRIBE YOU HOW GRATEFUL I AM!!!
I was getting desperate.......nothing worked....but now im really ashamed,,,,,I can't believe how easy it was,,,,!!!
Cheers! Keep it up!

---

### Post by Tom--d on 2008-06-21
> **alchemist0 said:**
> YES!! YEAAAAAHHHH!!!!! MAN I CANT EVEN DESCRIBE YOU HOW GRATEFUL I AM!!!
I was getting desperate.......nothing worked....but now im really ashamed,,,,,I can't believe how easy it was,,,,!!!
Cheers! Keep it up!

Yay! :D

So how did it work for you?
Did the Network Manager applet work as well?
What encryption does your Wireless have?


*You can press the ribbon star thingy to say thanks :)*

---

### Post by mbarvian on 2008-06-21
may I ask which Toshiba laptop you have?  I have an a125-s7422 Satellite.

---

### Post by Tom--d on 2008-06-21
I have a Toshiba A200 IVO

---

### Post by mbarvian on 2008-06-21
Hmm, well, I tried the tutorial and ndiswrapper, and it says everything is installed correctly, hardware is detected, but I still cannot view wireless networks:confused:.  Anyway, great tutorial :)

---

### Post by alchemist0 on 2008-06-21
> **Tom--d said:**
> Yay! :D

So how did it work for you?
Did the Network Manager applet work as well?
What encryption does your Wireless have?


*You can press the ribbon star thingy to say thanks :)*

I did press the ribbon thingy heheheh!
HOWEVER: This whole tutorial worked for me......when I was using the liveCD (I did so cuz ndiswrapper wouldnt work). Now that Im using the hard-disk-installed Ubuntu (after I persuaded ndiswrapper to work) all the problems mentioned above show up......I'll try this and that and I'll keep u informed.

Plus, I have no wireless router, im just stealing internet from the neighbors using ones...heheheh:)....so Im not under a certain encrypion....:)...THANX FOR EVERYTHING!!

---

### Post by alchemist0 on 2008-06-21
Oh....I Have a Toshiba L40-18Y....

---

### Post by popeye64 on 2008-06-21
Hi,
thanks to Tom--d, I got my wireless up on my Toshiba Satellite Pro L40. I am running WPA with TKIP, and I am using the ghome network manager. I am using the "Driver(RTL8187B).tar.gz" posted by Tom--d in this thread, under ndiswrapper.

$ndiswrapper -l
net8187b : driver installed
        device (0BDA:8197) present

I had to add this line to the .inf file:
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

Thanks again to Tom--d.

---

### Post by Tom--d on 2008-06-21
> **alchemist0 said:**
> I did press the ribbon thingy heheheh!
HOWEVER: This whole tutorial worked for me......when I was using the liveCD (I did so cuz ndiswrapper wouldnt work). Now that Im using the hard-disk-installed Ubuntu (after I persuaded ndiswrapper to work) all the problems mentioned above show up......I'll try this and that and I'll keep u informed.

Plus, I have no wireless router, im just stealing internet from the neighbors using ones...heheheh:)....so Im not under a certain encrypion....:)...THANX FOR EVERYTHING!!


hehe, yeah, no encryption is the best for this wireless card due to its incompatibility with everything xD
but I use wep, and now it works :)
I think wpa works as well. (im quite sure as well).

Glad it worked for you :)

---

### Post by Tom--d on 2008-06-21
> **popeye64 said:**
> Hi,
thanks to Tom--d, I got my wireless up on my Toshiba Satellite Pro L40. I am running WPA with TKIP, and I am using the ghome network manager. I am using the "Driver(RTL8187B).tar.gz" posted by Tom--d in this thread, under ndiswrapper.

$ndiswrapper -l
net8187b : driver installed
        device (0BDA:8197) present

I had to add this line to the .inf file:
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

Thanks again to Tom--d.


No problem! 
Glad it worked!

Also, if you feel nice. say thanks to my first post :P (little ribbon start thingy on the post, near the bottom of the post.)


Thanks!

---

### Post by alchemist0 on 2008-06-22
After all, my realtek wont work......It DID work while I was using the Ubuntu liveCD, but now I've downloaded and tried numerous drivers and I've reinstalled ndiswrapper equal times....Nothing worked....Ndiswrapper reports that the card exists, but it just won't work....I see nothing more to be done....:(...It's rather strange, isn't it?

---

### Post by Tom--d on 2008-06-22
> **alchemist0 said:**
> After all, my realtek wont work......It DID work while I was using the Ubuntu liveCD, but now I've downloaded and tried numerous drivers and I've reinstalled ndiswrapper equal times....Nothing worked....Ndiswrapper reports that the card exists, but it just won't work....I see nothing more to be done....:(...It's rather strange, isn't it?

Weird. Very Weird. I don't know what to do :\

---

### Post by johanhartman on 2008-06-26
I did everything you said in the first post, and it worked perfectly... sort of.

The network card is seen and it even sees all the surrounding networks with their strengths, but when I try to connect with my WPA encrypted router it takes very long. After it finally connects, network manager shows that the strength is 0% and I have no internet connection.

---

### Post by Tom--d on 2008-06-26
> **johanhartman said:**
> I did everything you said in the first post, and it worked perfectly... sort of.

The network card is seen and it even sees all the surrounding networks with their strengths, but when I try to connect with my WPA encrypted router it takes very long. After it finally connects, network manager shows that the strength is 0% and I have no internet connection.

Ok. The wireless card is not perfect with Linux. Network manager doesn't like the card, at all.

Thats why you need to follow after that part. Re-read it again. Follow every step. Use the link which is provided and use that for WPA. (As what I've shown was my WEP key).

---

### Post by johanhartman on 2008-06-26
Never mind I forgot to try system >> administration >> network to manually connect. That works fine now

---

### Post by Tom--d on 2008-06-26
> **johanhartman said:**
> Never mind I forgot to try system >> administration >> network to manually connect. That works fine now

Good :)
Glad it worked :)

---

### Post by Tonyphase on 2008-06-27
im having trouble wit this terribly and i finally got the driver to be recognized after weeks.
however in network manager i only see wired connection and point to point connection

I've read this tutorial and got stuck just after that part.
can you please help me?

---

### Post by Tom--d on 2008-06-27
> **Tonyphase said:**
> im having trouble wit this terribly and i finally got the driver to be recognized after weeks.
however in network manager i only see wired connection and point to point connection

I've read this tutorial and got stuck just after that part.
can you please help me?

:\
Sorry to say, but I do not have enough experience to know why its doing that.

Whats the outcome of iwconfig?

---

### Post by Tonyphase on 2008-06-27
> **Tom--d said:**
> :\
Sorry to say, but I do not have enough experience to know why its doing that.

Whats the outcome of iwconfig?

```

tony@tony-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by Tom--d on 2008-06-27
mm.. It looks to be that it hasn't seen a wireless card. :\

Are you sure its the 8197 card?

---

### Post by Tonyphase on 2008-06-27
> **Tom--d said:**
> mm.. It looks to be that it hasn't seen a wireless card. :\

Are you sure its the 8197 card?

yeah it is. in windows wireless drivers it says hardware present and the switch in the front of the laptop for my wireless is on but thats what im getting

---

### Post by whawes on 2008-07-01
It's possible that those who can't get this working despite having followed the instructions to the letter are running a 64 bit release of Ubuntu. Since the Realtek Win98 network card driver is 32-bit, you'll need the 32 bit version of Ubuntu to run it (32 bit Ubuntu can be installed on a 64 bit machine without problems btw).

Verify whether you have 32 or 64 bit Ubuntu using:

```

# getconf LONG_BIT
(32-bit returns 32, 64-bit returns 64)

```

If you're running 64 bit Ubuntu and have followed the OP's instructions, you can verify the problem as follows:

```

# modprobe -r ndiswrapper
# modprobe ndiswrapper

```

Now check /var/log/messages and /var/log/syslog for something similar to:

```

Jul  1 15:32:53 <machine_name> kernel: [  683.306299] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

```

Don't be tempted at this point to try and install one of the 64 bit Realtek drivers as an alternative - they will hang the entire network stack on your machine and will require a boot into recovery mode to remove them. At the time of writing installing 32 bit Ubuntu is the only way to get this particular wireless card working.

The good news is that once installed, it works fine on Hardy using both WPA+WPA2.

HTH.

---

### Post by Tom--d on 2008-07-01
You are correct!

It only works with 32bit as the only Diver (I think) you can use is the Win98,  (32 bit).

---

### Post by johanhartman on 2008-07-01
I followed this tutorial a few days ago and got my wireless working, though without network manager. I connected it manually by going to System>>Administration>>Network, I don't know if this uses Network Manager anyway or not.

But I realised that after booting, connecting to my network takes a very long time and I have to try several times before it connects. My network is wpa1 protected so I decided to follow the howto-link mentioned in this howto to manually configure the network. That made no difference. I tried installing wicd and using that instead of network manager but exactly the same problem persists.

I've seen on the network history graph in system monitor that every time I attempt to connect theres a burst of both down- and upload activity before it simply drops again. Also my family who share the network with me have noticed that every time I boot Ubuntu they are temporarily kicked out of the network. Finally, when I boot Vista the network connection is not established automatically like it used to be but this is easily fixed by switching the wireless off and on again, whereas the position of the wireless switch makes no difference to my connectivity on Ubuntu.

Bit of an info overload I know but I don't know much about this, so nor do I know what is relevant or not.

---

### Post by johanhartman on 2008-07-01
> **johanhartman said:**
> ...I have to try several times before it connects...

I think perhaps I just have to wait a while before it will successfully connect.

---

### Post by Tom--d on 2008-07-01
> **johanhartman said:**
> I followed this tutorial a few days ago and got my wireless working, though without network manager. I connected it manually by going to System>>Administration>>Network, I don't know if this uses Network Manager anyway or not.

But I realised that after booting, connecting to my network takes a very long time and I have to try several times before it connects. My network is wpa1 protected so I decided to follow the howto-link mentioned in this howto to manually configure the network. That made no difference. I tried installing wicd and using that instead of network manager but exactly the same problem persists.

I've seen on the network history graph in system monitor that every time I attempt to connect theres a burst of both down- and upload activity before it simply drops again. Also my family who share the network with me have noticed that every time I boot Ubuntu they are temporarily kicked out of the network. Finally, when I boot Vista the network connection is not established automatically like it used to be but this is easily fixed by switching the wireless off and on again, whereas the position of the wireless switch makes no difference to my connectivity on Ubuntu.

Bit of an info overload I know but I don't know much about this, so nor do I know what is relevant or not.

Try a different encryption?
Or no encryption and hide the SSID?
Easier for Ubuntu :)

---

### Post by johanhartman on 2008-07-02
I don't know if that will work, because I've tried connecting to a different, completely unencrypted network and the same thing happens.

Can anyone tell me how to get rid of any mention of my network on Ubuntu so I can try from the start to see if I did anything wrong the first time round.

---

### Post by Tom--d on 2008-07-02
Does Network Manager work for you?
Try to connect that way.

If not, 
Do this in terminal
```
iwlist scan
```
Post the outcome.

---

### Post by johanhartman on 2008-07-02
For iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:90:D0:4A:75:86
                    ESSID:"steven"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:90:D0:4B:80:97
                    ESSID:"shirley12"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:0F:B5:D1:AA:8C
                    ESSID:"Limpopo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:17:9A:F2:E1:95
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

note I want to connect to cell 03.

I originally tried network manager but im now using wicd which uninstalls network manager, anyway as wicd and connecting manually, network manager works but only after several attempts...

---

### Post by Tom--d on 2008-07-02
Your Wireless card is working fine :) 

Its like mine. Network Manager doesn't work as it should do. This is due to the Driver not made for this card. The only driver for this card is the Vista one (I've got it) but Ndiswrapper cannot use the Vista Drivers yet. But when they do. This will be sorted, I hope :)

Do not use Network manager and wcid. Uninsatall them all. And get rid of network-manager and network-manager-gnome.
You will need to make a little script to make this work. 

Follow these steps in this link. It shows everything, even for your encryption.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by johanhartman on 2008-07-02
ill try when i have time and post back

thanks

---

### Post by johanhartman on 2008-07-04
> **Tom--d said:**
> Do not use Network manager and wcid. Uninsatall them all. And get rid of network-manager and network-manager-gnome.
You will need to make a little script to make this work. 

Follow these steps in this link. It shows everything, even for your encryption.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

OK I've had time to try this, but I still cannot connect. When I type;
"sudo ifconfig wlan0 up", it just accepts it and waits for next command.
Then when I type; "sudo dhclient wlan0", it tries for a while but then says; "No DHCPOFFERS received."

The only thing I can still think of doing then is to try using a static IP, but I'm not terribly optimistic...

---

### Post by Caveageman on 2008-07-04
What can i do if my id is 8187????

---

### Post by Tom--d on 2008-07-04
> **johanhartman said:**
> OK I've had time to try this, but I still cannot connect. When I type;
"sudo ifconfig wlan0 up", it just accepts it and waits for next command.
Then when I type; "sudo dhclient wlan0", it tries for a while but then says; "No DHCPOFFERS received."

The only thing I can still think of doing then is to try using a static IP, but I'm not terribly optimistic...

You need to give iwconfig the info of your wireless. 

For example. 
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid "linksys" (If you want encrpptyion, use the link which is provided on the first post. It will tell you how to do it).
sudo dhclient wlan0

Post the outcome

---

### Post by Tom--d on 2008-07-04
> **Caveageman said:**
> What can i do if my id is 8187????

Use the same Driver, but I think it works better as that driver is made for that card.

Just use the Win98 driver and use Network Manager. Should all work :)

Just incase, download the drivers from somewhere. The one I edited may alter the way the card works :\

---

### Post by icdelg on 2008-07-14
After tinkering with the driver some more I found that I can get the driver to install properly in ndiswrapper if I add the line 

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
 
under the "IDs for X64" section as well.
I can't believe it took me so long to figure that out since I'm running 64 bit version of Hardy!

(Also, I used the X64 driver to get it to work.)

---

### Post by Tom--d on 2008-07-14
I cannot comment on 64bit driver as I dont know what happens. 

I use 32bit.

---

### Post by Comic on 2008-07-20
Hello, and what a terrific site, I am totaly new to Linux and have started my journey with Ubuntu 8.0.4..what a challenge. 

I am attempting to hook up my wireless internet which has the rtl8187 chipset driver, while following post #1 of this thread I got to step 5 " Installing the new driver" well when I goto " System" "Administration" " Windows Wireless driver" and double click on it, a Window pops up and goes away so fast I have no idea what it says or even looks like. Would anyone have any idea why this is happening ? Thanks in Advance for any help I may receive

Also Kudos to all those who give their time to help noob's like myself

---

### Post by Tom--d on 2008-07-20
First thing.
You do not need to double click it ;) 
Single click is fine :) 

And then you should see a box appear in your middle of your screen. This is where root (the super user) will ask for your password. Enter that and then from there.. you shall see :)

---

### Post by Comic on 2008-07-20
> **Tom--d said:**
> First thing.
You do not need to double click it ;) 
Single click is fine :) 

And then you should see a box appear in your middle of your screen. This is where root (the super user) will ask for your password. Enter that and then from there.. you shall see :)

Just amazing what one simple click will do..lol..so use to winblows..I will turn 50 this summer and must say I still love a good challenge, getting this wirelss network up and running is that good challenge.

Thank you my friend..Comic

(update) while reading your post i tried it, and the window came up and stayed, but I closed it, and wanted to make this post and then rerurn to page 1 and open it again and follow the instructions...well I tired while bac on pg1 and no go..pops up then goes away..

---

### Post by onewithnature83 on 2008-07-20
Hello. Just putting it on the offering table. I personally wrote this how-to. Yes there are disadvantages. ndiswrapper is a disadvantage all by its own. 

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

Its worth at least looking at. --TJ

---

### Post by Comic on 2008-07-20
> **onewithnature83 said:**
> Hello. Just putting it on the offering table. I personally wrote this how-to. Yes there are disadvantages. ndiswrapper is a disadvantage all by its own. 

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

Its worth at least looking at. --TJ

I will be very happy to look at it, as right now I need all the help I can get..I have the strong urge to do a fresh install of Ubuntu, and start fresh. I think what might help me is to get a book or a list of common commands used with Linux. If it were not for the ability to copy/paste I would not be getting anywhere..Thank you for the link.

---

### Post by Tom--d on 2008-07-21
Yes, there are 2 ways of getting this card to work. 

I don't know whats better as I haven't tried the other way. 
I think I heard that it cannot read the signal level. 
Right?

---

### Post by Comic on 2008-07-21
> **Tom--d said:**
> Yes, there are 2 ways of getting this card to work. 

I don't know whats better as I haven't tried the other way. 
I think I heard that it cannot read the signal level. 
Right?

Well Im just now learning what it takes to even get it close to working..but, I took 1 nice step forward yesterday, then 3 huge steps backwards while trying to edit a file to download some files from a repository..I was following the steps in the link posted below when I made e error in my editing, then compounded the problem by saving the file..I am really green at Linux, but have had enough yrs behind the keyboard that I can usually work my way through my problems with tips and hints..here is the error I have :

'E:Malformed line 3 in source list /etc/apt/sources.list (dist), E:The list of sources could not be read

This error is in the update manager..any ideas how to correct it ??

here are the steps I was following :

hxxp://ryanunderdown.com/wp-content/uploads/2007/02/turkeyfarm.html
( edited the HTTP with XX..not sure about live link posting )

---

### Post by Comic on 2008-07-21
I have removed the error by just removing line 2-3 all together, but I believe that has affected my update because when I continued on trying to grab the files from the repository I got the following :


"E: Some index files failed to download, they have been ignored, or old ones used instead.
echotesters@Wireless-Ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
echotesters@Wireless-Ubuntu:~$ sudo apt-get install aircrack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack
echotesters@Wireless-Ubuntu:~$ sudo apt-get install kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kismet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
echotesters@Wireless-Ubuntu:~$ sudo apt-get install airsnort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package airsnort "

But it has downloaded  the "Linux Source 2.6.24"..and Im working on following the rest rest of the steps..I would like to edit the whole thing and start over..but Im totaly lost on what the first 3 lines in text-editor said originaly.

---

### Post by The Browncoat Cat on 2008-07-21
I have been having problems with my RTL8187b WI-FI card.  I have followed the instructions in the first post on this thread, and my laptop now knows that there should be a WI-FI card present.  However, the card is still refusing to work. When I enter the command ```
"ndiswrapper -l" i get the following
net8187b : driver installed
        device (0BDA:0158) present
```
Also NDISGTK tells me that "net8187b" has been installed and that the hardware is present.  However, the card refuses to switch itself on and connect to my network.  The network manager tells me that only the Ethernet interface and the lo interface are present, there is no mention of any wireless network. The command "iwconfig" reports the following:
```
lo     no wireless extentions
eth1   no wireless extentions
```

Pressing the "FN" key on my keyboard and holding down F10 is supposed to switch the card on, but this does not work with Ubuntu.  Have you any suggestions how I can get the WI-FI card to switch on?

---

### Post by Tom--d on 2008-07-21
> **The Browncoat Cat said:**
> I have been having problems with my RTL8187b WI-FI card.  I have followed the instructions in the first post on this thread, and my laptop now knows that there should be a WI-FI card present.  However, the card is still refusing to work. When I enter the command ```
"ndiswrapper -l" i get the following
net8187b : driver installed
        device (0BDA:0158) present
```
Also NDISGTK tells me that "net8187b" has been installed and that the hardware is present.  However, the card refuses to switch itself on and connect to my network.  The network manager tells me that only the Ethernet interface and the lo interface are present, there is no mention of any wireless network. The command "iwconfig" reports the following:
```
lo     no wireless extentions
eth1   no wireless extentions
```

Pressing the "FN" key on my keyboard and holding down F10 is supposed to switch the card on, but this does not work with Ubuntu.  Have you any suggestions how I can get the WI-FI card to switch on?

You do not have the correct driver for your wireless card.

Your wireless card is:
0BDA:0158

My Wireless card is:
0BDA:0197

It makes a lot of difference.
Uninstall the driver, download the correct windows driver or even see if there are linux drivers for that card. They maybe :)

---

### Post by The Browncoat Cat on 2008-07-22
> **Tom--d said:**
> You do not have the correct driver for your wireless card.

Your wireless card is:
0BDA:0158

My Wireless card is:
0BDA:0197

It makes a lot of difference.
Uninstall the driver, download the correct windows driver or even see if there are linux drivers for that card. They maybe :)

Yes, I realise all of that.  I am using the latest official Windows driver that came with my laptop, which should work with NDISWrapper "out of the box".  The solution you came up with for your WI-FI card almost worked, with modifications, on mine.  Looks as if I have more work to do to get my card working. :(

---

### Post by Tom--d on 2008-07-22
O right.
I've never seen that ID number for that card.

What Laptop is it and can you post the outcome of 
```
lspci
```

---

### Post by The Browncoat Cat on 2008-07-22
> **Tom--d said:**
> O right.
I've never seen that ID number for that card.

What Laptop is it and can you post the outcome of 
```
lspci
```

The command "lspci" produces the following results:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
0d0:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

The command "lsubs" produces the following results:
```
Bus 003 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

I suspect that there should be at least a mention of the RealTek WI-Fi card somewhere in the listing produced by "lspci".

---

### Post by onewithnature83 on 2008-07-22
> 
I suspect that there should be at least a mention of the RealTek WI-Fi card somewhere in the listing produced by "lspci".


this wifi chipset does not use the PCI bus for any communication.. 

So there should not be any mention of it under the output of lspci. 

The card is on the USB bus as you have shown with lsusb. 

Also.. alot of you here spending alot of time and effort to make use of windows drivers.. 

My method takes approx 5 min. to complete, does not make use of windows in any way. and works everytime!

yes its true that WAP/WAP2 is not supported.. and signal strength is not displayed.  

you assess the pro's and con's and find what is best for you.

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

---

### Post by The Browncoat Cat on 2008-07-22
> **onewithnature83 said:**
> this wifi chipset does not use the PCI bus for any communication.. 
So there should not be any mention of it under the output of lspci. 
The card is on the USB bus as you have shown with lsusb. 
I assumed that it was a PCI based device.  So, I have learnt something new today.:)

I have tried to follow your instructions but fall at the last hurdle.  the instruction```
sudo ./makedrv
```results in the error```
sudo: ./makedrv command not found
```similarly, the command ```
sudo ./wlan0up
```results in a message ```
sudo: ./wlan0up command not found
```

---

### Post by The Browncoat Cat on 2008-07-23
> **The Browncoat Cat said:**
> I assumed that it was a PCI based device.  So, I have learnt something new today.:)

I have tried to follow your instructions but fall at the last hurdle.  the instruction```
sudo ./makedrv
```results in the error```
sudo: ./makedrv command not found
```similarly, the command ```
sudo ./wlan0up
```results in a message ```
sudo: ./wlan0up command not found
```Sorry to be relying to my own post, but I have worked out what went wrong above.

---

### Post by snuffy on 2008-07-25
tom, you rock my world!  i was all ready to chuck this damn thing in the bin and buy a new one!

followed your instructions, very easy for a beginner... works perfectly. 

cheers mate.


tim.

---

### Post by Tom--d on 2008-07-25
> **snuffy said:**
> tom, you rock my world!  i was all ready to chuck this damn thing in the bin and buy a new one!

followed your instructions, very easy for a beginner... works perfectly. 

cheers mate.


tim.


Hey, 

Thanks :)
That has now made my day :D


I tried to make it really easy :)

Clad it got working for you.

Just one question.
Do you use Wifi-Radar or Network Manager?

Thanks,
Tom

Ps. Do you have msn? (mail me if you wanna talk :) )
O and, press the ribbon with a star on the post of me. It says Thanks :)

---

### Post by snuffy on 2008-07-26
just checked tom, its Network Manager. not through choice, just because it showed up.  is wi-fi radar a better choice?

i got WPA working with AES encryption. wouldn't work with TKIP though.

tim.

---

### Post by Tom--d on 2008-07-26
> **snuffy said:**
> just checked tom, its Network Manager. not through choice, just because it showed up.  is wi-fi radar a better choice?

i got WPA working with AES encryption. wouldn't work with TKIP though.

tim.


er, for WEP encryption, yes. 
And it doesnt ask for your password at start. 
but it doesnt keep a connection all the time. if its inactive. it will disconnect. (I just keep Pidgin open and internet is always connected).

Stick with Network Manager :) As there is nothing wrong with it. Why fix it?

---

### Post by silvertwilight on 2008-07-30
At first, I found that Ubuntu recognized the usb dongle (rtl 8187), but
when I tried firefox, it wouldn't connect to the D-Link 524 wireless
connector that I use upstairs.  I put a sheet of aluminum foil on the 
wall behind the d-link, then used a metal vegetable strainer and 
cut a square hole in the bottom to put a short usb cable extender
before attaching the usb wifi dongle. Pointed this toward the d-link
router.  Booted Ubuntu from CD-rom.  Evidently the signal strength
was now strong enough for Firefox to connect to the internet.  Didn't 
have to make any changes to Ubuntu which boots in about three minutes
from the CD iso. Now don't have to worry about getting on the net without
MSXP.   

Next problem to figure out is the fx5200 card which Ubuntu doesn't 
seem to recognize since I can't get the res to 1024 by 768 which I could
do in XP.

---

### Post by Ptero-4 on 2008-08-04
> **icdelg said:**
> After tinkering with the driver some more I found that I can get the driver to install properly in ndiswrapper if I add the line 

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
 
under the "IDs for X64" section as well.
I can't believe it took me so long to figure that out since I'm running 64 bit version of Hardy!

(Also, I used the X64 driver to get it to work.)

Which driver did you use for that (can you pls post the link to it)? where (in the inf file) you stick the lines you add? And does it work (as in network manager works after you install the driver, the OS/console/sudo remain operational, and the card actually connects)?

---

### Post by Tom--d on 2008-08-05
> **Ptero-4 said:**
> Which driver did you use for that (can you pls post the link to it)? where (in the inf file) you stick the lines you add? And does it work (as in network manager works after you install the driver, the OS/console/sudo remain operational, and the card actually connects)?

I have added the 64bit driver to this post.
I have modified it. Hopefully it should work. 

I can't guarantee anything due to I've never used 64bit.

---

### Post by Ptero-4 on 2008-08-05
> **Tom--d said:**
> I have added the 64bit driver to this post.
I have modified it. Hopefully it should work. 

I can't guarantee anything due to I've never used 64bit.

Just tried it, windoze´d Hardy so bad I had to raise elephants.

---

### Post by Tom--d on 2008-08-06
> **Ptero-4 said:**
> Just tried it, windoze´d Hardy so bad I had to raise elephants.

Dang.
Sorry, I cannot help you with the 64bit as I have no information on where to start.

:(

---

### Post by Ptero-4 on 2008-08-07
No worries. 2.6.27rc2 makes the wifi work (breaks hibernation though).

---

### Post by hypoluxa68 on 2008-08-12
in lsusb i don't even see realtek.

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
ubuntu@ubuntu:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c51b Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000


could someone please help me figure out what i'm doing wrong.

tia

---

### Post by Tom--d on 2008-08-13
> **hypoluxa68 said:**
> in lsusb i don't even see realtek.

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
**0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
ubuntu@ubuntu:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c51b Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000


could someone please help me figure out what i'm doing wrong.

tia

You do not have the wireless card. The wireless card is in bold. The one above it is a Ethernet card.

---

### Post by hypoluxa68 on 2008-08-13
the realtek card is the only one that seems to not be working. i have intenet access when i plug the box in to the router directly but no wireless. it does work with vista :( 

i'm totally new to linux and i'm not quite sure what the difference is between the ethernet and wireless card. when i installed xp on the same box i had the same problem with the realtek card but i eventually got it working using drivers for a different model of the same brand.

any help you could offer would be appreciated. this is the only hinderance i have in installing kubuntu as my primary os. well, there is also a wine problem but i'll research that further.

thanks in advance.

---

### Post by Tom--d on 2008-08-13
You do not have a Realtek wireless card. This thread is for the Realtek RTL8187B wireless card.
Your WIRED card is realtek. I do not know what to do with that, sorry. Ask around on the forums.

You have a Atheros AR242x Wireless card and it 'should work' as Atheros is known to be good with Linux.
Try here:
[http://ubuntuforums.org/showthread.php?t=873980](http://ubuntuforums.org/showthread.php?t=873980)

Hope this helped at all.

---

### Post by hypoluxa68 on 2008-08-13
thanks for your help. still trying to figure out all this linux stuff. hope to be wireless soon :)

---

### Post by maxy04 on 2008-08-15
excuse me for the question, i'm italian and i can't understand all you wrote.
i have an RTL8187B, and i use wpa-tkip.
can i use wpa with that card and ndiswrapper?
i tryed the driver from cuervo and win98 drivers + ndiswrapper, but either say "wpa is not supported".

---

### Post by Tom--d on 2008-08-15
> **maxy04 said:**
> excuse me for the question, i'm italian and i can't understand all you wrote.
i have an RTL8187B, and i use wpa-tkip.
can i use wpa with that card and ndiswrapper?
i tryed the driver from cuervo and win98 drivers + ndiswrapper, but either say "wpa is not supported".

Do not use the drivers from Cuervo. They are very very very buggy.

The Win98 Windows Driver (which is on the 3rd post I think (I made it as an attachment)..download that. Install that Driver with Ndiswrapper. (Just follow the 1st post on this thread).

I have used WPA Passphrase on it. I don't know about tkip as I only have WEP at my home wireless network. Try it and find out.
Post back here if you need any more help.

---

### Post by Mincher on 2008-08-28
Hi,

I'm investigating this to try and get my wireless working (Toshiba Satellite L40-18Z). No luck as of yet.

Just to make you aware, my wireless device seems to link to wlan1 rather than wlan0.

---

### Post by Tom--d on 2008-08-28
> **Mincher said:**
> Hi,

I'm investigating this to try and get my wireless working (Toshiba Satellite L40-18Z). No luck as of yet.

Just to make you aware, my wireless device seems to link to wlan1 rather than wlan0.

That doesn't matter, at all. All it means is that you have used another wireless card and which is the name of wlan0.
Your other wireless card is wlan1.

JUST make sure, for the RTL8187B card, use the right name. wlan0/wlan1

---

### Post by aa_siempre on 2008-08-30
Hi there. I've managed to follow your directions perfectly (I have an 8197, same Toshiba laptop as OP). Windows Wireless Drivers reports that the hardware is present, so obviously it's all going well. Wrong.

I have a 64-bit machine - both drivers report that the hardware is detected. I'm running KDE, which makes the latter part of your directions...different.

When I open the KDE network manager, it doesn't detect any wifi interface. 
I tried using wifi-radar, but that won't even start.

Any suggestions anybody?

---

### Post by Tom--d on 2008-08-30
> **aa_siempre said:**
> Hi there. I've managed to follow your directions perfectly (I have an 8197, same Toshiba laptop as OP). Windows Wireless Drivers reports that the hardware is present, so obviously it's all going well. Wrong.

I have a 64-bit machine - both drivers report that the hardware is detected. I'm running KDE, which makes the latter part of your directions...different.

When I open the KDE network manager, it doesn't detect any wifi interface. 
I tried using wifi-radar, but that won't even start.

Any suggestions anybody?

There are a few things around this :)
Post the outcome of:
```
iwconfig
```
then
```
sudo ifconfig wlan0 up && iwconfig
```

---

### Post by u_lone on 2008-08-30
Hi,

I have a Toshiba A300D-14D. Here is the lsusb outcome:
```
Bus 006 Device 002: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 004: ID **0bda:8197** Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 15ca:00c3  
Bus 001 Device 001: ID 0000:0000
```

I've followed the steps. It seems to work because after I go System > Admin > Windows Wireless Drivers and install the driver, it says:

[I][B]net8187b
Hardware Present: Yes[/B][/I]

As the Network Manager was not working, I've installed the wifi-radar. But it is not working too.

Here some outcome...

```
**$ ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117360 (114.6 KB)  TX bytes:117360 (114.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:e5:9b:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:44:e5:9b:48  
          inet addr:169.254.7.34  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

```
**$ iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
**$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:e5:9b:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
```

```
**$ iwlist scan**
lo        Interface doesn't support scanning.

wlan0     No scan results
```

I've also followed _[this thread]("http://ubuntuforums.org/showthread.php?t=684495")_ and on the last step (sudo dhclient wlan0) I got this:
```
There is already a pid file /var/run/dhclient.pid with pid 7538
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:44:e5:9b:48
Sending on   LPF/wlan0/00:16:44:e5:9b:48
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And nothing more happens.

I don't know how WiFi Radar was suppose to work, but I had to put my connection manually and after that try to connect. It try to acquire an IP, but 30 seconds later it stops.

---

### Post by Tom--d on 2008-08-31
> **u_lone said:**
> Hi,

I have a Toshiba A300D-14D. Here is the lsusb outcome:
```
Bus 006 Device 002: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 004: ID **0bda:8197** Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 15ca:00c3  
Bus 001 Device 001: ID 0000:0000
```

I've followed the steps. It seems to work because after I go System > Admin > Windows Wireless Drivers and install the driver, it says:

[I][B]net8187b
Hardware Present: Yes[/B][/I]

As the Network Manager was not working, I've installed the wifi-radar. But it is not working too.

Here some outcome...

```
**$ ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117360 (114.6 KB)  TX bytes:117360 (114.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:e5:9b:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:44:e5:9b:48  
          inet addr:169.254.7.34  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

```
**$ iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
**$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:e5:9b:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
```

```
**$ iwlist scan**
lo        Interface doesn't support scanning.

wlan0     No scan results
```

I've also followed _[this thread]("http://ubuntuforums.org/showthread.php?t=684495")_ and on the last step (sudo dhclient wlan0) I got this:
```
There is already a pid file /var/run/dhclient.pid with pid 7538
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:44:e5:9b:48
Sending on   LPF/wlan0/00:16:44:e5:9b:48
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And nothing more happens.

I don't know how WiFi Radar was suppose to work, but I had to put my connection manually and after that try to connect. It try to acquire an IP, but 30 seconds later it stops.

Wifi Radar will not work. 
You will need iwconfig to work and dhclient but I see it doesn't.

How about try other Drivers and modify them? (like the Windows XP one Windows ME etc. (Not Vista, Nidswarpper doesn't have support for them, yet).

---

### Post by u_lone on 2008-08-31
> **Tom--d said:**
> Wifi Radar will not work. 
You will need iwconfig to work and dhclient but I see it doesn't.

How about try other Drivers and modify them? (like the Windows XP one Windows ME etc. (Not Vista, Nidswarpper doesn't have support for them, yet).
It didn't work too.

I've also tried to change the approach following _[this]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b")_, but didn't work too. I got an error on this step:
```
**$ sudo ./wlan0up**
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

```

---

### Post by The Dork Lord on 2008-08-31
Having the same problem as U-Lone here, even turning off WEP at the router didn't allow me to join. Iwlist scanning does not reveal any networks either

---

### Post by aa_siempre on 2008-08-31
> **Tom--d said:**
> There are a few things around this :)
Post the outcome of:
```
iwconfig
```
then
```
sudo ifconfig wlan0 up && iwconfig
```

```
/home/adrian# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

```
~$ su -c 'ifconfig wlan0 up && iwconfig'
Password:
wlan0: ERROR while getting interface flags: No such device

```

I have tried using both the 32 and 64-bit drivers to no avail despite it saying that the hardware has been detected.

Somebody said back on page 6 that getting this to work on 64-bit Linux is impossible...am I going to have to install 32-bit?

---

### Post by Tom--d on 2008-09-01
> **aa_siempre said:**
> ```
/home/adrian# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

```
~$ su -c 'ifconfig wlan0 up && iwconfig'
Password:
wlan0: ERROR while getting interface flags: No such device

```

I have tried using both the 32 and 64-bit drivers to no avail despite it saying that the hardware has been detected.

Somebody said back on page 6 that getting this to work on 64-bit Linux is impossible...am I going to have to install 32-bit?

If you are using the 64 bit drivers and it said Hardware Present. Then there is a way around that. Its quite easy as well.

Let me look for it again (Forgot the commands etc)

Just can you post back here the MAC address of the wireless card.

---

### Post by aa_siempre on 2008-09-01
If iwconfig isn't showing any details of my wireless card, then how will I get Linux to see the wireless card in the first place in order to get my MAC? Presumably, I'll have to boot into Windows (where the wireless works) and ipconfig /all to get the MAC address...

I tried dmesg and that showed no sign of it either. As I said earlier, however, lsusb shows it (8197)

This is the output my router and ipconfig in Windows gives me for my MAC address: 00-16-44-82-9E-22

---

### Post by Xnst on 2008-09-02
Hi,

I am having the same problem as you guys. However. I downloaded the latest win-driver from realtek and used the Win2000 .inf file, modified as described elsewhere in this thread, and installed it with ndiswrapper. Now I get replies from $ iwlist scan searches and everything seems to work. But, it doesn't. I cannot connect to my network. Could be because I use WEP.

I do not have the time right now to pursue this. Hopefully, someone find this uncomplete information useful anyhow.

---

### Post by Tom--d on 2008-09-03
> **Xnst said:**
> Hi,

I am having the same problem as you guys. However. I downloaded the latest win-driver from realtek and used the Win2000 .inf file, modified as described elsewhere in this thread, and installed it with ndiswrapper. Now I get replies from $ iwlist scan searches and everything seems to work. But, it doesn't. I cannot connect to my network. Could be because I use WEP.

I do not have the time right now to pursue this. Hopefully, someone find this uncomplete information useful anyhow.

Right. Thats good :) Because thats the same with me. Cannot conenct to WEP (With Network Manager, its some bug they have got).

Try Wifi-Radar, install it (in the repos (add/remove) and then try to connect to it. It works for me with Wifi-Radar+WEP

---

### Post by Tom--d on 2008-09-03
> **aa_siempre said:**
> If iwconfig isn't showing any details of my wireless card, then how will I get Linux to see the wireless card in the first place in order to get my MAC? Presumably, I'll have to boot into Windows (where the wireless works) and ipconfig /all to get the MAC address...

I tried dmesg and that showed no sign of it either. As I said earlier, however, lsusb shows it (8197)

This is the output my router and ipconfig in Windows gives me for my MAC address: 00-16-44-82-9E-22

Thanks,
Sorry for the late reply. I've just started College. 

I will look into that now :)

---

### Post by Tom--d on 2008-09-03
> **aa_siempre said:**
> If iwconfig isn't showing any details of my wireless card, then how will I get Linux to see the wireless card in the first place in order to get my MAC? Presumably, I'll have to boot into Windows (where the wireless works) and ipconfig /all to get the MAC address...

I tried dmesg and that showed no sign of it either. As I said earlier, however, lsusb shows it (8197)

This is the output my router and ipconfig in Windows gives me for my MAC address: 00-16-44-82-9E-22

Right.
Install the WIn98 driver and then do this: (make sure the Hardware is Present!!)

Do this:
```
gksu gedit /etc/udev/rules.d/70.persistent-net.rules
```
and at a new line put this:
```
# USB device 0x0bda:0x8197 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:44:82:9E:22", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

Make sure you make no mistakes!
Reboot and then see if wireless is working.

---

### Post by aa_siempre on 2008-09-03
> **Tom--d said:**
> Right.
Install the WIn98 driver and then do this: (make sure the Hardware is Present!!)

Do this:
```
gksu gedit /etc/udev/rules.d/70.persistent-net.rules
```
and at a new line put this:
```
# USB device 0x0bda:0x8197 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:44:82:9E:22", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

Make sure you make no mistakes!
Reboot and then see if wireless is working.

Great! Thanks for the response. No need to apologise for the slight delay, I appreciate it greatly. I'll try this when I get home from work if I have time and I'll post the results.

Cheers.

---

### Post by aa_siempre on 2008-09-03
No luck with that. I've managed to create the file and add that line, as well as edit some other files in the /etc/udev/rules.d folder to include that line of code, but KDE network manager isn't showing it, and iwconfig shows nothing. I'm not sure what the problem is. I've even tried with the Win 2000 drivers.

---

### Post by Tom--d on 2008-09-04
Post the outcomes of:
```
lsusb
```
```
lspci
```
```
lshw
```
```
ndiswrapper -l
```

---

### Post by aa_siempre on 2008-09-06
> **Tom--d said:**
> Post the outcomes of:
```
lsusb
```
```
lspci
```
```
lshw
```
```
ndiswrapper -l
```

```
/home/adrian# lsusb
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 007 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp.
Bus 007 Device 002: ID 05e3:0608 Genesys Logic, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000

```

```
/home/adrian# lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)

```

```
/home/adrian# lshw
aalin
    description: Computer
    product: EQUIUM A200
    vendor: TOSHIBA
    version: PSAF5E-002005KS
    serial: Z7044213Q
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=oem-specific uuid=1850DBE0-A05C-11DC-A70E-00A0D18FBADB
  *-core
       description: Motherboard
       product: SANTA ROSA CRB
       vendor: Intel Corporation
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.70 (11/06/2007)
          size: 104KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 1460MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capacity: 4MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:f5000000-f50fffff iomemory:d0000000-dfffffff ioport:1800-1807 irq:5
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 1MB
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:f5100000-f51fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:58
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f5404800-f5404bff irq:185
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:f5200000-f5203fff irq:90
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 14
                serial: 00:a0:d1:8f:ba:db
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.5 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:f0000000-f0003fff ioport:2000-20ff irq:82
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:66
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:18a0-18bf irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f5404c00-f5404fff irq:66
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.18-6-amd64 ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 1
                   bus info: usb@7:1
                   version: 7.02
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                 *-usb:0
                      description: Mass storage device
                      product: Cypress AT2LP
                      vendor: Cypress Semiconductor Corp.
                      physical id: 1
                      bus info: usb@7:1.1
                      logical name: scsi0
                      version: 2.40
                      serial: DEF10C13B1CD
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
                    *-disk
                         description: SCSI Disk
                         product: DK23FB-60
                         vendor: HITACHI_
                         physical id: 0.0.0
                         bus info: scsi@0:0.0.0
                         logical name: /dev/sdb
                         version: 0000
                         size: 55GB
                         capabilities: partitioned partitioned:dos
                       *-volume:0
                            description: HPFS/NTFS partition
                            physical id: 1
                            bus info: scsi@0:0.0.0,1
                            logical name: /dev/sdb1
                            capacity: 27GB
                            capabilities: primary
                       *-volume:1
                            description: W95 FAT32 (LBA) partition
                            physical id: 2
                            bus info: scsi@0:0.0.0,2
                            logical name: /dev/sdb2
                            capacity: 18GB
                            capabilities: primary
                       *-volume:2
                            description: Linux filesystem partition
                            physical id: 3
                            bus info: scsi@0:0.0.0,3
                            logical name: /dev/sdb3
                            capacity: 9491MB
                            capabilities: primary bootable
                       *-volume:3
                            description: Extended partition
                            physical id: 4
                            bus info: scsi@0:0.0.0,4
                            logical name: /dev/sdb4
                            size: 470MB
                            capacity: 470MB
                            capabilities: primary extended partitioned partitioned:extended
                          *-logicalvolume
                               description: Linux swap / Solaris partition
                               physical id: 5
                               logical name: /dev/sdb5
                               capacity: 470MB
                               capabilities: nofs
                 *-usb:1
                      description: Mouse
                      product: Microsoft Wheel Mouse Optical
                      vendor: Microsoft
                      physical id: 3
                      bus info: usb@7:1.3
                      version: 1.21
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: RTL8187B_WLAN_Adapter
                   vendor: Manufacturer_Realtek
                   physical id: 6
                   bus info: usb@7:6
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: Mobile IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=0
             resources: ioport:1810-181f irq:193
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorp CDDVDW TS-L632H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: TO01
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
                      capabilities: partitioned partitioned:mac
                    *-volume:0 UNCLAIMED
                         description: Apple partition map
                         physical id: 1
                         capacity: 1KB
                    *-volume:1 UNCLAIMED
                         description: Apple HFS
                         physical id: 2
                         capacity: 4185MB
        *-storage
             description: SATA controller
             product: Mobile SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: ioport:1c00-1c07 ioport:18d4-18d7 ioport:18d8-18df ioport:18d0-18d3 ioport:18e0-18ff iomemory:f5404000-f54047ff irq:74
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK1237GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: DL13
                serial: Y7DEFBXLS
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Primary partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 1500MB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 55GB
                   capabilities: primary
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 54GB
                   capabilities: primary
        *-serial
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:88000000-880000ff ioport:1c20-1c3f irq:193

```

```
:/home/adrian# ndiswrapper -l
installed drivers:
net8187b                driver installed, hardware (0BDA:8197) present

```

It's all there... even lshw lists it as present but says "*-usb:1 UNCLAIMED". (8187B driver)

---

### Post by Tom--d on 2008-09-06
Are you on 64bit or 32bit?

---

### Post by aa_siempre on 2008-09-06
64-bit processor, so I'm running 64-bit linux. That's what the installer auto-detected anyway. I've tried the 64-bit driver and it doesn't work either.

---

### Post by Tom--d on 2008-09-07
> **aa_siempre said:**
> 64-bit processor, so I'm running 64-bit linux. That's what the installer auto-detected anyway. I've tried the 64-bit driver and it doesn't work either.

Thats your problem. 
The Win98 is 32bit driver. It will not work within 64bit. The 64bit drivers dont work either. 

If you want to get this card to work. I suggest 32bit. (it will work fine with your processor. You just might see a slight difference in speed when it comes to encoding.

---

### Post by aa_siempre on 2008-09-07
Ok I'll give it a shot when I have a chance. Thanks for the advice.

---

### Post by aa_siempre on 2008-09-22
Ok - I reinstalled onto 32-bit Linux, with GNOME and everything. Followed the instructions to the word, ndiswrapper and ndisgtk both say "hardware present", lshw says "unclaimed" like before.

wifi-radar doesn't detect anything, ifconfig shows nothing, iwconfig shows nothing.

Now I'm really stumped!

---

### Post by Tom--d on 2008-09-22
> **aa_siempre said:**
> Ok - I reinstalled onto 32-bit Linux, with GNOME and everything. Followed the instructions to the word, ndiswrapper and ndisgtk both say "hardware present", lshw says "unclaimed" like before.

wifi-radar doesn't detect anything, ifconfig shows nothing, iwconfig shows nothing.

Now I'm really stumped!

There are a few things around this:

Before you check ifconfig, do this command:
```
sudo ifconfig wlan0 up
```
If ifconfig doesn't spit anything out. Your good :) Then check ifconfig and wlan0 'should be there'

If that doesnt work. 
Can you please tell me the mac address of your wireless card.

---

### Post by aa_siempre on 2008-09-22
I'll try that command next time I'm home and have the time, thanks!

Regarding the MAC Address, I gave that to you earlier and have again done as you outlined in [ This post]("http://ubuntuforums.org/showpost.php?p=5718091&postcount=118")

---

### Post by Tom--d on 2008-09-22
> **aa_siempre said:**
> I'll try that command next time I'm home and have the time, thanks!

Regarding the MAC Address, I gave that to you earlier and have again done as you outlined in [ This post]("http://ubuntuforums.org/showpost.php?p=5718091&postcount=118")

Ah, yeah. Your the same guy :p
Well. Im stumped!

Post the outcome of dmesg (will be long, for debugging really)

---

### Post by aa_siempre on 2008-09-22
Outcomes

> aadeb:/home/adrian# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device



Ubuntu forums give me some ******** error when I try and post dmesg, something about images in my message.

---

### Post by Tom--d on 2008-09-23
> **aa_siempre said:**
> Outcomes




Ubuntu forums give me some ******** error when I try and post dmesg, something about images in my message.

Right, do this command before you post dmesg.
```
sudo modprobe ndiswrapper
```
and now:
copy the hole outcome of dmesg (Crtl+A) and then copy it and past it in here BUT put it in

 [*code]dmesg-output-here[*/code]

**WITHOUT the *!!!!!**

---

### Post by Tom--d on 2008-09-24
I have now heard that there is native support for this wireless card in the new kernel (2.6.27).
The kernel will be in 8.10

:D

---

### Post by aa_siempre on 2008-09-24
Great news! The new kernel is available in Alpha 6 of Intrepid Ibex, available here:[http://www.ubuntu.com/testing/intrepid/alpha6]("http://www.ubuntu.com/testing/intrepid/alpha6")

I'm going to download it and give it a test when I can. Will report back the results.

---

### Post by Tom--d on 2008-09-24
> **aa_siempre said:**
> Great news! The new kernel is available in Alpha 6 of Intrepid Ibex, available here:[http://www.ubuntu.com/testing/intrepid/alpha6]("http://www.ubuntu.com/testing/intrepid/alpha6")

I'm going to download it and give it a test when I can. Will report back the results.

Cool.
I will download it as well to see :)

Just be careful with it. Strange things might happen since its alpha ;)

---

### Post by Tom--d on 2008-09-24
**It worked OUT OF THE BOX! :D:D**

Network Manager was working.
Connected to my wireless which has WEP on it fine and was on the internet :)

---

### Post by Tom--d on 2008-10-15
Run this command if it keeps on dropping:

```
sudo iwconfig wlan0 rate 5.5M fixed
```

Sorts ALL the problems :)

---

### Post by johanhartman on 2008-10-21
I'm no expert :D, so bear with me...

A while ago with the software updates (synaptic) I got an update for linux headers to 2.6.24-21-generic. One of the notes with the update mentioned something about native support for rtl8187. Does anyone know about this, because I would be all too happy if this would give me better support than ndiswrapper with my wifi card (which works but has some problems).

[2.6.24-21-generic-after.dmesg]("http://launchpadlibrarian.net/18673629/2.6.24-21-generic-after.dmesg")

ctrl + f --> "rtl" on the page linked above will show what I mean. Please inform if I understand correctly, if this is at all relevant to me.

PS: I'm using Hardy.

---

### Post by Tom--d on 2008-10-21
> **johanhartman said:**
> I'm no expert :D, so bear with me...

A while ago with the software updates (synaptic) I got an update for linux headers to 2.6.24-21-generic. One of the notes with the update mentioned something about native support for rtl8187. Does anyone know about this, because I would be all too happy if this would give me better support than ndiswrapper with my wifi card (which works but has some problems).

[2.6.24-21-generic-after.dmesg]("http://launchpadlibrarian.net/18673629/2.6.24-21-generic-after.dmesg")

ctrl + f --> "rtl" on the page linked above will show what I mean. Please inform if I understand correctly, if this is at all relevant to me.

PS: I'm using Hardy.


Nono, 
The support is on the new Kernel (2.6.27) which is in Ubuntu 8.10 (released on the 30th October). Ubuntu 8.04's Kernel is 2.6.24. The update you got it probably for bug fixes.

RE-read the first bit of my first post. The blue writing. It all explains there, and if anymore help. Just ask!
(with 8.10, remember to run that command 'sudo iwconfig wlan0 rate 5.5M fixed' to solve all the problems with the native driver. The bug is known and hopefully be fixed soon). You can put that command in the file /etc/rc.local to run it everytime you boot. Just put it BEFORE the exit 0

---

### Post by johanhartman on 2008-10-21
okay, ill wait till 8.10 is a little more stable and then i'll finally be freeeeee

---

### Post by Tom--d on 2008-10-21
> **johanhartman said:**
> okay, ill wait till 8.10 is a little more stable and then i'll finally be freeeeee

Hehe, yeah. But to be honest. Most of the software is stable. (The kernel, gnome 2.24 etc).

---

### Post by johanhartman on 2008-11-01
Me again! I'm working from the live cd of intrepid (which works perfectly, even network manager and my wireless card!). I also upgraded my hardy install to intrepid, but for some reason the wireless doesn't work as it does on the live cd. Could this be because this tutorial left some loose ends that network manager could not tie up?

---

### Post by ixenn on 2008-11-02
Hi there, I also cannot get my card working after an upgrade from 8.04 2 hours ago. I was only using ndiswrapper drivers before. I have removed all instances of ndiswrapper and sudo modprobe -r ndiswrapper and it seems like the card is being detected but ubuntu just can't assign a driver to it?

this is the output from lshw -C network


*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:f2:0c:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

This is after I have ran the 'sudo ifconfig wlan0 up' command, before running this it says *-network:0 Disabled


this is the line in my 70-persistent-net rules


# USB device 0x0bda:0x8189 (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:a8:f2:0c:06", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


I need to get this going and feel as if though im on the verge of a breakthrough. Thanks for any help.

---

### Post by Tom--d on 2008-11-02
> **ixenn said:**
> Hi there, I also cannot get my card working after an upgrade from 8.04 2 hours ago. I was only using ndiswrapper drivers before. I have removed all instances of ndiswrapper and sudo modprobe -r ndiswrapper and it seems like the card is being detected but ubuntu just can't assign a driver to it?

this is the output from lshw -C network


*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:f2:0c:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

This is after I have ran the 'sudo ifconfig wlan0 up' command, before running this it says *-network:0 Disabled


this is the line in my 70-persistent-net rules


# USB device 0x0bda:0x8189 (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:a8:f2:0c:06", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


I need to get this going and feel as if though im on the verge of a breakthrough. Thanks for any help.




Do this and see if wireless works.

```
sudo modprobe rtl8187
```

Does it work then?

---

### Post by Tom--d on 2008-11-02
> **johanhartman said:**
> Me again! I'm working from the live cd of intrepid (which works perfectly, even network manager and my wireless card!). I also upgraded my hardy install to intrepid, but for some reason the wireless doesn't work as it does on the live cd. Could this be because this tutorial left some loose ends that network manager could not tie up?

There is a problem with upgrading.
I think this is why:

Because in Hardy you are using Ndiswrapper. When upgrading, Ubuntu still thinks that that wireless card is only going to be used by the ndiswrapper driver. Not the rtl8187 driver.
By removing ndiswrapper and doing this command:
```
sudo modprobe rtl8187
```
The wireless should be working, if so.

Add rtl8187 to the file, /etc/modprobe.conf
```
gksu gedit /etc/modprobe.conf
```
This then loads up the driver at start up.

---

### Post by mrmond on 2008-11-02
> **Tom--d said:**
> **It worked OUT OF THE BOX! :D:D**

Network Manager was working.
Connected to my wireless which has WEP on it fine and was on the internet :)


Using a Toshiba L350D Equium
No wireless detected using intrepid live cd.
On hardy ndiswrapper shows networks using xp32bit driver but can't connect even with encryption turned off.
Hoped 8.10 would solve my problems with 8187b driver but doesn't seem to be detected on my machine.

Very frustrated.

---

### Post by noodles222 on 2008-11-02
hi

i am using Toshiba satellite A210, realtek rtl8187b works great on 8.10 ubuntu now but when i connect to a network in ubuntu it works and when i reboot into vista (i have dual boot vista and ubuntu) and want to connect to the same network i cant!!! WHY??

---

### Post by johanhartman on 2008-11-02
Same for me, although I'm not too worried. With Hardy it still worked in Vista with a little coaxing but now I can't connect at all in Vista. But as I said in intrepid it works fine now - thanks to Tom--d - it even connects automatically on startup without kicking everyone off the network (as it did with ndiswrapper in hardy).

---

### Post by ixenn on 2008-11-02
sudo modprobe rtl8187 does not change anything, it does not return any errors though, ive also added rtl8187 to /etc/modules. dmesg shows it loading at startup

---

### Post by Thrawns Spawn on 2008-11-02
hi guys,  i was just wondering if anything in this thread would be useful for my card? I run a belkin f5d7050 v5, with the chipset being realtek rtl8187b. using lsusb command i get 'belkin corp..... id 050d:705e'. i am trying to use ndiswrapper, it says hardware is present. however i do not have a wlan channel in 'lshw -c network'. 

thank you in advance

---

### Post by Tom--d on 2008-11-02
> **mrmond said:**
> Using a Toshiba L350D Equium
No wireless detected using intrepid live cd.
On hardy ndiswrapper shows networks using xp32bit driver but can't connect even with encryption turned off.
Hoped 8.10 would solve my problems with 8187b driver but doesn't seem to be detected on my machine.

Very frustrated.

Can you please post the outcome of:
```
lsusb
```

Thanks.

---

### Post by Tom--d on 2008-11-02
> **ixenn said:**
> sudo modprobe rtl8187 does not change anything, it does not return any errors though, ive also added rtl8187 to /etc/modules. dmesg shows it loading at startup

Right now post the outcome of 'dmesg' (It will be long).
Thanks.

---

### Post by Tom--d on 2008-11-02
> **noodles222 said:**
> hi

i am using Toshiba satellite A210, realtek rtl8187b works great on 8.10 ubuntu now but when i connect to a network in ubuntu it works and when i reboot into vista (i have dual boot vista and ubuntu) and want to connect to the same network i cant!!! WHY??

Strange!

In Vista, can you search networks? Does Wireless even work?

---

### Post by ixenn on 2008-11-02
thanks i just did a clean install. to much hassle

---

### Post by Tom--d on 2008-11-02
> **Thrawns Spawn said:**
> hi guys,  i was just wondering if anything in this thread would be useful for my card? I run a belkin f5d7050 v5, with the chipset being realtek rtl8187b. using lsusb command i get 'belkin corp..... id 050d:705e'. i am trying to use ndiswrapper, it says hardware is present. however i do not have a wlan channel in 'lshw -c network'. 

thank you in advance


Can you please try Ubuntu 8.10 LiveCD and see if Wireless works?

---

### Post by ixenn on 2008-11-02
I have noticed that my wireless speed has been greatly reduced. I had been able to download at 500-700kb/s now its 300-450kb/s.

---

### Post by mrmond on 2008-11-02
> **Tom--d said:**
> Can you please post the outcome of:
```
lsusb
```

Thanks.

Will try in morning but have just looked on my windows partition before going to bed and hardware id from system properties says 8198, not 8197

Got the feeling that if this is the problem I'm up the creek.
:(
I think another guide for using ndiswrapper and the modified driver said it would only work for 8197.
thanks for any info.

mrmond

ok just found my 8.10 live cd.

lsusb does indeed report 8198 as the id for realtek network.

sudo modprobe rtl8197 then lsmod showed module as loaded but nothing from connection manager.

D'ya think ndiswrapper is the way to go  ?

---

### Post by Tom--d on 2008-11-03
> **ixenn said:**
> I have noticed that my wireless speed has been greatly reduced. I had been able to download at 500-700kb/s now its 300-450kb/s.

Have you put iwconfig wlan0 rate 5.5M fixed in /etc/rc.local?

---

### Post by Tom--d on 2008-11-03
> **mrmond said:**
> Will try in morning but have just looked on my windows partition before going to bed and hardware id from system properties says 8198, not 8197

Got the feeling that if this is the problem I'm up the creek.
:(
I think another guide for using ndiswrapper and the modified driver said it would only work for 8197.
thanks for any info.

mrmond

ok just found my 8.10 live cd.

lsusb does indeed report 8198 as the id for realtek network.

sudo modprobe rtl8197 then lsmod showed module as loaded but nothing from connection manager.

D'ya think ndiswrapper is the way to go  ?


Aha, the ID of 8198. It will work.
The rtl8187 driver doesnt have support for the 8198 driver (YET! Talks about it!) so ndiswrapper will be used.
With the driver I posted on the 1st post. Download it, extract and then go into the net8187.inf file. Find this:
```
;;****************************************************************************

;; IDs for 98SE/ME/2K/XP

;;****************************************************************************

[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```
and change the PID_8187 to PID_8198 and install the driver in ndiswrapper.

That should do it.

Its the same wireless card with a different ID number, thats all.

---

### Post by Thrawns Spawn on 2008-11-03
no it will not work on live cd.

---

### Post by johanhartman on 2008-11-03
When I upgraded from hardy to intrepid and started using network-manager again I noticed that in the NetworkManager Applet under wireless networks, it said; "device unmanaged".

Just FYI, to fix this:
```

gksu gedit /etc/NetworkManager/nm-system-settings.conf
```

then change:
> [ifupdown]
managed=false

to:
> [ifupdown]
managed=true

This will probably apply to most user of this tutorial...

---

### Post by Tom--d on 2008-11-03
> **Thrawns Spawn said:**
> no it will not work on live cd.


Are you sure its a rtl8187B chipset?

---

### Post by Tom--d on 2008-11-03
> **johanhartman said:**
> When I upgraded from hardy to intrepid and started using network-manager again I noticed that in the NetworkManager Applet under wireless networks, it said; "device unmanaged".

Just FYI, to fix this:
```

gksu gedit /etc/NetworkManager/nm-system-settings.conf
```

then change:


to:


This will probably apply to most user of this tutorial...

Thank you.
but my /etc/NetworkManager/nm-system-settings.conf says down... and my wireless still works.

---

### Post by noodles222 on 2008-11-03
> Strange!

In Vista, can you search networks? Does Wireless even work?

yes, thats strange i know, yep i can see wireless networks but cant connect to those used in ubuntu

---

### Post by Tom--d on 2008-11-03
> **noodles222 said:**
> yes, thats strange i know, yep i can see wireless networks but cant connect to those used in ubuntu

Very strange! I do not know what to do here due to I haven't been on a Windows machine for a while now. Sorry I can't help.

---

### Post by noodles222 on 2008-11-04
seeems to me like it is a ubuntu bug or something cause i reinstall completly Vista and Ubuntu, put new drivers and also BIOS - uuuf.. so i dont know, it seems like something is blocking wireless in ubuntu even after restart... as i said, only thing to fix it is always shut down computer!!!!

---

### Post by Tom--d on 2008-11-04
> **noodles222 said:**
> seeems to me like it is a ubuntu bug or something cause i reinstall completly Vista and Ubuntu, put new drivers and also BIOS - uuuf.. so i dont know, it seems like something is blocking wireless in ubuntu even after restart... as i said, only thing to fix it is always shut down computer!!!!

Very strange.
Report that as a bug in Launchpad and see if there is any news on it. And it might get fixed.

---

### Post by darth.k on 2008-11-04
Hi guys, I've been trying all day to get my card, the 8197, to work using this guide.  I've installed ndiswrapper and have installed the win98 drivers.  This seems to work to a certain extent, I can see all the wireless networks in my building including my own, which has a strong signal.  My problem however is when I try to connect to the network.  I input my wep information and I get both little green spheres to light green however it stalls after this and fails to connect stating "requesting network address from the wireless network" before failing.  Using 8.1, for info;

lsusb;

```
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci;

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"O2wirelessD51446"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:9F:44:EA:5F   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by johanhartman on 2008-11-05
Hi,

although my wireless is now working with the rtl8187 driver that comes with 8.10, it is a bit intermittant and the range is reduced to such an extent that I cannot connect in the room I used to with ndiswrapper. I have to move closer to the router now (but that is on the stairs... not comfortable!).

Is there any way to fix this since using the new network manager is much nicer than wicd and the ndiswrapper has other problems.

BTW: I have tried;
```
sudo iwconfig wlan0 rate 5.5M fixed
```

---

### Post by Tom--d on 2008-11-05
> **darth.k said:**
> Hi guys, I've been trying all day to get my card, the 8197, to work using this guide.  I've installed ndiswrapper and have installed the win98 drivers.  This seems to work to a certain extent, I can see all the wireless networks in my building including my own, which has a strong signal.  My problem however is when I try to connect to the network.  I input my wep information and I get both little green spheres to light green however it stalls after this and fails to connect stating "requesting network address from the wireless network" before failing.  Using 8.1, for info;

lsusb;

```
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci;

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"O2wirelessD51446"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:9F:44:EA:5F   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


Are you on Intrepid or Hardy?
If Interpid, read the very first part of the thread. Its got native support now and should work out of the box. But read it first and do the commands there.

---

### Post by Tom--d on 2008-11-05
> **johanhartman said:**
> Hi,

although my wireless is now working with the rtl8187 driver that comes with 8.10, it is a bit intermittant and the range is reduced to such an extent that I cannot connect in the room I used to with ndiswrapper. I have to move closer to the router now (but that is on the stairs... not comfortable!).

Is there any way to fix this since using the new network manager is much nicer than wicd and the ndiswrapper has other problems.

BTW: I have tried;
```
sudo iwconfig wlan0 rate 5.5M fixed
```

I know. The range is reduced. I noticed that. I guess ndiswrapper is your only option I guess.
Just blacklist the module rtl8187 in /etc/modprobe.d/blacklist

---

### Post by darth.k on 2008-11-05
> **Tom--d said:**
> Are you on Intrepid or Hardy?
If Interpid, read the very first part of the thread. Its got native support now and should work out of the box. But read it first and do the commands there.

Thanks for the reply.

I tried the guide on 8.04 and had this problem.  I then disabled the driver in ndiswrapper before uninstalling it and upgrading to 8.10.  After the upgrade the wireless wasn't reqcognised at all so I reinstalled ndiswrapper and the win98 drivers and I'm back to the same problem, I can see my network but can't connect.

---

### Post by Tom--d on 2008-11-05
> **darth.k said:**
> Thanks for the reply.

I tried the guide on 8.04 and had this problem.  I then disabled the driver in ndiswrapper before uninstalling it and upgrading to 8.10.  After the upgrade the wireless wasn't reqcognised at all so I reinstalled ndiswrapper and the win98 drivers and I'm back to the same problem, I can see my network but can't connect.

I know your problem.

Remove Network Manager and Network Manager Gnome from Synaptic Package Manager then install Wifi-Radar (Does the same thing as Networkmanager but better for this card (And actually connects. Its what I used when I have ndiswrapper running). It will connect at boot. No password needed. :)

---

### Post by darth.k on 2008-11-05
Thanks, did a fresh install all good now!

---

### Post by johanhartman on 2008-11-07
> **Tom--d said:**
> I know your problem.

Remove Network Manager and Network Manager Gnome from Synaptic Package Manager then install Wifi-Radar (Does the same thing as Networkmanager but better for this card (And actually connects. Its what I used when I have ndiswrapper running). It will connect at boot. No password needed. :)

That... and network manager has recently started causing kernel panics for me:(

---

### Post by Tom--d on 2008-11-07
> **johanhartman said:**
> That... and network manager has recently started causing kernel panics for me:(

Could not be network Manager, could be the driver.
Right, when all loaded up. go on the internet.. look around etc.

Then, like in 5 mins of browsing, post here the outcome dmesg please.

---

### Post by johanhartman on 2008-11-07
I'm thinking that its nm because it first happened when I accidentally tried to connect to a wireless network at work (I always use ethernet there). It tried to connect for a second or two then went into kernel panic, after I reboot after the hard shutdown it logged in and immediately locked up again. This happened two more times then I realised that instead of logging in I can switch to tty1 where it wouldn't lock up. There I uninstalled nm, the kernel panics stopped then. so its something to do with nm or a combination between nm and the driver.

I re-installed nm again and got a panic once during shutdown but not any more. Here's the dmesg anyway:
```
[    1.085081] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    1.085090] PCI: bridge 0000:00:1e.0 32bit mmio: [fe600000, fe6fffff]
[    1.085136] bus 00 -> node 0
[    1.085159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.085975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.086346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.086814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.146160] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    1.148333] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    1.148863] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    1.149391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    1.149918] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[    1.150437] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    1.150964] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    1.151492] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    1.157886] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - B4, should be 4A [20080609]
[    1.157915] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.157944] pnp: PnP ACPI init
[    1.157944] ACPI: bus type pnp registered
[    1.165951] pnp: PnP ACPI: found 13 devices
[    1.165951] ACPI: ACPI bus type pnp unregistered
[    1.165951] PnPBIOS: Disabled by ACPI PNP
[    1.168085] PCI: Using ACPI for IRQ routing
[    1.172052] NET: Registered protocol family 8
[    1.172058] NET: Registered protocol family 20
[    1.172096] NetLabel: Initializing
[    1.172096] NetLabel:  domain hash size = 128
[    1.172096] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.172117] NetLabel:  unlabeled traffic allowed by default
[    1.172129] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.172142] hpet0: 3 64-bit timers, 14318180 Hz
[    1.174324] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.174332]    actual entries 65620
[    1.174517] AppArmor: AppArmor Filesystem Enabled
[    1.174552] ACPI: RTC can wake from S4
[    1.176047] Switched to high resolution mode on CPU 0
[    1.176811] Switched to high resolution mode on CPU 1
[    1.180059] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.180091] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.180099] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.180106] system 00:08: ioport range 0x400-0x41f has been reserved
[    1.180113] system 00:08: ioport range 0x500-0x53f has been reserved
[    1.180121] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.180129] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.180137] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    1.180145] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    1.180153] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.180170] system 00:0a: ioport range 0x250-0x253 has been reserved
[    1.180178] system 00:0a: ioport range 0x256-0x25f has been reserved
[    1.180185] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.180193] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.180209] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    1.180225] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.180232] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    1.180240] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.180247] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    1.217049] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.217055] pci 0000:00:1c.0:   IO window: disabled
[    1.217066] pci 0000:00:1c.0:   MEM window: disabled
[    1.217074] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.217086] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.217092] pci 0000:00:1c.1:   IO window: disabled
[    1.217102] pci 0000:00:1c.1:   MEM window: disabled
[    1.217110] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.217122] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.217130] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    1.217141] pci 0000:00:1c.2:   MEM window: 0xfde00000-0xfe5fffff
[    1.217151] pci 0000:00:1c.2:   PREFETCH window: 0x000000bdf00000-0x000000bfefffff
[    1.217164] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.217172] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    1.217182] pci 0000:00:1e.0:   MEM window: 0xfe600000-0xfe6fffff
[    1.217191] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.217223] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.217234] pci 0000:00:1c.0: setting latency timer to 64
[    1.217251] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.217260] pci 0000:00:1c.1: setting latency timer to 64
[    1.217278] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.217287] pci 0000:00:1c.2: setting latency timer to 64
[    1.217302] pci 0000:00:1e.0: setting latency timer to 64
[    1.217310] bus: 00 index 0 io port: [0, ffff]
[    1.217315] bus: 00 index 1 mmio: [0, ffffffff]
[    1.217320] bus: 01 index 0 mmio: [0, 0]
[    1.217325] bus: 01 index 1 mmio: [0, 0]
[    1.217330] bus: 01 index 2 mmio: [0, 0]
[    1.217335] bus: 01 index 3 mmio: [0, 0]
[    1.217339] bus: 02 index 0 mmio: [0, 0]
[    1.217344] bus: 02 index 1 mmio: [0, 0]
[    1.217349] bus: 02 index 2 mmio: [0, 0]
[    1.217353] bus: 02 index 3 mmio: [0, 0]
[    1.217358] bus: 03 index 0 io port: [b000, bfff]
[    1.217364] bus: 03 index 1 mmio: [fde00000, fe5fffff]
[    1.217369] bus: 03 index 2 mmio: [bdf00000, bfefffff]
[    1.217374] bus: 03 index 3 mmio: [0, 0]
[    1.217379] bus: 05 index 0 io port: [c000, cfff]
[    1.217384] bus: 05 index 1 mmio: [fe600000, fe6fffff]
[    1.217389] bus: 05 index 2 mmio: [0, 0]
[    1.217394] bus: 05 index 3 io port: [0, ffff]
[    1.217399] bus: 05 index 4 mmio: [0, ffffffff]
[    1.217419] NET: Registered protocol family 2
[    1.232120] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.232652] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.233338] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.233805] TCP: Hash tables configured (established 131072 bind 65536)
[    1.233813] TCP reno registered
[    1.240199] NET: Registered protocol family 1
[    1.240456] checking if image is initramfs... it is
[    2.935610] Freeing initrd memory: 7927k freed
[    2.936226] Simple Boot Flag at 0x51 set to 0x1
[    2.938103] audit: initializing netlink socket (disabled)
[    2.938143] type=2000 audit(1226085295.936:1): initialized
[    2.952705] highmem bounce pool size: 64 pages
[    2.952719] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.958391] VFS: Disk quotas dquot_6.5.1
[    2.958596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.958827] msgmni has been set to 1762
[    2.959110] io scheduler noop registered
[    2.959117] io scheduler anticipatory registered
[    2.959123] io scheduler deadline registered
[    2.959151] io scheduler cfq registered (default)
[    2.959178] pci 0000:00:02.0: Boot video device
[    3.006797] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.006862] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.006931] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.007037] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.007231] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.007294] pcieport-driver 0000:00:1c.1: found MSI capability
[    3.007359] pci_express 0000:00:1c.1:pcie00: allocate port service
[    3.007462] pci_express 0000:00:1c.1:pcie03: allocate port service
[    3.007656] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    3.007721] pcieport-driver 0000:00:1c.2: found MSI capability
[    3.007787] pci_express 0000:00:1c.2:pcie00: allocate port service
[    3.007883] pci_express 0000:00:1c.2:pcie02: allocate port service
[    3.007973] pci_express 0000:00:1c.2:pcie03: allocate port service
[    3.008715] isapnp: Scanning for PnP cards...
[    3.362504] isapnp: No Plug & Play device found
[    3.442510] hpet_resources: 0xfed00000 is busy
[    3.442737] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.447997] brd: module loaded
[    3.448167] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.448474] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.451033] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.451692] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.451706] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.451713] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.451719] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.451725] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.452638] mice: PS/2 mouse device common for all mice
[    3.452934] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.452971] rtc0: alarms up to one month, y3k, hpet irqs
[    3.453305] EISA: Probing bus 0 at eisa.0
[    3.453355] EISA: Detected 0 cards.
[    3.453362] cpuidle: using governor ladder
[    3.453368] cpuidle: using governor menu
[    3.454607] TCP cubic registered
[    3.454664] Using IPI No-Shortcut mode
[    3.455104] registered taskstats version 1
[    3.455355]   Magic number: 0:739:242
[    3.455404] tty ttysf: hash matches
[    3.455561] rtc_cmos 00:03: setting system clock to 2008-11-07 19:14:57 UTC (1226085297)
[    3.455569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.455574] EDD information not available.
[    3.455938] Freeing unused kernel memory: 424k freed
[    3.456030] Write protecting the kernel text: 2576k
[    3.456095] Write protecting the kernel read-only data: 936k
[    3.489001] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.745186] fuse init (API version 7.9)
[    3.817084] ACPI: SSDT 3F7B83D0, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    3.818542] ACPI: SSDT 3F7B86B0, 060F (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    3.821230] Monitor-Mwait will be used to enter C-1 state
[    3.821238] Monitor-Mwait will be used to enter C-2 state
[    3.821245] Monitor-Mwait will be used to enter C-3 state
[    3.821708] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.821845] processor ACPI0007:00: registered as cooling_device0
[    3.821856] ACPI: Processor [P001] (supports 8 throttling states)
[    3.822671] ACPI: SSDT 3F7B8300, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    3.824066] ACPI: SSDT 3F7B8620, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    3.828023] Marking TSC unstable due to TSC halts in idle
[    3.847461] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.847597] processor ACPI0007:01: registered as cooling_device1
[    3.847608] ACPI: Processor [P002] (supports 8 throttling states)
[    3.853812] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    3.874270] ACPI: Expecting a [Reference] package element, found type C
[    3.874730] thermal LNXTHERM:01: registered as thermal_zone0
[    3.882740] ACPI: Thermal Zone [THRM] (56 C)
[    4.223173] usbcore: registered new interface driver usbfs
[    4.223225] usbcore: registered new interface driver hub
[    4.230333] usbcore: registered new device driver usb
[    4.236228] USB Universal Host Controller Interface driver v3.0
[    4.236312] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.236330] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.236338] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.236428] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.236481] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    4.236747] usb usb1: configuration #1 chosen from 1 choice
[    4.236812] hub 1-0:1.0: USB hub found
[    4.236828] hub 1-0:1.0: 2 ports detected
[    4.444446] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.444465] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.444474] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.444544] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    4.444595] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    4.444795] usb usb2: configuration #1 chosen from 1 choice
[    4.444860] hub 2-0:1.0: USB hub found
[    4.444876] hub 2-0:1.0: 2 ports detected
[    4.548444] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.548463] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.548472] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.548530] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.548583] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    4.548794] usb usb3: configuration #1 chosen from 1 choice
[    4.548864] hub 3-0:1.0: USB hub found
[    4.548880] hub 3-0:1.0: 2 ports detected
[    4.556044] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.652407] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.652426] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.652435] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.652490] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    4.652542] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    4.652748] usb usb4: configuration #1 chosen from 1 choice
[    4.652815] hub 4-0:1.0: USB hub found
[    4.652830] hub 4-0:1.0: 2 ports detected
[    4.724776] usb 1-2: configuration #1 chosen from 1 choice
[    4.753707] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.833166] No dock devices found.
[    4.861457] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.861475] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.861484] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.861553] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    4.861611] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    4.861819] usb usb5: configuration #1 chosen from 1 choice
[    4.861883] hub 5-0:1.0: USB hub found
[    4.861898] hub 5-0:1.0: 2 ports detected
[    4.917913] SCSI subsystem initialized
[    4.957896] libata version 3.00 loaded.
[    4.968905] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.968933] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.968941] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.969027] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    4.972948] ehci_hcd 0000:00:1a.7: debug port 1
[    4.972960] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.972978] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaff400
[    4.976902] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    4.989068] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.989347] usb usb6: configuration #1 chosen from 1 choice
[    4.989416] hub 6-0:1.0: USB hub found
[    4.989433] hub 6-0:1.0: 4 ports detected
[    5.154874] usb 4-2: configuration #1 chosen from 1 choice
[    5.158042] usb 1-2: USB disconnect, address 2
[    5.198531] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.198561] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.198570] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.198648] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    5.202595] ehci_hcd 0000:00:1d.7: debug port 1
[    5.202607] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.202626] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaff000
[    5.217061] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.217558] usb usb7: configuration #1 chosen from 1 choice
[    5.217637] hub 7-0:1.0: USB hub found
[    5.217654] hub 7-0:1.0: 6 ports detected
[    5.397080] usb 6-2: new high speed USB device using ehci_hcd and address 2
[    5.425609] 8139cp 0000:05:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.425620] 8139cp 0000:05:07.0: Try the "8139too" driver instead.
[    5.434986] ata_piix 0000:00:1f.1: version 2.12
[    5.435012] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.435091] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.435259] scsi0 : ata_piix
[    5.435551] scsi1 : ata_piix
[    5.438543] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    5.438551] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    5.440213] 8139too Fast Ethernet driver 0.9.28
[    5.536931] usb 6-2: configuration #1 chosen from 1 choice
[    5.541652] usb 4-2: USB disconnect, address 2
[    5.616656] ata1.00: ATAPI: PIONEER DVD-RW  DVR-K17A, 3.52, max UDMA/33
[    5.648748] ata1.00: configured for UDMA/33
[    5.648857] ata2: port disabled. ignoring.
[    5.658501] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K17A 3.52 PQ: 0 ANSI: 5
[    5.658708] ahci 0000:00:1f.2: version 3.0
[    5.658742] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    5.658893] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.658903] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    5.658913] ahci 0000:00:1f.2: setting latency timer to 64
[    5.669037] scsi2 : ahci
[    5.674817] scsi3 : ahci
[    5.675001] scsi4 : ahci
[    5.675366] ata3: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 220
[    5.675374] ata4: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 220
[    5.675381] ata5: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaffa00 irq 220
[    5.819406] usbcore: registered new interface driver hiddev
[    5.819460] usbcore: registered new interface driver usbhid
[    5.819468] usbhid: v2.6:USB HID core driver
[    6.000121] Clocksource tsc unstable (delta = -117399514 ns)
[    6.096138] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    6.261386] usb 4-2: configuration #1 chosen from 1 choice
[    6.273049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.275234] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.276232] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.276240] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.279263] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-2/4-2:1.0/input/input2
[    6.299219] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2
[    6.640226] ata3.00: ATA-8: TOSHIBA MK1646GSX, LB113M, max UDMA/100
[    6.640235] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.642798] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.642922] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.642930] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.643785] ata3.00: configured for UDMA/100
[    6.976142] ata4: SATA link down (SStatus 0 SControl 300)
[    7.312139] ata5: SATA link down (SStatus 0 SControl 300)
[    7.328325] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[    7.334218] 8139too 0000:05:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.335477] eth0: RealTek RTL8139 at 0xc800, 00:1e:8c:fc:db:48, IRQ 16
[    7.335484] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.363328] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    7.363424] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    7.399059] Driver 'sd' needs updating - please use bus_type methods
[    7.399298] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.399347] sd 2:0:0:0: [sda] Write Protect is off
[    7.399353] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.399438] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.399600] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.399647] sd 2:0:0:0: [sda] Write Protect is off
[    7.399655] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.399742] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.399753]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.456166] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.456176] Uniform CD-ROM driver Revision: 3.20
[    7.456398] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    7.479728]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    7.516400] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.060158] PM: Starting manual resume from disk
[    8.060167] PM: Resume from partition 8:5
[    8.060172] PM: Checking hibernation image.
[    8.060440] PM: Resume from disk failed.
[    8.114962] kjournald starting.  Commit interval 5 seconds
[    8.114997] EXT3-fs: mounted filesystem with ordered data mode.
[   12.227097] udevd version 124 started
[   12.495117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.495117] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.263909] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   12.495117] Linux agpgart interface v0.103
[   12.495117] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.495117] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.495117] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.495117] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   12.495117] synaptics: Toshiba Satellite L40 detected, limiting rate to 40pps.
[   12.495117] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input4
[   12.495117] iTCO_vendor_support: vendor-support=0
[   12.495117] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   12.495117] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.902740] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.902740] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.065153] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
[   16.065153] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.084452] ACPI: Power Button (FF) [PWRF]
[   16.085359] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   16.277912] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   16.310000] ACPI: Power Button (CM) [PWRB]
[   16.310175] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   16.356271] ACPI: Sleep Button (CM) [SLPB]
[   16.358153] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input8
[   16.401749] ACPI: Lid Switch [LID]
[   16.416143] ACPI: Battery Slot [BAT0] (battery present)
[   16.416718] ACPI: AC Adapter [AC0] (off-line)
[   16.418564] acpi device:21: registered as cooling_device2
[   16.418913] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/input/input9
[   16.419404] asus-laptop: Asus Laptop Support version 0.42
[   16.427614] asus-laptop:   T20 model detected
[   16.435477] Registered led device: asus::mail
[   16.468349] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.764223] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   16.764230]          hardware, use at your own risk
[   16.765353] phy0: Selected rate control algorithm 'pid'
[   16.913444] phy0: hwaddr 00:16:44:93:ad:38, RTL8187BvE V0 + rtl8225z2
[   16.913506] usbcore: registered new interface driver rtl8187
[   19.211312] lp: driver loaded but no devices found
[   19.548006] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k
[   19.594661] EXT3 FS on sda6, internal journal
[   20.357720] type=1505 audit(1226085318.429:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4281
[   20.759128] type=1505 audit(1226085318.829:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4286
[   20.759522] type=1505 audit(1226085318.829:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4286
[   21.045081] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.295834] ACPI: WMI: Mapper loaded
[   23.599656] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.762026] apm: BIOS not found.
[   23.926574] ppdev: user-space parallel port driver
[   25.269702] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.269720] vboxdrv: Successfully done.
[   25.269725] vboxdrv: Found 2 processor cores.
[   25.273341] vboxdrv: fAsync=0 offMin=0x348 offMax=0x1170
[   25.273362] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   25.273368] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   28.165294] Bluetooth: Core ver 2.13
[   28.165703] NET: Registered protocol family 31
[   28.165714] Bluetooth: HCI device and connection manager initialized
[   28.165723] Bluetooth: HCI socket layer initialized
[   28.211136] Bluetooth: L2CAP ver 2.11
[   28.211151] Bluetooth: L2CAP socket layer initialized
[   28.261776] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.261793] Bluetooth: BNEP filters: protocol multicast
[   28.319731] Bridge firewalling registered
[   28.320091] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.337246] Bluetooth: RFCOMM socket layer initialized
[   28.338832] Bluetooth: RFCOMM TTY layer initialized
[   28.338841] Bluetooth: RFCOMM ver 1.10
[   28.358037] Bluetooth: SCO (Voice Link) ver 0.6
[   28.358044] Bluetooth: SCO socket layer initialized
[   32.095193] [drm] Initialized drm 1.1.0 20060810
[   32.103359] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.103375] pci 0000:00:02.0: setting latency timer to 64
[   32.105587] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.481447] eth0: link down
[   50.741001] NET: Registered protocol family 17
[   61.930670] wlan0: authenticate with AP 00:0f:b5:d1:aa:8c
[   61.932323] wlan0: authenticated
[   61.932334] wlan0: associate with AP 00:0f:b5:d1:aa:8c
[   61.934465] wlan0: RX AssocResp from 00:0f:b5:d1:aa:8c (capab=0x431 status=0 aid=14)
[   61.934474] wlan0: associated
[   70.887877] CPU0 attaching NULL sched-domain.
[   70.887895] CPU1 attaching NULL sched-domain.
[   70.905802] CPU0 attaching sched-domain:
[   70.905810]  domain 0: span 0-1 level MC
[   70.905814]   groups: 0 1
[   70.905820]   domain 1: span 0-1 level CPU
[   70.905823]    groups: 0-1
[   70.905829] CPU1 attaching sched-domain:
[   70.905831]  domain 0: span 0-1 level MC
[   70.905834]   groups: 1 0
[   70.905839]   domain 1: span 0-1 level CPU
[   70.905842]    groups: 0-1
[   90.010103] NET: Registered protocol family 10
[   90.011432] lo: Disabled Privacy Extensions
[   90.012923] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  100.297018] wlan0: no IPv6 routers present
[  140.521342] type=1503 audit(1226085438.592:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/14379/net/" pid=14379 profile="/usr/sbin/cupsd"
[  141.626887] type=1503 audit(1226085439.696:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/15442/net/" pid=15442 profile="/usr/sbin/cupsd"
[  141.627576] type=1503 audit(1226085439.696:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.630466] type=1503 audit(1226085439.700:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.633245] type=1503 audit(1226085439.704:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.635739] type=1503 audit(1226085439.704:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.638241] type=1503 audit(1226085439.708:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.640951] type=1503 audit(1226085439.712:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.643513] type=1503 audit(1226085439.712:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.645346] type=1503 audit(1226085439.716:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
johanhartman@johanhartman-laptop:~$ 


```

---

### Post by Tom--d on 2008-11-07
> **johanhartman said:**
> I'm thinking that its nm because it first happened when I accidentally tried to connect to a wireless network at work (I always use ethernet there). It tried to connect for a second or two then went into kernel panic, after I reboot after the hard shutdown it logged in and immediately locked up again. This happened two more times then I realised that instead of logging in I can switch to tty1 where it wouldn't lock up. There I uninstalled nm, the kernel panics stopped then. so its something to do with nm or a combination between nm and the driver.

I re-installed nm again and got a panic once during shutdown but not any more. Here's the dmesg anyway:
```
[    1.085081] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    1.085090] PCI: bridge 0000:00:1e.0 32bit mmio: [fe600000, fe6fffff]
[    1.085136] bus 00 -> node 0
[    1.085159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.085975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.086346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.086814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.146160] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    1.148333] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    1.148863] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    1.149391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    1.149918] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[    1.150437] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    1.150964] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    1.151492] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    1.157886] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - B4, should be 4A [20080609]
[    1.157915] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.157944] pnp: PnP ACPI init
[    1.157944] ACPI: bus type pnp registered
[    1.165951] pnp: PnP ACPI: found 13 devices
[    1.165951] ACPI: ACPI bus type pnp unregistered
[    1.165951] PnPBIOS: Disabled by ACPI PNP
[    1.168085] PCI: Using ACPI for IRQ routing
[    1.172052] NET: Registered protocol family 8
[    1.172058] NET: Registered protocol family 20
[    1.172096] NetLabel: Initializing
[    1.172096] NetLabel:  domain hash size = 128
[    1.172096] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.172117] NetLabel:  unlabeled traffic allowed by default
[    1.172129] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.172142] hpet0: 3 64-bit timers, 14318180 Hz
[    1.174324] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.174332]    actual entries 65620
[    1.174517] AppArmor: AppArmor Filesystem Enabled
[    1.174552] ACPI: RTC can wake from S4
[    1.176047] Switched to high resolution mode on CPU 0
[    1.176811] Switched to high resolution mode on CPU 1
[    1.180059] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.180091] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.180099] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.180106] system 00:08: ioport range 0x400-0x41f has been reserved
[    1.180113] system 00:08: ioport range 0x500-0x53f has been reserved
[    1.180121] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.180129] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.180137] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    1.180145] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    1.180153] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.180170] system 00:0a: ioport range 0x250-0x253 has been reserved
[    1.180178] system 00:0a: ioport range 0x256-0x25f has been reserved
[    1.180185] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.180193] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.180209] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    1.180225] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.180232] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    1.180240] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.180247] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    1.217049] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.217055] pci 0000:00:1c.0:   IO window: disabled
[    1.217066] pci 0000:00:1c.0:   MEM window: disabled
[    1.217074] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.217086] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.217092] pci 0000:00:1c.1:   IO window: disabled
[    1.217102] pci 0000:00:1c.1:   MEM window: disabled
[    1.217110] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.217122] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.217130] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    1.217141] pci 0000:00:1c.2:   MEM window: 0xfde00000-0xfe5fffff
[    1.217151] pci 0000:00:1c.2:   PREFETCH window: 0x000000bdf00000-0x000000bfefffff
[    1.217164] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.217172] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    1.217182] pci 0000:00:1e.0:   MEM window: 0xfe600000-0xfe6fffff
[    1.217191] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.217223] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.217234] pci 0000:00:1c.0: setting latency timer to 64
[    1.217251] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.217260] pci 0000:00:1c.1: setting latency timer to 64
[    1.217278] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.217287] pci 0000:00:1c.2: setting latency timer to 64
[    1.217302] pci 0000:00:1e.0: setting latency timer to 64
[    1.217310] bus: 00 index 0 io port: [0, ffff]
[    1.217315] bus: 00 index 1 mmio: [0, ffffffff]
[    1.217320] bus: 01 index 0 mmio: [0, 0]
[    1.217325] bus: 01 index 1 mmio: [0, 0]
[    1.217330] bus: 01 index 2 mmio: [0, 0]
[    1.217335] bus: 01 index 3 mmio: [0, 0]
[    1.217339] bus: 02 index 0 mmio: [0, 0]
[    1.217344] bus: 02 index 1 mmio: [0, 0]
[    1.217349] bus: 02 index 2 mmio: [0, 0]
[    1.217353] bus: 02 index 3 mmio: [0, 0]
[    1.217358] bus: 03 index 0 io port: [b000, bfff]
[    1.217364] bus: 03 index 1 mmio: [fde00000, fe5fffff]
[    1.217369] bus: 03 index 2 mmio: [bdf00000, bfefffff]
[    1.217374] bus: 03 index 3 mmio: [0, 0]
[    1.217379] bus: 05 index 0 io port: [c000, cfff]
[    1.217384] bus: 05 index 1 mmio: [fe600000, fe6fffff]
[    1.217389] bus: 05 index 2 mmio: [0, 0]
[    1.217394] bus: 05 index 3 io port: [0, ffff]
[    1.217399] bus: 05 index 4 mmio: [0, ffffffff]
[    1.217419] NET: Registered protocol family 2
[    1.232120] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.232652] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.233338] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.233805] TCP: Hash tables configured (established 131072 bind 65536)
[    1.233813] TCP reno registered
[    1.240199] NET: Registered protocol family 1
[    1.240456] checking if image is initramfs... it is
[    2.935610] Freeing initrd memory: 7927k freed
[    2.936226] Simple Boot Flag at 0x51 set to 0x1
[    2.938103] audit: initializing netlink socket (disabled)
[    2.938143] type=2000 audit(1226085295.936:1): initialized
[    2.952705] highmem bounce pool size: 64 pages
[    2.952719] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.958391] VFS: Disk quotas dquot_6.5.1
[    2.958596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.958827] msgmni has been set to 1762
[    2.959110] io scheduler noop registered
[    2.959117] io scheduler anticipatory registered
[    2.959123] io scheduler deadline registered
[    2.959151] io scheduler cfq registered (default)
[    2.959178] pci 0000:00:02.0: Boot video device
[    3.006797] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.006862] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.006931] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.007037] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.007231] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.007294] pcieport-driver 0000:00:1c.1: found MSI capability
[    3.007359] pci_express 0000:00:1c.1:pcie00: allocate port service
[    3.007462] pci_express 0000:00:1c.1:pcie03: allocate port service
[    3.007656] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    3.007721] pcieport-driver 0000:00:1c.2: found MSI capability
[    3.007787] pci_express 0000:00:1c.2:pcie00: allocate port service
[    3.007883] pci_express 0000:00:1c.2:pcie02: allocate port service
[    3.007973] pci_express 0000:00:1c.2:pcie03: allocate port service
[    3.008715] isapnp: Scanning for PnP cards...
[    3.362504] isapnp: No Plug & Play device found
[    3.442510] hpet_resources: 0xfed00000 is busy
[    3.442737] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.447997] brd: module loaded
[    3.448167] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.448474] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.451033] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.451692] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.451706] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.451713] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.451719] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.451725] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.452638] mice: PS/2 mouse device common for all mice
[    3.452934] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.452971] rtc0: alarms up to one month, y3k, hpet irqs
[    3.453305] EISA: Probing bus 0 at eisa.0
[    3.453355] EISA: Detected 0 cards.
[    3.453362] cpuidle: using governor ladder
[    3.453368] cpuidle: using governor menu
[    3.454607] TCP cubic registered
[    3.454664] Using IPI No-Shortcut mode
[    3.455104] registered taskstats version 1
[    3.455355]   Magic number: 0:739:242
[    3.455404] tty ttysf: hash matches
[    3.455561] rtc_cmos 00:03: setting system clock to 2008-11-07 19:14:57 UTC (1226085297)
[    3.455569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.455574] EDD information not available.
[    3.455938] Freeing unused kernel memory: 424k freed
[    3.456030] Write protecting the kernel text: 2576k
[    3.456095] Write protecting the kernel read-only data: 936k
[    3.489001] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.745186] fuse init (API version 7.9)
[    3.817084] ACPI: SSDT 3F7B83D0, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    3.818542] ACPI: SSDT 3F7B86B0, 060F (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    3.821230] Monitor-Mwait will be used to enter C-1 state
[    3.821238] Monitor-Mwait will be used to enter C-2 state
[    3.821245] Monitor-Mwait will be used to enter C-3 state
[    3.821708] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.821845] processor ACPI0007:00: registered as cooling_device0
[    3.821856] ACPI: Processor [P001] (supports 8 throttling states)
[    3.822671] ACPI: SSDT 3F7B8300, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    3.824066] ACPI: SSDT 3F7B8620, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    3.828023] Marking TSC unstable due to TSC halts in idle
[    3.847461] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.847597] processor ACPI0007:01: registered as cooling_device1
[    3.847608] ACPI: Processor [P002] (supports 8 throttling states)
[    3.853812] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    3.874270] ACPI: Expecting a [Reference] package element, found type C
[    3.874730] thermal LNXTHERM:01: registered as thermal_zone0
[    3.882740] ACPI: Thermal Zone [THRM] (56 C)
[    4.223173] usbcore: registered new interface driver usbfs
[    4.223225] usbcore: registered new interface driver hub
[    4.230333] usbcore: registered new device driver usb
[    4.236228] USB Universal Host Controller Interface driver v3.0
[    4.236312] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.236330] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.236338] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.236428] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.236481] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    4.236747] usb usb1: configuration #1 chosen from 1 choice
[    4.236812] hub 1-0:1.0: USB hub found
[    4.236828] hub 1-0:1.0: 2 ports detected
[    4.444446] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.444465] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.444474] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.444544] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    4.444595] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    4.444795] usb usb2: configuration #1 chosen from 1 choice
[    4.444860] hub 2-0:1.0: USB hub found
[    4.444876] hub 2-0:1.0: 2 ports detected
[    4.548444] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.548463] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.548472] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.548530] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.548583] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    4.548794] usb usb3: configuration #1 chosen from 1 choice
[    4.548864] hub 3-0:1.0: USB hub found
[    4.548880] hub 3-0:1.0: 2 ports detected
[    4.556044] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.652407] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.652426] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.652435] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.652490] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    4.652542] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    4.652748] usb usb4: configuration #1 chosen from 1 choice
[    4.652815] hub 4-0:1.0: USB hub found
[    4.652830] hub 4-0:1.0: 2 ports detected
[    4.724776] usb 1-2: configuration #1 chosen from 1 choice
[    4.753707] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.833166] No dock devices found.
[    4.861457] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.861475] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.861484] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.861553] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    4.861611] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    4.861819] usb usb5: configuration #1 chosen from 1 choice
[    4.861883] hub 5-0:1.0: USB hub found
[    4.861898] hub 5-0:1.0: 2 ports detected
[    4.917913] SCSI subsystem initialized
[    4.957896] libata version 3.00 loaded.
[    4.968905] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.968933] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.968941] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.969027] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    4.972948] ehci_hcd 0000:00:1a.7: debug port 1
[    4.972960] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.972978] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaff400
[    4.976902] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    4.989068] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.989347] usb usb6: configuration #1 chosen from 1 choice
[    4.989416] hub 6-0:1.0: USB hub found
[    4.989433] hub 6-0:1.0: 4 ports detected
[    5.154874] usb 4-2: configuration #1 chosen from 1 choice
[    5.158042] usb 1-2: USB disconnect, address 2
[    5.198531] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.198561] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.198570] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.198648] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    5.202595] ehci_hcd 0000:00:1d.7: debug port 1
[    5.202607] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.202626] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaff000
[    5.217061] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.217558] usb usb7: configuration #1 chosen from 1 choice
[    5.217637] hub 7-0:1.0: USB hub found
[    5.217654] hub 7-0:1.0: 6 ports detected
[    5.397080] usb 6-2: new high speed USB device using ehci_hcd and address 2
[    5.425609] 8139cp 0000:05:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.425620] 8139cp 0000:05:07.0: Try the "8139too" driver instead.
[    5.434986] ata_piix 0000:00:1f.1: version 2.12
[    5.435012] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.435091] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.435259] scsi0 : ata_piix
[    5.435551] scsi1 : ata_piix
[    5.438543] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    5.438551] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    5.440213] 8139too Fast Ethernet driver 0.9.28
[    5.536931] usb 6-2: configuration #1 chosen from 1 choice
[    5.541652] usb 4-2: USB disconnect, address 2
[    5.616656] ata1.00: ATAPI: PIONEER DVD-RW  DVR-K17A, 3.52, max UDMA/33
[    5.648748] ata1.00: configured for UDMA/33
[    5.648857] ata2: port disabled. ignoring.
[    5.658501] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K17A 3.52 PQ: 0 ANSI: 5
[    5.658708] ahci 0000:00:1f.2: version 3.0
[    5.658742] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    5.658893] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.658903] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    5.658913] ahci 0000:00:1f.2: setting latency timer to 64
[    5.669037] scsi2 : ahci
[    5.674817] scsi3 : ahci
[    5.675001] scsi4 : ahci
[    5.675366] ata3: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 220
[    5.675374] ata4: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 220
[    5.675381] ata5: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaffa00 irq 220
[    5.819406] usbcore: registered new interface driver hiddev
[    5.819460] usbcore: registered new interface driver usbhid
[    5.819468] usbhid: v2.6:USB HID core driver
[    6.000121] Clocksource tsc unstable (delta = -117399514 ns)
[    6.096138] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    6.261386] usb 4-2: configuration #1 chosen from 1 choice
[    6.273049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.275234] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.276232] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.276240] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.279263] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-2/4-2:1.0/input/input2
[    6.299219] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2
[    6.640226] ata3.00: ATA-8: TOSHIBA MK1646GSX, LB113M, max UDMA/100
[    6.640235] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.642798] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.642922] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.642930] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.643785] ata3.00: configured for UDMA/100
[    6.976142] ata4: SATA link down (SStatus 0 SControl 300)
[    7.312139] ata5: SATA link down (SStatus 0 SControl 300)
[    7.328325] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[    7.334218] 8139too 0000:05:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.335477] eth0: RealTek RTL8139 at 0xc800, 00:1e:8c:fc:db:48, IRQ 16
[    7.335484] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.363328] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    7.363424] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    7.399059] Driver 'sd' needs updating - please use bus_type methods
[    7.399298] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.399347] sd 2:0:0:0: [sda] Write Protect is off
[    7.399353] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.399438] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.399600] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.399647] sd 2:0:0:0: [sda] Write Protect is off
[    7.399655] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.399742] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.399753]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.456166] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.456176] Uniform CD-ROM driver Revision: 3.20
[    7.456398] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    7.479728]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    7.516400] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.060158] PM: Starting manual resume from disk
[    8.060167] PM: Resume from partition 8:5
[    8.060172] PM: Checking hibernation image.
[    8.060440] PM: Resume from disk failed.
[    8.114962] kjournald starting.  Commit interval 5 seconds
[    8.114997] EXT3-fs: mounted filesystem with ordered data mode.
[   12.227097] udevd version 124 started
[   12.495117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.495117] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.263909] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   12.495117] Linux agpgart interface v0.103
[   12.495117] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.495117] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.495117] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.495117] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   12.495117] synaptics: Toshiba Satellite L40 detected, limiting rate to 40pps.
[   12.495117] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input4
[   12.495117] iTCO_vendor_support: vendor-support=0
[   12.495117] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   12.495117] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.902740] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.902740] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.065153] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
[   16.065153] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.084452] ACPI: Power Button (FF) [PWRF]
[   16.085359] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   16.277912] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   16.310000] ACPI: Power Button (CM) [PWRB]
[   16.310175] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   16.356271] ACPI: Sleep Button (CM) [SLPB]
[   16.358153] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input8
[   16.401749] ACPI: Lid Switch [LID]
[   16.416143] ACPI: Battery Slot [BAT0] (battery present)
[   16.416718] ACPI: AC Adapter [AC0] (off-line)
[   16.418564] acpi device:21: registered as cooling_device2
[   16.418913] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/input/input9
[   16.419404] asus-laptop: Asus Laptop Support version 0.42
[   16.427614] asus-laptop:   T20 model detected
[   16.435477] Registered led device: asus::mail
[   16.468349] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.764223] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   16.764230]          hardware, use at your own risk
[   16.765353] phy0: Selected rate control algorithm 'pid'
[   16.913444] phy0: hwaddr 00:16:44:93:ad:38, RTL8187BvE V0 + rtl8225z2
[   16.913506] usbcore: registered new interface driver rtl8187
[   19.211312] lp: driver loaded but no devices found
[   19.548006] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k
[   19.594661] EXT3 FS on sda6, internal journal
[   20.357720] type=1505 audit(1226085318.429:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4281
[   20.759128] type=1505 audit(1226085318.829:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4286
[   20.759522] type=1505 audit(1226085318.829:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4286
[   21.045081] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.295834] ACPI: WMI: Mapper loaded
[   23.599656] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.762026] apm: BIOS not found.
[   23.926574] ppdev: user-space parallel port driver
[   25.269702] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.269720] vboxdrv: Successfully done.
[   25.269725] vboxdrv: Found 2 processor cores.
[   25.273341] vboxdrv: fAsync=0 offMin=0x348 offMax=0x1170
[   25.273362] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   25.273368] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   28.165294] Bluetooth: Core ver 2.13
[   28.165703] NET: Registered protocol family 31
[   28.165714] Bluetooth: HCI device and connection manager initialized
[   28.165723] Bluetooth: HCI socket layer initialized
[   28.211136] Bluetooth: L2CAP ver 2.11
[   28.211151] Bluetooth: L2CAP socket layer initialized
[   28.261776] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.261793] Bluetooth: BNEP filters: protocol multicast
[   28.319731] Bridge firewalling registered
[   28.320091] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.337246] Bluetooth: RFCOMM socket layer initialized
[   28.338832] Bluetooth: RFCOMM TTY layer initialized
[   28.338841] Bluetooth: RFCOMM ver 1.10
[   28.358037] Bluetooth: SCO (Voice Link) ver 0.6
[   28.358044] Bluetooth: SCO socket layer initialized
[   32.095193] [drm] Initialized drm 1.1.0 20060810
[   32.103359] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.103375] pci 0000:00:02.0: setting latency timer to 64
[   32.105587] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.481447] eth0: link down
[   50.741001] NET: Registered protocol family 17
[   61.930670] wlan0: authenticate with AP 00:0f:b5:d1:aa:8c
[   61.932323] wlan0: authenticated
[   61.932334] wlan0: associate with AP 00:0f:b5:d1:aa:8c
[   61.934465] wlan0: RX AssocResp from 00:0f:b5:d1:aa:8c (capab=0x431 status=0 aid=14)
[   61.934474] wlan0: associated
[   70.887877] CPU0 attaching NULL sched-domain.
[   70.887895] CPU1 attaching NULL sched-domain.
[   70.905802] CPU0 attaching sched-domain:
[   70.905810]  domain 0: span 0-1 level MC
[   70.905814]   groups: 0 1
[   70.905820]   domain 1: span 0-1 level CPU
[   70.905823]    groups: 0-1
[   70.905829] CPU1 attaching sched-domain:
[   70.905831]  domain 0: span 0-1 level MC
[   70.905834]   groups: 1 0
[   70.905839]   domain 1: span 0-1 level CPU
[   70.905842]    groups: 0-1
[   90.010103] NET: Registered protocol family 10
[   90.011432] lo: Disabled Privacy Extensions
[   90.012923] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  100.297018] wlan0: no IPv6 routers present
[  140.521342] type=1503 audit(1226085438.592:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/14379/net/" pid=14379 profile="/usr/sbin/cupsd"
[  141.626887] type=1503 audit(1226085439.696:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/15442/net/" pid=15442 profile="/usr/sbin/cupsd"
[  141.627576] type=1503 audit(1226085439.696:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.630466] type=1503 audit(1226085439.700:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.633245] type=1503 audit(1226085439.704:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.635739] type=1503 audit(1226085439.704:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.638241] type=1503 audit(1226085439.708:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.640951] type=1503 audit(1226085439.712:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.643513] type=1503 audit(1226085439.712:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
[  141.645346] type=1503 audit(1226085439.716:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=15442 profile="/usr/sbin/cupsd"
johanhartman@johanhartman-laptop:~$ 


```

To be honest, there is nothing abnormal there.

Elimate things. Remove network manager and install wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Does wired connections as well as wireless :)

---

### Post by m0nkfish on 2008-11-12
Hi

I've been dual-booting Hardy (K)ubuntu on my laptop for the last few months and once I'd followed the instructions in this thread, I'd got it to work on *some* encrypted wireless networks. However, having just upgraded to Intrepid I find that I can no longer connect wirelessly to my network. I'm sitting ~2m from the router so I don't think it's a distance problem...

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914                           
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

Any steps I should take?

---

### Post by johanhartman on 2008-11-12
I've been looking around for a fix for my [range problems]("http://ubuntuforums.org/showpost.php?p=6109425&postcount=169") mention earlier in this thread when I came across [this]("http://aircrack-ng.org/doku.php?id=r8187&DokuWiki=df606c53c8f63cccc89292219b478c97").

Would someone more knowledgeable please tell me if this would work before I try it as it seems to be potentially damaging
> Power Settings

The transmit power can be adjusted using:

 iwconfig wlan0 txpower <value of 0 to 35>

With 0 being the lowest and 35 being the highest transmit power. The default is 5 which is normal. In order to use higher values, you must first “enable” the high power option. See the next section regarding how to do this. WARNING: Enabling high power can damage or destroy your wireless device. Use this feature at your own risk.

It is important to understand that the values are relative power values, not absolute. Meaning that they do not refer to dBm or mW values.

To view the current setting enter:

 iwlist wlan0 txpower

The system responds with the current setting:

 wlan0     unknown transmit-power information.
 
        Current Tx-Power=5 dBm        (3 mW)

You MUST ignore the dBm and mW labels. The value of “5” above is the actual value in the 0 to 35 range. Unfortunately due to driver constraints, the “dBm (3mW)” are also displayed but must be ignored. 

---

### Post by m0nkfish on 2008-11-12
> **johanhartman said:**
> I've been looking around for a fix for my [range problems]("http://ubuntuforums.org/showpost.php?p=6109425&postcount=169") mention earlier in this thread when I came across [this]("http://aircrack-ng.org/doku.php?id=r8187&DokuWiki=df606c53c8f63cccc89292219b478c97").

Would someone more knowledgeable please tell me if this would work before I try it as it seems to be potentially damaging

How disconcerting... My default wireless power was set to 20dBm (!)

---

### Post by johanhartman on 2008-11-12
yeah mines 27, which is good enough, just not upstairs in my room :(

---

### Post by Tom--d on 2008-11-12
> **m0nkfish said:**
> Hi

I've been dual-booting Hardy (K)ubuntu on my laptop for the last few months and once I'd followed the instructions in this thread, I'd got it to work on *some* encrypted wireless networks. However, having just upgraded to Intrepid I find that I can no longer connect wirelessly to my network. I'm sitting ~2m from the router so I don't think it's a distance problem...

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914                           
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

Any steps I should take?

If you used ndiswrapper in Hardy and upgraded to 8.10 with native support. having ndiswrapper as your driver it might mess things around.
The best thing I can say if to have a fresh install of 8.10. This will make all the settings right.

---

### Post by Tom--d on 2008-11-12
> **johanhartman said:**
> yeah mines 27, which is good enough, just not upstairs in my room :(

My is 20 but this is using the Ndiswrapper driver.

Thanks for the information as well.
Over time (In 9.04) the wireless driver will be better. Just remember. Its experimental driver for the RTL8187B. Expect bugs.

---

### Post by m0nkfish on 2008-11-12
:( It's taken me hours to get everything working, I think a fresh 8.10 install would kill me... Any easy way to remove ndiswrapper?

---

### Post by Tom--d on 2008-11-13
> **m0nkfish said:**
> :( It's taken me hours to get everything working, I think a fresh 8.10 install would kill me... Any easy way to remove ndiswrapper?

No problem. Just do these commands and it should sort it.
```
sudo apt-get purge ndiswrapper-common
```
Then
```
sudo modprobe -r ndiswrapper
```
```
sudo modprobe rtl8187
```
```
sudo iwconfig wlan0 rate 5.5M fixed
```
^^^^^^^Make sure you run this! It fixes the bugs in the driver (Read the first post).

If all works well:
run these
```
gksu gedit /etc/rc.local
```
BEFORE exit 0, put these lines:
```
modprobe rtl8187
iwconfig wlan0 rate 5.5M fixed
```

That should do it.

---

### Post by m0nkfish on 2008-11-20
For some reason I'm not getting wlan0 on iwconfig now. The wireless switch is on, do I need to install another driver?

EDIT:
Haha, my bad - mistook the L for a 1 in 'rtl8187'. Now the problem is that I can't seem to find the router. I'm guessing it's the range problem? Setting the rate didn't seem to fix it.

---

### Post by Tom--d on 2008-11-20
> **m0nkfish said:**
> For some reason I'm not getting wlan0 on iwconfig now. The wireless switch is on, do I need to install another driver?

EDIT:
Haha, my bad - mistook the L for a 1 in 'rtl8187'. Now the problem is that I can't seem to find the router. I'm guessing it's the range problem? Setting the rate didn't seem to fix it.

The wireless support is not fully working yet. Its only some support for the card.
For example, range is not as long as it should be. (my guess it will be fixed, hopefully, in the next ubuntu.)
Ndiswrapper is your only other way of getting around that.

---

### Post by m0nkfish on 2008-11-23
ndiswrapper wasn't working before, though - and now I can't even seem to download it again... using **sudo apt-get install ndiswrapper-common** etc just tells me that the package can't be found :/

---

### Post by Tom--d on 2008-11-23
> **m0nkfish said:**
> ndiswrapper wasn't working before, though - and now I can't even seem to download it again... using **sudo apt-get install ndiswrapper-common** etc just tells me that the package can't be found :/

You need to do sudo apt-get update first.

---

### Post by Tom--d on 2008-12-28
Update:

you can now download the latest wireless drivers, here:

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by onewithnature83 on 2008-12-28
To all:

While, I understand the frustration, you all encounter when dealing with the RTL8187b wireless chipset, There are all sorts of solutions at your disposal. Some are better than others only in opinion and needs. 

Tom-d. I do believe we have been in contact via e-mail a few times regarding the status of this chipset in the ubuntu distro as well as others.

Let me say Tom-d that I fully understand the basis for the Ubuntu wiki, and that registered users may edit or enhance pages at will w/out consent of the original writer. However, it would be at minimum "kind" in nature to append your information you wish to share at the end of the page rather than quote 

'''Please read this before anything!''' > [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) " 

on the 1st line. (kinda rude, considering the hours of support I have spent helping users w/out any benefit to myself) 

I welcome any information that could benefit users of this hardware but I think I very clearly outlined a specific method and all other suggestions should be presented as "additional info" rather than a redirection. 

I will only "move" your link not "remove" it, cause I think all should be aware of their choices when it comes to making this hardware work!. 

For those who might be interested here is the URL to my Ubuntu Wiki How-to:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

No, its not the only solution, but its one that works! I have used this method for about a year now, w/out any issue other than signal strength is not supported, it is not restricted on speed as in the 8.10 versions kernel module (2.6.27) and it operates stable and fast. I do local FTP transfers at 3+ mb/sec not 400-500 kb/sec 

And if your one that runs 8.10, I offer you no solution at all, other than use the included kernel module at your own risk, w/ or w/out the fixed data rate, or ndiswrapper which I personaly refuse due to not wanting anything to do with supporting microsoft code.

Good luck to all!

--TJ (onewithnature83)

---

### Post by Tom--d on 2008-12-28
> **onewithnature83 said:**
> To all:

While, I understand the frustration, you all encounter when dealing with the RTL8187b wireless chipset, There are all sorts of solutions at your disposal. Some are better than others only in opinion and needs. 

Tom-d. I do believe we have been in contact via e-mail a few times regarding the status of this chipset in the ubuntu distro as well as others.

Let me say Tom-d that I fully understand the basis for the Ubuntu wiki, and that registered users may edit or enhance pages at will w/out consent of the original writer. However, it would be at minimum "kind" in nature to append your information you wish to share at the end of the page rather than quote 

'''Please read this before anything!''' > [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) " 

on the 1st line. (kinda rude, considering the hours of support I have spent helping users w/out any benefit to myself) 

I welcome any information that could benefit users of this hardware but I think I very clearly outlined a specific method and all other suggestions should be presented as "additional info" rather than a redirection. 

I will only "move" your link not "remove" it, cause I think all should be aware of their choices when it comes to making this hardware work!. 

For those who might be interested here is the URL to my Ubuntu Wiki How-to:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

No, its not the only solution, but its one that works! I have used this method for about a year now, w/out any issue other than signal strength is not supported, it is not restricted on speed as in the 8.10 versions kernel module (2.6.27) and it operates stable and fast. I do local FTP transfers at 3+ mb/sec not 400-500 kb/sec 

And if your one that runs 8.10, I offer you no solution at all, other than use the included kernel module at your own risk, w/ or w/out the fixed data rate, or ndiswrapper which I personaly refuse due to not wanting anything to do with supporting microsoft code.

Good luck to all!

--TJ (onewithnature83)

Hello,
Thanks for contacting me.
I apologize for that. I was in a hurry at the time (Really!).
Would you kindly put a third solution to the Wireless? As a link to my thread?

I'm on the same leg as you on the ndiswrapper bit. I don't want to have it. I would prefer native.
I might look into compiling the driver you are using. Last time I done that, it didn't work. But saying that, I didn't know much at the time.
Thanks,
Tom

---

### Post by mali2 on 2009-01-04
I think now i am at right place, now please help me out.... 

I am using the ubuntu 8.10 > 2.6.27. and my chipset is rtl 8187b (ID:8198 )
From following link: 
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) 
I used the driver for 2.6.27 kernel support. After installing it, I got the wireless lists and When I connect with my Router, it connected successfully and I used it for few minutes, but after 2 to 4 minutes Internet trafic stops and I unable to surf the internet. And i also tried to connect with other wireless router, but then it never connect with any one, even with my own router. Then i try to restart my PC, it again start work but only for 2 minutes then stop working. I also tried to fix the bit rate 5.5 MBps in the rc.local file. But same problem. 
I will be very very thank ful, if u will guide me.
thanks

---

### Post by Tom--d on 2009-01-04
> **mali2 said:**
> I think now i am at right place, now please help me out.... 

I am using the ubuntu 8.10 > 2.6.27. and my chipset is rtl 8187b (ID:8198 )
From following link: 
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) 
I used the driver for 2.6.27 kernel support. After installing it, I got the wireless lists and When I connect with my Router, it connected successfully and I used it for few minutes, but after 2 to 4 minutes Internet trafic stops and I unable to surf the internet. And i also tried to connect with other wireless router, but then it never connect with any one, even with my own router. Then i try to restart my PC, it again start work but only for 2 minutes then stop working. I also tried to fix the bit rate 5.5 MBps in the rc.local file. But same problem. 
I will be very very thank ful, if u will guide me.
thanks

Okay.
When you first connect to your router, open up a terminal and put in this:
```
sudo iwconfig wlan0 rate 5.5M fixed
```

Does it give any errors back? If not, it worked. Now try surfing. Is it better?

If it comes back with an error about no wlan0, change wlan0 with wlan1 in the command.

---

### Post by mali2 on 2009-01-04
> **Tom--d said:**
> Okay.
When you first connect to your router, open up a terminal and put in this:
```
sudo iwconfig wlan0 rate 5.5M fixed
```

Does it give any errors back? If not, it worked. Now try surfing. Is it better?

If it comes back with an error about no wlan0, change wlan0 with wlan1 in the command.

Yep! It Works :D:D, Thank you very much... as i am in ubuntu and using that wirless i m sending u this reply, finally it works :D. Once again thankyou very much. :popcorn:

previously i was using the command in the rc.local , which i think start by starting the ubuntu, and that was not working but this is working great... :D I am realy amazed and happy .

---

### Post by mali2 on 2009-01-04
Now can i fixed it , so that every time i start the ubuntu and wirless it should be fixed automatically instead of using this command explicitely every time?

---

### Post by Tom--d on 2009-01-05
> **mali2 said:**
> Now can i fixed it , so that every time i start the ubuntu and wirless it should be fixed automatically instead of using this command explicitely every time?

Yes

Do this:
```
gksu gedit /etc/rc.local
```

Before the exit 0, put this:
```
iwconfig wlanX rate 5.5M fixed
```

**Where X is your number for your wireless card. Check it with iwconfig in terminal**

This will run at start up so you will not need to manually edit the bit rate :D

---

### Post by mali2 on 2009-01-06
> **Tom--d said:**
> Yes

Do this:
```
gksu gedit /etc/rc.local
```

Before the exit 0, put this:
```
iwconfig wlanX rate 5.5M fixed
```

**Where X is your number for your wireless card. Check it with iwconfig in terminal**

This will run at start up so you will not need to manually edit the bit rate :D

hmmm... Thanks Tom :)
I am wandering about the thing... When i used my ubuntu wireless and after restarting the system for switching in windows Vista then windows wireless do not work untill and unless i completely shutdown my system and then start it again in windows Vista, Now this driver which i m using is modified in the sense that It changes the chip ID to 8198 with forced hack, does it affect the window driver? even after restart ??? can u suggest some thing or tell me reasoning of it?

---

### Post by Tom--d on 2009-01-06
> **mali2 said:**
> hmmm... Thanks Tom :)
I am wandering about the thing... When i used my ubuntu wireless and after restarting the system for switching in windows Vista then windows wireless do not work untill and unless i completely shutdown my system and then start it again in windows Vista, Now this driver which i m using is modified in the sense that It changes the chip ID to 8198 with forced hack, does it affect the window driver? even after restart ??? can u suggest some thing or tell me reasoning of it?

I've heard this before. I do not know why or how it does that. It is a bug in the Linux driver. I'm sure of it.
Also, there is no hack here for it to detect the 8198. That's in the driver.
Wait?
Where and how did you install your driver?

If it does this all the time, maybe use Ndiswrapper?

---

### Post by godfromdfo on 2009-01-30
*reads whole thread* ahh, that may be why the 64bit version of 8.10 might not be working -_- *downloads 32bit 8.10*

---

### Post by Tom--d on 2009-01-30
> **godfromdfo said:**
> *reads whole thread* ahh, that may be why the 64bit version of 8.10 might not be working -_- *downloads 32bit 8.10*

:p

---

### Post by raunhar on 2009-02-07
I tried this but no help.
After this the system didnot shut down properly.

---

### Post by AlexBellisBrown on 2009-02-07
Some launchpad bug reports: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946)

And the most interesting one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473)

It states there is a fix schedualed shortly in a new kernel. Fingers crossed. :)

---

### Post by molder on 2009-02-22
I found that network keys are case sensitive when setting up wireless for my ps3

---

### Post by freeztar on 2009-03-07
Preface: I'm a complete Linux noobie. 

After spending about 12 hours over the last few days trying to get this to work, I'm a bit bummed out. :(

I've looked at every thread here regarding this issue and at this point I have tried about 8 different methods with no success. Certain methods have allowed me to connect, but I lose connection anywhere from 5-120 minutes. After a reboot, it works again and then stops working after a while. 

I'm using the latest kernel in 8.10. I have Ndiswrapper and it does not work. I've tried the modified drivers that were recommended in a tutorial on this forum. Upon trying to "sudo ./wlan0up", I get the following errors:

```
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

```

I'm at a loss with how to get this nic working and it's driving me crazy. At this point, I'd be happy to revert to the time when it actually worked, but required rebooting every 20 minutes or so (sometimes less, sometimes more). I have no idea how to do this though as I'm a noob.

Any help regarding this problem would be more than greatly appreciated. I hate having to use XP because I can't get online in Ubuntu. :(

---

### Post by freeztar on 2009-03-07
Ok, so I found another suggestion on a Suse board about using wireless-compat package. I didn't see this in my repositories, so I didn't feel comfortable installing it. I'm a noob and trying to rebuild the kernel, well, I don't think I'm there yet. ;)

Anyhow, it talked about using modprobe %driver-name%. I had tried this before and it always said could not find it. I just tried it again, after doing what was described in my last post, and it worked! It took about 20 seconds and then connected. (we'll see if it holds, but at least it is working for now) I'm not sure what exactly it did though. I used ```
sudo modprobe rtl8187
``` from within the modified driver directory as su. Does this mean it loaded the modified driver, or since I was su is it possible that it loaded the original driver that came with my build from some other location? In other words, does modprobe work directory specific?

---

### Post by afeasfaerw23231233 on 2009-03-11
BUMP

The wireless lan Realtek 8187 (ID 0bda:8187) in Ubuntu makes me mad. 
I have searched this forum and started threads about this issue nearly everyday this two weeks but still can't find a solution. 

And now I find this thread. I will try your method to fix the bit rate to 5.5Mb/s soon and see if it helps.

Currently I am using ndiswrapper with win 98 drivers. The problem of ndiswrapper with win 98 drivers is the unacceptable weak signal strength. The connection is broken if distance from the router to the notebook is more than 3 metres, making the wlan completely useless to me. 

It teaches me a great lesson of checking compatibility with linux before buying any hardwares.

---

### Post by greenjumper on 2009-03-11
I had tried the speed limiting that is recommended at the very beginning of this thread with some success. It definitely reduced the frequency of my internet hanging. However, today after reading another thread I uninstalled Network Manager and installed Wicd. I know it hasn't yet been 24 hours but already I am noticing that the speed of my internet is much more stable and I haven't yet had to once do a restart!
Perhaps this is a step that can help some of you?
Good luck!

---

### Post by afeasfaerw23231233 on 2009-03-11
Hi, did you do some stress test such as P2P, bittorrent, samba, etc for it?
And did you do the range test for signal strength?

I am using Wicd too. The network manager doesn't work well for me. 
When it is using the native driver, the connection will hang within 2 minutes while bittorrenting. I am going to try the method from OP to chop down the bit rate to 5.5mb/s.

---

### Post by afeasfaerw23231233 on 2009-03-11
> **greenjumper said:**
> I had tried the speed limiting that is recommended at the very beginning of this thread with some success. It definitely reduced the frequency of my internet hanging. However, today after reading another thread I uninstalled Network Manager and installed Wicd. I know it hasn't yet been 24 hours but already I am noticing that the speed of my internet is much more stable and I haven't yet had to once do a restart!
Perhaps this is a step that can help some of you?
Good luck!

Hi, are you using the native driver or ndiswrapper? The native driver is never stable to me!

---

### Post by afeasfaerw23231233 on 2009-03-11
I am now using the native driver rtl8187 and have ndiswrapper uninstalled. The range of accessibilty really increase! I think the connection doesn't hang even I am beyond 20 metres from the router. But I get a quite severe penalty on speed. The downloading rate decrease from 2.6MB/s to 1.3MB/s and up rate decrease from 2.8MB/s to 500KB/s. And the maximum bittorent rate drops from 1.2MB/s to 500KB/s.

The router of my manual says the farther the signal transfers, the lower the speed rate. But I think I still have to fix the rate in Ubuntu but not the router as I need the wifi in the outside. 

Is it because the wireless lan card is incapable to auto-negotiate the rate with the router so that I can never walk 3 metre away from the router without the ** iwconfig wlan0 rate 5.5M fixed ** option? I mean the speed rate should be able to drop accordingly the client is far way from the router, but the driver may have some kind of bug so it keeps the fixed rate of 54mb/s.

But I still have another question. With the native driver the connection isn't stable if a fixed low rate isn't set even the router just lie beside the notebook. 

I will learn how to use the command iwconfig and iwlist to test with different fixed rate and post more result soon.

---

### Post by greenjumper on 2009-03-11
I have so far only been using the native driver! After using it for a bit longer with Wicd I can't really say that it's much better. It worked for a long time (about 6 hours) without having any problems, but I have just had to restart my system about 6 times to even get connected!

Would you say that it works better with Ndiswrapper?

Does anyone know if the support is going to be better in the upcoming new kernel?

I have to say that theis network card never even worked 100% for me with windows - I think we basically just have a rubbish bit of hardware!
I sent my notebook back to Toshiba a few weeks ago because it kept disconnecting whilst in Windows and is till under guarantee, but they said that there was absolutely nothing wrong with it!

I would be interested to know what you think about maybe using ndiswrapper though.

---

### Post by afeasfaerw23231233 on 2009-03-11
First of all thanks for your reply.

I think I finally get the solution. The fixed rate work for me so far. I am quite sure my connection hangs because the driver (either the native or the ndiswrapper win 98 one) doesn't know how to do the auto-negotiation with the router. For example, in Windows XP the transfer rate would drop as the signal is decreasing accordingly. But in Ubuntu the transfer rate always stucks at 54mb/s even though the signal is decreasing. 

According to the man page of iwconfig
```


rate/bit[rate]
    For cards supporting multiple bit rates, set the bit-rate in b/s. The bit-rate is the speed at which bits are transmitted over the medium, the user speed of the link is lower due to medium sharing and various overhead.
    You may append the suffix k, M or G to the value (decimal multiplier : 10^3, 10^6 and 10^9 b/s), or add enough '0'. Values below 1000 are card specific, usually an index in the bit-rate list. Use auto to select automatic bit-rate mode (fallback to lower rate on noisy channels), which is the default for most cards, and fixed to revert back to fixed setting. If you specify a bit-rate value and append auto, the driver will use all bit-rates lower and equal than this value.
    Examples :
    iwconfig eth0 rate 11M
    iwconfig eth0 rate auto
    iwconfig eth0 rate 5.5M auto 


```

I don't know what's the default setting of the rate parameter of Ubuntu native driver/ ndiswrapper. But even though I set it as "iwconfig wlan0 rate 5.5M auto" I notice that the transfer rate is always 54mb/s from the command "iwconfig" after the connection is established. And it will always stuck at 54mb/s, no matter the signal is greatly weaken as I walk away from the router. So I think the "auto" option cannot be used, probably it's a bug. 

And once I fixed the rate (the lower the better, but you will be penalized by decreasing connection speed), everything becomes fine. The driver doesn't know how to auto-negotiate with the router so you must fixed the rate for it, or it will just hold at 54mb/s and doesn't let you be 3 metres away from it. 

I set it as 12mb/s and now the notebook can access the internet in any place at home (I just live in an apartment, so the the distance isn't so long. But the thick cement wall greatly reduce the signal). If I fix it as 1mb/s I bet I can even connect my own network 200 metres away(as the user manual said, providing it doesn't exagerrate its statistic), but the speed may similate the good ole day 56k dial-up. 

If you want to test which rate is suitable for you, first run
```
iwlist scan 
```
It will show all the rates support by your adapter
For mine it is: 
```
wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:DF:63:DA
                    ESSID:"homerouter269"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=59/100  Signal level:36/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023c37e4170
                    Extra: Last beacon: 92ms ago


```
I test with all the bit rates and find out 12Mb/s is most suitable for me(at home). If I am in the library and find out the connection suddenly drops, it may imply the signal is too weak and the bit rates should be even lower. Then just run 
```
 sudo iwconfig wlan0 5.5M fixed (1M should work in any case but too slow) 
```
Open wicd, disconnect and then connect. If it doesn't work then lower the bit rate again.

I use samba to test different speed rates with the router TOUCHING the notebook: 

```

rate(mb/s)	download(mb/s)	upload(mb/s)
54		2.0		1.9
48		2.0		1.9
36		2.0		1.7
24		2.0		1.4
12		2.0		1.0
11		0.7-0.9		0.78
9		2.0		0.78
6		1.9		0.57
5.5		1.6		0.5
2		1.4		0.2
1		1.1		0.07-0.14

``` I am using WPA so it should be slower than unencrypted connection [max 2.8Mb/s]
The speed of fixed rate 11M fluctuating during the test (maybe another bug?) So I would avoid it. 

I find out another interesting bug. The "Link quality" and "Signal level" behave strangely. When the router is very near the notebook, the Link quality shows 90/100 but the Signal level shows 3/65. When the router is very far from the notebook, the Link quality shows 10/100 and Signal level shows 65/65! Maybe it's the cause of the failure of auto-negotiation? 

Hope that it can help any people who have a wireless lan card with Realtek 8187 chipset. 

I haven't done the stability test, but if this native driver doesn't work I can simply switch back to ndiswrapper. But ndiswrapper sometimes hangs my computer at bootup. Still no one answer that thread related to this problem yet.

> **greenjumper said:**
> I have so far only been using the native driver! After using it for a bit longer with Wicd I can't really say that it's much better. It worked for a long time (about 6 hours) without having any problems, but I have just had to restart my system about 6 times to even get connected!

Would you say that it works better with Ndiswrapper?

Does anyone know if the support is going to be better in the upcoming new kernel?

I have to say that theis network card never even worked 100% for me with windows - I think we basically just have a rubbish bit of hardware!
I sent my notebook back to Toshiba a few weeks ago because it kept disconnecting whilst in Windows and is till under guarantee, but they said that there was absolutely nothing wrong with it!

I would be interested to know what you think about maybe using ndiswrapper though.
But this wireless network card works great in win xp. So far it doesn't have problem. Perhaps it's too early to say. I just get my laptop two weeks ago. For the last resort you may need to buy an internal wlan card or a usb dongle. Actually I was going to get one too as I think that I can't never get this piece of 8187 work. Luckily finally it does. 

I think the win 98 driver of Ndiswrapper is stable. But it sometimes hang the system at bootup! No one answer my thread yet. 


By the way, how comes you need to restart it six times for getting connected?

Perhaps you should check your setting in Windows and your router too?

I am sorry that I can't give answer for your question. I am just a newb though I have been using Ubuntu for nearly two years. 


AAH, this problem finally fixed and I can go to sleep now!

p.s. sorry for my bad English

---

### Post by greenjumper on 2009-03-11
I'm afraid I've sort of half given up!

I had absolutley no luck with the in-built support, and just out of curiosity I plugged the wireless dongle from my old laptop in and suddenly the wireless works like a dream!
I really hope that the people who understand these things can sort it out sometime with this device, but it looks like, that until they do I'll have to rely on another bit of (external) hardware.
It's such a shame because I find the whole Ubuntu experience a joy, but an operating system without reliable internet is like... well you know!

---

### Post by afeasfaerw23231233 on 2009-03-11
Did you try the fixed rate method?

---

### Post by afeasfaerw23231233 on 2009-03-12
Adding the line **iwconfig wlan0 rate 12M fixed** in /etc/rc.local wouldn't fix the rate my wireless lan card isn't trigger on before bootup. I have to add "iwconfig wlan0 rate 12M fixed" in Wicd's preconnection script. If I am outside and the signal is poor, I just need to edit the preconnection script and restart it.

---

### Post by greenjumper on 2009-03-12
I tried the fixed rate method as described at the beginning of this thread, but it didn't seem to make much difference. Maybe I need to alter the Wicd configuration too? Could you tell me how I do that please - not really very knowledgeable with the terminal and all that!

---

### Post by afeasfaerw23231233 on 2009-03-12
Heheh, I am a newb too. 
First of all you have to ensure the bit rate is being fixed. 
Type this in terminal
```

iwconfig

```
Mine shows ```

wlan0     IEEE 802.11bg  ESSID:"homerouter269"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:19:5B:DF:63:DA   
          **Bit Rate=12 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=79/100  Signal level:16/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` That means the rate is fixed at 12Mb/s
If it is 54Mb/s, then I am quite sure that it is not fixed. 
For safty reason you should set it as 5.5Mb/s first, and increase this value as you are are sure this rate is stable.
So, 
Open wicd and click the "scripts" button, it will ask you for a password. Fill "iwconfig wlan0 rate 5.5M fixed" (no quotation marks) in the Pre-connecton Script blank, then click OK. Disconnect and then connect again. [please see the screenshots]
Open the terminal and enter the following command
```
iwconfig 
```
Now it should show **Bit Rate=5.5 Mb/s**
Ping your gateway and see if it is stable. If you don't know the IP of your router, you can use this command to figure it out
```
 route 
```
For me it is 192.168.123.1
So ping 192.168.123.1
```
 ping 192.168.123.1 
```
It should return something like these continuously 
```

coppen@coppen-laptop:~$ ping 192.168.123.1
PING 192.168.123.1 (192.168.123.1) 56(84) bytes of data.
64 bytes from 192.168.123.1: icmp_seq=1 ttl=64 time=1.60 ms
64 bytes from 192.168.123.1: icmp_seq=2 ttl=64 time=3.39 ms
64 bytes from 192.168.123.1: icmp_seq=3 ttl=64 time=2.39 ms
64 bytes from 192.168.123.1: icmp_seq=4 ttl=64 time=1.28 ms
64 bytes from 192.168.123.1: icmp_seq=5 ttl=64 time=1.52 ms
64 bytes from 192.168.123.1: icmp_seq=6 ttl=64 time=2.65 ms
64 bytes from 192.168.123.1: icmp_seq=7 ttl=64 time=1.29 ms
64 bytes from 192.168.123.1: icmp_seq=8 ttl=64 time=1.79 ms
64 bytes from 192.168.123.1: icmp_seq=9 ttl=64 time=2.31 ms
...blablabla

```

Now you can stress test your connection by samba, p2p, opening dozens of tabs in firefox or whatever you like. (I know there's a "iperf" command but I'm too lazy to learn :)). If it is stable enough then you can tune up the value in the Pre-connecton Scripts of Wicd. Disconnect and connect again, and do the stress/range test again. You don't need to switch off the terminal which is running the ping command. Keep it on and see if error messages such as "connection timeout" or "network unreachable" appear. I am a bit greedy so I fixed it at 12M. But be careful that the assigned bit rate must be supported by your wlan card. This command would tell you what bit rates is supported 
```
 iwlist scan
```
For me it is 
```

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:DF:63:DA
                    ESSID:"homerouter269"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=79/100  Signal level:16/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                 [B]   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s [/b]
                    Extra:tsf=0000002dd7122179
                    Extra: Last beacon: 4ms ago


```
Hope that some experts could read this thread and help us.

---

### Post by greenjumper on 2009-03-12
My rate is according to the output of iwconfig already set to 5.5 so that is not the problem! I could try setting it even lower?! Maybe then it will become more stable and hopefully not too slow, what do you think?
Another thought is that I have read that the driver for this card doesn't cope with encyrption very well. My network currently uses WPA2 maybe if I change it to WPA1?
What do you reckon?

---

### Post by afeasfaerw23231233 on 2009-03-12
Is your connecton stable at 5.5mb/s? Does the ping give you some error message? 
If it is still not stable then I doubt that the signal may be too weak, and you may try 2mb/s and 1mb/s to test it again. 
I read somewhere in the net WPA1 with AES (not TPIK) is secure enough. I don't know if it is the WPA2 causing the instability. But you may try WPA1, that's not a difficult setting in the router.

---

### Post by greenjumper on 2009-03-12
Pinging my router doesn't seem to work it just says:

Do you want to ping broadcast? Then -b

I can't get anything that looks like your output!

---

### Post by afeasfaerw23231233 on 2009-03-12
Oops. I never receive a message like ```
Do you want to ping broadcast? Then -b 
``` in ping. Would you please post the following result:
```
 ifconfig 
```
```
iwconfig
```
```
iwlist scan
```
```
route
```

---

### Post by greenjumper on 2009-03-12
> adam@adam-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:96:ad:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:8f:2d:8c  
          inet addr:192.168.0.154  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe8f:2d8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:822420 (822.4 KB)  TX bytes:126444 (126.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-8F-2D-8C-64-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



> adam@adam-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Melad"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:A7:EC:F6   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=58/100  Signal level:-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

> adam@adam-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:A7:EC:F6
                    ESSID:"Melad"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-42 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000008e2d2b183
                    Extra: Last beacon: 84ms ago

pan0      Interface doesn't support scanning.


> adam@adam-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         localhost       0.0.0.0         UG    0      0        0 wlan0
adam@adam-laptop:~$ 


See anything interesting.....!

---

### Post by afeasfaerw23231233 on 2009-03-12
It seems that you have already connect to the router. But you ping the wrong IP which is not within your netmask (perhaps "disallow ping from LAN" is enabled in the router?). Do you know what's the IP of your router? You can also ping google.com or yahoo.com . 
```
ping google.com
```

---

### Post by greenjumper on 2009-03-12
Ok I'm pinging google.com at the moment! No errors so far!

P.S. Currently running at 2mb/s

---

### Post by afeasfaerw23231233 on 2009-03-12
Then just stress test it to see if it is stable. You can also open System > admistration > system monitor and check the network history.

---

### Post by greenjumper on 2009-03-12
It looks like this for me: 
```
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=453 ttl=241 time=178 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=454 ttl=241 time=179 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=455 ttl=241 time=183 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=456 ttl=241 time=183 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=457 ttl=241 time=184 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=458 ttl=241 time=183 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=459 ttl=241 time=178 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=460 ttl=241 time=179 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=461 ttl=241 time=178 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=462 ttl=241 time=182 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=463 ttl=241 time=182 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=464 ttl=241 time=178 ms

```

Considerably slower than yours isn't it!

---

### Post by greenjumper on 2009-03-12
And then it went like this when I opend about a million firefox tabs with lots of pictures:

```
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=23 ttl=241 time=293 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=25 ttl=241 time=335 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=26 ttl=241 time=448 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=27 ttl=241 time=492 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=29 ttl=241 time=248 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=30 ttl=241 time=517 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=33 ttl=241 time=446 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=34 ttl=241 time=250 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=36 ttl=241 time=247 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=38 ttl=241 time=349 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=39 ttl=241 time=465 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=40 ttl=241 time=429 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=41 ttl=241 time=308 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=42 ttl=241 time=223 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=43 ttl=241 time=304 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=44 ttl=241 time=319 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=45 ttl=241 time=313 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=46 ttl=241 time=368 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=47 ttl=241 time=365 ms

```

---

### Post by greenjumper on 2009-03-12
From the router (found the address) it looks more like yours
```
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=1.81 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=2.33 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=128 time=1.72 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=128 time=2.19 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=128 time=1.73 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=128 time=2.35 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=128 time=2.25 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=128 time=1.87 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=128 time=2.78 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=128 time=1.81 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=128 time=2.03 ms

```

---

### Post by greenjumper on 2009-03-12
Seems to be pretty stable, but then I thought it was yesterday as well and then all of a sudden it went mad!
Has yours been consistent the whole time since you made those changes yesterday?

---

### Post by afeasfaerw23231233 on 2009-03-12
I am planning to find a replacement antena from the second-hand market. The original antenna came with the router is just 2dBi. I heard that it helps a lot with signal boost. 
By the way can you tell how far are you from the router? The signal of my router drops significantly after passing one cement wall. And the room I am staying is around 10 metres away with 3 walls blocking it.

---

### Post by afeasfaerw23231233 on 2009-03-12
> **greenjumper said:**
> Seems to be pretty stable, but then I thought it was yesterday as well and then all of a sudden it went mad!
Has yours been consistent the whole time since you made those changes yesterday?

Yes it is quite consistent since I fixed it at 12mb/s. But speed decrease drastically as the notebook is away from the router. I am subscribing a 10mb/s cable (sharing) so it would be a waste of bandwidth! Let see if I can find a cheap replacement antenna under 5USD.

---

### Post by afeasfaerw23231233 on 2009-03-12
Bad news. The connection hung without a reason and I reinstall ndiswrapper win 98 driver again.

---

### Post by afeasfaerw23231233 on 2009-03-17
My connection disconnects every 2-3hr without a reason. It happens even the router is next to me. In windows xp it is fully functional. So I am sure there must be some problem in the ubuntu driver / ndiswrapper driver. 

2-3hr random disconnection. A bit annoying. No good but not too bad though. (tired...)

EDIT: the ndiswrapper is better. It loses connection every 2-3 hr. With the native rtl8187 driver 1hr is the maximum.

---

### Post by greenjumper on 2009-03-18
Hi again.

My connection has been working on my home network pretty well the last few days. It times out mybe once or twice a day when it is connected the whole day - I can live with that. The only thing I am still having bigger problems with is networks that use WEP encryption. I seem to remember reading somewhere that this is the worse type of encryption for the driver. Unfortunately my parents and my in-laws both use WEP! Not a major problem but annoying!
I still haven't tried Ndiswrapper - is it worth it?

---

### Post by afeasfaerw23231233 on 2009-03-18
Hi. 
I am a bit confused. Today I searched the forum again and finally found some ways to remove ndiswrapper completely and reinstalled the native rtl8187 driver. Now it's more than 4 hours without losing connection. It's a break-record for me. To be frank I'm really not sure whether the native driver or ndiswrapper is better. As you know I'm a newb too, the conclusion on my previous posts may be wrong. But one thing for sure is that the "fixed rate" method introduced by the OP definitely lower the frequence of losing connection as auto-negotiation doesn't work with the driver (either the native or ndiswrapper one). 
As long as the native driver working for you, I think you don't need to try ndiswrapper. Both the native driver and ndiswrapper driver can use WPA as encryption. I am now using WPA1 with the native driver, wicd as the network manager. 
(yeah, WEP is so weak.)

Why there's still no expert to help us?

---

### Post by afeasfaerw23231233 on 2009-03-21
Good news
My problem seems solved

[http://ubuntuforums.org/showthread.php?p=6932570#post6932570](http://ubuntuforums.org/showthread.php?p=6932570#post6932570)
On my system ndiswrapper wasn't installed correctly and the driver being used was the native rtl8187 actually. Now I have the native rtl8187 removed and using ndiswrapper without the "fixed rate script". The auto-negotiation works! The rate drops from 54mb/s to 1mb/s as the distance increases and the signal is weaken. So far it doesn't suffer from connection sudden lost problem. Although the ping command sometimes returns "DUP!" error, it still works well.

EDIT:
Greenjumper: You may try ndiswrapper if the native driver doesn't work. ndiswrapper can do the auto-negotiation of bandwidth. If your native driver just works well and the sudden disconnection doesn't happen frequently you can keep your native driver.

---

### Post by jonescsr on 2009-03-22
hey guys im having big difficulties getting my belkin to work. same model and all that running on 8.10 kubuntu. 

the probelm is, im trying to follow this tutorial, [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)

but the problem im running into is that i can't get root. it keeps asking me for the root pass and i never set up a root pass, so it asks for my pass... which is weird... because i am not root and it tells me that the only password i have ever given it is wrong.

and also, i tried sudo passwd root and then it said set "jones" password and my account name is jones, but i told it to passwd "root" and im guessing it is assuming im root, but then i cantmodify and save any files in /etc/udev/ or any other significant areas for that matter.

what is going on?! i was convinced by a friend to format my whole PC and go with kubuntu and his looked GREAT! but mine is just failing so bad...

---

### Post by jonescsr on 2009-03-23
tough crowd..

---

### Post by dunnerz on 2009-03-29
My Friends laptop is having issues....

Using 8.10, have previously applied the 
iwconfig wlan0 rate 5.5M fixed
to /etc/rc.local and it did the job. However, on the 2.6.27-11 kernel that fix has no affect, and it won't connection to the net after random time between 5 and 20 mins (although network manager says connected with no problems) - only rebooting machine fixes it

Working fine on the 2.6.27-9 and -7 kernels, so having to boot on the -9 all the time. Obviously a worry as my friend is quite new to Ubuntu/linux, so having to explain why is quite a tough ask (trying to alter grub to pick a different default) - worry that 9.04 will manifest this problem as well.


Any body have any ideas...?

---

### Post by afeasfaerw23231233 on 2009-03-29
Are you using the native rtl8187 driver or the ndiswrapper?

---

### Post by Tom--d on 2009-03-29
Hello dunnerz,

The Realtek Wireless card is a bitch, to put it bluntly.


To make the -9 default, Install a program called Startup-manager (something like that, can't remember of the to of my head). It is in Add/Remove and then go on it (System > Admin > Start...) and make the default kernel the one you want. Every time you boot, it will boot into that one :)

Also,
I'm sure its fixed with the new kernel in Ubuntu 9.04 (I can't confirm because I bought a new laptop, came with a Intel Wireless card (yay)).

---

### Post by dunnerz on 2009-03-30
> **afeasfaerw23231233 said:**
> Are you using the native rtl8187 driver or the ndiswrapper?

Thanks for the reply.... Native driver.

> **Tom--d said:**
> Hello dunnerz,

The Realtek Wireless card is a bitch, to put it bluntly.


To make the -9 default, Install a program called Startup-manager (something like that, can't remember of the to of my head). It is in Add/Remove and then go on it (System > Admin > Start...) and make the default kernel the one you want. Every time you boot, it will boot into that one :)

Also,
I'm sure its fixed with the new kernel in Ubuntu 9.04 (I can't confirm because I bought a new laptop, came with a Intel Wireless card (yay)).

Hi, 

Thanks for that - from the other searches, etc. it sound like most people are not having fun with this card (so I was quite happy with the original fix). Didn't know about startup manager, instead I cheated and commented out the other kernel in menu.lst, but this sounds like a much better method ! (learn something new everyday!)

I was hoping it was fixed in 9.04... think when it comes out I'll bite the bullet and upgrade it and hope that it fixes it (and if it doesn't, then I'll be trawling every page to find a solution!)


Thanks,
dunnerz.

---

### Post by Tom--d on 2009-03-30
> **dunnerz said:**
> Thanks for the reply.... Native driver.



Hi, 

Thanks for that - from the other searches, etc. it sound like most people are not having fun with this card (so I was quite happy with the original fix). Didn't know about startup manager, instead I cheated and commented out the other kernel in menu.lst, but this sounds like a much better method ! (learn something new everyday!)

I was hoping it was fixed in 9.04... think when it comes out I'll bite the bullet and upgrade it and hope that it fixes it (and if it doesn't, then I'll be trawling every page to find a solution!)


Thanks,
dunnerz.

Try the Ubuntu 9.04 Beta, its stable (for me). See if it works then.
There is always a way to get it to work :) Just don't give up.

---

### Post by migalhasm on 2009-03-30
hi,

i have 9.04 beta. it still hasn't been fixed. i still have to use iwconfig wlan0 rate 5.5M fixed to get it to work. and it sucks, because i have 10mbits at home and my laptop is locked at 5.5. i can't download stuff from the internet because it disconnects after a while. hope it'll be fixed in the final 9.04

---

### Post by Tom--d on 2009-03-30
> **migalhasm said:**
> hi,

i have 9.04 beta. it still hasn't been fixed. i still have to use iwconfig wlan0 rate 5.5M fixed to get it to work. and it sucks, because i have 10mbits at home and my laptop is locked at 5.5. i can't download stuff from the internet because it disconnects after a while. hope it'll be fixed in the final 9.04

Sorry to hear that.
Maybe try with the newest kernel? and compile it?

---

### Post by dunnerz on 2009-03-31
> **Tom--d said:**
> Try the Ubuntu 9.04 Beta, its stable (for me). See if it works then.
There is always a way to get it to work :) Just don't give up.

I won't give up - but being a friends laptop, I only get a chance to play with it occasionally (if it was my own, I wouldn't stop until resolved!) - so after quick fixes. My friend - being quite new to Ubuntu might struggle with the Beta, but as soon as it's a finial, I will upgrade it.....however......

> **migalhasm said:**
> hi,

i have 9.04 beta. it still hasn't been fixed. i still have to use iwconfig wlan0 rate 5.5M fixed to get it to work. and it sucks, because i have 10mbits at home and my laptop is locked at 5.5. i can't download stuff from the internet because it disconnects after a while. hope it'll be fixed in the final 9.04

If that fix doesn't work (have you added to /etc/rc.local ?), sounds like that 9.04 has the same issues as 8.10, 2.6.27-11 kernel (i.e. even after applying the fix, it still times out)?

---

### Post by Tom--d on 2009-03-31
> **dunnerz said:**
> I won't give up - but being a friends laptop, I only get a chance to play with it occasionally (if it was my own, I wouldn't stop until resolved!) - so after quick fixes. My friend - being quite new to Ubuntu might struggle with the Beta, but as soon as it's a finial, I will upgrade it.....however......



If that fix doesn't work (have you added to /etc/rc.local ?), sounds like that 9.04 has the same issues as 8.10, 2.6.27-11 kernel (i.e. even after applying the fix, it still times out)?


"new, much cleaner, rate control API "
That is in the new Kernel, 2.6.29
Basically this means (In theory) that all the problems with the wireless card will "disappear".

There is a way of updating all the wireless drivers in any Ubuntu release (Inculding the driver for the Wireless Card :D) to the lastest version (From Kernel 2.6.29)

This is how:

Download the package here: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

And extract it.

Then:
(In Terminal)
```
cd /home/username/Desktop/compact-wireless etc
```
```
make
```
```
sudo make install
```

Reboot!

Hope it fixes the problems.
(If wireless doesn't work at first, just, in termainl, run this command:
```
sudo modprobe rtl8187
```
Then wireless should work.
(If it does, stick that code (without sudo) in /etc/rc.local)

---

### Post by dunnerz on 2009-04-01
Tom--d,

Brilliant - thanks for your help.

I will give that a go at the weekend (when I see my Friend)


Thanks.

---

### Post by afeasfaerw23231233 on 2009-04-01
I am using ndiswrapper for realtek 8187L (ID:8187). The native driver (rtl8187) doesn't work for me. Fixing the rate (e.g. 1M) would only reduce the frequency of disconnection. Also, in my system the native driver cannot auto-negotiate the rate as the signal is weaken. After I have install ndiswrapper with win98 driver the connection is perfect even it's in extremly high trafic. 

p.s. I am using Intrepid i686

---

### Post by sosostris on 2009-04-02
I experienced the same problems described in this thread. 
Updating [http://wiki.ubuntuusers.de/Linux_Wireless](http://wiki.ubuntuusers.de/Linux_Wireless) and activating channel11-13 fixed the problem for me on Intrepid(amd64) 2.6.27-11, with RTL8187B usb wlan.

---

### Post by dunnerz on 2009-04-03
> **Tom--d said:**
> "new, much cleaner, rate control API "
That is in the new Kernel, 2.6.29
Basically this means (In theory) that all the problems with the wireless card will "disappear".

There is a way of updating all the wireless drivers in any Ubuntu release (Inculding the driver for the Wireless Card :D) to the lastest version (From Kernel 2.6.29)

This is how:

Download the package here: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

And extract it.

Then:
(In Terminal)
```
cd /home/username/Desktop/compact-wireless etc
```
```
make
```
```
sudo make install
```

Reboot!

Hope it fixes the problems.
(If wireless doesn't work at first, just, in termainl, run this command:
```
sudo modprobe rtl8187
```
Then wireless should work.
(If it does, stick that code (without sudo) in /etc/rc.local)

My Friend followed your instructions (by himself - I'm well impressed) - and it fixed it perfectly - so many thanks for your help.

Also, sounds like good news that it is fixed in 9.04. :D

---

### Post by tatterdemalion on 2009-04-16
> **Tom--d said:**
> Hope it fixes the problems.
(If wireless doesn't work at first, just, in termainl, run this command:
```
sudo modprobe rtl8187
```
Then wireless should work.
(If it does, stick that code (without sudo) in /etc/rc.local)

Thank you for the hint. :)
I had done it before and it seemed to work. But this time on another laptop, (same model as mine) it did not. :(

Here is the last lines of make command:
```

ibertas/if_sdio.o
/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.c:53: error: &#8216;SDIO_DEVICE_ID_MARVELL_8688WLAN&#8217; undeclared here (not in a function)
make[4]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.o] Error 1
make[3]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/taner/Desktop/compat-wireless-2009-04-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
Does it **make** any sense to anyone out there?

---

### Post by oobe-feisty on 2009-04-19
> **tatterdemalion said:**
> Thank you for the hint. :)
I had done it before and it seemed to work. But this time on another laptop, (same model as mine) it did not. :(

Here are the last lines of make command:
```

ibertas/if_sdio.o
/home/taner/Masaüstü/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.c:53: error: ‘SDIO_DEVICE_ID_MARVELL_8688WLAN’ undeclared here (not in a function)
make[4]: *** [/home/taner/Masaüstü/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.o] Error 1
make[3]: *** [/home/taner/Masaüstü/compat-wireless-2009-04-16/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/taner/Masaüstü/compat-wireless-2009-04-16/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/taner/Masaüstü/compat-wireless-2009-04-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
Does it **make** any sense to anyone out there?




it doesnt make any sense to me i came accross your post cause i googled the same term i just downloaded a 5 day older tar ball and that worked must be a bug that they need to get out 

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2)

this is the one i downloaded that built fine

---

### Post by sosostris on 2009-04-21
Thx for posting the link anyway. 
I also cannot compile the package for the last ~10days. 
I am pretty new to ubuntu but could it be the kernel 2.6.27-11 is just no longer supported? You can actually make the build work by defining the constant by yourself. Nevertheless it got me in trouble later and the package totally broke my wlan.


Now I installed the 04-08 version and it works like a charm. It also solves the well known issue of losing your wlan connection when doing to much upload (eg torrent).

---

### Post by tatterdemalion on 2009-04-23
> **oobe-feisty said:**
> it doesnt make any sense to me i came accross your post cause i googled the same term i just downloaded a 5 day older tar ball and that worked must be a bug that they need to get out 

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2)

this is the one i downloaded that built fine

Thanks. I will try that one. :)

---

### Post by ElVirolo on 2009-04-25
I installed the latest compat-wireless drivers, and it doesn't make much difference. I'm still downloading at 125 KB/s although I have a 30 Mb connection.

I tried installing linux-backports-modules-jaunty, but I get the following error after I do sudo modprobe rtl8187 :
```
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rtl8187.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

This is what dmesg says : ```
[ 1379.165140] rtl8187: Unknown symbol ieee80211_generic_frame_duration
[ 1379.165328] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[ 1379.165332] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe
[ 1379.166763] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[ 1379.166767] rtl8187: Unknown symbol ieee80211_unregister_hw
[ 1379.167231] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[ 1379.167235] rtl8187: Unknown symbol ieee80211_rx_irqsafe
[ 1379.167477] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[ 1379.167481] rtl8187: Unknown symbol ieee80211_rts_duration
```

---

### Post by ElVirolo on 2009-04-25
After adding this : options cfg80211 ieee80211_regdom="EU" to /etc/modprobe.d/options, i was able to use the backported module.

However the problem stays the same.

---

### Post by Ropechoborra on 2009-04-26
[COLOR="Silver"]I was able to make my rtl8187b work in ubuntu 8.04 with this driver [http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz](http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz)

In ubuntu 9.04 the wireless card is recogniced and it connects to my router (at least it says its connected) but i don't have internet connection or ping response for the router.

Any ideas?[/COLOR]

Soultion found !! Installing the new driver release from Realtek (2009). You can download it from here [http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314](http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314)

Special thanks to pimpinjg. ( [http://ubuntuforums.org/showthread.php?p=7157415#post7157415](http://ubuntuforums.org/showthread.php?p=7157415#post7157415) )

---

### Post by Tom--d on 2009-04-27
> **tatterdemalion said:**
> Thank you for the hint. :)
I had done it before and it seemed to work. But this time on another laptop, (same model as mine) it did not. :(

Here is the last lines of make command:
```

ibertas/if_sdio.o
/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.c:53: error: ‘SDIO_DEVICE_ID_MARVELL_8688WLAN’ undeclared here (not in a function)
make[4]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas/if_sdio.o] Error 1
make[3]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/taner/Desktop/compat-wireless-2009-04-16/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/taner/Desktop/compat-wireless-2009-04-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
Does it **make** any sense to anyone out there?

Hey :)
It's been a while since I've been on here.

You need to instal the package "build-essintal" to build the drivers. Then it should just work :D
Don't forget to modprobe rtl8187 to see if it worked:)

---

### Post by ElVirolo on 2009-04-30
Thanks Ropechoborra, the driver you mentionned works quite well indeed!

Edit : in fact, it works fantastically well !

---

### Post by phantom3113 on 2009-05-27
> **ElVirolo said:**
> Thanks Ropechoborra, the driver you mentioned works quite well indeed!

Edit : in fact, it works fantastically well !

I installed the driver(s) and it/they worked as well over here...sort of. After blacklisting the old ones and then makeing, make installing, and then rebooting, I lost wireless connections (even after changing preferences in wicd to wlan1 instead of wlan0). I attempted to fix it a few times, but then gave up and went to bed. This morning, I woke up and turned on my computer expecting to return to the fixing attempt only to find that my wireless now worked, and exceptionally well at that. However, after about 15 minutes, it went away. With the old drivers, my wireless was always on. With these, the card seems to respond to the wireless switch built into the laptop (the wifi light on the laptop is on; prev. it wasn't) Unfortunately my switch is broken and stuck in the off position :( On the other hand, I've now had the computer on for the past hour without losing internet. Needless to say, I'm a little confused and I'm not sure if it's "working" yet. Also, here's dmesg |grep 818:

```
[    0.548181] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   13.924167] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
[   13.924173] rtl8187: Initializing module
[   13.924175] rtl8187: Wireless extensions version 22
[   13.924178] rtl8187: Initializing proc filesystem
[   13.984482] rtl8187: idProduct:0x8189, bcdDevice:0x200
[   14.041994] rtl8187: Channel plan is 0 
[   14.042492] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[   14.451801] rtl8187: Card MAC address is 00:16:44:1a:5d:e6
[   14.935740] rtl8187: EEPROM Customer ID: 00
[   14.936110] rtl8187: Driver probe completed
[   14.939223] usbcore: registered new interface driver rtl8187
[   19.968182] apm: BIOS not found.
[   26.417418] rtl8187: rtl8187_open process 
[   26.418922] rtl8187: Now Radio ON!
[   26.429354] rtl8187: Card successfully reset
[   30.390085] rtl8187: DIG is enabled, set default initial gain index to 4
[   30.392061] rtl8187: RTL8187 + 8225 Initial Gain State 4: -74 dBm 
[   30.398076] rtl8187: WIRELESS_MODE_G
[   30.442278] rtl8187: rtl8187_open process complete
[   32.441058] rtl8187: IPSEnter(): Turn off RF.
[   32.442216] rtl8187: Now Radio OFF!
[   34.137058] rtl8187: rtl8180_down process
[   34.816177] rtl8187: rtl8187_open process 
[   34.866540] rtl8187: Card successfully reset
[   38.864333] rtl8187: DIG is enabled, set default initial gain index to 4
[   38.866449] rtl8187: RTL8187 + 8225 Initial Gain State 4: -74 dBm 
[   38.872447] rtl8187: WIRELESS_MODE_G
[   38.929651] rtl8187: rtl8187_open process complete
[   38.930168] rtl8187: ISLeave(): Turn on RF.
[   38.932461] rtl8187: Now Radio ON!
[  114.932888] rtl8187: GPIO Polling Methord Will Turn Radio Off
[  114.935634] rtl8187: Now Radio OFF!
[  124.932854] rtl8187: GPIO Polling Methord Will Turn Radio On
[  124.935344] rtl8187: Now Radio ON!
[ 1242.984375] rtl8187: RTL8187 + 8225 Initial Gain State 3: -78 dBm 
[ 1282.992322] rtl8187: RTL8187 + 8225 Initial Gain State 2: -78 dBm 
[ 1314.935361] rtl8187: GPIO Polling Methord Will Turn Radio Off
[ 1314.942861] rtl8187: Now Radio OFF!
[ 1322.933186] rtl8187: GPIO Polling Methord Will Turn Radio On
[ 1322.938035] rtl8187: Now Radio ON!
[ 1475.544050] rtl8187: RTL8187 + 8225 Initial Gain State 3: -78 dBm 

```

---

### Post by Lex Luthor on 2009-06-01
> **Ropechoborra said:**
> [COLOR="Silver"]
In ubuntu 9.04 the wireless card is recogniced and it connects to my router (at least it says its connected) but i don't have internet connection or ping response for the router.

Any ideas?[/COLOR]

Soultion found !! Installing the new driver release from Realtek (2009). You can download it from here [http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314](http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314)


I've got a new notebook and it came with RTL8187B (I think the code is 0bda).
I'am getting very very angry to make it work with ubuntu 9.04. My wife is claiming to put Vista back. I don't want, but I will have no choice if I could not make this wireless work.
I have the same problem as said above: can connect but cannot browse, unless I am very close to the AP.
Does this solution works on 9.04 jaunty ?

---

### Post by rubblebuster on 2009-08-09
> **Ropechoborra said:**
> 
Soultion found !! Installing the new driver release from Realtek (2009). You can download it from here [http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314](http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314)

Special thanks to pimpinjg. ( [http://ubuntuforums.org/showthread.php?p=7157415#post7157415](http://ubuntuforums.org/showthread.php?p=7157415#post7157415) )

Well thanks for that find. Unfortunately it finally didn't succeeded, but at least I can do the following with that driver:

- driver loads on start-up
- I can see my AP using iwlist scan wlan0
- I can see my AP in wicd

but if I try to connect using wicd I get the following in the syslog:

```
Aug  9 23:01:53 erik-laptop kernel: [  313.804329] rtl8187: ISLeave(): Turn on RF.
Aug  9 23:01:53 erik-laptop kernel: [  313.816699] rtl8187: Now Radio ON!
Aug  9 23:01:53 erik-laptop kernel: [  314.015730] Linking with xxx_01, channel:1
Aug  9 23:01:53 erik-laptop kernel: [  314.032690] channel(1). is invalide
Aug  9 23:01:55 erik-laptop kernel: [  316.046702] Linking with xxx_01, channel:1
Aug  9 23:01:55 erik-laptop kernel: [  316.072570] channel(1). is invalide
Aug  9 23:01:58 erik-laptop kernel: [  318.572488] Linking with xxx_01, channel:1
Aug  9 23:01:58 erik-laptop kernel: [  318.589368] channel(1). is invalide

```Any ideas about that?

I'm using Ubuntu 9.04 with 2.6.28-12-generic. My 8187B is actually a

lsusb:
```
Bus 002 Device 003: ID 0bda:[COLOR=Red]**8197**[/COLOR] Realtek Semiconductor Corp. RTL8187B Wireless Adapter
```Currently I'm running the driver provided by [linuxwireless.org]("http://linuxwireless.org/"). These worked fine until I had to re-position my WLAN-router a few days ago. Now the distance between computer and router is a little bit larger (some metres) and I encounter poor download-performance. :-(

That's the reason why I wanted to give these Realtek driver a try...

Many thanks in advance & cheers, Erik

---

### Post by mabula on 2009-08-11
Hi there,
 
I've installed ubuntu 9.04 a couple of days ago and couldn't get my Netgear USB 2.0 stick with RTL8187B chipset to work properly. I've tried several suggestions like turning off acpi, using alternative ndiswrapper driver, turning off wpa2, ipv6 and so on....
 
I was considering to buy another usb stick that would work until I stumbled on this thread on the ubuntu forum.
 
Fixing the rate at 5.5M works perfectly. Before my connection with the router came up but pinging the router wouldn't work most of the time. Now each ping is succesfull so I guess this is the solution :P. I will try to increase my fixed rate to see what happens...
 
Thanks a lot!
 
Mabula

---

### Post by Nikkiru on 2009-11-16
I'm new to this forum, befuddled by a lot of the jargon, not very adept at using the search function, and this is a dauntingly long thread. So please forgive me if this has already been covered.

 I have a driver which according to its readme file:

> Release Date: 2007-08-22, ver 1.24
RTL8187B Linux driver version 1.24

   --This driver supports RealTek RTL8187/RTL8187B Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5/6/7, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc.
     2.4 kernel:
     Redhat 9.2, etc
   - Support Client mode for either infrastructure or adhoc mode
   - Support WEP, WPAPSK and WPA2PSK connection

I'm not especially tech savvy, but I do understand that Ubuntu is based on a debian kernel. And not being especially tech savvy, I haven't yet figured out how to install this driver in Ubuntu 9.1.

I would be very grateful if somebody could give me an idiot-proof step-by-step rundown on the installation process for this driver.

---

### Post by Nikkiru on 2009-11-16
I found my way to the terminal, and tried a command somebody showed me in another thread. If I'm reading it right, it seems to be indicating that the system hasd detected both  my internal and external wifi cards:

> nikkiru@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I'd be grateful if somebody would tell me what "no wireless extensions" means and what (if anything) I can do about it. And maybe even how to associate these devices, assuming that they *need* to be associated in order to function.

---

### Post by The Pixel Developer on 2010-01-10
> **Ropechoborra said:**
> [COLOR=Silver]I was able to make my rtl8187b work in ubuntu 8.04 with this driver [http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz](http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz)

In ubuntu 9.04 the wireless card is recogniced and it connects to my router (at least it says its connected) but i don't have internet connection or ping response for the router.

Any ideas?[/COLOR]

Soultion found !! Installing the new driver release from Realtek (2009). You can download it from here [http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314](http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314)

Special thanks to pimpinjg. ( [http://ubuntuforums.org/showthread.php?p=7157415#post7157415](http://ubuntuforums.org/showthread.php?p=7157415#post7157415) )

I downloaded this driver for Karmic, but it wouldn't compile. I comment out the code it was complaining about (crazy) and got it to compile. Before I was getting speeds of 1MB/s now I'm hitting the 15s and 20s.

Thanks.

---

### Post by GonzalitoUY on 2010-03-17
> **oobe-feisty said:**
> it doesnt make any sense to me i came accross your post cause i googled the same term i just downloaded a 5 day older tar ball and that worked must be a bug that they need to get out 

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/04/compat-wireless-2009-04-13.tar.bz2)

this is the one i downloaded that built fine

I've had this problem of losing my connection when I was using torrents, I'll check this driver.SO far, after installing and follow the instructions on the Readme, all seems okay, currently checking the torrent issue.
Will keep informing

---

### Post by GonzalitoUY on 2010-03-20
Sadly, using torrents still disables my wifi adapter (and I think all my network) after using for a while.
Anyone still have that issue using RTL8187B?
I'm seriously considering gettin another miniPCIe card

---

### Post by aishwaryaukey on 2010-03-30
hi.... can u tell me what to do if i want to install rtl8187b on RHEL5???

---

