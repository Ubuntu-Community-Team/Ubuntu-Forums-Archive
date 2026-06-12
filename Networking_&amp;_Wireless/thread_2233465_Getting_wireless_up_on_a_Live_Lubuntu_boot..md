---
title: "Getting wireless up on a Live Lubuntu boot."
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by jacatone on 2014-07-08
Have an old Powerbook G4 running MacOSX 10.5. The Lubuntu v12.04 for PowerPC installs fine but doesn't automatically recognize public wifi. What commands or instructions would I need to add the SSID, Mac address manually to get the wifi to work? Thanks.

---

### Post by Bucky Ball on 2014-07-08
So you click on the network icon and there are no available networks I presume? You are sure the wireless card is up and running okay?

Could you post the output of this command, please:

```
sudo lshw -C network
```

---

### Post by jacatone on 2014-07-08
Yeah, when I run Lubuntu in "live" mode, it doesn't show anything, but when I run Mac OSX which automatically connects it shows all the networks.  Lubuntu has an "Add" in the Wireless Networking window so I'm guessing I just need to add the SSID, Mac address and so on to connect.

---

### Post by Bucky Ball on 2014-07-08
Ah, you are running from a liveDVD./USB? Then there is a chance you have no drivers installed for your card. The output of the command I gave, please.

It may not be possible to install your required drivers in a Live boot, and even if it was, the moment you reboot they will be gone.

---

### Post by jacatone on 2014-07-09
Here it is:

```
lubuntu@lubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16
       resources: irq:52 memory:80084000-80085fff
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 80
       serial: 00:0a:95:b1:c3:3a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=1.0 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:93:82:00:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-powerpc-smp firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

I usually find that a "live" install is the same as a HDD install. I sure hope I can get Lubuntu to work. It's a lot faster than OSX. That os is such a bloated pig.

---

### Post by Bucky Ball on 2014-07-09
Please use [code] [ /code] tags for terminal output. Makes it neater and easier to read. I have added them to your last post so you can click 'edit' and see how to do it (you can also click 'go advanced', highlight the code and click the # icon).

The correct driver seems to be installed. You say it doesn't recognise wifi hotspots. Does it recognise your home network, if you have one, without issue?

---

### Post by jacatone on 2014-07-09
Still doesn't find any available wifi networks. No, I just use free dialup at home. Doesn't this "sudo lshw -C network" just tell me what I have? I found a driver for the "BCM4306 802.11b/g Wireless LAN Controller" but it was a tar.gz file. Haven't been able to find a .deb file yet.  I tried the Ubuntu 12.04 for PowerPC, but it wouldn't load in live mode.

---

### Post by yancek on 2014-07-10
Your thread title state 'trying to install Lubuntu' but your question is about connecting to wireless.  In post #5, you seem to indicate you are running from a Live CD.  If you are using a CD/DVD, it is a read-only filesystem and any changes you make to your configuration will be lost on reboot as pointed out above.  That is the major difference between an actual install and running Live.  Install to a hard drive should be faster.   You should be able to extract the tar.gz file by right clicking and selecting Extract Here.  Take a look at the directory created which should have the same name as the tar.gz file.  There is usually a README file or something with instructions.

---

### Post by Bucky Ball on 2014-07-10
> **jacatone said:**
> Doesn't this "sudo lshw -C network" just tell me what I have?

Yes. You have the wrong driver by the looks. You need to do this:
```

