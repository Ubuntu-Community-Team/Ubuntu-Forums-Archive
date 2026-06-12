---
title: "[SOLVED] Problem setting up zd1211b WiFi Link USB Adapter for NDS"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by guedesav on 2008-10-27
I've been trying to set my WIFI Link USB Adapter ([http://www.mayflash.com/pc/pc041/pc041.htm](http://www.mayflash.com/pc/pc041/pc041.htm)) in Ubuntu and still didn't manage to. I've found [this thread by henrik_daver]("http://ubuntuforums.org/archive/index.php/t-422499.html") and it was quite helpful, but still it isn't working, so let me tell you what I've got. First, some outputs

> >lsusb
Bus 005 Device 003: ID 0ace:1215 ZyDAS 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


> >usbmodules --device /proc/bus/usb/005/003
zd1211rw
zd1211b


Note: zd1211rw is already on modprobe.d/blacklist

So, I follow the steps given by henrik, with one slight modification:

```

modprobe -r zd1211b
depmod
modprobe -v zd1211b
modprobe zd1211b
ip link set dev wlan0 up
iwconfig wlan0 mode master key off
iwconfig wlan0 essid "NSD-WFC"
ifconfig eth0 0.0.0.0 up
ifconfig wlan0 0.0.0.0 up
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0
ifconfig br0 0.0.0.0 up
dhcpcd br0

```

I set the bridge's IP as 0.0.0.0 so I won't lose my internet connection. I figured the 0.0.0.0 IP is meant to share the internet connection, just like I have to set eth0 to 0.0.0.0 for ADSL to work.

Anyway, the result is that my DS detects the network, it tries to connect(the signal icon turns green), but it fails with a 52101 error or something alike(really, sometimes it's that, sometimes it's 52000... it varies). Also, dhcpcd stops mostly a minute after I start it, I wonder if that's a bad sign as well.

Truth is, the device is somewhat buggy, for in Windows, if you disconnect and reconnect the USB, the network won't work unless you restart the PC(at least with me, and yes, I have contacted the manufacturer already). It still doesn't make sense, though, and the manufacturer doesn't provide any support for Linux. Actually, they say "it does not work under Linux system", but I guess it's just bulshit, because the install CD provides drivers(buggy code, didn't compile) and guides for installing it on Linux.

So, that's it all. Any help is appreciated, any further information you need to help me solve this problem, just ask and I'll provide.

Thanks in advance.

---

### Post by guedesav on 2008-11-24
Okay, "thanks a lot" for all your help, I've got some help elsewhere(special thanks for timemage, on the ##linux IRC room), and for all of you who found this topic and is experiencing the same problem, here's what I did...

After having the driver compiled, zd1211rw o blacklist and et cetera, everything is "almost" done. First, we need to configure dhcp. It has to include a subnet for the wlan0(or whatever interfce the device maps to):

> 
#/etc/dhcpd.conf
subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers 208.67.222.222, 208.67.220.220;
	option ip-forwarding on;
	range dynamic-bootp 192.168.0.10 192.168.0.254;
	default-lease-time 21600;
	max-lease-time 43200;
}


DNS values may vary. Now, next thing to do is put the device to actually work! Step by step...

> 
iwconfig wlan0 mode master
iwconfig wlan0 essid "NSD-WFC"
iwconfig wlan0 key:senha


Here we're configuring the network. It can be done through /etc/network/interfaces, but I still haven't got the time to research more about it. Also, sometimes I feel the signal is horribly down, so I added a "power off" option to turn off power saving. Next!

> 
ifconfig wlan0 192.168.0.1


This will make so that wlan0 is the router to the wireless network. Simple like this.

> 
/etc/init.d/dhcp restart


This will enable DHCP in the wireless. If DHCP fails, it might be because another interface(avahi generated, for example) is trying to be DHCP-ed, but it can't. Anyway, there can be several causes, and I can't guess what it'll be. Just wish it works right! :D

> 
iptables -t nat -A POSTROUTING -s 192.168.0.0/255.255.255.0 -j MASQUERADE 


This will allow internet sharing through your wireless interface, so the DS will be able to connect. Now test the connection and have fun! :D

---

