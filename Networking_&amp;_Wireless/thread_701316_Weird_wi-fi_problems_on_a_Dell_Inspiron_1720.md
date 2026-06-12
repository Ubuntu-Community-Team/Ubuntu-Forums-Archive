---
title: "Weird wi-fi problems on a Dell Inspiron 1720"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by kongle on 2008-02-19
We have a really frustrating problem with the wireless network functionality on our Dell Inspiron 1720, running Gutsy, It seems like the wireless network card is called "Intel Pro/Wireless 3945 802.11 a/g Mini Card Wireless".

Basically, seemingly at random, the the wireless functionality turns off. The wi-fi LED on the box starts blinking, and the wi-fi software (WIcd, which I installed at some point while trying to solve the problem) consequently can do nothing. Actually, it also stops working completely after some playing around with it. :)

It seems like I can get the wi-fi up and running again only by restarting the computer, and even then, very often, the same problem is there from the beginning. Multiple restarts may be required. After everything from a few minutes to many hours of use, wi-fi will once again drop out of function.

Any clues? I tried searching, but I did not find any similar problem descriptions.

Many thanks in advance. :)

---

### Post by jan quark on 2008-02-19
please post some info

run these commands in terminal and post the output

```
iwconfig
```

```
ifconfig
```
```

sudo iwlist scan
```

```
sudo lshw -C network
```

---

### Post by kongle on 2008-02-19
Thank you. :) The commands were run when wi-fi is working, of course. I dunno if it would be interesting for you if I ran some of them when wi-fi is out of function as well.

```
rh@tore2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Riise Hamre"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:41:D1:32   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-65 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:169   Missed beacon:0
```

```
rh@tore2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:7E:96:7A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:67:7C:0F  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe67:7c0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11455 errors:0 dropped:170 overruns:0 frame:0
          TX packets:7618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9080939 (8.6 MB)  TX bytes:1384723 (1.3 MB)
          Interrupt:17 Base address:0xe000 Memory:f9fff000-f9ffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
rh@tore2:~$ sudo iwlist scan
[sudo] password for rh:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:41:D1:32
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=73/100  Signal level=-61 dBm  Noise level=-61 dBm
                    Extra: Last beacon: 8ms ago
```

```
rh@tore2:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:67:7c:0f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.0.103 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:7e:96:7a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
```

There you go. Thank you again.

---

### Post by Hightide on 2008-02-19
HI Kongle

See if  this [thread]("http://ubuntuforums.org/archive/index.php/t-653503.html") is relevant

regards

:)

---

### Post by kongle on 2008-02-19
Thank you, Hightide, but I don't think it is. It appears that the solution was the wireless switch on his laptop. I tried the one on mine, but it appears not to work.

Anyway, I was thinking, maybe this problem is hard to fix, but this problem wouldn't be too much of a problem if there would be some way around that of rebooting the computer all the time. There must be another way, or what? Can I completely deactivate network functionality in Ubuntu, and then reactivate it again, for instance? Any clues what could be an alternative way to regain wireless connection, apart from rebooting?

---

### Post by jonas meyer on 2008-02-20
I am having the exact same issue on the same machine.  So either dell sent out a bad batch of cards, or there is a software issue of some sort with the drivers.  I thought I might just have a bad wireless card, but that seems much less likely now.  Please help us!

---

### Post by rustybronco on 2008-02-20
> **kongle said:**
> Thank you. :) T

```
rh@tore2:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:67:7c:0f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**ipw3945** driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.0.103 latency=0 link=yes module=**ipw3945** multicast=yes wireless=IEEE 802.11g
```
  