sudo apt-get update
sudo apt-get install firmware-b43-installer
```

You may need to blacklist the driver you have installed now, but try that first.

Again, any changes you make will be lost when you reboot so this is all fairly pointless in any case. There's not a lot of help we can give you and as yancek says, your thread title is completely misleading as you are not trying to install Lubuntu, you are trying to get wireless working on a Live boot (I have now changed the title accordingly). 

A fruitless exercise in the long run if it is not running already (unless you NEVER switch your computer off or restart).

I advise a dual-boot if you want to go much further than this where your wireless card would probably work 'out-of-the-box'. Well supported card. Good luck.

PS: You need the b43 driver only. At the moment you have this:

driver=b43-pci-bridge

... and this card: BCM4306. Wrong for that card. See here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jacatone on 2014-07-10
Your right, rebooting would delete any change. I'll go ahead and do a HDD install and go from there. Just in case, how do I blacklist the driver I'll have installed first? Thanks again for all your help.

---

### Post by Bucky Ball on 2014-07-10
I wouldn't worry about that now as the situation may well be totally different when you install to hard drive. See how you go. Your card is well supported and there is a good chance it will work 'out of the box' with a full install. 

The majority of wireless cards don't work on a Live boot.I suggest you mark this thread as solved (in lieu of 'resolved') and post a new thread with a descriptive title in the appropriate forum area if you have any issues with/after the install (one support question per thread, please). Post a link here if you like. Good luck. ;)

---

### Post by jacatone on 2014-07-13
I decided to install Lubuntu 14.04 for PowerPC in hopes it would be able to find the available wifi networks. No luck there either. At least it's only a 2.1 GB install on the HDD whereas the MacOSX was 18.6GB. Anybody got any ideas on how I can get this wifi to connect?

---

### Post by Hadaka on 2014-07-13
Hi, please open a terminal ctrl/alt/t then
COPY  and paste this command.
```
lspci -n | grep 0280
```
your 4306 card has more than one possible driver
this will help us determine what driver you need.
thanks.

---

### Post by jacatone on 2014-07-13
Here it is:

jacatone@Powerbook:~$ lspci -n | grep 0280
0001:10:12.0 0280: 14e4:4320 (rev 03)

Using "sudo nm-applet" brought up the wireless icon in the taskbar anyway. Apparently this is a known issue. See the link below.

[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348)

---

### Post by Bucky Ball on 2014-07-14
Just give us:

```
sudo lshw -C network
```

That will give the card and the driver it is currently using and more details. Thanks.

As for the network manager, when it comes up are there wireless network available when you click it? Anyway, try 'Sessions & Startup' and make sure network manager is set to start with boot there.

---

### Post by jacatone on 2014-07-14
"jacatone@Powerbook:~$ sudo lshw -C network
[sudo] password for jacatone: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16
       resources: irq:52 memory:80084000-80085fff
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 80
       serial: 00:0a:95:b1:c3:3a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=1.0 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff
jacatone@Powerbook:~$" 

Still doesn't show the available wifi networks. Just an exclamation mark next to the wifi icon.

---

### Post by Bucky Ball on 2014-07-14
For that card you need the b43 driver. This:
> 
If you have a b43 card use the command
```

sudo apt-get install firmware-b43-installer
```

From here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29)

You may also need:

```
sudo apt-get install b43-fwcutter
```

See how you go.

---

### Post by Hadaka on 2014-07-14
Hi, per dr chilli555s handy guide here...
[http://ubuntuforums.org/showthread.php?t=2214110&](http://ubuntuforums.org/showthread.php?t=2214110&)
broadcom 4306 14e4:4320 (rev 03)
your wireless card works best with linux-firmware-nonfree driver
while connected to the internet via cable please do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```

Here is the fix from the wildman on your missing network icon
it is a known problem with lubuntu 14.04
[http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)

---

### Post by westie457 on 2014-07-14
@Hadaka
Not wanting to appear picky. Would you care to correct the typo's in the two commands listed?

sudo aptget update
sudo modprobe -rb43

Ignore me, my slow typing speed makes me look stupid at times.

---

### Post by jacatone on 2014-07-14
Guess I'll have to find an Ethernet connection somewhere in order to download this. Seems strange this bug has been in place for quite a while without a fix.

---

### Post by Bucky Ball on 2014-07-15
What bug? You're going to be lucky to get this up on a Live boot. Never intended for that. As I've said, if you do, the changes will be lost immediately on reboot ... :-k

---

