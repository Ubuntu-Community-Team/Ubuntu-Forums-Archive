---
title: "Help with my HP Pavilion dv6500"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by AlexBaranosky on 2011-01-04
Hi everyone,

I recently decided to take the plunge and set my HP Pavilion dv6500 up with Ubuntu 9.10 (the disk I have... I figure I can upgrade to 10 once I get the internet working on it... please, correct me if this strategy is a bad one)

I'm having trouble getting the wireless to work with my Broadcom wireless.  But beyond that I cannot even get my LAN to work.  When I plug in the internet cable a wheel spins indefinately in the upper right corner of the screen.  

Can anyone help me get my internet working? (LAN and wireless)

I read on another post that it would be helpful to post this data.

lspci -nn

lshw -C network

I cannot include the results of those commands because I don't have access to internet from the Ubuntu laptop.  However, I can give some pieces:

from lspci -nn: 
Network controller [0288]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311]

from lshw -C network:
*-network
   description: Ethernet interface
   product: MCP67 Etherent
   vendor: nVidia Corporation
   physical id: a
   bus info: pci@0000.00:01.0
   logical name: eth0
   version a2
   serial: 00:1b:24:da:2d:f4
   width: 32 bits
   clock: 66MHz
   capabiities: bus_master cap_list ethernet physical
   configuration: broadcast=yes driver=forcedth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast-yes

-network
    description: Network controller
    product: BCM4311 802.11b/g WLAN 
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:03:00.0
    version: 02
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list
    configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Thank you for the help,
Alex

---

### Post by Mercury_Alpha on 2011-01-04
Broadcom adapters can be a bit tricky. [Take a look here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for details on how to work with them.

---

### Post by Bucky Ball on 2011-01-04
10.04 LTS is for you. Broadcom are not tricky at all anymore. And it's a wireless card, not a modem. You will find STA and B43 in System->Administration->Hardware Drivers (or Additional Drivers in 10.04) ;)

Unfortunately, you need to be online to install the easy way.

---

### Post by AlexBaranosky on 2011-01-05
So I downloaded and installed from CD version 10.04.1  When I load the OS I have the same two problems.  It doesn't see my wireless network, and when I plug my ethernet in directly it doesn't work either.  I click autoeth0 and get a popup black window saying something along the lines of internet disconnected, with a image of a ethernet cord.

Any help is GREATLY appreciated! :)

Thanks in advance,
Alex

---

### Post by AlexBaranosky on 2011-01-05
> You will find STA and B43 in System->Administration->Hardware Drivers (or Additional Drivers in 10.04)

I did not see this line last night.  It was late I guess I missed it.  

I will look in System-> Administration->Hardware Drivers tonight after work and let you all know how it goes!

Thanks for the help,
Alex

---

### Post by AlexBaranosky on 2011-01-05
I don't have any internet access.  Hardware Drivers is trying to download a driver, but it can't access the net!

no proprietary drivers are in use on this system.

What can I do to get my laptop on the internet?

All help is GREATLLLLLLLLLY appreciated.

All the Best,
Alex

---

### Post by Bucky Ball on 2011-01-05
Ah, just about there. Could you open a terminal (Applications->Accessories->Terminal) and paste this in:

```
iwconfig
```then

```
 ifconfig
```Post the result back here. :)

Other thing is, with the cable plugged in, right click the spinning network icon. Is 'Enable Networking' ticked?

From there open 'Edit Connections'. Click your wired connection and check it is set up correctly. If you're not using a static IP, make sure it is not set to that but 'Automatic (DHCP)'. This will be in the IPV4 section of the setup.

*** Post #16 on this thread:

[http://ubuntuforums.org/showthread.php?p=10318623#post10318623](http://ubuntuforums.org/showthread.php?p=10318623#post10318623)

Might get you going. The fix seems to be unplugging everything from the machine for five minutes (including power). I have no idea what this is all about but it has worked for a number of people I have noticed. Good luck. ;)

---

### Post by AlexBaranosky on 2011-01-05
```
lo   no wireless extensions

eth0   no wireless extensions

wlan0   IEEE 802.11bg ESSID:off/any
        Mode:MAnaged Access Point: Not-Associated    Tx-Power=0 dBm
        Retry long limit:7   RTS thr:off   Fragment thr:off
        Power Management:off
```

then......

