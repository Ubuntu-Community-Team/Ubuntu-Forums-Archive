---
title: "can't establish wireless"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by aaryan on 2009-07-24
I just had Ubuntu 9.4 installed today. I am very new to Ubuntu, and have been messing around with it to try to get the hang of it. No matter how much I do, however, I cannot establish a wireless signal from my router, though I had no problem with that when I was using Windows XP. Any suggestions on how I can get this connection? I feel like I've tried everything! :confused:

---

### Post by mapes12 on 2009-07-24
Hi

Here are some guides that might help you out:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

The bottom line is that your wifi card needs to be supported in Linux.

---

### Post by LookTJ on 2009-07-24
To make sure that it is working, post the output of:
```
ifconfig
```

What wireless card do you have?

if you do not know, try:
```
lspci | grep Network
```
and post the output.

:)

---

### Post by aaryan on 2009-07-24
hi mapes,
I have a Dell XPS laptop
I used the following
lspci | grep Broadcom\Corporation
and the result was:
0c:00:0 Network controller : Broadcom Corporation BCM4328 802.11a/b/g/n (rev03)

---

### Post by shantiq on 2009-07-24
[B][COLOR=Teal]> **aaryan said:**
> I just had Ubuntu 9.4 installed today. I am very new to Ubuntu, and have been messing around with it to try to get the hang of it. No matter how much I do, however, I cannot establish a wireless signal from my router, though I had no problem with that when I was using Windows XP. Any suggestions on how I can get this connection? I feel like I've tried everything! :confused:


hope this helps   from[/COLOR][/B]

[FONT=arial black,sans-serif][B][COLOR=#3333ff][http://www.ubuntupocketguide.com/download/ubuntupocketguide-v1-1.zip](http://www.ubuntupocketguide.com/download/ubuntupocketguide-v1-1.zip)

which is free to download

on page 26

Wired (Ethernet)
As soon as you attach an Ethernet cable to your computer, your
computer will be online straight away. No configuration is necessary.
The exception is if your network doesn&#8217;t automatically assign IP
addresses (i.e. it lacks a DHCP server). This is rare, but is sometimes
the case in certain workplaces. In this case you&#8217;ll need to enter the IP,
subnet mask, gateway, and DNS addresses manually, as follows.
Configuring a static IP address (Ubuntu 8.10 and
above)
To configure a static IP address (non-DHCP) under Ubuntu 8.10,
right-click the NetworkManager icon at the top-right of the screen and
select Edit Connections. In the window that appears, ensure the Wired
tab is selected and click the Auto eth0 entry. Click the EDIT button. In
the new window that appears, click the IPv4 Settings tab, and select
Manual from the Method dropdown list. Click the ADD button and enter
your IP address, subnet mask, and gateway (router) details by clicking
the entries under relevant headings. Add the DNS addresses in the
DNS Servers text field (separate each address by a comma). You can
leave the Search Domains field blank. Click OK when done and reboot
the computer.
Configuring a static IP address (Ubuntu 8.04)
To configure a static IP address under Ubuntu 8.04, click System &#61537;
Administration &#61537; Network. In the program window that appears, click
the UNLOCK button and enter your password when prompted. Select the
Wired Connection entry and click the PROPERTIES button. In the dialog
box that appears, uncheck Enable Roaming Mode and, in the
26  : Configuring Ubuntu 
Configuration dropdown list, select Static IP Address. Enter the IP
address, subnet mask, and gateway (router) details into the relevant
text fields. Click OK and, in the parent dialog box, click the DNS tab and
then the ADD button. Enter the first DNS address and hit Enter. Click
ADD again and enter the second DNS address. Once done, click the
CLOSE button. You may have to reboot your computer before the new
configuration works.




shan  :D:D:D:D

[/COLOR][/B][/FONT]

---

### Post by aaryan on 2009-07-24
Hi,
this is my out put
lspci | grep Broadcom\ Corporation
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
aaryan@aaryan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:de:7a:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by aaryan on 2009-07-24
hi 
this is my output
lspci | grep Broadcom\ Corporation
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
aaryan@aaryan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:de:7a:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by LookTJ on 2009-07-24
from [this]("http://ubuntuforums.org/showthread.php?p=7345208&highlight=BCM4328#post7345208"):
> **Shadow121 said:**
> In a terminal do "sudo apt-get install b43-fwcutter"

Then disable and re-enable the driver in Ubuntu&#8217;s Restricted Driver Manager and it should work after a restart.


*EDIT*
Just in case:
> **Shadow121 said:**
> System>Admin>Hardware Drivers.  Activate it in there.

---

### Post by aaryan on 2009-07-24
i just ran the command and got the o/p as
reading package lists ... Done
Building dependency tree
Reading State information ...Done
E: Couldn't find package b43-fwcutter

I will still continue to disable and re enable the driver and restart and c

---

### Post by aaryan on 2009-07-24
in the top right corner it shows wireless enabled and has connected.
thanks a lot for your help. :)

