---
title: "D-Link Adapter Issues"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by FirefoxRocks on 2008-06-22
I have followed instructions from various articles about the installation of several packages of network tools in order to get the adapter detected and working but it still isn't working!!

My adapter is a DWA-130, which according to the list found at the [wiki](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53), is compatible.

I managed to install ndiswrapper and ndisgtk, along with the mandatory dependencies, onto my newly installed Ubuntu 8.04. According to the ndisgtk utility, my driver and adapter has been installed correctly.

Problem is, in the terminal when I run **iwconfig**, **ifconfig**, **depmod -a** or **modprobe ndiswrapper** (by sudo or regular user), the terminal window freezes and I need to reboot in order to open up a terminal again. In fact, I can only reboot by another console (Ctrl+Alt+F2 or something like that), the Quit button does not work.

The Network applet thing does not detect my wireless connection as it said it would after installing the appropriate drivers. I have tried setting up the netmw245.inf driver both at the command line and on the GUI, but both don't seem to work.

**lsusb** shows that the device is being detected, and **lshw -C network** does not show the device being detected. Once I had wlan0 showing in iwconfig, but after a reboot, that disappeared and now iwconfig doesn't even work.

I have searched the Ubuntu forums and this looks related: [http://ubuntuforums.org/showthread.php?t=796417&highlight=DWA+130](http://ubuntuforums.org/showthread.php?t=796417&highlight=DWA+130) . Could someone please tell me step-by-step what to do to fix this issue and get the adapter working again?

FirefoxRocks

---

### Post by FirefoxRocks on 2008-06-23
bump

---

### Post by dmizer on 2008-06-23
which windows driver did you load into ndiswrapper?

post the output of:
```
ndiswrapper -l
```

---

### Post by FirefoxRocks on 2008-06-23
Ok, I have made some more progress by doign different things (sorry, I didn't take notes).
 
Right now, the adapter detects my network (and my router) and has an IP address.
 
I am not on my Ubuntu system right now so I cannot post **ndiswrapper -l** output but will do as soon as possible. It is kinda hard because there is no Internet connection there :P
 
I am on the step that says Check DNS Settings and I can't ping to the IP address or the domain name. But using **ifconfig**, it shows that wlan0 has an IP address. It is set on DHCP right now.
 
Any ideas?

---

### Post by dmizer on 2008-06-23
i don't know what howto you're following, but if you have an ip address you've almost got it made.

a few things i can think of:
1) disable ipv6 - [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)
2) use opendns servers - [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by FirefoxRocks on 2008-06-24
I'm following the Help and Support program on Ubuntu.

I already have disabled IPv6

---

### Post by dmizer on 2008-06-24
> **FirefoxRocks said:**
> I'm following the Help and Support program on Ubuntu.

I already have disabled IPv6

okay ... did opendns not help?

---

### Post by FirefoxRocks on 2008-06-27
Nope, I don't think it is a DNS issue because pinging the IP address doesn't work (so obviously the domain name doesn't either)

---

### Post by dmizer on 2008-06-27
what is the output of:
```
lshw -C network
```
and
```
ndiswrapper -l
```

---

### Post by FirefoxRocks on 2008-06-27
/* iwconfig */

wlan0     IEEE 802.11g  ESSID:"dlink"  
        Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:3D:75:1B
        Bit Rate=78 Mb/s   Sensitivity=-200 dBm
        RTS thr=2346 B   Fragment thr=2346 B
        Encryption key:off
        Power Management:off
        Link Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/* lshw -C network */

 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:11:f3:52:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 link=yes multicast=yes wireless=IEEE 802.11g

/* ndiswrapper -l */

netmw245 : driver installed
    device (07D1:3B11) present

---

### Post by dmizer on 2008-06-28
humm ... how about also posting:
```
lsusb
```

---

### Post by FirefoxRocks on 2008-06-28
/* lsusb */

Bus 005 Device 002: ID 07D1:3B11 D-Link System

(There weren't any other devices plugged in, so the other ones were ID 0000:0000.)

---

### Post by dmizer on 2008-06-28
do you have usb 2.0 enabled in your bios?  is your laptop even usb 2.0 capable?

---

### Post by FirefoxRocks on 2008-06-30
Yes I have USB 2.0 capable on the **desktop**. Otherwise Windows XP would say that this device could work on a faster port...or w/e the message says.

---

### Post by FirefoxRocks on 2008-07-04
bump again......any other advice?

---

### Post by Shannon_VanWagner on 2008-08-24
Here's what worked for me:

The D-Link DWA-130(I have ver: A1) USB Wireless network adapter is said to work with ndiswrapper on this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

But the problem ( as of 08-24-08 ) is that when you download the driver for DWA-130 from the D-Link website, you get the Setup.exe file with no *.inf file to load with sudo ndisgtk.

So I cheated by going to a Windows XP machine and installing the driver there. Then I used the "date created" column view setting in XP to see that "\windows\inf\oem9.inf" was just created after installing the driver. Inside the oem9.inf file, there is a reference to "Mrvw243.sys" and "MRVW245.sys" driver files. So then I searched \windows (\windows\system32\drivers probably) for the two *.sys files and copied then copied all files named below onto my Ubuntu machine. I then used sudo ndisgtk and loaded the "oem9.inf" file into the ndiswrapper, rebooted, and now it works.

Here are the files I needed to load the ndiswrapper(not sure every single one is necessary):
oem9.inf
oem9.PNF
Mrvw243.sys
MRVW245.sys


So the next thing I did was notified D-Link that they should provide the raw *.inf and *.sys files so that we can use this device in Linux without having to extract the silly Setup.exe file on WinXP first.

Please yell at D-Link yourself to increase the popularity of this suggestion, emphasizing that we SHOULD NOT have to use WINXP at all to get these *.inf and *.sys files!!
Contact them here:
[http://support.dlink.com/contact/](http://support.dlink.com/contact/)

Note: for me, lsusb shows: Bus 001 Device 004: ID 07d1:3b11 D-Link System

Please digg this posting (using the link below) to encourage D-Link to change their ways and provide the *.inf and *.sys files directly:

Cheers! :guitar:

Shannon VanWagner

(submitted using a wireless connection with the DWA-130 Ver:A1)

---

### Post by FirefoxRocks on 2008-08-25
Actually, I got this working now.
By the way, D-Link did provide inf and sys files for its drivers on the CD included with the adapter.

Now the thing is, every time I boot up into Ubuntu, I have to open up a Terminal window, switch user to root and type the following commands:

modprobe ndiswrapper
iwconfig wlan0 essid "dlink"

Any idea on how to do this automatically?

---

### Post by dmizer on 2008-08-25
> **FirefoxRocks said:**
> Actually, I got this working now.
By the way, D-Link did provide inf and sys files for its drivers on the CD included with the adapter.

Now the thing is, every time I boot up into Ubuntu, I have to open up a Terminal window, switch user to root and type the following commands:

modprobe ndiswrapper
iwconfig wlan0 essid "dlink"

Any idea on how to do this automatically?

Well start by running this command:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```
Reboot. Then you can configure your wireless settings in system > administration > network

---

### Post by krash182 on 2009-03-05
I am having similar problems I installed my DWA-130 on my hp pavillion when it was running 7.  I got it to work so I then updated to 8.04 and lost everything involving my usb wireless.  If I even plug it in my whole computer locks up requiring a hard shutdown, removal of the DWA-130 stick and rebooting.  MY upgrade wiped our whatever setting I managed to use to make it work and now there is a very major conflict somewhere in the system.  I would like to make it work with the dwa 130 but if I cant i will take suggestions for another that Linux (UBUNTU) supports that is 1)/USB and 2/under $50.00  I shop Tiger Direct now that Comp USA closed.

---

### Post by Shannon_VanWagner on 2009-03-05
What happens if you Boot to the Ubuntu 8.10 LiveCD with your wireless device plugged in? Does it get detected, and if so - does it work?

If so, perhaps it's time to refresh your installation.

Shannon VanWagner

:popcorn:

---

### Post by tanha on 2009-04-28
> **Shannon_VanWagner said:**
> Here's what worked for me:

The D-Link DWA-130(I have ver: A1) USB Wireless network adapter is said to work with ndiswrapper on this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

But the problem ( as of 08-24-08 ) is that when you download the driver for DWA-130 from the D-Link website, you get the Setup.exe file with no *.inf file to load with sudo ndisgtk.

So I cheated by going to a Windows XP machine and installing the driver there. Then I used the "date created" column view setting in XP to see that "\windows\inf\oem9.inf" was just created after installing the driver. Inside the oem9.inf file, there is a reference to "Mrvw243.sys" and "MRVW245.sys" driver files. So then I searched \windows (\windows\system32\drivers probably) for the two *.sys files and copied then copied all files named below onto my Ubuntu machine. I then used sudo ndisgtk and loaded the "oem9.inf" file into the ndiswrapper, rebooted, and now it works.

Here are the files I needed to load the ndiswrapper(not sure every single one is necessary):
oem9.inf
oem9.PNF
Mrvw243.sys
MRVW245.sys


So the next thing I did was notified D-Link that they should provide the raw *.inf and *.sys files so that we can use this device in Linux without having to extract the silly Setup.exe file on WinXP first.

Please yell at D-Link yourself to increase the popularity of this suggestion, emphasizing that we SHOULD NOT have to use WINXP at all to get these *.inf and *.sys files!!
Contact them here:
[http://support.dlink.com/contact/](http://support.dlink.com/contact/)

Note: for me, lsusb shows: Bus 001 Device 004: ID 07d1:3b11 D-Link System

Please digg this posting (using the link below) to encourage D-Link to change their ways and provide the *.inf and *.sys files directly:

Cheers! :guitar:

Shannon VanWagner

(submitted using a wireless connection with the DWA-130 Ver:A1)

Are you using x86 or x86_64? Are you using it in 802.11g or 802.11n mode?

---

### Post by Shannon_VanWagner on 2009-04-28
It was x86 and 802.11g.

---

### Post by dmizer on 2009-04-28
> **Shannon_VanWagner said:**
> But the problem ( as of 08-24-08 ) is that when you download the driver for DWA-130 from the D-Link website, you get the Setup.exe file with no *.inf file to load with sudo ndisgtk.

To extract the driver from setup.exe, follow these directions: [http://ubuntuforums.org/showpost.php?p=4738306&postcount=5](http://ubuntuforums.org/showpost.php?p=4738306&postcount=5)

---

### Post by krash182 on 2009-11-12
never got detected,  moved to room with a ethernet cord.

---

