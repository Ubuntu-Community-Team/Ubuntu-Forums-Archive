---
title: "Wireless not connecting?"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by greyloki on 2008-08-06
Hi folks, I have a bit of a weird problem with my wireless connections on two machines.

What's happening is that i'm trying to connect to a wireless network (my home one, which i've tried with and without encryption - makes no difference), and though wicd or wlassistant or network-manager all show my network, I just can't connect to them. Checking the output of the terminal after running /opt/wicd/gui.py from within it seems to show that i'm not getting an IP address, but even when I give myself one (192.168.1.234), I don't get any internet access.

This all happens with the latest kernel - on my laptop I can go back to kernel version 2.4.20-16 using grub and wireless works fine, but as soon as I move up to the latest install on my laptop, it (wireless) just refuses to work.

My desktop machine I suspect may have the same problem (since i'm using the same USB wireless adapter between the two of them), but I can't confirm it because my display drivers go very odd if I try and login with anything but the latest kernel.

Here's a pastebin of the usual suspects taken from my desktop machine (which is more important to be wireless, since everyone else in the house seems to object to trailing lengths of Cat5...):

[http://pastebin.ubuntu.com/34837/](http://pastebin.ubuntu.com/34837/)

I'm using an Asus WL-167g USB wireless adapter which I believe uses the rt2500 series of drivers.

Thanks in advance for any help :)

---

### Post by pytheas22 on 2008-08-06
First of all, what are eth1 and eth2 (and why don't you have eth0)?  Are they both wired ethernet?

That aside, wlan1 does appear to be functioning correctly insofar as it seems to be able to associate with your network.  Does this command get you an IP:
```

sudo dhclient wlan1
```

If that doesn't help, please post the output of these commands so that we can confirm which driver you're using.  It could very well be the case that there's just a bug with the latest release of the driver:
```

lshw -C Network
lsusb
lspci -nn
```

---

### Post by greyloki on 2008-08-06
eth1 and eth2 are the two wired network adapters in my motherboard (an Asus board with an nVidia chipset that gives me two ethernet ports instead of the usual one) - I have no idea at all why I don't have an eth0 (or a wlan0, for that matter).

Here's the output of sudo dhclient wlan1, run after Wicd had tried to connect. I see from looking at the last line that it's saying it has received no DHCP offers, which is odd - in windows, the same USB adapter works fine on exactly the same network.

```
craig@craigsdesktop:~$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:11:2f:6b:e9:70
Sending on   LPF/wlan1/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Output from lshw -C Network (and sudo lshw -C Network):

```
craig@craigsdesktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:11:2f:6b:e9:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
craig@craigsdesktop:~$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:2f:6b:e9:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

Output from lsusb:

```
craig@craigsdesktop:~$ lsusb
Bus 002 Device 005: ID 0b05:1706 ASUSTek Computer, Inc. WL-167G 802.11g Adapter [ralink]
Bus 002 Device 002: ID 0d49:3200 Maxtor 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:092e Logitech, Inc. 
Bus 001 Device 004: ID 0dba:3000  
Bus 001 Device 001: ID 0000:0000  
craig@craigsdesktop:~$ 
```

Output from lspci -nn:

```
craig@craigsdesktop:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:06.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b9] (rev a1)
00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:0f.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:12.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:13.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a3)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a3)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a3)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a3)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a3)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GT] [10de:0391] (rev a1)
04:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)
craig@craigsdesktop:~$ 
```

---

### Post by pytheas22 on 2008-08-06
There do seem to be some strange things going on--for instance, I don't know why "lshw -C Network" only mentions your wireless device, not the ethernet as well.  Normally it should mention all detected devices, whether they're currently in use or not.

Anyway, since you do indeed have a Ralink card, one solution would be to compile the legacy Ralink drivers to replace the mac80211 ones (the ones that come by default in Ubuntu), which seem to be broken.  The legacy drivers work just as well as the newer ones and tend to be more reliable.  If you want to install the legacy driver for your card, run these commands (make sure you have a wired connection first):

```
sudo apt-get install rutilt build-essential
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -xzvf rt2570*
cd rt2570*/Module
make
sudo make install
sudo -s
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

This should fix the wireless.  An important point to note is that you'll no longer be able to use Network Manager to connect; you'll have to use Rutilt, which will be available under System>Administration>Rutilt Wireless Manager.

This will leave your mac80211 drivers intact--they'll just be blacklisted and ignored by the system--so you can easily switch back to them when you want, if the issue with the broken driver gets fixed later.

---

### Post by jkid on 2008-08-06
check your firewall if you have one .......

---

### Post by greyloki on 2008-08-06
pytheas22,

I ran the commands as illustrated in your code box - it seems that it installed succesfully (at least, no errors were generated either while I was compiling them or blacklisting the rt2500 ones), along with rutilt.

However, when I run rutilt (or sudo rutilt), I can't poll for wireless networks - it seems to start to, but before any networks appear the application seems to crash - the graphical window itself greys out and a dialogue box appears telling me the application has crashed and I have the option of cancelling or force quitting. Running from the terminal gives no information at all apart from 'Killed' when I force quit rutilt.

Creating a profile with the settings I know are correct (and DHCP IP settings) and applying that, bypassing entirely the 'scanning for networks' stage doesn't seem to work - I click 'apply', and the utility seems to 'just sit there' - no console output, no disk activity, no wireless activity from the USB adapter's status light, either.

jkid - do you mean a software firewall? If so, I don't think I have one installed - if I did, would the difference between wireless and wired connections make a difference to it? I'm writing this post on the machine in question through a cable, you see.

Thanks for your help so far, guys :)

---

### Post by pytheas22 on 2008-08-06
hmmm, I'm not sure what's going on Rutilt.  Could you please post the output of:
```

lsmod | grep rt
```

so that we can be sure it's using the correct driver?  Also, try rebooting your computer and see if that helps (you should have done this after compiling the new driver; sorry for forgetting to mention it in my instructions).

---

### Post by greyloki on 2008-08-06
Here's the output of lsmod | grep rt run after a full system restart:

```
craig@craigsdesktop:~$ lsmod | grep rt
exportfs                6016  1 nfsd
parport_pc             36260  0 
parport                37832  3 ppdev,parport_pc,lp
agpgart                34760  1 nvidia
craig@craigsdesktop:~$ 

```

However, though rtutil used to run before I restarted, after restarting it now tells me that it cannot find any wireless device at all.

ifconfig and iwconfig:

```
craig@craigsdesktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:60:b1:89:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 

eth2      Link encap:Ethernet  HWaddr 00:1d:60:b1:84:a8  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb1:84a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:747312 (729.7 KB)  TX bytes:163382 (159.5 KB)
          Interrupt:213 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1d:60:b1:89:c1  
          inet addr:169.254.8.218  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:214 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6048 (5.9 KB)  TX bytes:6048 (5.9 KB)

craig@craigsdesktop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      no wireless extensions.

craig@craigsdesktop:~$ 

```

lsusb:

```
craig@craigsdesktop:~$ lsusb
Bus 001 Device 005: ID 0b05:1706 ASUSTek Computer, Inc. WL-167G 802.11g Adapter [ralink]
Bus 001 Device 002: ID 0d49:3200 Maxtor 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:092e Logitech, Inc. 
Bus 002 Device 002: ID 0dba:3000  
Bus 002 Device 001: ID 0000:0000  
craig@craigsdesktop:~$ 

```

---

### Post by pytheas22 on 2008-08-06
It seems that the new driver that you compiled isn't loaded.  Does the wireless appear if you run these commands:
```

sudo modprobe rt2570
sudo ifconfig wlan0 up
```

Wait a few seconds and see if you can run Rutilt then.  If it still doesn't work, it could be the case that I had you compile the wrong driver (there are two options for Ralink legacy USB drivers and it's hard to tell which one should be used for which card), and installing the other one would fix the problem--but I'm pretty sure that it was the right choice, based on what I read.

---

### Post by greyloki on 2008-08-07
Here are the results of those commands:

```
craig@craigsdesktop:~$ sudo modprobe rt2570
[sudo] password for craig: 
FATAL: Module rt2570 not found.
craig@craigsdesktop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
craig@craigsdesktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:60:b1:89:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 

eth2      Link encap:Ethernet  HWaddr 00:1d:60:b1:84:a8  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb1:84a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480420434 (458.1 MB)  TX bytes:14536392 (13.8 MB)
          Interrupt:213 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1d:60:b1:89:c1  
          inet addr:169.254.8.218  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:214 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8748 (8.5 KB)  TX bytes:8748 (8.5 KB)

craig@craigsdesktop:~$ 

```

I see that Asus have a linux driver for this adapter listed on their support website - would it be worth trying that at some point? From what I remember, the WL-167g 'just worked' when I plugged it into my machines at 6.04 and 7.10.

EDIT: Though it's not really relevant, what is 'eth1:avahi'? I know it sounds kind of odd, but i've never seen it there until recently - same goes for wmaster0 (when it showed up in iwconfig earlier).

---

### Post by pytheas22 on 2008-08-07
> EDIT: Though it's not really relevant, what is 'eth1:avahi'? I know it sounds kind of odd, but i've never seen it there until recently - same goes for wmaster0 (when it showed up in iwconfig earlier).

As I understand it, wmaster is a physical interface, while wlan0 is the virtual interface that operates on it--the new Ralink drivers work on this model, instead of just creating one interface in iwconfig per device.  I think that eth1:avahi is the same idea.  I don't know all of the details, but it's supposed to be this way, so don't worry.
> 
I see that Asus have a linux driver for this adapter listed on their support website - would it be worth trying that at some point? From what I remember, the WL-167g 'just worked' when I plugged it into my machines at 6.04 and 7.10.

Their driver is probably mostly the same as the one that you already tried to compile.  Ralink released drivers under the GPL a few years ago, and that's probably the code that Asus has on its website.  The driver that I'm trying to have you compile (from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)) is based on the same code but is a little better (more features, support for 64-bit), so I'd stick with that for now.

As for your wireless still not working, it looks like the new driver didn't get compiled or installed correctly for some reason.  Please try running the following code again and post the output so that we can check to make sure the new driver is being built properly:
```

wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
tar -xzvf rt2570*
cd rt2570*/Module
make
sudo make install
sudo modprobe rt2570
```

---

### Post by greyloki on 2008-08-07
Here we are:

```
craig@craigsdesktop:~$ cd Desktop/
craig@craigsdesktop:~/Desktop$ wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
--20:30:23--  http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
           => `rt2570-cvs-daily.tar.gz'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,734 (261K) [application/x-gzip]

100%[====================================>] 267,734      277.80K/s             

20:30:25 (277.06 KB/s) - `rt2570-cvs-daily.tar.gz' saved [267734/267734]

craig@craigsdesktop:~/Desktop$ tar -xvzf rt25
rt2500-cvs-2008080614/   rt2500-cvs-daily.tar.gz  rt2570-cvs-daily.tar.gz
craig@craigsdesktop:~/Desktop$ tar -xvzf rt2570-cvs-daily.tar.gz 
rt2570-cvs-2008080713/
rt2570-cvs-2008080713/FAQ
rt2570-cvs-2008080713/THANKS
rt2570-cvs-2008080713/CHANGELOG
rt2570-cvs-2008080713/CVS/
rt2570-cvs-2008080713/CVS/Root
rt2570-cvs-2008080713/CVS/Repository
rt2570-cvs-2008080713/CVS/Entries.Log
rt2570-cvs-2008080713/CVS/Entries
rt2570-cvs-2008080713/LICENSE
rt2570-cvs-2008080713/Module/
rt2570-cvs-2008080713/Module/auth.c
rt2570-cvs-2008080713/Module/rt2x00debug.h
rt2570-cvs-2008080713/Module/md5.c
rt2570-cvs-2008080713/Module/rtusb_data.c
rt2570-cvs-2008080713/Module/rtusb_info.c
rt2570-cvs-2008080713/Module/rtmp_ckipmic.h
rt2570-cvs-2008080713/Module/rt_config.h
rt2570-cvs-2008080713/Module/assoc.c
rt2570-cvs-2008080713/Module/CVS/
rt2570-cvs-2008080713/Module/CVS/Root
rt2570-cvs-2008080713/Module/CVS/Repository
rt2570-cvs-2008080713/Module/CVS/Entries
rt2570-cvs-2008080713/Module/rt2570sw.h
rt2570-cvs-2008080713/Module/wpa.c
rt2570-cvs-2008080713/Module/sync.c
rt2570-cvs-2008080713/Module/iwpriv_usage.txt
rt2570-cvs-2008080713/Module/rtusb_bulk.c
rt2570-cvs-2008080713/Module/mlme.h
rt2570-cvs-2008080713/Module/connect.c
rt2570-cvs-2008080713/Module/rtmp_tkip.c
rt2570-cvs-2008080713/Module/auth_rsp.c
rt2570-cvs-2008080713/Module/oid.h
rt2570-cvs-2008080713/Module/rtusb_init.c
rt2570-cvs-2008080713/Module/TESTING
rt2570-cvs-2008080713/Module/rt2570.h
rt2570-cvs-2008080713/Module/rtusb_io.c
rt2570-cvs-2008080713/Module/sha1.h
rt2570-cvs-2008080713/Module/mlme.c
rt2570-cvs-2008080713/Module/rtusb_main.c
rt2570-cvs-2008080713/Module/md5.h
rt2570-cvs-2008080713/Module/rtusb.h
rt2570-cvs-2008080713/Module/wpa.h
rt2570-cvs-2008080713/Module/rtmp_wep.c
rt2570-cvs-2008080713/Module/rtmp_def.h
rt2570-cvs-2008080713/Module/Makefile
rt2570-cvs-2008080713/Module/rtmp_type.h
rt2570-cvs-2008080713/Module/rt2x00debug.c
rt2570-cvs-2008080713/Module/sanity.c
rt2570-cvs-2008080713/README
craig@craigsdesktop:~/Desktop$ cd rt2570-cvs-2008080713/
craig@craigsdesktop:~/Desktop/rt2570-cvs-2008080713$ cd Module/
craig@craigsdesktop:~/Desktop/rt2570-cvs-2008080713/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_main.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/mlme.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_bulk.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/connect.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/sync.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_init.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtmp_tkip.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/wpa.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtmp_wep.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_info.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/assoc.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/auth.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/auth_rsp.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/md5.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_io.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/sanity.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rtusb_data.o
  CC [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rt2x00debug.o
  LD [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rt2570.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/craig/Desktop/rt2570-cvs-2008080713/Module/rt2570.mod.o
  LD [M]  /home/craig/Desktop/rt2570-cvs-2008080713/Module/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
craig@craigsdesktop:~/Desktop/rt2570-cvs-2008080713/Module$ sudo make install
[sudo] password for craig: 
2.6 module install
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/craig/Desktop/rt2570-cvs-2008080713/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  INSTALL /home/craig/Desktop/rt2570-cvs-2008080713/Module/rt2570.ko
  DEPMOD  2.6.24-18-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
craig@craigsdesktop:~/Desktop/rt2570-cvs-2008080713/Module$ sudo modprobe rt2570
craig@craigsdesktop:~/Desktop/rt2570-cvs-2008080713/Module$ 
```

---

### Post by pytheas22 on 2008-08-07
Alright, that all looks good.  If you run:
```

sudo modprobe rt2570
sudo ifconfig rausb0 up
sudo rutilt
```

you should be able to connect.  Yes?

---

### Post by greyloki on 2008-08-07
I wasn't able to connect with WEP encryption enabled, but once I disabled that I was seemingly able to get a DHCP lease from my router - however, ping shows that I can't even access my router's config page (nor through my browser), and normal webpages also don't work.

Console Output (first two tries with WEP):

```
craig@craigsdesktop:~$ sudo ifconfig rausb0 up
craig@craigsdesktop:~$ sudo rutilt
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:2f:6b:e9:70
Sending on   LPF/rausb0/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
craig@craigsdesktop:~$ There is already a pid file /var/run/dhclient.pid with pid 13315
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:2f:6b:e9:70
Sending on   LPF/rausb0/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.pid with pid 13341
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:2f:6b:e9:70
Sending on   LPF/rausb0/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.pid with pid 13365
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:2f:6b:e9:70
Sending on   LPF/rausb0/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.71 from 192.168.1.254
DHCPREQUEST of 192.168.1.71 on rausb0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.71 from 192.168.1.254
bound to 192.168.1.71 -- renewal in 41343 seconds.

craig@craigsdesktop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.66 icmp_seq=1 Destination Host Unreachable
From 192.168.1.66 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.254 ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3015ms

craig@craigsdesktop:~$ 
```

EDIT: The 'system tray' icon of rutilt, and its 'Statistics' tab both show that i'm connected to my network with a link quality of around 70% (-60ish dBm signal, and -80ish dBm noise).

---

### Post by pytheas22 on 2008-08-07
That's weird.  I've never had a problem with the rt2570 driver before.  Did you try rebooting to see if it helps?  Also, what are the contents of /etc/resolv.conf after you get an IP from the router?

---

### Post by greyloki on 2008-08-10
I'm sorry for not responding to this thread sooner - Real Life got in the way, as it has a habit of doing :P

I'm actually posting this from my desktop - for some reason (i'm guessing the restart), I was able to connect properly using rutilt - here are the outputs of both the rutilt command and my /etc/resolv.conf, for future reference:

sudo rutilt:

```
craig@craigsdesktop:~$ There is already a pid file /var/run/dhclient.pid with pid 6638
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:2f:6b:e9:70
Sending on   LPF/rausb0/00:11:2f:6b:e9:70
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.71 from 192.168.1.254
DHCPREQUEST of 192.168.1.71 on rausb0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.71 from 192.168.1.254
bound to 192.168.1.71 -- renewal in 39522 seconds.
```

/etc/resolv.conf:

```
search home
nameserver 192.168.1.254
```

Thank you very much for all your help, pytheas22 :)

---

### Post by pytheas22 on 2008-08-10
I'm glad that's finally solved, and sorry it ended up being more complicated than I originally thought.

Just so you know, if you ever want to revert to the original drivers that you were using (which seem to have been broken by a bad update but will hopefully be fixed by a future update), open up the blacklist:
```

sudo gedit /etc/modprobe.d/blacklist
```

and put a # in front of all of the lines from "blacklist rt2500usb" to "blacklist rt2x00usb," inclusive (a # tells the system to ignore that line).  Then add:
```

blacklist rt2570
```

to the blacklist, and save it.  After a reboot, you should be using the original drivers again, which have the advantage of working with Network Manager instead of relying on Rutilt.

If you find that the original drivers are still broken, remove the #'s from the appropriate lines in the blacklist, and unblacklist rt2570.

If you run into more trouble let me know; otherwise enjoy Ubuntu!

---