---

### Post by aaryan on 2009-07-24
how do i now get the other drivers like the audio and video drivers to work?

---

### Post by aaryan on 2009-07-24
hi,
How do I install or get my audio and video files to work?

---

### Post by swoody on 2009-07-24
Hi aaryan, and welcome to the forums ):P 

For a bit more in depth info on how to get all your multimedia needs working, you may want to check out this great post:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also, as it's a *great* reference to have on hand, or even just read over while you're learning the ropes in Ubuntu, you may want to download the Free Beginner's guide from the link in my signature. 

Hopefully that'll take care of your issues for now, but as always don't be afraid to ask anything on these forums :D

---

### Post by aaryan on 2009-07-24
thanks a lot, I'll try tht and get back 2 u.

---

### Post by aaryan on 2009-07-24
Hi,
I tried the instructions from the document and got the following results stating that there is not enough free space 
the out put is :
aaryan@aaryan-laptop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for aaryan: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090724134939
aaryan@aaryan-laptop:~$ gksudo gedit /etc/apt/sources.list
aaryan@aaryan-laptop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_IN
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_IN      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_IN  
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg [189B]         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_IN
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Translation-en_IN
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Translation-en_IN     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_IN   
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release [74.6kB]                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [57.9kB]        
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release [49.6kB]             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2092B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [17.4kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [611B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [23.1kB]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B]     
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Packages [1253kB]              
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]  
Get:18 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages [3258B]              
Get:19 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages [8357B]          
Get:20 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources [3200B]               
Get:21 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources [5932B]           
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Packages [8848B]         
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Sources [555kB]                
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Sources [3156B]          
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages [4757kB]          
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources [2375kB]           
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages [197kB]         
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources [107kB]          
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Packages [121kB]       
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Packages [2092B] 
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Sources [37.8kB]       
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Sources [611B]   
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Packages [41.6kB]  
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Sources [11.7kB]   
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Packages [3933B] 
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Sources [1349B]  
Fetched 9789kB in 16min 57s (9617B/s)                                          
Reading package lists... Done
aaryan@aaryan-laptop:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
[sudo] password for aaryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 169 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-installer freepats gsfonts-x11 java-common
  liba52-0.7.4 libamrnb3 libamrwb3 libass1 libavcodec-unstripped-52
  libavformat52 libavutil-unstripped-49 libcdaudio1 libcelt0 libdc1394-22
  libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado0
  libfftw3-3 libfreebob0 libgmyth0 libid3tag0 libiptcdata0 libjack0 liblrdf0
  libmad0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3
  libmpeg2-4 libmysqlclient15off libneon27-gnutls libofa0 libopenspc0
  libpostproc51 libquicktime1 libraptor1 libsidplay1 libsoundtouch1c2
  libstdc++5 libswscale0 libtwolame0 libwildmidi0 libx264-65 libxml++2.6-2
  libxvidcore4 mysql-common odbcinst1debian1 raptor-utils sun-java6-bin
  ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc
  w32codecs
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs equivs libdvdcss2
  debhelper fakeroot build-essential libfftw3-dev jackd liblrdf0-dev
  sidplay-base xsidplay libmyodbc odbc-postgresql libct1 mplayer
The following NEW packages will be installed:
  alsa-oss cabextract faac faad flashplugin-installer flashplugin-nonfree
  freepats gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse java-common
  liba52-0.7.4 libamrnb3 libamrwb3 libass1 libavcodec-unstripped-52
  libavformat52 libavutil-unstripped-49 libcdaudio1 libcelt0 libdc1394-22
  libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado0
  libfftw3-3 libfreebob0 libgmyth0 libid3tag0 libiptcdata0 libjack0 liblrdf0
  libmad0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmp4v2-0
  libmpcdec3 libmpeg2-4 libmysqlclient15off libneon27-gnutls libofa0
  libopenspc0 libpostproc51 libquicktime1 libraptor1 libsidplay1
  libsoundtouch1c2 libstdc++5 libswscale0 libtwolame0 libwildmidi0 libx264-65
  libxml++2.6-2 libxvidcore4 mysql-common non-free-codecs odbcinst1debian1
  raptor-utils sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
  ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc
  unrar w32codecs
0 upgraded, 77 newly installed, 0 to remove and 169 not upgraded.
Need to get 95.4MB of archives.
After this operation, 215MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.
aaryan@aaryan-laptop:~$

---

### Post by aaryan on 2009-07-24
how do I determine the disk space now as i am getting the warning of no sufficient disk space for installing the updates where as i have a 250 gb hard disk

---

### Post by swoody on 2009-07-24
Just go to Applications>Accessories>Disk Usage Analyzer

That will show you your total amount of space, as well as how much free space you have.

---

