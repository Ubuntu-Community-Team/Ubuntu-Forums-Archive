---
title: "[SOLVED] No Wireless with Broadcom 4306...ssb module problem????"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by rmin714 on 2008-10-01
I've done through several threads and done as many installs trying to get this wireless card connected. As best as I can figure out it has something to do with the ssb module conflicting with ndiswrapper. There have been some threads asking for the following commands so if anyone could point me in the right direction I would greatly appreciate it.

user:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:11:43:57:be:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a ip=192.168.0.69 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0b:7d:22:f3:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
user:~$ lspci -nn
\00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
user:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
user:~$ uname -m
i686
user:~$

---

### Post by ittiam on 2008-10-01
Have you blacklisted the kernel bcm43xx driver? You can blacklist it in /etc/modprobe.d/blacklist. 

[http://ubuntuforums.org/showthread.php?t=898113](http://ubuntuforums.org/showthread.php?t=898113)

The above link might help you.

---

### Post by pytheas22 on 2008-10-01
Yes, ssb is the problem.  If you type these commands:
```

sudo apt-get install bcm43xx-fwcutter
```

(after typing this, you should be asked at some point if you want to automatically download and install firmware; say yes, then continue with the rest of the commands)

```
sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
sudo modprobe -r b43 b44 b43legacy ssb
sudo modprobe bcm43xx
sudo ifconfig eth1 up

```
does that make your wireless work?  If so, we can apply a permanent fix so that things will work automatically from now on.  If it still doesn't work after running those commands, please post the output of:
```

cat /lib/firmware
lspci -nn | grep -i broadcom
lshw -C Network
lsmod | grep -e bcm -e b4 -e ssb
```

---

### Post by rmin714 on 2008-10-02
Thanks for the replies.

I did the commands and after the "sudo ifconfig eth1 up" command I did see that wireless was working (blue bars and my network was listed under the Network Manager) which is great as this is furthest I've gotten. However, I lost all keyboard control. Thinking this was due to the fact that I have really been messing with this install doing several different tutorials that haven't worked, I did a clean install, ran all updates of the update manager then ran the first command to install bcm43xx-fwcutter again. Everything was going fine until I tried the following command. 

user:~$ modprobe -r b43 b44 b43legacy ssb
FATAL: Error removing b43 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted
user:~$ 

At this point I just stopped and thought I would seek advice. Not trying to waste your time just trying to get a clean install. Thanks again for getting me this far.

user:~$ cat /lib/firmware
cat: /lib/firmware: Is a directory

user:~$ lspci -nn |grep -i broadcom
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

user:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:57:be:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a ip=192.168.0.28 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:22:f3:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

user:~$ lsmod | grep -e bcm -e b4 -e ssb
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
user:~$

---

### Post by ittiam on 2008-10-02
You need to be root to execut modprobe and access /etc files.

do the following during which it will prompt for the root password.

```
sudo modprobe -r b43 b44 b43legacy ssb
sudo cat /lib/firmware
```

---

### Post by Ayuthia on 2008-10-02
> **rmin714 said:**
> Thanks for the replies.

I did the commands and after the "sudo ifconfig eth1 up" command I did see that wireless was working (blue bars and my network was listed under the Network Manager) which is great as this is furthest I've gotten. However, I lost all keyboard control. Thinking this was due to the fact that I have really been messing with this install doing several different tutorials that haven't worked, I did a clean install, ran all updates of the update manager then ran the first command to install bcm43xx-fwcutter again. Everything was going fine until I tried the following command. 

user:~$ modprobe -r b43 b44 b43legacy ssb
FATAL: Error removing b43 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted
user:~$ 
The Operation not permitted message came because the command was not run with sudo.  However, based on the information that you show further, it looks like you are now trying to use b43 instead of bcm43xx.

> 
user:~$ cat /lib/firmware
cat: /lib/firmware: Is a directoryI think that pytheas22 meant to request 'ls /lib/firmware' (without the quotes) instead of cat.  Try using the ls command instead.  It will help us see what firmware you have installed for the Broadcom card.

> user:~$ lsmod | grep -e bcm -e b4 -e ssb
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
user:~$

This information here is showing that you are trying to use the b43 driver instead of the bcm43xx.  Once you show us the files in the /lib/firmware directory, we should be able to figure out which way to go.

---

### Post by pytheas22 on 2008-10-02
Yes, as the above posters say, please try running the 'modprobe -r' command prefixed with 'sudo'; it should work then (if you get error messages to the effect of 'error: module XXX does not exist in /proc/modules', you can ignore them).  Hopefully it won't kill the keyboard this time.

---

### Post by rmin714 on 2008-10-02
Thank you one and all. I executed these commands (with sudo...sorry my bad)

sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
sudo modprobe -r b43 b44 b43legacy ssb
sudo modprobe bcm43xx
sudo ifconfig eth1 up

and it worked great after that. 
pytheas22 you mentioned that I may need to make this permanent fix? I'm guessing I'll run these 4 commands when I restart then execute some command so it loads everytime? Thanks again everyone.

---

### Post by pytheas22 on 2008-10-03
Glad to hear it worked.  To make the fix permanent, type:

```
sudo gedit /etc/init.d/wifi-fix.sh
```

A blank text file will open up.  Add to the file these lines:

```
#!/bin/bash

modprobe -r b43 b44 b43legacy ssb
modprobe bcm43xx
ifconfig eth1 up
```

Then save and close the file, and run these commands so that the system knows to run this script every time it boots:
```

cd /etc/init.d
sudo -s
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

From then on, your wireless card should be working automatically each time you reboot your computer, without any manual intervention required.  Please let me know if it works.

---

### Post by rmin714 on 2008-10-07
I've been using the computer and connecting to wired and wireless networks without having to do anything manually. Do you think I should still implement the "permanent fix"?  Thanks

---

### Post by pytheas22 on 2008-10-07
If it's been working so far without a problem, then no, I wouldn't worry about the permanent fix.  I admit that I don't know why it would work on its own, but if it is, all the better.  You might want to keep a link to this thread or a file with the commands you need to get the wireless running on hand just in case, but otherwise, I wouldn't fix what's not broken.

---

### Post by rmin714 on 2008-10-09
Excellent. I'll keep detailed notes and thanks again.

---

### Post by petizo on 2008-10-24
Hello pytheas22,

I have followed your instructions and my wireless card blue bars appeared,  it seemed to have worked.  I disconnected the wire and continue to work, once I rebooted the settings went away I missed the last steps on how to r amake it permanent.  I follow those steps and now the bars come back up and it says connaected.  I rebooted one more time without the wire plugged in and now the bars show up but it there is no connection,  it looks like the network card is not obtaining an IP address, do you have any sugestions on this?
Your advise will be greatly appreciated

---

### Post by pytheas22 on 2008-10-25
petizo: please reboot, then before running any other commands, post the output of:
```

ls -l /etc/init.d/wifi-fix.sh
cat /etc/init.d/wifi-fix.sh
lshw -C Network
sudo iwlist scan
```

That will help to figure out what's really going on and how to fix it.

---

### Post by petizo on 2008-10-28
Hello phyteas,

I have not use the system since my last post.  I decided to check today and there was your post thanks.  To my surprise the wireless card did obtain an IP this time.

The output you requested is below.  Do you have any idea why it does this?  Last time a rebooted a few times and it did not make a difference.

jorge@jorge-laptop:~$ ls -l /etc/init.d/wifi-fix.sh
-rwxr-xr-x 1 root root 81 2008-10-24 23:08 /etc/init.d/wifi-fix.sh
jorge@jorge-laptop:~$ 
jorge@jorge-laptop:~$ cat /etc/init.d/wifi-fix.sh
#!/bin/bash

modprobe -r b43 b44 b43legacy ssb
modprobe bcm43xx
ifconfig eth1 up
jorge@jorge-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:46:ae:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-21-generic ip=192.168.8.101 latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:89:e3:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.8.106 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
jorge@jorge-laptop:~$ sudo iwlist scan
[sudo] password for jorge: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0D:88:ED:68:F5
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-79 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 3280ms ago
          Cell 02 - Address: 00:80:C8:2B:69:75
                    ESSID:"petizo"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 48ms ago

jorge@jorge-laptop:~$

---

### Post by pytheas22 on 2008-10-28
petizo: I don't see anything that looks wrong.  Were you able to actually load web pages if you unplugged the ethernet wire?  You did definitely have an IP address on the wireless interface, so it should work.

If you continue to have problems, please post the output of the following commands during one of the sessions where your wireless is not working:
```

lspci -nn
uname -m
lshw -C Network
sudo iwlist scan
iwconfig eth1
```

---

