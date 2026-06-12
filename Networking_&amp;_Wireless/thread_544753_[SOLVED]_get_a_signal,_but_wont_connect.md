---
title: "[SOLVED] get a signal, but wont connect"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by belias on 2007-09-06
hi, i need some help. i'm trying to connect a ralink chip usb adapter (on kubuntu 7.04) to a linksys wrt54gs. i have tried a number of different drivers, wicd, ndiswrapper (although im not sure if i installed driver correctly) and even other linux distributions. My problem is that I can see networks, but can't connect to them (same problem with 2 different drivers and 3 different distributions).

---

### Post by belias on 2007-09-06
here, does this give any1 an idea?
[PHP]belias@belias:~$ iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.462 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:36:78:25
          RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

belias@belias:~$ lsusb
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0402:5661 ALi Corp.
Bus 001 Device 001: ID 0000:0000
belias@belias:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:60272 (58.8 KiB)  TX bytes:60272 (58.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:CA:19:AD:EF
          inet6 addr: fe80::2c0:caff:fe19:adef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:7430 (7.2 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-CA-19-AD-EF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/PHP]

---

### Post by tgalati4 on 2007-09-06
>sudo iwconfig wlan0 essid "your wireless network name" key open 32:34:45:32:34
>sudo ifconfig wlan0 ip 192.168.1.110 netmask 255.255.255.0
>sudo route add default gw 192.168.1.1
>ping [www.google.com](www.google.com)

Modify as needed.

---

### Post by belias on 2007-09-06
hi, thanks. I'm getting unknown host.
[PHP]belias@belias:~$ sudo iwconfig wlan0 essid "The Grid" key open 32:34:45:32:34
Password:
belias@belias:~$ sudo ifconfig wlan0 ip 192.168.1.110 netmask 255.255.255.0
ip: Unknown host
ifconfig: `--help' gives usage information.
belias@belias:~$ sudo ifconfig wlan0 ip 192.168.1.110 netmask 255.255.255.0
ip: Unknown host
ifconfig: `--help' gives usage information.
belias@belias:~$ sudo route add default gw 192.168.1.1
belias@belias:~$ ping www.google.com
ping: unknown host www.google.com[/PHP]

---

### Post by kevdog on 2007-09-07
Lets see what driver you are trying to use -- Its a usb dongle with ra chipset, so its possibly a rt73 or rt2500 chipset is what Im guessing.

Can you post
lsmod | grep rt

---

### Post by belias on 2007-09-07
sorry for the wait, im usbing back and forth, and couldn't find the vertical line button, lol. [PHP]belias@belias:~$ lsmod | grep rt
rt2570                186432  0
rt73usb                33536  0
rt2x00lib              11904  1 rt73usb
mac80211              175364  3 rc80211_simple,rt73usb,rt2x00lib
crc_itu_t               3072  1 rt73usb
gameport               16520  1 snd_via82xx
snd_mpu401_uart         9472  1 snd_via82xx
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                35400  1 via_agp
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
usbcore               134280  6 usb_storage,libusual,rt2570,rt73usb,uhci_hcd
belias@belias:~$
[/PHP]

---

### Post by tgalati4 on 2007-09-07
Your essid is called "The Grid".  What did you set the WEP password to?  I just made one up.  And you used it.  You need to either turn off the WEP password in your router, or set your own password.

With no password:

>sudo iwconfig wlan0 essid "The Grid" key off
>sudo ifconfig wlan0 ip 192.168.1.110 netmask 255.255.255.0

Unknown host simply means that networking is down.

You also need to verify what your subnet is.  Your local area network could be 192.168.0.XX.  Your router will tell you--log into it with a browser--http://192.168.0.1 or [http://192.168.1.1](http://192.168.1.1)

---

### Post by belias on 2007-09-07
yea, subnet is 255.255.255.0. same result, uknown host on the second command. i have encryp off for now. network is fine though, im using it on different pc
edit: key off this last time btw

---

### Post by belias on 2007-09-07
see:
[PHP]belias@belias:~$ sudo iwconfig wlan0 essid "The_Grid" key off
Password:
belias@belias:~$ sudo ifconfig wlan0 ip 192.168.1.1 netmask 255.255.255.0
ip: Unknown host
ifconfig: `--help' gives usage information.
belias@belias:~$[/PHP]
note: i just changed the name in the router to include the underscore, based on some1's suggestion on another post.

---

### Post by kevdog on 2007-09-07
I must be totally stupid since I really havent gotten a hold of what your problem is?

What if you just try the following with the WEP key off as you stated
sudo ifconfig wlan0 down
sudo killall dhclient dhclient3
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "The_Grid"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

---

### Post by belias on 2007-09-07
lol, i've been battling this thing for a week now! standby, I'll try that.

---

### Post by belias on 2007-09-07
[PHP]belias@belias:~$ sudo ifconfig wlan0 down
Password:
belias@belias:~$ sudo killall dhclient dhclient3
dhclient: no process killed
belias@belias:~$ sudo ifconfig wlan0 up
belias@belias:~$ sudo iwconfig wlan0 essid "The_Grid"
belias@belias:~$ sudo iwconfig wlan0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
belias@belias:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:ca:19:ad:ef
Sending on   LPF/wlan0/00:c0:ca:19:ad:ef
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
belias@belias:~$

[/PHP]

---

### Post by kevdog on 2007-09-07
Ok next plan of attack but will take some work on your part.  Lets try to update your driver. Here are the instructions:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by belias on 2007-09-07
good morning. ok lets give this a try. if i get stuck somewhere i'll post.

---

### Post by Vadi on 2007-09-07
I'm getting the same problem with one of the wireless cards (a motorola one). In iwlist list it gives "" as the ESSID, when you try and set something on it, it refuses.

I haven't bothered playing with it too much because another linksys card works as soon as I plug it in, heh.

---

### Post by belias on 2007-09-07
vadi, i don't have such luck, lol. 
kev, i got all the way to step 14 and believe i did everything right. On the last command it picked up the linksys addresses, submask, but the network manager doesn't see the networks anymore..i tried restarting network manager, but same thing, didn't see networks. (the only change i made was rename the tar file in the beginning, for easy use in terminal). This is where i am right now, haven't configured the auto reboot yet. 
[PHP]belias@belias:~$ cd /usr/src
belias@belias:/usr/src$ sudo cp ~/rt73 /usr/src
belias@belias:/usr/src$ sudo tar -xvzf rt73
rt73-cvs-2007090709/
rt73-cvs-2007090709/FAQ
rt73-cvs-2007090709/THANKS
rt73-cvs-2007090709/CHANGELOG
rt73-cvs-2007090709/CVS/
rt73-cvs-2007090709/CVS/Root
tar: rt73-cvs-2007090709/CVS/Root: time stamp 2007-09-07 10:35:50 is 10593.018975958 s in the future
rt73-cvs-2007090709/CVS/Repository
tar: rt73-cvs-2007090709/CVS/Repository: time stamp 2007-09-07 10:35:50 is 10593.016330092 s in the future
rt73-cvs-2007090709/CVS/Entries.Log
tar: rt73-cvs-2007090709/CVS/Entries.Log: time stamp 2007-09-07 10:35:51 is 10594.014481813 s in the future
rt73-cvs-2007090709/CVS/Entries
tar: rt73-cvs-2007090709/CVS/Entries: time stamp 2007-09-07 10:35:51 is 10594.012570956 s in the future
rt73-cvs-2007090709/LICENSE
tar: rt73-cvs-2007090709/CVS: time stamp 2007-09-07 10:35:51 is 10594.011039477 s in the future
rt73-cvs-2007090709/Module/
rt73-cvs-2007090709/Module/auth.c
rt73-cvs-2007090709/Module/rt73.h
rt73-cvs-2007090709/Module/rt73.bin
rt73-cvs-2007090709/Module/rt2x00debug.h
rt73-cvs-2007090709/Module/md5.c
rt73-cvs-2007090709/Module/rtusb_data.c
rt73-cvs-2007090709/Module/rtmp_main.c
rt73-cvs-2007090709/Module/rt_config.h
tar: rt73-cvs-2007090709/Module/rt_config.h: time stamp 2007-09-07 10:35:57 is 10599.957222317 s in the future
rt73-cvs-2007090709/Module/assoc.c
rt73-cvs-2007090709/Module/CVS/
rt73-cvs-2007090709/Module/CVS/Root
tar: rt73-cvs-2007090709/Module/CVS/Root: time stamp 2007-09-07 10:35:51 is 10593.952087309 s in the future
rt73-cvs-2007090709/Module/CVS/Repository
tar: rt73-cvs-2007090709/Module/CVS/Repository: time stamp 2007-09-07 10:35:51 is 10593.949681137 s in the future
rt73-cvs-2007090709/Module/CVS/Entries
tar: rt73-cvs-2007090709/Module/CVS/Entries: time stamp 2007-09-07 10:35:53 is 10595.947404312 s in the future
rt73-cvs-2007090709/Module/wpa.c
tar: rt73-cvs-2007090709/Module/CVS: time stamp 2007-09-07 10:35:53 is 10595.945235602 s in the future
rt73-cvs-2007090709/Module/sync.c
rt73-cvs-2007090709/Module/rtmp_info.c
rt73-cvs-2007090709/Module/iwpriv_usage.txt
rt73-cvs-2007090709/Module/rtusb_bulk.c
rt73-cvs-2007090709/Module/mlme.h
rt73-cvs-2007090709/Module/connect.c
rt73-cvs-2007090709/Module/rtmp_tkip.c
rt73-cvs-2007090709/Module/auth_rsp.c
rt73-cvs-2007090709/Module/oid.h
rt73-cvs-2007090709/Module/rtmp_init.c
rt73-cvs-2007090709/Module/TESTING
rt73-cvs-2007090709/Module/rtusb_io.c
rt73-cvs-2007090709/Module/rtmp.h
rt73-cvs-2007090709/Module/mlme.c
rt73-cvs-2007090709/Module/md5.h
rt73-cvs-2007090709/Module/wpa.h
rt73-cvs-2007090709/Module/rtmp_wep.c
rt73-cvs-2007090709/Module/rtmp_def.h
rt73-cvs-2007090709/Module/Makefile
rt73-cvs-2007090709/Module/rtmp_type.h
rt73-cvs-2007090709/Module/sanity.c
rt73-cvs-2007090709/README
tar: rt73-cvs-2007090709/Module: time stamp 2007-09-07 10:35:57 is 10599.816992243 s in the future
tar: rt73-cvs-2007090709: time stamp 2007-09-07 10:35:51 is 10593.815130555 s in the future
belias@belias:/usr/src$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [1cfbb2778c6fde3aed5caf08923bf2e9-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)'
This disc is called:
'Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)'
Copying package lists...gpgv: Signature made Tue 17 Apr 2007 01:55:04 AM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
belias@belias:/usr/src$ sudo aptitude update
Err http://security.ubuntu.com feisty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign http://security.ubuntu.com feisty-security Release
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://security.ubuntu.com feisty-security/universe Sources
Err http://us.archive.ubuntu.com feisty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://security.ubuntu.com feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com feisty Release
Ign http://us.archive.ubuntu.com feisty-updates Release
Err http://security.ubuntu.com feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Sources
Err http://us.archive.ubuntu.com feisty/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_US
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_US
Reading package lists... Done
belias@belias:/usr/src$ sudo aptitude install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8050kB of archives. After unpacking 33.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package linux-libc-dev.
(Reading database ... 75262 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
belias@belias:/usr/src$ cd /usr/src/rt73-cvs-2007090709
belias@belias:/usr/src/rt73-cvs-2007090709$ sudo make
make: *** No targets specified and no makefile found.  Stop.
belias@belias:/usr/src/rt73-cvs-2007090709$ Module
cbash: Module: command not found
belias@belias:/usr/src/rt73-cvs-2007090709$ cd Module
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/md5.o
  LD [M]  /usr/src/rt73-cvs-2007090709/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/rt73-cvs-2007090709/Module/rt73.mod.o
  LD [M]  /usr/src/rt73-cvs-2007090709/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo strip -s rt73.ko
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo strip -S rt73,ko
strip: 'rt73,ko': No such file
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo strip -S rt73.ko
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
make[2]: Warning: File `/usr/src/rt73-cvs-2007090709/Module/rt_config.h' has modification time 9.4e+03 s in the future
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2007090709/Module/md5.o
  LD [M]  /usr/src/rt73-cvs-2007090709/Module/rt73.o
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /usr/src/rt73-cvs-2007090709/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-15-generic/extra ...
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/rt73-cvs-2007090709/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  INSTALL /usr/src/rt73-cvs-2007090709/Module/rt73.ko
  DEPMOD  2.6.20-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo ifconfig wlan0 down
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo modprobe -r rt73usb
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo modprobe -r rt2570
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo modprobe -r rt2500usb
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo modprobe -r rt2x00lib
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ gksu gedit /etc/modprobe.d/blacklist
The program 'gksu' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksu: command not found
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ kdesu kate /etc/modprobe.d/blacklist
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-root/kconf_update1oGH3a.tmp:1
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo modprobe -v rt73
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:132144 (129.0 KiB)  TX bytes:132144 (129.0 KiB)

wlan1     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo ifconfig wlan1 up
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo iwconfig wlan1 essid The_Grid
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo iwconfig wlan1 key off
belias@belias:/usr/src/rt73-cvs-2007090709/Module$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:c0:ca:19:ad:ef
Sending on   LPF/wlan1/00:c0:ca:19:ad:ef
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.105 -- renewal in 35266 seconds.
belias@belias:/usr/src/rt73-cvs-2007090709/Module$

[/PHP]

---

### Post by kevdog on 2007-09-07
Oh yea -- forget network manager -- wont work with ra drivers, but WICD or rutilt are alternatives, so dont worry about that!

Two things I see
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.105 -- renewal in 35266 seconds. 

#1. You dont have a resolv.conf file???
Here is what is in mine:
search hsd1.il.comcast.net.
nameserver 192.168.1.1

#2. From the last line you are connected to the router and you were given an ip address.  You may have problems with domain name resolution (see above), but can you ping yahoo or something (here is there IP address)
ping 66.94.234.13

Also ping your router
192.168.1.1

---

### Post by belias on 2007-09-07
does the yahoo ping ever stop? it keep's going and going

---

### Post by kevdog on 2007-09-07
sorry unlike windows you either need to break it with cntr-c or do the following 

ping -c4 xxx.xxx.xxx.xxx

---

### Post by belias on 2007-09-07
i just x'd out the terminal.
> **kevdog said:**
>  
#1. You dont have a resolv.conf file???
Here is what is in mine:
search hsd1.il.comcast.net.
nameserver 192.168.1.1


don't know what a resolv.conf file is. where do i find/change it? router? does the "il" stand for illinois, i ask because i have comcast in florida.

here are some of the ping results..

[PHP]belias@belias:~$ ping 66.94.234.13
PING 66.94.234.13 (66.94.234.13) 56(84) bytes of data.
64 bytes from 66.94.234.13: icmp_seq=1 ttl=46 time=108 ms
64 bytes from 66.94.234.13: icmp_seq=2 ttl=46 time=106 ms
64 bytes from 66.94.234.13: icmp_seq=3 ttl=46 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=4 ttl=46 time=104 ms
64 bytes from 66.94.234.13: icmp_seq=5 ttl=45 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=6 ttl=46 time=111 ms
64 bytes from 66.94.234.13: icmp_seq=7 ttl=45 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=8 ttl=46 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=9 ttl=46 time=104 ms
64 bytes from 66.94.234.13: icmp_seq=10 ttl=46 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=11 ttl=45 time=114 ms
64 bytes from 66.94.234.13: icmp_seq=12 ttl=46 time=105 ms
64 bytes from 66.94.234.13: icmp_seq=13 ttl=45 time=103 ms

belias@belias:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.65 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.83 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.40 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.93 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.71 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.48 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=2.26 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=2.04 ms


[/PHP]

---

### Post by kevdog on 2007-09-07
Try just making a /etc/resolv.conf file:

gksu gedit /etc/resolv.conf

with the following
nameserver 192.168.1.1

---

### Post by belias on 2007-09-07
alright, i had to use "kdesu kate" in kubuntu...in the term there were six devices that failed to open, but the wordpad did with the entries:
search hsd1.fl.comcast.net.
nameserver 68.87.74.162
nameserver 68.87.68.162

so do i add, nameserver 192.168.1.1 and delete the other two, above, or add and LEAVE the other two there?

---

### Post by kevdog on 2007-09-07
Im confused, you have a /etc/resolv.conf file????

Ok dont do anything just yet,

What if you just ping -c4 google.com (like that).  Does that work??

---

### Post by belias on 2007-09-07
[PHP]belias@belias:~$ ping -c4 google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=240 time=46.7 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=240 time=46.3 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=240 time=45.1 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=240 time=46.9 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 45.137/46.298/46.924/0.733 ms
belias@belias:~$
[/PHP]

---

### Post by kevdog on 2007-09-07
So you are connected....everything works right??

---

### Post by belias on 2007-09-07
not yet, i'm trying to install wicd, but it told me to ditch network manager..did it. Then it couldn't install because it needed python glade and python gtk2 installed...i downloaded the python suite and just installed that..now it says those two files "are not configured yet"...so i'm on that now. I'll post soon when i have the wicd installed and hopefully connected.
edit: scratch that..any idea how to configure the python files?

---

### Post by kevdog on 2007-09-07
You dont really need network manager, wicd or anything else during this testing phase if you know how to bring the network up manually.  Im lazy, but I cant remember if I included this in the post.

Its a series of
sudo ifconfig
sudo iwconfig
sudo iwconfig
sudo dhclient 

statements. (Well thats not all WICD does, but it is at its core anyway).

Did you do these statements earlier???  If not please post
iwlist scan

And make sure no wpa/wep is included in the router for right now.

---

### Post by belias on 2007-09-07
sorry i went out to eat. Great news..I am OnLIne!:guitar:
THANK YOU VERY MUCH! I also ran through the steps again on Ubuntu and got the same result. 
so anything else i should do or know?

---

