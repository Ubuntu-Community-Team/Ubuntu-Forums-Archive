---
title: "b43/b43legacy Troubleshooting Tips"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2008-05-03
**b43/b43legacy Troubleshooting Tips**
This is going to be a simple troubleshooting guide for b43/b43legacy users using the native driver and not the NDISwrapper version.  The NDISwrapper troubleshooter can be found at [http://ubuntuforums.org/showthread.php?t=780590](http://ubuntuforums.org/showthread.php?t=780590)

If you are looking at how to install your Broadcom wireless driver, please see [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

**Cards that are known to not work with b43/b43legacy(from the [www.linuxwireless.org](www.linuxwireless.org) site):**
The 802.11a part of the 4309 and 4312 is not supported.
There is no support for any Draft 802.11n features. We are working on it.
BCM 4328/4329

**From the b43 mailing list:**
Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

**Chipsets known not to be working in Ubuntu with b43/b43legacy(you can check by typing lspci -nn at the terminal):**
14e4:4311 rev 01
14e4:4312 rev 02
From what I understand, there was a patch applied right before the Hardy release that fixed them, but it broke most of the other ones!  From what I understand the developers for the b43/b43legacy drivers have it fixed in the 2.6.25 kernel.  For those who are brave, you can go to their site ([http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)) and try to patch it on your own.

If you are one of those people, sorry you cannot have a piece of the b43/b43legacy pie just yet.  Please try some of the NDISwrapper pie!!! ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff))

TSB 1.0:
My wireless card does not start up after installing the LiveCD.  
This is because the native driver needs the firmware.  Please see [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754) on how to get it installed.

TSB 2.0:
I am not for sure if I have it set up correctly all I know is that it is not working.

TSB 2.1.1:
The first thing we can confirm is that the firmware is loaded in the proper place.  At the terminal do:
```
ls /lib/firmware/b43
ls /lib/firmware/b43legacy
```
If you get information back, then it most likely did install the firmware properly.  This what gets created when you install b43-fwcutter.

TSB 2.1.2:
We can also confirm that it is trying to use the correct module:
```
lshw -C network
```
It should return something like:
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 11:cc:bb:44:ee:99
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.9.126 multicast=yes wireless=IEEE 802.11g
```
Look at the first configuration line.  There should be a driver=b43-pci-bridge and module=ssb.

TSB 2.1.3:
Verify that the modules are loaded properly.
You will either have a b43 or a b43legacy module along with ssb.  ndiswrapper and bcm43xx are conflicting drivers.  In order to see what we have, we can list out our modules by typing lsmod.  To take things out a step further, we will narrow it down to the modules we are concerned with:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```This will only grab the modules that start with b43, ssb, bcm43xx, or ndiswrapper.

TSB 2.1.3.1
Remove conflicting modules.
If you see bcm43xx or ndiswrapper in your lsmod list, you will need to remove them.  Do this by:
```
sudo modprobe -r <module>
```
Replace <module> with bcm43xx or ndiswrapper.  You will also want to remove the modules we want.  We will reload them next.  You should only have b43 or b43legacy and ssb.  Remove the ones that were listed like you did for bcm43xx and ndiswrapper.

TSB 2.1.3.2
Reload modules.
Depending on the module that showed up in lsmod (b43 or b43legacy), load that back.
```
sudo modprobe <module>
```
Replace <module> with b43 or b43legacy based on what showed up in your lsmod list.  If you did not have one of them, try b43 first.  There is a greater chance that it is the one you need.

TSB 2.1.3.3
Verify that it works.  If it does great!  If it doesn't, create a post asking for help.

TSB 2.1.4:
Remove any conflicting drivers in /etc/modules.
/etc/modules contains modules that the kernel does not load automatically.  If a module is in here and is not blacklisted, it will load when you boot your computer.  We will see if bcm43xx or ndiswrapper are in there.
```
cat /etc/modules|grep -i -e bcm43xx -e ndiswrapper
```
If bcm43xx or ndiswrapper shows up, then we need to edit the file and add a # in front of it.  You can edit the file by using the following or use your favorite editor in sudo/root mode:
```
gksu <gedit/kate> /etc/modules
```
Use kate if you are using Kubuntu.  gedit should be on the others Ubuntu flavors.  You will need root/sudo permission because the file is located in /etc which is a protected directory.

TSB 2.1.5:
Blacklist conflicting drivers.
In order to make sure that the conflicting drivers to not come back when you reboot, add them to /etc/modprobe.d/blacklist.  This file prevents the loading of a module.  Check and see if they are already there:
```
cat /etc/modprobe.d/blacklist |grep -i -e bcm43xx -e ndiswrapper
```
Anything that shows up without a # in front of it means that they are already there.  For those that did not show up:
```
echo blacklist <module>|sudo tee -a /etc/modprobe.d/blacklist
```
Replace <module> with the module that did not show up in our previous check.  Do it for each module.

TSB 2.1.6:
Remove needed modules from blacklist.
There is a chance that the modules that we need are blacklisted.  Check it by doing:
```
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e b43legacy -e ssb
```
Only add -e b43legacy if that is your module and only add -e b43 if b43 is your module.  If you don't know, do ```
lsmod|grep -i -e b43
``` and see which is listed.
Edit the file and add a # in front of the module so that it is commented out (it won't load the module):
```
gksu <gedit/kate> /etc/modprobe.d/blacklist
```
Use kate if you are using Kubuntu.  Other Ubuntu flavors should be able to use gedit or find your favorite editor and run it with sudo/root privileges.

If for some reason, things still are not working, please create a post in forum and add your lspci -nn information.

---

### Post by luxscs on 2008-06-15
Ayuthia,

Great guide!
Unfortunately, I am at step TSB 2.1.3.3. and still can't connect.

My WiFi card is a Linksys WMP54GS, using the BroadCom BCM4306 (rev 03) chipset.
> 
05:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)


I've installed Cafuego's Component broadcom package, so I have all the firmware.

Output of "lshw -C network" gives:
>   
*-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:64:fd:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I initially had bcm43xx installed. After having removed it, the <  lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper > command gives:
> 
b43                   126760  0 
rfkill                 10128  2 b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb                    37252  1 b43


I'm still not able to connect though although I can scan and my signalquality is at 70%. 

Any ideas? I don't think my wife will stand for another weekend with a 10m network cable across two floors.

BTW, I've went down ndiswrapper route as well. No luck.

---

### Post by Ayuthia on 2008-06-15
> **luxscs said:**
> Ayuthia,

Great guide!
Unfortunately, I am at step TSB 2.1.3.3. and still can't connect.

My WiFi card is a Linksys WMP54GS, using the BroadCom BCM4306 (rev 03) chipset.


I've installed Cafuego's Component broadcom package, so I have all the firmware.

Output of "lshw -C network" gives:


I initially had bcm43xx installed. After having removed it, the <  lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper > command gives:


I'm still not able to connect though although I can scan and my signalquality is at 70%. 

I am not for sure if you have encryption set or not.  You can try turning it off it you have it on.  I have also seen that Network Manager does not play well with this card at times.  You could try installing wifi-radar or wicd.  My Dell laptop has this chipset and it seems pretty happy with KNetwork Manager.  I have not run into any problems with connecting with that one.  I am not for sure about how it will work on the Gnome desktop though.

You could also try changing channels on your router.  It could just be interference causing you to not be able to connect.

You can also try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwconfig wlan0 <essid>
sudo dhclient wlan0
```
Sometimes removing the module and reloading helps.  I have not been able to figure out what causes that yet.  I have not had to really use it much in 2.6.24-19 (you can check your kernel version by typing 'uname -r' (without quotes) at the terminal).

