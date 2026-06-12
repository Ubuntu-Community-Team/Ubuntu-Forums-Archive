---
title: "Problems with broadcom 4318"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by gtkourounis on 2006-12-13
everything is properly installed, the card shows up on my computer, but when i try to connect to my router it just doesnt work. anyone has an idea what the problem might be?????

---

### Post by cilynx on 2006-12-13
Did you get the firmware from the Windows driver?  Without it, it shows up, but doesn't actually work.

---

### Post by gtkourounis on 2006-12-13
if you are asking if i have blacklisted it and then installed it again with ndiswrapper then yes. its showing up, its activated, but it just doesnt connect to my router. i dunno, i will try to get you some termail outputs.

---

### Post by gtkourounis on 2006-12-13
hope that this helps you,

```


neudeck@neudeck-laptop:~$ lspci | grep Broadcom\ Corporation
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
neudeck@neudeck-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
neudeck@neudeck-laptop:~$ cd /home/neudeck/Desktop
neudeck@neudeck-laptop:~/Desktop$ sudo -i
Password:
root@neudeck-laptop:~# modprobe ndiswrapper
root@neudeck-laptop:~# ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a4:4d:90:7b
Sending on   LPF/eth1/00:14:a4:4d:90:7b
Sending on   Socket/fallback
root@neudeck-laptop:~# ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a4:4d:90:7b
Sending on   LPF/eth1/00:14:a4:4d:90:7b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@neudeck-laptop:~# dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a4:4d:90:7b
Sending on   LPF/eth1/00:14:a4:4d:90:7b
Listening on LPF/eth0/00:c0:9f:ee:11:c5
Sending on   LPF/eth0/00:c0:9f:ee:11:c5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 242561 seconds.
root@neudeck-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@neudeck-laptop:~#


```

---

### Post by cilynx on 2006-12-13
aha, you did it that way.

I am a strong disbeliever in ndiswrapper.  Maybe I'm the only one, but I think wrapping the Windows driver is a bad idea. 

If you want to try my way:

Unblacklist bcm34xx
install fwcutter
```

sudo apt-get install bcm43xx-fwcutter

```
It'll ask if you want to run some script from /usr/share/bcm43xx-fwcutter/
You want to run the script.  It'll download and chop up the firmware
Finish the setup, then reboot.  You don't really have to reboot, but it's the easiest way.
Your module will be bcm43xx.
Just in case you need proof:
```

rcw@angus:~$ lsmod|grep ndis
rcw@angus:~$ lsmod|grep bcm
bcm43xx               141844  0 
ieee80211softmac       39040  1 bcm43xx
ieee80211     
rcw@angus:~$ lspci|grep -i bcm
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
rcw@angus:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"wolfteck"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:14:BF:8E:E0:6F   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=75/100  Signal level=-41 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:122  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rcw@angus:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:14:A5:72:1C:91  
          inet addr:192.168.1.189  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe72:1c91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28274 errors:0 dropped:694 overruns:0 frame:0
          TX packets:26960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26308463 (25.0 MiB)  TX bytes:3754759 (3.5 MiB)
          Interrupt:21 Base address:0x8000 

rcw@angus:~$ 

```

I don't really know why folks say the native driver doesn't work...

On your system...are you running a dhcp server on your laptop?  Why are you getting an address from dhclient when you have no connectivity?

---

### Post by gtkourounis on 2006-12-13
i have connectivity with my wired connection, i have no connectivity with my wireless connection. And would i also have to unistall ndiswrapper and all of the things that i installed with it for this to work?

btw, thanx for the help, really appreciate it.

---

### Post by cilynx on 2006-12-14
Gotcha.  You may have to wipe out all of ndiswrapper, I'm not sure as I've never used it.  I do know that bcm43xx is higher priority in the module load sequence.  That's why you have to blacklist it to use ndiswrapper.  I would think better safe than sorry and completely nuke ndiswrapper if you're going to try bcm43xx-fwcutter.

---

### Post by gtkourounis on 2006-12-14
i am still experiencing the same exact problem, the card shows up everything is functioning but the card makes no connection with the router