There you go. Thank you again.
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)
[https://bugs.launchpad.net/ipw3945/+bug/109887](https://bugs.launchpad.net/ipw3945/+bug/109887)

 possibly you could upgrade to the iwl3945 drivers and try that.   [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045)

***edit***was it the 64bit install?

---

### Post by jonas meyer on 2008-02-21
Those links are very relevant.  Thanks!

I have noticed the errors associated with this bug

[https://bugs.launchpad.net/ipw3945/+bug/109887](https://bugs.launchpad.net/ipw3945/+bug/109887)

in my console when I had this error.  It seems to have a very small chance of happening on each packet, as described there, because I see it more often when I am streaming movies from my htpc or playing games online.  I will attempt to replace ipw3945 with iwl4965 and report back about success.

---

### Post by jonas meyer on 2008-02-21
Sadly, attempting to use modprobe to install iwl3945 or iwl4965 resulted in a "symbol not found" error.  Looks like I am stuck with ipw for now unless someone comes up with a new solution.

---

### Post by rustybronco on 2008-02-21
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by jonas meyer on 2008-02-21
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I'm not really sure what to do with this.  I already tried to install the driver using modprobe.  Can you at least link to a howto?

---

### Post by rustybronco on 2008-02-24
> **jonas meyer said:**
> [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I'm not really sure what to do with this. Can you at least link to a howto?
Sure can, [http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi)

had sporatic internet for a day and a half because of a change over to comcast (not their problem ), sorry taking so long to get back to you.

---

### Post by jonas meyer on 2008-02-25
Sadly, during the "make" process, I got all sorts of compile errors in the code.  I installed the kernel-source package, and even figured out how to point the make at the right spot on ubuntu, but I draw the line at debugging the driver itself.  I guess I'll just have to live with it until someone produces a compiled iwl driver that I can install with dpkg.  Will iwl be included by default in hardy?

---

### Post by rustybronco on 2008-02-25
Is not the iwl3945 driver in 7.10 also?

Just so you know you are not alone [http://forum.notebookreview.com/showthread.php?t=164795](http://forum.notebookreview.com/showthread.php?t=164795) look through it,  it may help getting the correct windows drivers to try with ndiswrapper.

reading material...
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)  not the same model, but.
[http://www.linlap.com/wiki/Dell+Inspiron+1720](http://www.linlap.com/wiki/Dell+Inspiron+1720)
> Wireless	Yes	Use the iwl3945 driver

EDIT*** looks like the iwl3945 started with the 2.6.23-kernel
feeling your oats? like trying new things? don't mind "CRASHES" and the reinstalls that come with it? [http://ubuntuforums.org/showpost.php?p=3993033&postcount=1](http://ubuntuforums.org/showpost.php?p=3993033&postcount=1)
(Thats why I keep a few spare hard drives around.)

---

### Post by jonas meyer on 2008-02-29
Thanks!  I must admit I am afraid to upgrade my kernel to the hardy heron version because of the problems that were reported with disk encryption, which I use on both my drives.  Otherwise, I'd totally be down for that kind of experimentation.  I think I'll wait a couple weeks (for some of the nastier bugs in launchpad to settle out) and then just reinstall with hardy.  Then I should be able to get this fixed.  I really appreciate all the help you've given.  Right now, this error is just kind of annoying for me, and not really a show stopper, but hopefully our conversation has been helpful to other members of the community.

> **rustybronco said:**
> Is not the iwl3945 driver in 7.10 also?

Just so you know you are not alone [http://forum.notebookreview.com/showthread.php?t=164795](http://forum.notebookreview.com/showthread.php?t=164795) look through it,  it may help getting the correct windows drivers to try with ndiswrapper.

reading material...
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)  not the same model, but.
[http://www.linlap.com/wiki/Dell+Inspiron+1720](http://www.linlap.com/wiki/Dell+Inspiron+1720)


EDIT*** looks like the iwl3945 started with the 2.6.23-kernel
feeling your oats? like trying new things? don't mind "CRASHES" and the reinstalls that come with it? [http://ubuntuforums.org/showpost.php?p=3993033&postcount=1](http://ubuntuforums.org/showpost.php?p=3993033&postcount=1)
(Thats why I keep a few spare hard drives around.)

---

### Post by heldal on 2008-03-02
> **rustybronco said:**
> [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

If it only was that simple. Sadly it involves a kernel rebuild as bits of the wireless API has changed. The iwlwifi drivers in gutsy were barely alpha quality. 

This illustrates the biggest issue people have with ubuntu, that very few bugs are dealt with between main releases. Hardly any bugs are fixed unless they are security related. With 7.04 a simple packaging error (a missing file) left users with the latest nvidia-cards in the cold. Now 7.10 leaves most users with intel wireless-cards in limbo. The problems were identified early on so it should have been quite easy to include more recent versions of the iwlwifi drivers and tools with one of the kernel+modules updates which have been issued for 7.10. It seems the ubuntu-project lacks a mechanism to identify and deal with problems that affect large groups of users.

---