```
eth0   Link encap:Ethernet   HWaddr 00:1b:24:da:2d:f4
       inet6 addr: fe80::21b:24ff:feda:2df4/64  Scope:Link
       UP BROADCAST MULTICAST   MTU:1500   Metric:1
       RX packets:2165 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:132481 (132.4 KB)  TX bytes:2222 (2.2 KB)
       Interrupt:27

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1.128  Scope:Host
       UP LOOPBACK RUNNING  MTU:16436  Metric:1
       RX packets:268 errors:0 dropped:0 overrunes:0 frame:0
       TX packets:268 errors:0 dropped:0 overrunes:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:21200 (21.2 KB)  TX bytes:21200 (21.2 KB)
```



Thanks for all the help.

---

### Post by bkratz on 2011-01-05
Here is a pretty good page for installation with no ethernet access

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Bucky Ball on 2011-01-05
> **AlexBaranosky said:**
> 

Thanks for all the help.

Pleasure. Please read and try the things at the end of my last post (#7). I have edited it. 

You *can* install STA without connection but you need a machine somewhere with a connection for b43. This is a last resort. Let's see if we can't get your wired connection working first as this will save a lot of time, not to mention brain aches for a new user. If wired is not working it's a problem apart from your wireless issue.

While I think of it: Shutdown, plug in the ethernet cable, reboot. Any different? If not, right click network icon and 'Edit connections', delete the wired connection (auto eth0 probably) restart the machine with cable in. Any different?

---

### Post by AlexBaranosky on 2011-01-05
REVISED:

***I see I needed to right-click to see the options you working referring to.  ***

the spinning network icon is no longer there on this new version of Ubuntu.  there is instead a icon to the left of the volume, like wireless waves.  

Enable Networking is indeed checked.

Under Edit Connections Automatic (DHCP) is indeed selected.

...

EDIT: going to try restart suggestions nows.

---

### Post by AlexBaranosky on 2011-01-05
So I restarted the computer after deleting the auto eth0.  It didn't resolve the issue.  Then I wondered if maybe the problem wasn't actually Ubuntu but my LAN card.  I restarted the computer in Windows and could not get the LAN working. I dropped my laptop a while back and had to have the motherboard replaced ad i wonder if the LAN was broken in that incident. I never use LAN so its entirely possible.

Crap.

So assuming my LAN is broken in some way, what is the other way to get my wireless working?  Is it possible to get the drivers from another computer and put them on a thumb drive perhaps??

Thanks again for all the help.

Alex

---

### Post by AlexBaranosky on 2011-01-05
Currently downloading driver for 64-bit here: 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

MORE INFO:

oh man, I have to compile c code to get the driver working, which means it will be native code, and thus Windowsy if I compile it right?  So if I cannot compile it in Windows, and then transfer to my Ubuntu machine via thumb-drive / CD-R what can I do here?

Hopefully I'm wrong and I can compile the C in Cygwin.

BUILD ATTEMPT UPDATE:

I downloaded mingw32-make and tried using it to compile the driver.  It couldn't recognize KBUILD_NOPEDANTIC:

```
C:\Users\Alex and Paula\Desktop\hybrid-portsrc_x86_64-v5_100_82_38.tar>mingw32-make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
'KBUILD_NOPEDANTIC' is not recognized as an internal or external command,
operable program or batch file.
mingw32-make: *** [all] Error 1
```

---

### Post by waynefoutz on 2011-01-05
It doesn't have to be this difficult. There is an Ubuntu remix out there called SuperOS (formerly Super Ubuntu.) It's nothing more than Ubuntu with more software installed out of the box, and the drivers you are trying to install will be there for you as well. The only difference is that it's a bigger download, so you'll have to burn the .iso on a DVD. I guarantee this will work on your machine, because I installed 10.04 on that particular HP machine. 


[http://hacktolive.org/wiki/Super_OS#Download]("http://hacktolive.org/wiki/Super_OS#Download") 

The drivers for the Wifi adapter didn't install by default, but when it searched for them it found them, because they are on the DVD. You also get lots of other cool software like Google Chrome and Ubuntu Tweak installed out of the box. Flash and Java as well.

---

### Post by AlexBaranosky on 2011-01-06
Super OS sounds enticing.  I'll have to pick up some DVD-R's tomorrow.

---

### Post by Bucky Ball on 2011-01-06
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You can install STA driver without internet. b43: You need access to a machine (not the one you're trying to get online,  obviously) which has access to the net.

Super OS may well install a whole lot of other things you DON'T need. Better to add them later but up to you.

From your outputs, the wireless card shows up. This generally means it is operational. BUT, a busted card could be the issue. USB wireless dongles are cheap (I bought one for AU$12). That is the easy option.

Have a look here:

[http://computers.shop.ebay.com/USB-Wireless-Adapters-/45002/i.html?_nkw=computer&_catref=1&_fln=1&_trksid=p3286.c0.m282](http://computers.shop.ebay.com/USB-Wireless-Adapters-/45002/i.html?_nkw=computer&_catref=1&_fln=1&_trksid=p3286.c0.m282)

There's a couple there which use Ralink chips. These should work 'out of the box' but email seller or have a look in local computer shops and ask the assistant (no guarantees they'll have any idea 'bout Linux compatibility, of course!) ;)

This doesn't explain why your ethernet cable connection is not working. :confused:

---

### Post by waynefoutz on 2011-01-06
> **Bucky Ball said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You can install STA driver without internet. b43: You need access to a machine (not the one you're trying to get online,  obviously) which has access to the net.

Super OS may well install a whole lot of other things you DON'T need. Better to add them later but up to you.

From your outputs, the wireless card shows up. This generally means it is operational. BUT, a busted card could be the issue. USB wireless dongles are cheap (I bought one for AU$12). That is the easy option.

Have a look here:

[http://computers.shop.ebay.com/USB-Wireless-Adapters-/45002/i.html?_nkw=computer&_catref=1&_fln=1&_trksid=p3286.c0.m282](http://computers.shop.ebay.com/USB-Wireless-Adapters-/45002/i.html?_nkw=computer&_catref=1&_fln=1&_trksid=p3286.c0.m282)

There's a couple there which use Ralink chips. These should work 'out of the box' but email seller or have a look in local computer shops and ask the assistant (no guarantees they'll have any idea 'bout Linux compatibility, of course!) ;)

This doesn't explain why your ethernet cable connection is not working. :confused:


From the site:
 >    * NEW: Based on Ubuntu 10.10
    * NEW: Easy installation of Nvidia, ATI and Broadcom drivers, even without an internet connection (see bellow)
    * NEW: usb-creator, Live USB creator right from the DVD menu (replacing cd2usb)
    * NEW: Java re-added, replacing OpenJDK (only Java works with some banking websites)
    * NEW: All software in the Super OS repository updated to their latest versions
    * Additional Multimedia Support: VLC, support for DVD-playback, MP3 support and for other formats, like QuickTime video, Real video, Windows Media Video, Flash Video, DivX, Xvid, (.mov, .wmv, .flv, .avi, etc...) etc...
    * Internet software: aMSN, Skype, Opera, Google Chrome and Firefox (all browsers include Flash)
    * Portable Applications available (RUNZ included)
    * Programs are easier to run: App Runner is included
    * Mount tar.gz/.zip/.rar/.iso files with File mounter
    * Other software: Ubuntu Tweak and GParted
    * Super OS has it's own repository, in addition to the official Ubuntu repositories
    * Live USB creator (usb-creator) right from the DVD menu (see second image)
    * Improved compatibility with 32-bits applications, by including ia32-libs (64-bits version)
    * Wubi, allowing easy installation alongside Windows
    * Computer Janitor disabled, since it is pretty much a useless and confusing program
    * Focus on making it very usable offline 


I didn't make SuperOS, it's not my baby, and I got nothing to gain by promoting it. It installs all the stuff I'd usually install anyway. I use it because it's a fantastic time saver. When I install on a blank hard drive, it shaves off 30 minutes to an hour off the job, because the job is pretty much done for you after the first boot. All the restricted extras are installed , DVD playback works, proprietary drivers are installed without the need for an internet connection, etc. If there is an application that it installs that you don't want, such as Google Chrome, you can simply remove it. Their custom repository is real nice too, you can add that to any Ubuntu, which will add programs like Google Earth into your Software Center that normally don't come packaged in .deb files. The way I see it, it's a fantastic shortcut to get a fully working system on the first boot.

---

### Post by Bucky Ball on 2011-01-06
> **waynefoutz said:**
> From the site:It installs all the stuff I'd usually install anyway.

Didn't think you 'made' SuperOS. Point taken. But what you'd install anyway might not be what other people would. There are some users who avoid third party drivers and sources at all costs unless their hands are tied and no choice. ;)

---

### Post by AlexBaranosky on 2011-01-06
Ahha!!

I have a wireless USB adapter, and I can connect to the internet using it on my Ubuntu machine!  

Now what should I do to get the proper driver(s) for the builtin wireless card?

MORE INFO:

I did it!!!  I used the usb wireless adapter to enable me to go to administration -> hardware drivers, and downloaded the sta driver, and a video card driver.

Thanks for all the help, I couldn't have done it without you.

---

### Post by Bucky Ball on 2011-01-06
MATE!!!! Excellent news and well done yourself! :lol:

Told you if you could get online it would be that easy ... ;)

Welcome to the forums, enjoy the OS and the learning curve, mark thread as 'Solved' from 'Thread Tools', and don't be shy to repost about any further issues. Good luck with it all. ;)

Bucky

---