> Any ideas? I don't think my wife will stand for another weekend with a 10m network cable across two floors.:)
I am in a similar situation.  I have a 33m network cable going from my router to my desktop (I haven't bought a wireless card for the desktop yet).  She doesn't seem to be too thrilled about it.  The only thing going for me is that the computer is for the kids...

---

### Post by luxscs on 2008-06-15
Thanks for replying.

> **Ayuthia said:**
> I am not for sure if you have encryption set or not.  You can try turning it off it you have it on.  I have also seen that Network Manager does not play well with this card at times.  You could try installing wifi-radar or wicd.  My Dell laptop has this chipset and it seems pretty happy with KNetwork Manager.  I have not run into any problems with connecting with that one.  I am not for sure about how it will work on the Gnome desktop though.

Yes, I have encryption turned on, but my neighbors don't and I'm not able to connect to their wireless either. :o
I've installed wifi-radar. Wifi-radar connects to the network, but can't obtain an IP address. Same with the neighbor's unencrypted network ;) 

> **Ayuthia said:**
> 
You could also try changing channels on your router.  It could just be interference causing you to not be able to connect.

Haven't tried that yet, but as my wireless works fine in vista and for my laptop, I guess the issue can't be interference.

> **Ayuthia said:**
> 
You can also try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwconfig wlan0 <essid>
sudo dhclient wlan0
```
Sometimes removing the module and reloading helps.  I have not been able to figure out what causes that yet.  I have not had to really use it much in 2.6.24-19 (you can check your kernel version by typing 'uname -r' (without quotes) at the terminal).

I'm using the 2.6.24-18 kernel version.
Executing the above commands again seem to point to an issue obtaining an IP address as well.

Here's what I get on dhclient:
> 
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:64:fd:e3
Sending on   LPF/wlan0/00:12:17:64:fd:e3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I'm guessing the "unknown hardware address" is not a good thing. :???:
I'll google around a bit, but if you have any ideas I'll be happy to hear them.

The kids are having more luck than me. Their computer is sitting next to the gateway. :)

---

### Post by Ayuthia on 2008-06-15
> **luxscs said:**
> Thanks for replying.


Yes, I have encryption turned on, but my neighbors don't and I'm not able to connect to their wireless either. :o
I've installed wifi-radar. Wifi-radar connects to the network, but can't obtain an IP address. Same with the neighbor's unencrypted network ;) 


Haven't tried that yet, but as my wireless works fine in vista and for my laptop, I guess the issue can't be interference.


I'm using the 2.6.24-18 kernel version.
Executing the above commands again seem to point to an issue obtaining an IP address as well.

Here's what I get on dhclient:


I'm guessing the "unknown hardware address" is not a good thing. :???:
I'll google around a bit, but if you have any ideas I'll be happy to hear them.

The kids are having more luck than me. Their computer is sitting next to the gateway. :)

If you have no issues with using the proposed repository, it seems that some people are having better luck with 2.6.24-19 instead of 18.

As for Vista vs. Ubuntu wireless, you have to remember that the drivers are different in the two systems so it could be possible that you can connect with Vista, but still get interference in Ubuntu.  Not saying that this is the case, but it would be an easy test to eliminate.

---

### Post by luxscs on 2008-06-16
I tried both: no luck ](*,)

---

### Post by Primate101 on 2008-06-16
I'm in the exact same situation. I can "see" my networks (one encrypted and one not), but I cannot connect. I'm using the exact same software--b43 and the WMP54GS :(.

**Please** tell me if you find a solution!

---

### Post by Ayuthia on 2008-06-16
luxscs and Primate101, have you tried the NDISwrapper link:
[http://ge.ubuntuforums.com/showthread.php?t=779754&page=8](http://ge.ubuntuforums.com/showthread.php?t=779754&page=8)

See post #72 that has the link.  jamesmorad has the same card and chipset as you.

Primate101, you might just double-check your chipset and make sure that it is a 4306 rev 03 because I was able to find a card with the same name, but it was a 4318 instead.

Can the both of you post your lspci -nnm?  I just want to see the difference between your card and mine.  I have the 4306 rev 03 and it is working will with the b43 and NDISwrapper option.  However, my card is in my laptop instead of the Linksys so I am guessing that the subvendor is different.

---

### Post by Primate101 on 2008-06-16
Yeah, I have the 4306 card. Here's my lspci output:

01:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Thanks for all you're help!

---

### Post by Joker5bb on 2008-06-16
hi there guys i would like you to read my post here [http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0)
its a complete how-to on aircracking with b43 (Broadcom) 

:lolflag:

---

### Post by Primate101 on 2008-06-16
I couldn't get it to work with b43, but I managed to get ndiswrapper working again :).

First, install ndiswrapper from your LiveCD. Then, put in your WMP54GS CD, and navigate to /media/cdrom#/Drivers. Type ndiswrapper -i bcmwl5.inf at the terminal.

Finally, type the following:
```
sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe ndiswrapper
```

This makes the network manager work perfectly (it actually connects)!

Now, I'm a complete newb at Ubuntu, so could someone tell me how to do that automatically?

---

### Post by Ayuthia on 2008-06-16
> **Primate101 said:**
> I couldn't get it to work with b43, but I managed to get ndiswrapper working again :).

First, install ndiswrapper from your LiveCD. Then, put in your WMP54GS CD, and navigate to /media/cdrom#/Drivers. Type ndiswrapper -i bcmwl5.inf at the terminal.

Finally, type the following:
```
sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe ndiswrapper
```

This makes the network manager work perfectly (it actually connects)!

Now, I'm a complete newb at Ubuntu, so could someone tell me how to do that automatically?

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```This comes from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").  I am not for sure if you have a Broadcom wired card or not.  If you don't the b44 portion is not necessary.  If you are not sure, you can leave it in there.  It won't hurt anything because it will just be a module out there with nothing to do.

---

### Post by luxscs on 2008-06-18
> **Ayuthia said:**
> 
Can the both of you post your lspci -nnm?

Here's the part relative to my wireless card:
> 
05:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Unknown device [0015]" 

I've been down the ndiswrapper route before, with no luck. In light of Primate101's success I'll give it another go next weekend.

I need to take a closer look at Joker5bb's post as well.

---

### Post by Joker5bb on 2008-06-20
> **luxscs said:**
> Here's the part relative to my wireless card:


I've been down the ndiswrapper route before, with no luck. In light of Primate101's success I'll give it another go next weekend.

I need to take a closer look at Joker5bb's post as well.

sure guys even if you dont want to aircrack just update your kernel to 2.6.25.7 my how to is here 
[http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0)
 

b43 is better supported in that kernel!

then install like this

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

restart pc and your good to go no more codes are needed

:lolflag:

---

### Post by Joker5bb on 2008-06-20
you see the major problem is 

There is a known bug in b43 that is partially fixed in 2.6.25, and will
be fixed completely in 2.6.26. (It's already fixed in the
compat-wireless package.) B43 sets the transmit power and sensitivity of the card incorrectly.


:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by luxscs on 2008-06-21
Ndiswrapper doesn't work for me. Started from a clean ubentu install and followed the same procedure as Primate101. No luck. :-( I followed the more extensive procedure from alex_kent_18 ([http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)). Still no luck. :( 

Then I tried upgrading to 2.6.25. Other than based on Joker's advise, I read a post from somebody part of the b43 developer group, who confirmed that the 2.6.25 kernel was a lot more stable to use with these wireless drivers.
Unfortunately I don't seem to be able to get the new kernel working either. ](*,) 

After having gone through Joker's procedure and rebooting the machine with the 2.6.25.7 kernel, Ubuntu first seems to load fine, asking me for user and password. But after having run through the start-up procedure, at the point where the desktop is being loaded, I first get a black screen followed by a white one. And that's the end of it.

Anyway, I'm slowly but surely coming to the conclusion that configuring wireless is to large of a task for this ubuntu newbie. I think I'll spend some more energy on getting my DBV-S2 device working and sorting out MythTV, which was the initial reason for me to give linux a try!

---

### Post by Joker5bb on 2008-06-21
> **luxscs said:**
> Ndiswrapper doesn't work for me. Started from a clean ubentu install and followed the same procedure as Primate101. No luck. :-( I followed the more extensive procedure from alex_kent_18 ([http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)). Still no luck. :( 

Then I tried upgrading to 2.6.25. Other than based on Joker's advise, I read a post from somebody part of the b43 developer group, who confirmed that the 2.6.25 kernel was a lot more stable to use with these wireless drivers.
Unfortunately I don't seem to be able to get the new kernel working either. ](*,) 

After having gone through Joker's procedure and rebooting the machine with the 2.6.25.7 kernel, Ubuntu first seems to load fine, asking me for user and password. But after having run through the start-up procedure, at the point where the desktop is being loaded, I first get a black screen followed by a white one. And that's the end of it.

Anyway, I'm slowly but surely coming to the conclusion that configuring wireless is to large of a task for this ubuntu newbie. I think I'll spend some more energy on getting my DBV-S2 device working and sorting out MythTV, which was the initial reason for me to give linux a try!


hey man compile a new kernel is not easy task what you have now is a graphics card problem you brobably enabled the restrictive driver in the previous kernel.

---

### Post by NoDecaf on 2008-08-12
i am having a similar, but different issue. my wireless card is now on (the led was not lit until after i installed the b43 driver/firmware), however unlike some of you, i cannot see any wireless networks at all (and there are half a dozen i should be picking up).

system > administration > hardware drivers shows Broadcom B43 wireless driver checked (enabled) and "in use".

Running Hardy w/ 2.6.24-19 kernel

```
$ lspci -nn |grep Broadcom
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

```
$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:14:7c:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.101 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:cb:3a:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

```
$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
~$ sudo ls /lib/firmware/b43
a0g0bsinitvals4.fw  a0g0initvals5.fw     a0g1initvals13.fw    b0g0bsinitvals4.fw  b0g0initvals4.fw    lp0initvals13.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals5.fw  b0g0initvals5.fw    pcm4.fw           ucode13.fw
a0g0initvals4.fw    a0g1bsinitvals5.fw   b0g0bsinitvals13.fw  b0g0initvals13.fw   lp0bsinitvals13.fw  pcm5.fw           ucode4.fw

```


```
~$ sudo lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input

```

```
~$ cat /etc/modprobe.d/blacklist |grep -i -e bcm43xx -e ndiswrapper
blacklist bcm43xx

```

following all the troubleshooting steps everything seems to be in order, however neither network manager or wicd (having removed network manager) show any networks available.

the only thing i see that doesn't look normal is 

```
~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: [COLOR="Red"]unknown hardware address type 801[/COLOR]
wmaster0: [COLOR="Red"]unknown hardware address type 801[/COLOR]
Listening on LPF/wlan0/00:90:4b:cb:3a:b2
Sending on   LPF/wlan0/00:90:4b:cb:3a:b2
Sending on   Socket/fallback
```

this is driving me crazy.. any help would be greatly appreciated.

---

### Post by Ayuthia on 2008-08-12
> **NoDecaf said:**
> i am having a similar, but different issue. my wireless card is now on (the led was not lit until after i installed the b43 driver/firmware), however unlike some of you, i cannot see any wireless networks at all (and there are half a dozen i should be picking up).

system > administration > hardware drivers shows Broadcom B43 wireless driver checked (enabled) and "in use".

Running Hardy w/ 2.6.24-19 kernel

```
$ lspci -nn |grep Broadcom
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

```
$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:14:7c:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.101 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:cb:3a:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

```
~$ sudo ls /lib/firmware/b43
a0g0bsinitvals4.fw  a0g0initvals5.fw     a0g1initvals13.fw    b0g0bsinitvals4.fw  b0g0initvals4.fw    lp0initvals13.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals5.fw  b0g0initvals5.fw    pcm4.fw           ucode13.fw
a0g0initvals4.fw    a0g1bsinitvals5.fw   b0g0bsinitvals13.fw  b0g0initvals13.fw   lp0bsinitvals13.fw  pcm5.fw           ucode4.fw

```


```
~$ sudo lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input

```

```
~$ cat /etc/modprobe.d/blacklist |grep -i -e bcm43xx -e ndiswrapper
blacklist bcm43xx

```

following all the troubleshooting steps everything seems to be in order, however neither network manager or wicd (having removed network manager) show any networks available.

the only thing i see that doesn't look normal is 

```
~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: [COLOR="Red"]unknown hardware address type 801[/COLOR]
wmaster0: [COLOR="Red"]unknown hardware address type 801[/COLOR]
Listening on LPF/wlan0/00:90:4b:cb:3a:b2
Sending on   LPF/wlan0/00:90:4b:cb:3a:b2
Sending on   Socket/fallback
```

this is driving me crazy.. any help would be greatly appreciated.

You might want to report your card to this link:
[http://ubuntuforums.org/showthread.php?t=885173](http://ubuntuforums.org/showthread.php?t=885173)
He is one of the people who works on the b43 driver.  He is looking for people with your card because he has a fix that might work for it.

---

### Post by NoDecaf on 2008-08-12
> **Ayuthia said:**
> You might want to report your card to this link:
[http://ubuntuforums.org/showthread.php?t=885173](http://ubuntuforums.org/showthread.php?t=885173)
He is one of the people who works on the b43 driver.  He is looking for people with your card because he has a fix that might work for it.

ok, thanks for the tip. i will do that.

---

### Post by NoDecaf on 2008-08-13
installed WinXP. rebooted to Linux. Card now sees and connects to wireless networks with no other changes.

---

### Post by saffagirl on 2008-08-14
I've asked on another post ,but this looks like the most relative to one of my probs. I've got as far as sudo modprobe; but am not getting any thing. in the config i see broadcast yes driver=r189 driverversion-2.2.lk latency=255; however at configuration there is no driver listed. latency =0. I have at present a dualboot situation, but have no wired or wireless connection in ubuntu complete newbie....

Broadcom is dell wireless n1505 card; ie 4328 rev 03 ; wired- realtek rtl8111 8168b. 

thanks for a good guide.

---

### Post by Ayuthia on 2008-08-14
> **saffagirl said:**
> I've asked on another post ,but this looks like the most relative to one of my probs. I've got as far as sudo modprobe; but am not getting any thing. in the config i see broadcast yes driver=r189 driverversion-2.2.lk latency=255; however at configuration there is no driver listed. latency =0. I have at present a dualboot situation, but have no wired or wireless connection in ubuntu complete newbie....

Broadcom is dell wireless n1505 card; ie 4328 rev 03 ; wired- realtek rtl8111 8168b. 

thanks for a good guide.
Since you have a 4328 card, you will need to use ndiswrapper.  The 4328 card is a wireless-n device and they are currently not supported by the b43 driver yet.  From your other posts, you have mentioned that you have already installed it.  If that is the case, please try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Start at step 2d.  This is the suggested driver for your card.  If you run into any problems, just come back and let us know where you are stuck.

---

### Post by saffagirl on 2008-08-14
hi thanks for your help so far I feel like I'm making progress,

I'm stuck on 3. I'm getting warnings in lines 41-45 in modprobe.d/blacklist (saying  ignorning bad line starting with sudo and mkdir and fatal module ndiswrapper not found . earlier I edited it I think,but i'm not sure how to correct this. Other posts were saying uninstall ndiswrapper, which i did and reinstalled, but obviously have remnants but am unsure how to get into modprobe again.  sorry, like i said a newbie, which is not so good. Anyway, the other problem is that i'm being told interfaces.org isn't a directory

sorry for the longwindedness, i can't copy as am on a different machine...

---

### Post by Ayuthia on 2008-08-14
> **saffagirl said:**
> hi thanks for your help so far I feel like I'm making progress,

I'm stuck on 3. I'm getting warnings in lines 41-45 in modprobe.d/blacklist (saying  ignorning bad line starting with sudo and mkdir and fatal module ndiswrapper not found . earlier I edited it I think,but i'm not sure how to correct this. Other posts were saying uninstall ndiswrapper, which i did and reinstalled, but obviously have remnants but am unsure how to get into modprobe again.  sorry, like i said a newbie, which is not so good. Anyway, the other problem is that i'm being told interfaces.org isn't a directory

sorry for the longwindedness, i can't copy as am on a different machine...
Ok.  What we could do for now is try to clean up those lines in /etc/modprobe.d/blacklist.  Everything in that file should start with blacklist or else it should have a # (the symbol used to let the system know that everything beyond that symbol is a comment) in front of it.  For now, you can edit the file:
```
gksu gedit /etc/modprobe.d/blacklist
```
and you can place a # in front of lines 41-45.

Since you don't have a working connection yet, check and see if ndiswrapper is properly installed:
```
ndiswrapper -v
```
You should get a result like this:
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.26-ARCH/kernel/drivers/net/wireless/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.26-ARCH SMP preempt mod_unload

```It won't be exactly like this because I am currently in Arch.
You will need to make sure that the utils version 1.9 is there and that the version is 1.50 or greater.

The next thing that you need to see is if the driver is installed ok:
```
ndiswrapper -l
```
You should see something like this:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)
```The thing that you are looking for is that the driver is installed and that the device is present.  Your device number is going to be different since your card is a 4328.  You might see an alternate driver there, but that is ok.

If this is all ok, we can then try loading the ndiswrapper module again:
```
sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```
If a message comes back after you do 'sudo modprobe ndiswrapper', please type:
```
dmesg|grep ndiswrapper
```and see if any error messages come up.  If it does, you most likely have a bad driver and will need to look for another possible driver.  If this happens, can you check the following for me:
```
lspci -nnmvkd 14e4:*
```
It will report something like this:
```
Device: 03:00.0
Class:  Network controller [0280]
Vendor: Broadcom Corporation [14e4]
Device: BCM4311 802.11b/g WLAN [4311]
SVendor:        Hewlett-Packard Company [103c]
SDevice:        BCM4311 802.11b/g Wireless LAN Controller [1363]
Rev:    01
Driver: ndiswrapper
Module: ssb
```
What I would like you to report back is the numbers in the brackets for the Vendor, Device, SVendor, and SDevice.  In my example what I am asking for is: 14e4 4311 103c 1363.  This may help us identfy a driver that has supports that vendor and subvendor.

---

### Post by saffagirl on 2008-08-18
HI thanks for all  your help so far...I really appreciate it. Sorry for the delay, I was away during the weekdn.
OK,
I've modified the modprobe blacklist but now am getting this msg with ndiswrapper, so have come a bit unstuck...

Basically says not installed, may need to download from the website. I've re-installed it from the repository..so the question is do i run sudo ndiswrapper -i,  but what driver do i use?

As for version, haven't managed to test this. i have gone onto the dell website where it has a 89mb download for my chipset..A17_R174291.exe (which when unzipped comes as wirless n 1370. the driver version in vista is 4.170.25.17 ...I don't know if this helps.

---

### Post by Ayuthia on 2008-08-18
> **saffagirl said:**
> HI thanks for all  your help so far...I really appreciate it. Sorry for the delay, I was away during the weekdn.
OK,
I've modified the modprobe blacklist but now am getting this msg with ndiswrapper, so have come a bit unstuck...

Basically says not installed, may need to download from the website. I've re-installed it from the repository..so the question is do i run sudo ndiswrapper -i,  but what driver do i use?

As for version, haven't managed to test this. i have gone onto the dell website where it has a 89mb download for my chipset..A17_R174291.exe (which when unzipped comes as wirless n 1370. the driver version in vista is 4.170.25.17 ...I don't know if this helps.

You will want to try the driver in the no-fluff site first:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Look for step 2d and download that file.  It is a smaller file so hopefully that will work.

The one that you mentioned is a vista driver.  The drivers for Vista are not supported by NDISwrapper as of yet so it will most likely not work.

---

### Post by saffagirl on 2008-09-01
The one I mentioned was vista, but I have found an xp driver on the dell website.[http://support.euro.dell.com/support/downloads/download.aspx?c=uk&cs=ukbsdt1&l=en&s=bsd&releaseid=R174291&SystemID=VOS_N_1310&servicetag=&os=WW1&osl=uk&deviceid=14147&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819]("http://support.euro.dell.com/support/downloads/download.aspx?c=uk&cs=ukbsdt1&l=en&s=bsd&releaseid=R174291&SystemID=VOS_N_1310&servicetag=&os=WW1&osl=uk&deviceid=14147&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819")

However, I've looked at feisty fluff solution. Seems like ndiswrapper doesn't like me. I now get fatal error with ndiswrapper (even though I have repeatedly reinstalled it). so can get no further than step 1. I feel like I've moved back a few steps.

So now I'm sitting with ndiswrapper, i've downloaded a  new copy as well but am learning how to install it without the packages 9as said a noob).....thanks in advance

---

### Post by Ayuthia on 2008-09-02
> **saffagirl said:**
> 
However, I've looked at feisty fluff solution. Seems like ndiswrapper doesn't like me. I now get fatal error with ndiswrapper (even though I have repeatedly reinstalled it). so can get no further than step 1. I feel like I've moved back a few steps.

So now I'm sitting with ndiswrapper, i've downloaded a  new copy as well but am learning how to install it without the packages 9as said a noob).....thanks in advance

What part are you doing in step 1 that is creating the fatal error?

If you are trying to install ndiswrapper from scratch (not from the repositories), you will need to have build-essential (should be on the install CD and if you have a wired connection you can go into Synaptic and install it).    From there the compiling should be able to be done based on the instructions for compiling ndiswrapper.  If you do get stuck, just let us know where and we can try to help.

---

### Post by saffagirl on 2008-09-03
> **Ayuthia said:**
> What part are you doing in step 1 that is creating the fatal error?

If you are trying to install ndiswrapper from scratch (not from the repositories), you will need to have build-essential (should be on the install CD and if you have a wired connection you can go into Synaptic and install it).    From there the compiling should be able to be done based on the instructions for compiling ndiswrapper.  If you do get stuck, just let us know where and we can try to help.


HI Ayuthia, thanks so much for being so patient...I really appreciate it.

Ok ndiswrapper installed from cd -this all is cool now, but it looks like modprobe is giving me hassles....(also I noticed my driver installed, but there is no version listed is this normal)?

This is where the prob is.
joytjie@joytjie-laptop:~$ sudo ndiswrapper -i 

bcmwl5.inf
[sudo] password for joytjie: 
driver bcmwl5 

is already installed

joytjie@joytjie-laptop:~$ sudo depmod -a

joytjie@joytjie-laptop:~$ ndiswrapper -l
bcmwl5 : 

driver installed
	device (14E4:4328) present

joytjie@joytjie-laptop:~$ depmod -a

[B]FATAL: Could not open /lib/modules/2.6.24-16-

generic/modules.dep.temp for writing: Permission 

denied[/B]
joytjie@joytjie-laptop:~$ 

From there I cannot go on.

Is there anymore info needed? I didn't redo blacklist cos I figured that was messy. The driver was already installed previously...but how do I see which one?

Thanks , again , in advance.

---

### Post by Ayuthia on 2008-09-03
> **saffagirl said:**
> H
This is where the prob is.
joytjie@joytjie-laptop:~$ sudo ndiswrapper -i 

bcmwl5.inf
[sudo] password for joytjie: 
driver bcmwl5 

is already installed

This means that you already have a driver there.  You should do the following:
```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```
It will remove the old driver and replace it with the new one.

> joytjie@joytjie-laptop:~$ sudo depmod -a

joytjie@joytjie-laptop:~$ ndiswrapper -l
bcmwl5 : 

driver installed
	device (14E4:4328) present

joytjie@joytjie-laptop:~$ depmod -a

[B]FATAL: Could not open /lib/modules/2.6.24-16-

generic/modules.dep.temp for writing: Permission 

denied[/B]

You left out the sudo in the depmod -a so you received the Permission denied.  Since you already did the depmod -a the first time, you don't need to do it again.
> Is there anymore info needed? I didn't redo blacklist cos I figured that was messy. The driver was already installed previously...but how do I see which one?

Thanks , again , in advance.

You should not have to do the blacklisting again because it is already there.  As for the driver that was installed previously, I covered that in the first part of this post.  We should just remove the previous one and try the new one.

---

### Post by saffagirl on 2008-09-04
Hi Ayuthia,
Ok, I've tried your instructions and I have a prob (sorry)

This is what I got...
i uninstalled the driver then tried to reinstall it.

sudo ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Now I know the driver is on my home folder but obviously not in sbin  (and nor is there an ndiswrapper folder that i could view graphically, I don't think) so the question is how do i move it to this folder? Hopefully I can then get the ball rolling again...

Thanks again, really appreciate this.

---

### Post by Ayuthia on 2008-09-04
> **saffagirl said:**
> Hi Ayuthia,
Ok, I've tried your instructions and I have a prob (sorry)

This is what I got...
i uninstalled the driver then tried to reinstall it.

sudo ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Now I know the driver is on my home folder but obviously not in sbin  (and nor is there an ndiswrapper folder that i could view graphically, I don't think) so the question is how do i move it to this folder? Hopefully I can then get the ball rolling again...

Thanks again, really appreciate this.
What this is telling you is that you are currently not in the directory where the bcmwl5.inf file is located.  All you need to do is change to where the bcmwl5.inf is located and run 'sudo ndiswrapper -i bcmwl5.inf' (without the quotes) again.

---

### Post by saffagirl on 2008-09-05
Ok I've moved the file into sbin (should I have installed it into ndiswrapper?). However, this is the latest error- it goes back to modprobe again. NDISWRAPPER IS DEFINITELY INSTALLED...

jlaptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper
FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.

Used ndisgtk at this point- tried installing from sbin location and that wouldn't work, but then used the one in my home folder which is now installed and I still couldn't get it to work
...this is what happened after that



(network-admin:7208): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7208): CRITICAL **: Unable to lookup session information for process '7208
'
joytjie@joytjie-laptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper

FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.


(network-admin:7516): Gtk-WARNING **: Unknown property: GtkComboBox.items


** 
(network-admin:7516): 
CRITICAL **: Unable to lookup session information for process '7516'
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 354, in <module>
    NdisGTK()
 
 File "/usr/sbin/ndisgtk", line 127, in __init__
    gtk.main()
KeyboardInterrupt

Thanks again- I'm hoping this will work this time, am feeling completely frustrated, but really appreciate all your effort thusfar.

---

### Post by saffagirl on 2008-09-05
Ok I've moved the file into sbin (should I have installed it into ndiswrapper?). However, this is the latest error- it goes back to modprobe again. NDISWRAPPER IS DEFINITELY INSTALLED...

jlaptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper
FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.

Used ndisgtk at this point- tried installing from sbin location and that wouldn't work, but then used the one in my home folder which is now installed and I still couldn't get it to work
...this is what happened after that



(network-admin:7208) : Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7208) : CRITICAL **: Unable to lookup session information for process '7208
'
joytjie@joytjie-laptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper

FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.


(network-admin:7516) : Gtk-WARNING **: Unknown property: GtkComboBox.items


** 
(network-admin:7516) : 
CRITICAL **: Unable to lookup session information for process '7516'
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 354, in <module>
    NdisGTK()
 
 File "/usr/sbin/ndisgtk", line 127, in __init__
    gtk.main()
KeyboardInterrupt

Thanks again- I'm hoping this will work this time, am feeling completely frustrated, but really appreciate all your effort thusfar.

---

### Post by Ayuthia on 2008-09-05
> **saffagirl said:**
> Ok I've moved the file into sbin (should I have installed it into ndiswrapper?). However, this is the latest error- it goes back to modprobe again. NDISWRAPPER IS DEFINITELY INSTALLED...

jlaptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper
FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.

Used ndisgtk at this point- tried installing from sbin location and that wouldn't work, but then used the one in my home folder which is now installed and I still couldn't get it to work
...this is what happened after that



(network-admin:7208): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7208): CRITICAL **: Unable to lookup session information for process '7208
'
joytjie@joytjie-laptop:~$ sudo ndisgtk
module configuration information is stored in /etc/modprobe.d/ndiswrapper

FATAL: Module ndiswrapper not found.

FATAL: Module ndiswrapper not found.


(network-admin:7516): Gtk-WARNING **: Unknown property: GtkComboBox.items


** 
(network-admin:7516): 
CRITICAL **: Unable to lookup session information for process '7516'
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 354, in <module>
    NdisGTK()
 
 File "/usr/sbin/ndisgtk", line 127, in __init__
    gtk.main()
KeyboardInterrupt

Thanks again- I'm hoping this will work this time, am feeling completely frustrated, but really appreciate all your effort thusfar.

I think that I have confused you.  The bcmwl5.inf file does not need to be in /usr/sbin.  The file should be where it was originally.  The /usr/sbin error message that you saw was from ndiswrapper.  The ndiswrapper application is located in /usr/sbin.  The message that you received was an error message from ndiswrapper's source code.

So if your bcmwl5.inf file was located at /home/joytjie/Desktop/bcmwl5, you should do the following:
```
sudo ndiswrapper -e bcmwl5
cd /home/joytjie/Desktop/bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```

Unfortunately, I have never used ndisgtk before so I am not for sure about how to run that application.  I think that the application is run from System->Administration (from the Panel) but I could be wrong.

Can you post the results of ndiswrapper -v:
```
cd /home
ndiswrapper -v
```

---

### Post by saffagirl on 2008-09-05
Ok, I now see what you meant, sorry i thought you meant I need to move it. anyway, you meant I need to point it to a another area.. like i said I'm a newbie-  I have an idea in dos and am a wiz at windows, but am going right back  to basics here.But am learning a lot:)

I'll give this a go and get back to you asap.

As for ndisgtk- I just went sudo ndisgtk and voila it opened...

---

### Post by saffagirl on 2008-09-05
Here's the latest - I can see in sbin both ndiswrapper and ndiswrapper-1.9 - is this normal? Might this be part of the problem?

joytjie@joytjie-laptop:~$ sudo ndiswrapper -e bcmw15
[sudo] password for joytjie: 
couldn't delete /etc/ndiswrapper/bcmw15: No such file or directory
joytjie@joytjie-laptop:~$ cd /home/joytjie/bcm43xx/
joytjie@joytjie-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
jjoytjie@joytjie-laptop:~$ ndiswrapper -v

modinfo: could not find module ndiswrapper

module version is too old!

utils version: '1.9', utils version needed by module: '0'

module details:

modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

joytjie@joytjie-laptop:~$

---

### Post by Ayuthia on 2008-09-05
> **saffagirl said:**
> Here's the latest - I can see in sbin both ndiswrapper and ndiswrapper-1.9 - is this normal? Might this be part of the problem?

This is normal.
> joytjie@joytjie-laptop:~$ sudo ndiswrapper -e bcmw15
[sudo] password for joytjie: 
couldn't delete /etc/ndiswrapper/bcmw15: No such file or directory
It looks like you used a 1 instead of a lower case L in bcmwl5 so the driver was not removed.
> jjoytjie@joytjie-laptop:~$ ndiswrapper -v

modinfo: could not find module ndiswrapper

module version is too old!

utils version: '1.9', utils version needed by module: '0'

module details:

modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

joytjie@joytjie-laptop:~$Can you try the following:
```
cd /home
ndiswrapper -v
```
The difference is that I am moving you up a directory where I know that there are no ndiswrapper files.  It tends to confuse the ndiswrapper -v command.

---

### Post by saffagirl on 2008-09-05
Gotcha :) Moved up the directory.

modinfo: could not find module ndiswrapper


You may need to upgrade driver and/or utils to latest versions available at

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)


Like I said, i've reinstalled it from the distro at least 2x. I can definitely see it in sbin, so why is there no module? I've got the tar waiting but am unsure how to install from a tar to a specific folder.

---

### Post by Ayuthia on 2008-09-05
Well, we can try and compile the most up to date version.  Before we do that, do you have a working internet connection in Ubuntu?  Can you also post the results of the following:
```
aptitude search build-essential
aptitude search ndis
```
We will need build-essential in order to compile ndiswrapper.

---

### Post by saffagirl on 2008-09-05
still no working  net connection on ubuntu, I thought the wrealtek card would be more of a challenge (I'm hoping I'm wrong) 

Here's what you asked needed :
joytjie@joytjie-laptop:~$ aptitude search build-essential
p   build-essential                 - informational list of build-essential pack

joytjie@joytjie-laptop:~$ aptitude search ndis
i  ndisgtk                                                                - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)       

