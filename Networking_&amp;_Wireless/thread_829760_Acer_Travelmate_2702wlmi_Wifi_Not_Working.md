---
title: "Acer Travelmate 2702wlmi Wifi Not Working"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by williebear on 2008-06-15
Hi All, newbiew here. I thought I would try something different on my laptop and was advised to try ubuntu. INstallation great, everything works fine apart from the wifi.i have tried to install via ndiswrapper via system > admin> wireless adapters and installed the xp driver. This is seen and I can configure the card ip etc. It looks as if it has connected but only shows 1mb and no traffic.

from ifconfig 
wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:4d:96:91
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe4d:9691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:e8200000-e8200800
from iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can someone point me in the right direction as this is doing my head in.
p.s I have also remove all encyrption from wireless to see if that is the issue. To no avail...

Many thanks Willie

---

### Post by williebear on 2008-06-15
i guess, no-one has had this issue?
ill keep trying today, if no joy i will update and prob head back to windows...only because there is no reason for having a laptop without wireless capability...:(

---

### Post by rlzyoner on 2008-06-15
Open a terminal and type
*ndiswrapper -l*
This will list the drivers that ndiswrapper are currently using.
Ensure that the windows wireless driver is there

*modprobe ndiswrapper * (This loads the driver)

*ndiswrapper -m *

Now try to connect again and see how that goes

---

### Post by williebear on 2008-06-16
Hi I tried this all ok..but last part stated alias already there. I also reinstalled , this worked then on reboot same. Any ideas?

---

### Post by kuric on 2011-04-26
Old thread, but hey...

$ sudo apt-get install build-essential ndiswrapper-utils-1.9

$ wget [http://www.edbl.no/karmic/acerhk-fixed.tar.bz2](http://www.edbl.no/karmic/acerhk-fixed.tar.bz2)

$ sudo gedit /usr/src/linux-headers-2.6.35-22/Makefile

Find and comment the KBUILD line, like this, and save:
ifdef CONFIG_FUNCTION_TRACER
# KBUILD_CFLAGS	+= -pg
endif

$ tar -xvjf acerhk-fixed.tar.bz2 
$ cd acerhk-0.5.35/
$ make 
$ sudo make install 

$ sudo gedit /usr/src/linux-headers-2.6.35-22/Makefile

Dont' forget to uncomment the KBUILD line.

$ sudo /sbin/modprobe acerhk autowlan=1
$ echo 0 > /proc/driver/acerhk/wirelessled
$ echo 1 > /proc/driver/acerhk/wirelessled

$ sudo gedit /etc/modules
Add this line:
acerhk

$ sudo gedit /etc/modprobe.d/acerhk.conf
Write this and save:
options acerhk autowlan=1

Now, google for Wireless(80211BG)_Acer_2.23.08.2004_XPx86
Download Wireless(80211BG)_Acer_2.23.08.2004_XPx86.zip to your /home/username folder and extract files.

$ cd Wireless(80211BG)_Acer_2.23.08.2004_XPx86
$ cd Winxp
$ sudo ndiswrapper -i neti2220.inf
$ sudo modprobe ndiswrapper
$ sudo ifup wlan0
$ sudo ndiswrapper -m
$ ndiswrapper -l
$ sudo modprobe ndiswrapper

$ sudo gedit /etc/network/interfaces 
Add this line:
wlan0 

$ sudo su
$ echo "ndiswrapper" >> /etc/modules
$ exit

So you thaught it was easy, hum? Reboot and turn on your wi-fi, right and left-clicking in the network-manager icon ;)

---

