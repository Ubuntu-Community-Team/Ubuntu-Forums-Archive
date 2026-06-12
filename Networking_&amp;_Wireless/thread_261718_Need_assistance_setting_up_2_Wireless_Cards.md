---
title: "Need assistance setting up 2 Wireless Cards"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by komputes on 2006-09-20
I have 2 wireless cards and I would like to have them work in Ubuntu. My Ethernet card work fine and I wish to install a Broadcom Wireless LAN B+G (which is integrated) and a Sagem SA 802.11g USB Dongle. I was told that these would work with the original windows drivers and ndiswrapper.

So I installed NDISwrapper through Automatix, and I did some research on the drivers for my drivers.

Here is the link for Broadcom Wireless LAN B+G Driver 3.100.46
[http://support.acer-euro.com/drivers/notebook/as_3000_5000.html](http://support.acer-euro.com/drivers/notebook/as_3000_5000.html)

As for the Sagem 802.11g USB Dongle - this is the info I got off a website reporting someone with linux who got it working:
Status partially supported
( Wifi dongle )	( Category: Networking )
ID	0x0cde:0x0006
Driver	no driver available
Linux-USB link	 
Vendor link	 
Comment	On linux/x86, ndiswrapper can load win32 drivers to use the device.

So I was wondering if someone could post instructions to solve my problem so that both my wlan cards work through ndiswrapper. As well, from what I've seen you need to know the SSID of every Access Point you connect to, is there no Wireless Manager which comes close to windows-like click-and-connect simplicity?

---

### Post by Crayoneater on 2006-09-20
you install the windows driver using ndiswrapper...you need the *.inf file and the *.sys file from the windows driver folder.  you need to open a terminal and type:

sudo ndiswrapper -i *.inf

(replace the * with the actual file name, and remember that it is case sensitive)

then type ndiswrapper -l  to see if is says the hardware and driver are present

then type: iwlist scan and it will tell you what device name your card is eth1 or wlan0 probably) and it will tell you the ssids that it finds.

then type: sudo iwconfig eth1 essid (insert ssid here)

then type: sudo dhclient eth1

oh, and then your internet should be working, and you can type: sudo ndiswrapper -m

as far as having it connect easily, you can try programs like network-manager (it doesn't seem to work for some people though...like me), gtk-wifi (this is what i use, although when i installed the .deb file for it, the location of some of the icons were wrong and it didn't work until i fixed it), and there are a few other programs that make connecting to wireless  a lot easier.

---

### Post by komputes on 2006-09-20
Tried that, didn't work, take a look. Plus after all of this i went into th e network settings (control panel) and I do not see a wlan0, just the good old eho0 for the ethernet and eth1 for the wireless, that won't connect.

```
xx@xx:~$ $sudo ndiswrapper -l
No drivers installed
xx@xx:~$ sudo -s
Password:
root@xx:~# cd /home/xx/802BG/
root@xx:~/802BG# $sudo ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@xx:~/802BG# ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
root@xx:~/802BG# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

root@xx:~/802BG# sudo iwconfig eth1 essid Linksys
root@xx:~/802BG# sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:a4:1a:00:00
Sending on   LPF/eth1/00:14:a4:1a:00:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@xx:~/802BG# sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@xx:~/802BG#
```

I have all the coorect files in my home dir under 802BG:

The inf and sys files are:
bcmwl5a.inf
bcmwl5.sys

[Strrrrrr-ike One]

---

### Post by Melcar on 2006-09-20
As far as the Broadcom chip goes, you have to blacklist the Linux provided driver (bcm43xx) first and then load up the ndiswrapper driver.  This is what I do when installing my Broadcom drivers
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper")

I would imagine it would be a similar process for your other device.  Of course, this comes from the guy who can't even get an ancient Trendnet wireless card working:p .

---

### Post by komputes on 2006-09-20
> **Melcar said:**
> As far as the Broadcom chip goes, you have to blacklist the Linux provided driver (bcm43xx) first and then load up the ndiswrapper driver.  This is what I do when installing my Broadcom drivers
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper")

I would imagine it would be a similar process for your other device.  Of course, this comes from the guy who can't even get an ancient Trendnet wireless card working:p .

Already tried this:
```
sudo -s
sudo gedit /etc/modprobe.d/blacklist

add:

##Aspire 5000 Causes Broadcom wireless not to work
blacklist bcm43xx
```

didn't work, but I'll go through the whole 11 pages of forum stuff to see if someone found a solution (but the one on the front page doesn't work, already tried)! 
[Strrrrrr-ike Two]

---

### Post by NetworkGuy on 2006-09-20
> root@xx:~/802BG# ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
root@xx:~/802BG# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.



I didn't see you ```
modprobe ndiswrapper
```

I believe you have to load ndiswrapper

---