i   ndiswrapper-common                                                     - Common scripts required to use the utilities for ndiswrapper                    

v   ndiswrapper-modules-1.9                                                -                                                                                 

i   ndiswrapper-utils-1.9                                                  - Userspace utilities for the ndiswrapper Linux kernel module

---

### Post by Ayuthia on 2008-09-05
> **saffagirl said:**
> still no working  net connection on ubuntu, I thought the wrealtek card would be more of a challenge (I'm hoping I'm wrong) 

Here's what you asked needed :
joytjie@joytjie-laptop:~$ aptitude search build-essential
p   build-essential                 - informational list of build-essential pack

joytjie@joytjie-laptop:~$ aptitude search ndis
i  ndisgtk                                                                - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)       

i   ndiswrapper-common                                                     - Common scripts required to use the utilities for ndiswrapper                    

v   ndiswrapper-modules-1.9                                                -                                                                                 

i   ndiswrapper-utils-1.9                                                  - Userspace utilities for the ndiswrapper Linux kernel module

It looks like build-essential is from the install CD.  You will need to have this.  Go ahead and install it through Synaptic or by doing the following:
```
sudo aptitude install build-essential
```
Either method should work.  The next step will be to uninstall ndiswrapper:
```
sudo aptitude remove ndiswrapper-utils-1.9 ndiswrapper-common
```
From there, we will need to unpack the tarball for ndiswrapper.  Can you post the location of where the ndiswrapper source code file is located along with the version that you downloaded?

