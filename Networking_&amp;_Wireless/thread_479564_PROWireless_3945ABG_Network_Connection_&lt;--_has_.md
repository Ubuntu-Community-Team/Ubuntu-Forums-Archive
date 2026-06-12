---
title: "PRO/Wireless 3945ABG Network Connection &lt;-- has anyone gotten this card to work!!"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by zachflanders on 2007-06-20
For the life of me I cannot get my wireless to work.  I have tried a million fixes on a million threads an nothing seems to work!

Information:
I am running ubuntu studio.
I had to install pptpd and pptp-linux to connect to my wired connection in my dorm, and I have to run the following every time i want to connect to the internet:

chmod 755 vpn.sh
sudo ./vpn.sh start

Here is some more information for yall:

```
zach@zach:~$ lsmod | grep ipw
ipw3945               118944  1 
ieee80211              50924  1 ipw3945
zach@zach:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d6000000-d6000fff irq:17
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:71:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.67.231 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d8000000-d8000fff ioport:4000-403f irq:21
zach@zach:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:AF:71:5C  
          inet addr:192.168.67.231  Bcast:192.168.71.255  Mask:255.255.248.0
          inet6 addr: 2001:638:407:1e:216:36ff:feaf:715c/64 Scope:Global
          inet6 addr: fe80::216:36ff:feaf:715c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4247973 (4.0 MiB)  TX bytes:581022 (567.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63120 (61.6 KiB)  TX bytes:63120 (61.6 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:212.201.73.174  P-t-P:192.168.1.31  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:2904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2985704 (2.8 MiB)  TX bytes:392933 (383.7 KiB)

zach@zach:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

gre0      no wireless extensions.

ppp0      no wireless extensions.

```

related thread in the absolute beginner's forum : [here]("http://ubuntuforums.org/showthread.php?t=477809&highlight=Intel+Corporation+PRO%2FWireless+3945ABG+Network+Connection")

---

### Post by S15_88 on 2007-06-20
shoot sorry i misread your card # i thought u had a 4XXX and they aren't supported, check the supported card list because if yours isn't supported u'll have to use NDISwrapper.

---

### Post by chili555 on 2007-06-20
> has anyone gotten this card to work!!Absolutely! Answering from mine now.

It should be as easy as:```
sudo iwlist eth1 scan
```You should get a result like this:```
 Cell 01 - Address: 99:9C:41:19:58:77
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=81/100  Signal level=-53 dBm  Noise level=-53 dBm
                    Extra: Last beacon: 112ms ago
```Then you can do:```
sudo iwconfig eth1 essid myrouter1
sudo dhclient eth1
```Assuming there is no encryption, you should connect.

---

### Post by zachflanders on 2007-06-20
OK, i tired the iwlist thing, but it didn't work

```
zach@zach:~$ sudo iwlist eth1 scan
Password:
eth1      Interface doesn't support scanning.

```

The card is on the supported cards list (under Intel), I don't know why so many people are having problems with it.

I also installed the linux-image-2.6.20-16-lowlatency package as suggested [here]("http://ubuntuforums.org/showthread.php?t=457470&highlight=3945abg"), and rebooted, but no dice.

I think some key clues might be that the network controller has no logical name when i run lshw -C network, and the output from iwconfig looks very interesting to me ... but i don't really know anything.

---

### Post by cadnr on 2007-10-20
Hi,

I Just dist-upgraded from Dapper to Edgy then to Feisty and my 3945ABG stopped working after the upgrade to Edgy.

I have the same problem as you; no logical name under lshw -C network.

I can make the wireless work however by running 'sudo /sbin/ipw3945d-2.6.15-23-686'.  You would need to change the numbers at the end to match your kernel version I think.

I don't know why this script fails at startup.

Good luck.

---

### Post by elmopuck on 2007-10-21
Thanks in advance for helping a Ubuntu newbie.  I performed a fresh install of Gutsy Gibbon on a Dell Inspiron 6400.  Out of the gate, I have a wired connection, but no wireless.  The wireless connection does not appear in the Network Manager.  However, I have confirmed the following details:

```

matt@soprano-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:16:44:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=158.122.22.4 latency=64 module=b44 multicast=yes

```

Note that I do not have a [COLOR="Red"]Logical Name[/COLOR]

```

matt@soprano-laptop:~$ sudo lsmod | grep ipw3945

ipw3945               119840  1 

ieee80211              35656  1 ipw3945
```

I also tried one of the suggestions from this thread:

[HTML]matt@soprano-laptop:~$ uname -r 2.6.22-14-generic
matt@soprano-laptop:~$ sudo /sbin/ipw3945d-2.6.22-14-generic
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-10-21 18:03:02: ERROR: ipw3945d already running.  If ipw3945d is not running then you need to remove '/var/run/ipw3945d.pid' and try again.[/HTML]

I don't really know how to interpret the output from that last command -- I have tried to follow as many How-To's as I could find, but most of them stop after confirming that a driver is present and accounted for.  Could someone point me toward the right resource?

---

### Post by StevenHarper on 2007-10-21
Yes I have the same chipset in my laptop, its a known problem in GUTSY

I imagine it will be fixed soon,

However ONLY the WEP is broken, WPA and no encryption both work

Steve

---

### Post by raul_ on 2007-10-21
It's working here with Arch Linux. I'm using the ipw3945 module, i don't know if that helps.

Just in case, try a "sudo modprobe ipw3945" and "sudo ifconfig eth1 up"

---

### Post by Buffalo Soldier on 2007-10-21
Been working since gutsy tribe 5. the only problem it has is when waking up from suspend. besides that it's been flawless, even with WPA.