btw i have an acer aspire 5002WLMi

---

### Post by compwiz18 on 2006-12-14
> **cilynx said:**
> Gotcha.  You may have to wipe out all of ndiswrapper, I'm not sure as I've never used it.  I do know that bcm43xx is higher priority in the module load sequence.  That's why you have to blacklist it to use ndiswrapper.  I would think better safe than sorry and completely nuke ndiswrapper if you're going to try bcm43xx-fwcutter.
You can just **rmmod ndiswrapper** which will remove all traces of it - and then blacklist it too.  If you want it back, just remove it from the blacklist and **modprobe ndiswrapper**

---

### Post by gtkourounis on 2006-12-15
do you have any idea what might be going wrong guys????? why do the terminal keep telling me this

```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by gtkourounis on 2006-12-15
*bump*

do you any of you have any clue why this is not working???? i need this to be fixed by sunday because then i wont have acess to a wired internet connection.

thanx in advance

---

### Post by compwiz18 on 2006-12-15
Try: [http://ubuntuforums.org/showthread.php?p=1892673](http://ubuntuforums.org/showthread.php?p=1892673)

---

### Post by gtkourounis on 2006-12-16
its ok, no worries i will temporarily install windows just for the holidays. I am going away from home and i will need the wireless working, i work tomorrow, and i leave sunday so there wont be anytime for me to figure this thing out. First thing that i'll do when i am back is install ubuntu again.

Thanx for the support, hopefully we'll make this work after the holidays.

---

### Post by garlicsalt2 on 2006-12-20
download the firmware package directly:

wget -c [http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb](http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb)

and then install it manually: 

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

See this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

This guide does use ndiswrapper, which I never liked. Just download the firmware, and then reboot. This SHOULD work whichever method you use - either with or without ndiswrapper.

Alas, I am using a friend's notebook, and don't have the authority to install kubuntu, so I have to make do with just the Live CD. Fortunately, I have copied the firmware package to my USB HDD, from whence I can run dpkg manually to install the needed files. Now, if I could just find a firmware package for Knoppix...

---

### Post by towsonu2003 on 2006-12-21
try doing it this way:
```

sudo dhclient -r eth0 && sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 essid ESSIDNAME
sudo iwconfig eth1 ap MACADDRESSofAccessPoint  #not always needed
sudo iwconfig eth1 key WAPWEPorWhateverKey # not needed if you use unencrypted wifi
sudo dhclient eth1

```

> 
I don't really know why folks say the native driver doesn't work...
bc sometimes it just doesn;t work...

---

### Post by compwiz18 on 2006-12-21
> **towsonu2003 said:**
> try doing it this way:
```

sudo dhclient -r eth0 && sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 essid ESSIDNAME
sudo iwconfig eth1 ap MACADDRESSofAccessPoint  #not always needed
sudo iwconfig eth1 key WAPWEPorWhateverKey # not needed if you use unencrypted wifi
sudo dhclient eth1

```


bc sometimes it just doesn;t work...
It doesn't work on AMD64, or at least I can't get it to.  But ndiswrapper does...

---

### Post by towsonu2003 on 2006-12-21
> **compwiz18 said:**
> It doesn't work on AMD64, or at least I can't get it to.  But ndiswrapper does...

uhm, which one doesn't work on AMD64?  
this:
```

sudo dhclient -r eth0 && sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 essid ESSIDNAME
sudo iwconfig eth1 ap MACADDRESSofAccessPoint  #not always needed
sudo iwconfig eth1 key WAPWEPorWhateverKey # not needed if you use unencrypted wifi
sudo dhclient eth1
```
or this:
> native driver [bcm43xx]
?

---

### Post by compwiz18 on 2006-12-21
ndiswrapper works fine on amd64 (native [bcm43xx] doesn't), if you need help, see link in my signature or post a message here.

---

### Post by xpan on 2006-12-21
I am experiencing similar issues. The problem with the broadcom chipset is that it seems tricky to turn on the antenna. I think this problem is encountered on acer WLMi laptops only (like mine). I have only tried the ndisrwapper solutions with the windows drivers, which it didn't work

---