---

### Post by saffagirl on 2008-09-05
I'll do this all in the am, but the version downloaded is 1.53 from ndiswrapper.sourceforge.net ...thanks again :)

---

### Post by saffagirl on 2008-09-06
Installation done and ndiswrapper and ndisgtk removed

joytjie@joytjie-laptop:~$ sudo aptitude remove ndiswrapper-utils-1.9 ndiswrapper-common

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:

  ndisgtk 

The following packages will be REMOVED:

  ndiswrapper-common ndiswrapper-utils-1.9 

0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 213kB will be freed.

The following packages have unmet dependencies:

  ndisgtk: Depends: ndiswrapper-utils-1.9 but it is not installable

Resolving dependencies...

The following actions will resolve these dependencies:



Remove the following packages:

ndisgtk



Score is 119



Accept this solution? [Y/n/q/?] y

The following packages will be automatically REMOVED:

  ndisgtk 

The following packages will be REMOVED:

  ndisgtk ndiswrapper-common ndiswrapper-utils-1.9 

0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 565kB will be freed.
Do you want to continue? [Y/n/?] y

Writing extended state information... Done
(Reading database ... 97201 files and directories currently installed.)

Removing ndisgtk ...
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...

dpkg - warning: while removing ndiswrapper-common, directory `/etc/ndiswrapper' not empty so not removed.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
joytjie@joytjie-laptop:~$ 


The one thing that concerned me etc/ndiswrapper wasn't removed...anyway, that's the start:)

---

### Post by Ayuthia on 2008-09-06
> **saffagirl said:**
> 
The one thing that concerned me etc/ndiswrapper wasn't removed...anyway, that's the start:)
This message was expected but easily fixed.  Here are the commands to remove the two remaining files/folders:
**Step 1**
```
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