I guess maybe it's the ubuntu-studio kernel you're using.

---

### Post by elmopuck on 2007-10-21
Thanks for the responses.  I have tried Raul's suggestions above to no avail.  A key difference between many of the suggestions I find and the situation in which I find myself is the absence of a "Logical Name" in the Network Controller description.

Would someone explain to me why there would be no "Logical Name"?

Also, I've found some threads on other boards which suggest trying [WICD]("http://wicd.sourceforge.net/").  Is this a worthwhile angle to pursue?

---

### Post by raul_ on 2007-10-22
Last suggestion: try getting it to work with ndiswrapper. Probably it'll be called wlan0. If you need help with ndiswrapper let me know ;)

---

### Post by BC7333 on 2007-10-22
> **elmopuck said:**
> Thanks for the responses.  I have tried Raul's suggestions above to no avail.  A key difference between many of the suggestions I find and the situation in which I find myself is the absence of a "Logical Name" in the Network Controller description.

Would someone explain to me why there would be no "Logical Name"?

Also, I've found some threads on other boards which suggest trying [WICD]("http://wicd.sourceforge.net/").  Is this a worthwhile angle to pursue?


With Feisty, either WICD or WIFI radar worked pretty well..  Now upgraded to Gutsy and works really fine with standard network manager.  Only slight 'hitch' to get it working here with 3945abg.. [http://ubuntuforums.org/showthread.php?p=3577954#post3577954](http://ubuntuforums.org/showthread.php?p=3577954#post3577954)  This link may also address your logical name problem.

with each kernel upgrade wifi seemed to work better..

---

### Post by raul_ on 2007-10-22
I now changed to the iwlwifi driver and it's working even better. Try that module. You have to do a tweak in /etc/modprobe.conf , but I can't really help you specifically 'cause I'm using a different distribution. Anyway, ndiswrapper shoud work fine.

---

### Post by Zorael on 2007-10-22
Never got it to work, not in Feisty nor in Gutsy.

And to further explain: I've had TWO 3945abg cards,** one that worked out of the box**, and this one that just don't. It works in Windows.

I believe there are two versions of the cards - two revisions, if you will - and one of them is very, very incompatible with both the ipw3945 and the iwl3945 modules. People are having different problems, though - mine dies on me and can't detect networks, while spamming Detected Geography messages in dmesg. Yours seem to not have any wireless extensions.

And, since some get it to work with no effort, it's mostly scratched off as user error. In other words, "mine doesn't work at all, tried everything" versus "mine works flawlessly, no problems at all, have you tried turning it off and on again", to paraphrase myself from another post. Since I've had two cards, I *know* there's more to it than that.

I'm apparently not apt enough to get any of the latest nonstable modules to compile (always ending up in some error I can't interpret), so I'm eagerly awaiting that driver installer script I remember reading about some month ago.

---

### Post by elmopuck on 2007-10-22
OK.  I am trying to use NDISWRAPPER, but I am not sure how to interpret this list on sourcefourge:

[FONT="Courier New"][COLOR="Navy"]Card: Intel PRO/Wireless 3945ABG
   [LIST]
[*]Driver: version 11.1.1.0 driver netw4v32.inf (from the intel web site) seemed to work fine but it turned out to be a dud. The Dell driver for the Dell Latitude D630 ([http://ftp.us.dell.com/network/R164255.EXE](http://ftp.us.dell.com/network/R164255.EXE)) also has netw4v32.inf and this one worked on my Dell Latitude D630 - go figure.
[*]Other: both drivers were evaluated on debian etch - wpa_supplicant didn’t seem to work, even with the Dell driver but WEP worked
[*]pciid: 8086:4222
[*]Driver: version 10.1.0.13 [http://www.intel.com/support/wireless/wlan/sb/cs-010623.htm](http://www.intel.com/support/wireless/wlan/sb/cs-010623.htm) (w39n51.inf, unfortunatly the download is 80MB because it’s packaged with “Intel PROset/Wireless software”, and drivers for the 2200BG and 2915ABG).
[*]Other: Tested on Gentoo Linux, with gentoo patched kernel 2.6.15-r1 (SMP hasn’t been tested yet, I had some problems with it, so reverted to non-SMP). You need to patch your kernel to use 16K Stacks (rather than the default 8K). Patches can be found via LinuxAnt. I found mine at [http://www.linuxant.com/driverloader/wlan/downloads-patches.php](http://www.linuxant.com/driverloader/wlan/downloads-patches.php)
[/LIST][/COLOR][/FONT]

Does that mean I should try the Dell download (a 59MB .exe) and execute it?

I have an Inspiron 6400 with the Intel PRO/Wireless 3945ABG (pciid: 8086:4222).

---

### Post by jai.vikram on 2007-12-04
guys m a newbie...and i got this thing working at foss.in 07 ....thanks to avi who did it...this is summarily what he did..or what i understood...
I am using gutsy gibbon
this usually happens when u dont have a network manager installed and the machine is not able to switch between the wired and wireless and at times failing to show up the device's existence. so checkout if network manager is installed, 

do...
```
iwconfig eth1 essid XYZ
```

do..
 ```
apt-get install network-manager-gnome
```

do.. ```
iwconfig
``` and u should see something like this

```
root@jai-laptop:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XYZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:08:5C:63:AD:3A   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality=58/100  Signal level=-76 dBm  Noise level=-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3678   Missed beacon:0
```

do
```
/etc/init.d/dbus restart
```

do 
```
dhclient eth1
``` ..needed if it didnt picked up already

this should work...it did...atleast for me

---

