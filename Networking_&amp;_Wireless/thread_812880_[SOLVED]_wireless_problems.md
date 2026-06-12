---
title: "[SOLVED] wireless problems"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by bdog676 on 2008-05-30
I followed the steps at [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

> lappy@lappy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6e:53:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:a5:a8:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
lappy@lappy-laptop:~$ sudo su
[sudo] password for lappy: 
root@lappy-laptop:/home/lappy# ifconfig wlan0 down
root@lappy-laptop:/home/lappy# dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:a5:a8:31
Sending on   LPF/wlan0/00:90:4b:a5:a8:31
Sending on   Socket/fallback
root@lappy-laptop:/home/lappy# ifconfig wlan0 up
root@lappy-laptop:/home/lappy# essid "home"
bash: essid: command not found
root@lappy-laptop:/home/lappy# iwconfig wlan0 essid "home"
root@lappy-laptop:/home/lappy# iwconfig wlan0 key a8******************************43
root@lappy-laptop:/home/lappy# iwconfig wlan0 mode Managed
root@lappy-laptop:/home/lappy# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:a5:a8:31
Sending on   LPF/wlan0/00:90:4b:a5:a8:31
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@lappy-laptop:/home/lappy# 

what am I doing wrong? I'm using a broadcom 40xx wireless and the driver is installed.

---

### Post by superprash2003 on 2008-05-30
could you post your iwconfig output

---

### Post by bdog676 on 2008-05-30
> lappy@lappy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lappy@lappy-laptop:~$ 

here

---

### Post by bdog676 on 2008-05-30
> DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

Is that trying to connect to my gateway? because it should be 192.168.1.1

---

### Post by superprash2003 on 2008-05-31
do you see any restricted drivers under System->administration->Restricted drivers manager ( or hardware drivers..)

---

### Post by bdog676 on 2008-05-31
> **superprash2003 said:**
> do you see any restricted drivers under System->administration->Restricted drivers manager ( or hardware drivers..)

yes. I have ati accelerated graphics driver and broadcom b43 wireless driver. Both are enabled and in use.

---

### Post by Unix_Slayer on 2008-05-31
Look at these posts. ==>[http://ubuntuforums.org/showthread.php?t=785578]("http://ubuntuforums.org/showthread.php?t=785578")
                         or ==>[http://ubuntuforums.org/showthread.php?t=800074]("http://ubuntuforums.org/showthread.php?t=800074")

Or you might try this one. ==>[http://ubuntuforums.org/showpost.php?p=4871609&postcount=5]("http://ubuntuforums.org/showpost.php?p=4871609&postcount=5")


Ask chili555. He seems to know what he's doing.

---

### Post by bdog676 on 2008-05-31
>  or ==>[http://ubuntuforums.org/showthread.php?t=800074]("http://ubuntuforums.org/showthread.php?t=800074")
That thread deals with usb wireless.
> 
Or you might try this one. ==>[http://ubuntuforums.org/showpost.php?p=4871609&postcount=5]("http://ubuntuforums.org/showpost.php?p=4871609&postcount=5")
I have rev3 not rev1 or rev2

---

### Post by bdog676 on 2008-05-31
btw unixslayer: Are you using 64 or 32 bit? I know 32 wouldn't use all that ram you're sporting.

---

### Post by Pioneer5000 on 2008-05-31
Try the link below. (scroll to bottom of page and look for last post by me).

[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

---

### Post by Unix_Slayer on 2008-05-31
> **bdog676 said:**
> btw unixslayer: Are you using 64 or 32 bit? I know 32 wouldn't use all that ram you're sporting.

64 Bit........

---

### Post by bdog676 on 2008-05-31
> **Pioneer5000 said:**
> Try the link below. (scroll to bottom of page and look for last post by me).

[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

no go...sorry

---

### Post by Unix_Slayer on 2008-05-31
> **bdog676 said:**
> I followed the steps at [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)



what am I doing wrong? I'm using a broadcom 40xx wireless and the driver is installed.

You can't have wireless, and wired running at the same time. It takes a lot of hard coding to make them both work at the same time. I have both my adapters working at the same time. Wireless to the internet, and the wired to the intranet. You have to disable the wired device. Then Pioneer's code should work. In knetworkmanager, do you see wireless ap's at all? Or do you see wired only?

---

### Post by bdog676 on 2008-06-02
> **Unix_Slayer said:**
> You can't have wireless, and wired running at the same time. It takes a lot of hard coding to make them both work at the same time. I have both my adapters working at the same time. Wireless to the internet, and the wired to the intranet. You have to disable the wired device. Then Pioneer's code should work. In knetworkmanager, do you see wireless ap's at all? Or do you see wired only?

I disabled the wired adapter in knetworkmanager and I was able to find and connect to my router. But after that it doesn't work. I can pull up the router utility and it shows I am connect but the wireless adapter keeps turning off and on ( i can tell because there's a light on the laptop) and reconnecting. I think this has to due with the wired adapter enabled itself. I find it enabled each time I go into knetworkmanager. I also cannot obtain a dns.

---

### Post by unutbu on 2008-06-02
Please post 
```

iwlist scan
cat /etc/resolv.conf
```

---

### Post by Unix_Slayer on 2008-06-03
> **bdog676 said:**
> I disabled the wired adapter in knetworkmanager and I was able to find and connect to my router. But after that it doesn't work. I can pull up the router utility and it shows I am connect but the wireless adapter keeps turning off and on ( i can tell because there's a light on the laptop) and reconnecting. I think this has to due with the wired adapter enabled itself. I find it enabled each time I go into knetworkmanager. I also cannot obtain a dns.


Is it possible to turn off the wired portion in the system Bios? It's probably one of those dual pci deals. Wired and wireless in one.

---

### Post by bdog676 on 2008-06-04
Not sure how, but I did get everything working by switching to kde, paraphrase stored in wallet now, everything works, thanks all. Oh, and the flashing wireless nic button on my laptop appears to by due to activity, like lights on a router. Windows left it solid so that confused me. :KS

---

### Post by Unix_Slayer on 2008-06-04
> **bdog676 said:**
> Not sure how, but I did get everything working by switching to kde, paraphrase stored in wallet now, everything works, thanks all. Oh, and the flashing wireless nic button on my laptop appears to by due to activity, like lights on a router. Windows left it solid so that confused me. :KS

Good Deal. I'm using KDE4. I had problems as well with the other X11's. On the lights.... WIndows uses the .inf file differently then Linux/Unix.

---