**Step 2**
The next step is to install build-essential:
```
sudo aptitude install build-essential
```
You can either do the command above or go into Synaptic and install it.

**Step 3**
The next step is to unpack the ndiswrapper tarball.  You will need to go into the directory where you have the 1.53 tar.gz file.  I am going to assume that it is the home directory:
```
cd
tar -xvvf ndiswrapper-1.53.tar.gz
```
The command tar will extract the .tar.gz file.  You should see some information scroll through as it unpacks.  This is because of the vv in the -xvvf command.  It just says to spit out a lot of information about what you are doing.

**Step 4**
The next set of commands will attempt to build ndiswrapper:
```
cd ndiswrapper-1.53
sudo make uninstall
sudo make clean
make
```
The make uninstall will go through and make sure that there is nothing out there for ndiswrapper.  The next one will clean out the folder of any lingering compiled code so that it can start fresh.  The make command will then compile the source code.  If there are no errors, we can then install.  The error message should show up at the end.

**Step 5**
```
sudo make install
```
This command does the actual install of ndiswrapper.  If no errors occur, then we can start the loading of the Windows driver.  That is the sudo ndiswrapper -i bcmwl5.inf command.

---

### Post by saffagirl on 2008-09-06
Hey Ayuthia - I've done this but think I might have been overzealous before going to make clean,(is this a problem?) i literally did sudo make uninstall about 50 x plus. Anyway, no errors apart from line 219 and the following.

OTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.

make[1]: Leaving directory `/home/joytjie/ndiswrapper-1.53/utils'

mkdir -p -m 0755 /usr/share/man/man8

install -m 644 ndiswrapper.8 /usr/share/man/man8
 
I just realised the 219 thing again. I'll change  directory and post shortly.

install -m 644 loadndisdriver.8 /usr/share/man/man8

joytjie@joytjie-laptop:~/ndiswrapper-1.53$ 

joytjie@joytjie-laptop:~/ndiswrapper-1.53$ sudo ndiswrapper -i bcmwl5.inf

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

joytjie@joytjie-laptop:~/ndiswrapper-1.53$

Your patience has been astounding, thanks :)

---

### Post by saffagirl on 2008-09-06
I've finally managed to get the driver installed ,at last.:guitar:. thank you so much.... bad news I've  still got no wifi.:confused: here's the details attached

---

### Post by Ayuthia on 2008-09-06
> **saffagirl said:**
> I've finally managed to get the driver installed ,at last.:guitar:. thank you so much.... bad news I've  still got no wifi.:confused: here's the details attached

Well, it looks like all went well with the install.  The make clean part is optional.  If you just unpacked the tarball and compiled, the make clean really is not necessary.

The next part would be to try and find a driver that works.  Your card is relatively new so finding a working driver might be difficult.  If I recall correctly, we used the driver recommended from the no-fluff site this time.  Is that correct?

I do have to say that this is the first time that I noticed that you had the 4328 card.  Because of this we do have another option.  You can go and download this driver:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

What you will want to do is download the Broadcom driver.  Once you do this, you will want to create a new folder in your home directory to build this driver:
```
cd 
mkdir wl_hybrid
```
copy the tar.gz file that you downloaded into wl_hybrid.  From there, do the following:
```

32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz
64 bit:                             tar -xzf <path>/hybrid-portsrc-x86_64.tar.gz

```Do whichever one applies to you.  I don't recall whether you have 32-bit or 64-bit.  You will then need to compile the code:
```

sudo make -C /lib/modules/`uname -r`/build M=`pwd` clean
sudo make -C /lib/modules/`uname -r`/build M=`pwd`

```The quotes in there are back quotes instead of the single quote.  It is used to execute the command in the quotes and replace the command with the result of the command.  So in this case, it is going to use the library from /lib/modules/2.6.24-19-generic (if that is the kernel version that you are using) and build the source in the current directory.

Once this is done, you will have a wl.ko file in that directory.  If you do, do the following:
```
sudo mkdir /lib/modules/`uname -r`/wl_hybrid
sudo cp wl.ko /lib/modules/`uname -r`/wl_hybrid
sudo depmod -a
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe wl
```
If this works, we can then make this driver be loaded permenantly.  There is a good chance that this driver will work.  It is a new driver that Broadcom made for Linux.

The only thing that I will say is that you will need to make sure that you are using the back quote instead of the single quote.  If you want to test it out before using it, try the following:
```
echo `uname -r`
```
and it should return something like 2.6.24-19-generic.  If it returns uname -r, then you used the single quote.

Sorry for changing direction on you.  I just have a feeling that this driver will work for you.

---

### Post by saffagirl on 2008-09-06
> **Ayuthia said:**
> 

The next part would be to try and find a driver that works.  Your card is relatively new so finding a working driver might be difficult.  If I recall correctly, we used the driver recommended from the no-fluff site this time.  Is that correct?  We


We did use the one suggested on the feisty fluff *bcmwl5 . I'm willing to give anything a shot at this point there's nothing to lose. I've got the xp drivers from the dell website as well (it appears to bcmwl6.inf) 

I'll give this a shot and get back to you.

One question, presumably we had the wrong driver installed do I need to do anything to clean up?

---

### Post by saffagirl on 2008-09-06
Ok my first snag I'm using 2.16 not 2.19. I'm being told permissions are being denied?Is this to do with the repositories I'm using?

sudo make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'

find: /home/joytjie/.gvfs: Permission denied

make: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'

joytjie@joytjie-laptop:~$

---

### Post by Ayuthia on 2008-09-06
> **saffagirl said:**
> Ok my first snag I'm using 2.16 not 2.19. I'm being told permissions are being denied?Is this to do with the repositories I'm using?

sudo make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'

find: /home/joytjie/.gvfs: Permission denied

make: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'

joytjie@joytjie-laptop:~$

This should be ok.  This is the clean up script.  The part where it received the Permission denied, it was doing a search but I am sure that it does not need anything in there.

You can go ahead to the next step.

As for the other driver that you had, it is a bcmwl6 driver which is not currently supported by ndiswrapper yet.

We don't need to do any clean up in ndiswrapper.  If this method works, all we will do is blacklist the ndiswrapper driver and we will be good to go.

---

### Post by saffagirl on 2008-09-07
Great news your 2nd solution worked :) I've msged you from my ubuntu partition! After reboot  I'm constantly being asked for my wep key for my network, although it shows as connected (from there I can't access the net)

Thanks so much for your patience and kind help....
I've downloaded .19 and the net does not work on it , but .16 almost does ( I thought it did, but obviously not holding wep hex key)

---

### Post by Ayuthia on 2008-09-07
> **saffagirl said:**
> Great news your 2nd solution worked :) I've msged you from my ubuntu partition! After reboot  I'm constantly being asked for my wep key for my network, although it shows as connected (from there I can't access the net)

Thanks so much for your patience and kind help....
I've downloaded .19 and the net does not work on it , but .16 almost does ( I thought it did, but obviously not holding wep hex key)

That is good news!  Unfortunately, you will have to do those steps again to get it to work on 2.6.24-19 because you have compiled a kernel module from source.  The one you built the first time was for 2.6.24-16.  You should only have to do this for 2.6.24-19 and hopefully after that, you will no longer need to do it anymore.  The wl driver is currently being tested in the hardy-proposed repositories so if all goes well, it will come out with the next kernel release.

---

### Post by saffagirl on 2008-09-07
Awesome. I'm now msging you from .19 kernel; hopefully it'll stay up. The wireless is working but I had a fatal NDISWRAPPER not found error. But like I said it's working :)

Now on to wired broadband, sound, mic, and webcam through trawling etc. 

THANKS so much for all your help- this is why I definitely wanted to get into UBUNTU -truly it does mean togetherness/community (I'm South African)and it comes through:) Appreciate all the time and effort.

---

### Post by Ayuthia on 2008-09-07
> **saffagirl said:**
> Awesome. I'm now msging you from .19 kernel; hopefully it'll stay up. The wireless is working but I had a fatal NDISWRAPPER not found error. But like I said it's working :)

Now on to wired broadband, sound, mic, and webcam through trawling etc. 

THANKS so much for all your help- this is why I definitely wanted to get into UBUNTU -truly it does mean togetherness/community (I'm South African)and it comes through:) Appreciate all the time and effort.

If you want to get rid of the ndiswrapper message, you can do the following:
```
echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist
```
and that should do it.  

I am glad to see that you are able to get it working.  Thanks for hanging in there!

---

### Post by saffagirl on 2008-09-09
Hi Ayuthia-  my wifi seems to gr8 except my wep hex key times out and no matter how many times I login again I can't login without restart where no wep key is needed, this does appear to be after period of inactivity at random or  hibernate. Do you have any idea what could cause this? Or why the wep key isn't holding?

Sorry to bug you, just trying to iron any problems out...otherwise loving ubuntu, am starting to be a convert :) I'm halfway ironing out probs- just need 2 org my other modem , webcam and dvd :) (But at least feel like i'm learning and loving the feel)

---

### Post by Ayuthia on 2008-09-09
> **saffagirl said:**
> Hi Ayuthia-  my wifi seems to gr8 except my wep hex key times out and no matter how many times I login again I can't login without restart where no wep key is needed, this does appear to be after period of inactivity at random or  hibernate. Do you have any idea what could cause this? Or why the wep key isn't holding?

Sorry to bug you, just trying to iron any problems out...otherwise loving ubuntu, am starting to be a convert :) I'm halfway ironing out probs- just need 2 org my other modem , webcam and dvd :) (But at least feel like i'm learning and loving the feel)

I am not for sure about why the WEP key is timing out.  The only thing that I can think that would cause this is NetworkManager.  Unfortunately, I don't have much experience in this.  I have not encrypted my wireless as of yet because there are no homes in my area that can get my wireless signal.  You could try using something like wicd.  Sorry I can't be too much help in this area.  I plan to work on this soon, but have not had a chance yet.

---

### Post by saffagirl on 2008-09-12
Hey Ayuthia,

thanks so much for getting back to me. No stress,At least the wireless doesn't time out if I make sure I login when I first boot up.

Thanks again.

---

### Post by Dragonbite on 2009-01-28
Argh..
I've done everything listed in the first, detailed post (after hopping from thread to thread here) and still no go.

I have a Broadcom 4309 a/b/g mini-pci card.

From all that I can see,
the b43 module/drivers are installed
the b43 legacy module/drivers are installed (just tried it, it hasn't been working before that his is the last thing I've tried)
the ssb module/drivers are installed

I've tried it with an older kernel to see if that was it.

Nothing is working! And this is a replacement card! The first card just stopped working on me and I thought maybe the card died. The second one is not showing anything different (both Broadcom).

It has moved it from wlan0 (which is what it was when it was working) to wlan1 showing wlan0 to "NO DEVICE FOUND"

I'm getting desperate!

---

### Post by kevdog on 2009-01-28
Do you really need to blacklist ndiswrapper since its a custom kernel module?  Why not simply remove reference to it from the /etc/modules file, and it will not by default load on startup?  I guess if someone wanted to add this after bootup, the blacklist file would prevent this, however what's the point in this?

---

### Post by Ayuthia on 2009-01-28
> **kevdog said:**
> Do you really need to blacklist ndiswrapper since its a custom kernel module?  Why not simply remove reference to it from the /etc/modules file, and it will not by default load on startup?  I guess if someone wanted to add this after bootup, the blacklist file would prevent this, however what's the point in this?
It has been a while, but there were times where ndiswrapper loaded up even though it was not in /etc/modules.  I have not seen that happen recently so removing it from /etc/modules might just be enough.  The wl module sometimes loads without the need of adding it to /etc/modules.  I will have to test that out further sometime.

---

### Post by gabetz08 on 2009-06-16
Ok so i have a problem. I have a hp zd7000a laptop with a broadcom 4303 wireless chip in it. i have b43 legacy installed and at least i am able to view the available wireless networks. The problem is that i am unable to connect to the networks. I have tried connecting to a WPA encrypted network and also an unencrypted one. Neither one has had any success. Any help would be greatly appreciated. Thanks

---

### Post by Ayuthia on 2009-06-16
> **gabetz08 said:**
> Ok so i have a problem. I have a hp zd7000a laptop with a broadcom 4303 wireless chip in it. i have b43 legacy installed and at least i am able to view the available wireless networks. The problem is that i am unable to connect to the networks. I have tried connecting to a WPA encrypted network and also an unencrypted one. Neither one has had any success. Any help would be greatly appreciated. Thanks

Can you post the results of:
```
dmesg|grep b43
```It might provide some clues.

---

### Post by gabetz08 on 2009-06-16
> **Ayuthia said:**
> Can you post the results of:
```
dmesg|grep b43
```It might provide some clues.

greg@Ubuntu:~$ dmesg|grep b43
b43-pci-bridge 0000:06:03.0: enabling device (0000 -> 0002)
b43-pci-bridge 0000:06:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
b43legacy-phy0: Broadcom 4301 WLAN found
b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
b43legacy-phy0 debug: Radio initialized
input: b43legacy-phy0 as /devices/virtual/input/input9
firmware: requesting b43legacy/ucode2.fw
firmware: requesting b43legacy/pcm4.fw
firmware: requesting b43legacy/b0g0initvals2.fw
b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
b43legacy-phy0 debug: Chip initialized
b43legacy-phy0 debug: 30-bit DMA initialized
Registered led device: b43legacy-phy0:tx
Registered led device: b43legacy-phy0:rx
Registered led device: b43legacy-phy0:radio
b43legacy-phy0 debug: Wireless interface started
b43legacy-phy0 debug: Adding Interface type 2
b43legacy-phy0: Radio hardware status changed to DISABLED

---

### Post by Ayuthia on 2009-06-17
Normally when the system switches the radio back to DISABLED, it means that you have not flipped the switch for your wireless card.  It does not seem to be the problem in your case since you are able to see wireless sites.

Are you dual-booting with Windows?  If so, can you see if you can connect there?

---

### Post by gabetz08 on 2009-06-17
> **Ayuthia said:**
> Normally when the system switches the radio back to DISABLED, it means that you have not flipped the switch for your wireless card.  It does not seem to be the problem in your case since you are able to see wireless sites.

Are you dual-booting with Windows?  If so, can you see if you can connect there?

i am with windows xp,it works fine, with any encryption

---

### Post by gabetz08 on 2009-06-24
> **gabetz08 said:**
> i am with windows xp,it works fine, with any encryption

Ayuthia any thoughts on what the problem might be, or does anyone else have any thoughts. Thanks for your help so far Ayuthia, any more would be much appreciated.

---

### Post by Ayuthia on 2009-06-25
I am thinking that it might be a bug.  It looks like some 4318 and 4303 cards are affected by this.  You might check and see if there is a configuration in Windows XP for your wireless card that will help it not turn off when the system shuts down.

This could be wrong, but from what I am understanding Windows will turn off your wireless card before shutting down.  Right now there seems to be a bug that is preventing the cards from turning on.  I think that there is a patch out there for it that was released in 2.6.31 so hopefully it will be backported soon.

The other option is to use ndiswrapper to turn on the card.

---

### Post by gabetz08 on 2009-06-26
> **Ayuthia said:**
> I am thinking that it might be a bug.  It looks like some 4318 and 4303 cards are affected by this.  You might check and see if there is a configuration in Windows XP for your wireless card that will help it not turn off when the system shuts down.

This could be wrong, but from what I am understanding Windows will turn off your wireless card before shutting down.  Right now there seems to be a bug that is preventing the cards from turning on.  I think that there is a patch out there for it that was released in 2.6.31 so hopefully it will be backported soon.

The other option is to use ndiswrapper to turn on the card.

how would i go about doing that, i followed this how to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and it did not work, the version of ubuntu i am using is ubuntu kernel 2.6.27-7-generic thanks again for your help,

---

### Post by Ayuthia on 2009-06-26
> **gabetz08 said:**
> how would i go about doing that, i followed this how to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and it did not work, the version of ubuntu i am using is ubuntu kernel 2.6.27-7-generic thanks again for your help,

Can you post the results of:
```
lshw -C network
ndiswrapper -l
```
It will help us see what wireless driver your system is currently using, and verify that ndiswrapper loaded properly.  If you already know that it is all correct, please also post:
```
dmesg|grep ndis
```It might provide some information about if it had problems with bringing up your wireless.

---

### Post by gabetz08 on 2009-06-28
> **Ayuthia said:**
> Can you post the results of:
```
lshw -C network
ndiswrapper -l
```
It will help us see what wireless driver your system is currently using, and verify that ndiswrapper loaded properly.  If you already know that it is all correct, please also post:
```
dmesg|grep ndis
```It might provide some information about if it had problems with bringing up your wireless.

It seems like i have done a fresh install of ubuntu since i followed that guide last, i wanted to be sure that following that guide was not causing my problems. the output i have is below for the first commands, should i follow this guide again and repost my results once i am finished?

greg@Ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:6f:08:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:55:33:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:4e:8c:87:36:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
greg@Ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
greg@Ubuntu:~$

---

### Post by Ayuthia on 2009-06-29
It looks like ndiswrapper is not currently installed.  I am thinking that you might try that option.

---

### Post by gabetz08 on 2009-06-29
> **Ayuthia said:**
> It looks like ndiswrapper is not currently installed.  I am thinking that you might try that option.

i followed the guide again and now that it is installed here is my output.

greg@Ubuntu:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:6f:08:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.134 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:72:d8:ae:3a:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:55:33:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
greg@Ubuntu:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed

the guide says it should say module=ndiswrapper and mine says module=ssb, and i tried the fix and that did not work, the driver iam using i downloaded from the hp website for my computer so i think it is correct. 

here is the second set of output

greg@Ubuntu:~/bcm43xx$ dmesg|grep ndis
[ 1683.730149] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1683.799648] usbcore: registered new interface driver ndiswrapper
[ 1842.373174] usbcore: deregistering interface driver ndiswrapper
[ 1842.697918] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1842.730511] usbcore: registered new interface driver ndiswrapper
greg@Ubuntu:~/bcm43xx$ 

thanks for your help again

---

### Post by Ayuthia on 2009-06-29
I don't really have an answer.  I am thinking that Windows is turning off your wireless and apparently there is some bug that is preventing Linux from turning on the radio for your card.  There seems to be a few cards affected by this.  I want to say that there is a fix made for 2.6.31 so hopefully they will backport it to this kernel.

---

### Post by gabetz08 on 2009-06-30
> **Ayuthia said:**
> I don't really have an answer.  I am thinking that Windows is turning off your wireless and apparently there is some bug that is preventing Linux from turning on the radio for your card.  There seems to be a few cards affected by this.  I want to say that there is a fix made for 2.6.31 so hopefully they will backport it to this kernel.

Thanks for all of your help. maybe i will get lucky and get it working, thanks again

---

### Post by gabetz08 on 2009-07-01
> **gabetz08 said:**
> Thanks for all of your help. maybe i will get lucky and get it working, thanks again

Ayuthia so i got it working, i reinstalled ubuntu, this time 8.04, i am not sure what i had installed last time but it might have been 8.1. i was originally using the newest driver that i could download which happens to have not worked. once i used the oldest driver i could get ndiswrapper worked perfectly, thanks for your help again

---

