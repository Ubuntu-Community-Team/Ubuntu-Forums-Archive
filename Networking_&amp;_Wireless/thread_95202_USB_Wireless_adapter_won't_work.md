---
title: "USB Wireless adapter won't work"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by nalmeth on 2005-11-26
Hey everyone..
I'm setting up my friends computer with breezy as you can tell, but the fact that he uses a USB wireless adapter has brought up difficulties..

His install wasn't complete as he couldn't download packages from home, so I brought his computer to my home and installed it through my router. I have been browsing around and downloaded a ton of wireless detection applications and none are picking up his adapter.

The device manager picks up his adapter, but does not know of its capabilities.
USBVIEW sees it aswell. Ubuntu is aware of the device but not sure what to do with it.
I downloaded a Ndiswrapper frontend as I'm not very familiar with it, and it claimed that it was able to install the drivers from his windows CD, but still no recognition anywhere else.

Does anyone know where I can find linux drivers for this USB adapter, or how have any idea howto set this up? I'm tempted to try using wine to install, but can't see that working very well.

Please post ANYTHING that comes to mind. Any comments or vague notions at all are greatly appreciated. I have until late Saturday and its 10:30 Friday right now. I will post ANY additional information needed.

thanks guys

---

### Post by nalmeth on 2005-11-26
more info 

_ndiswrapper -l_
Installed ndis drivers:
athfmwdl        driver present, hardware present
neta5agu        driver present, hardware present

(installed from CD through ndis frontend, should I find drivers elsewhere? more info below...)

[B]_iwconfig_
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/B]

[I]
_ifconfig_
eth0      Link encap:Ethernet  HWaddr 00:80:5F:95:37:A1
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5fff:fe95:37a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21476085 (20.4 MiB)  TX bytes:754050 (736.3 KiB)
          Interrupt:11 Base address:0x9800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14584 (14.2 KiB)  TX bytes:14584 (14.2 KiB)
[/I]

[B]_lspci_
.....
.....
.....
yada yada
0000:00:0c.0 Network controller: Compaq Computer Corporation               TX PCI UTP (rev 10)[/B]

_sudo dhclient wlan0_
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
jordan@ubuntu:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

ANY IDEAS? NEED MORE INFO?

---

### Post by mips on 2005-11-26
It might help if you tell us what Make & Model USB adapter it is, I did not pick anything up from your posts.

---

### Post by nalmeth on 2005-11-26
sorry bout that
its a D-Link WLAN DWL-G132 and the manufacturer is Atheros Communications Inc
its 12 mgbytes/s
I think it is unsupported and I have found only a proprietary solution.. 
[http://forum.libranet.com/viewtopic.php?t=6699&sid=2a9d04724d6edf632933bf7269b3f768](http://forum.libranet.com/viewtopic.php?t=6699&sid=2a9d04724d6edf632933bf7269b3f768)
Is there anything that can be done to avoid this?  I'm still thinking about trying wine instead... This kinda sucks..
The drivers have already been paid for and it does not make sense to pay again.
Any ideas appreciated 
thanks again

---

### Post by el duderino on 2005-11-26
I was reading another "wifi problem" post and saw some similarities. myke had to turn off his eth0 to get his wifi card to work...thought it might be worth a shot..

here's the thread: 
[http://www.ubuntuforums.org/showthread.php?t=95387](http://www.ubuntuforums.org/showthread.php?t=95387)

---

### Post by Lambert on 2005-11-26
[quote=nalmeth]sorry bout that
its a D-Link WLAN DWL-G132 and the manufacturer is Atheros Communications Inc
its 12 mgbytes/s
I think it is unsupported and I have found only a proprietary solution.. 
[http://forum.libranet.com/viewtopic.php?t=6699&sid=2a9d04724d6edf632933bf7269b3f768]("http://forum.libranet.com/viewtopic.php?t=6699&sid=2a9d04724d6edf632933bf7269b3f768")
Is there anything that can be done to avoid this?  I'm still thinking about trying wine instead... This kinda sucks..
The drivers have already been paid for and it does not make sense to pay again.
Any ideas appreciated 
thanks again[/quote]

If you run iwconfig and have no output other then your earlier post then the driver is not working properly or it's not the correct driver.

So let's start here.

run the command 

```
sudo lshw -businfo
```

and look for your device in the list. Notice it's class then run this command

```
sudo lshw -C <class>
```

Post that output here.
Also post the output of 

lsusb

---

### Post by lothrids on 2005-12-18
I am having the same problem. Here is the output from my USB adatper.

  *-usb UNCLAIMED
       description: Generic USB device
       product: USB WLAN Device
       vendor: Atheros Communications Inc
       physical id: 1
       bus info: usb@3:1
       version: 0.01
       serial: 1.0
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=480.0MB/s

---

### Post by Lambert on 2005-12-18
You need to use an app called ndiswrapper to get your device working. There's a link in my signature(in my first post on the page) for ndiswrapper.

---

### Post by eaterb on 2006-03-25
I am having the same problem.  Here is the output from: sudo lshw -C <class>

  *-usb UNCLAIMED
       description: Generic USB device
       product: USB WLAN Device
       vendor: Atheros Communications Inc
       physical id: 2
       bus info: usb@1:2
       version: 0.01
       serial: 1.0
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=12.0MB/s

and also the output from: lusb

Bus 001 Device 002: ID 2001:3a03 D-Link Corp. [hex]
Bus 001 Device 001: ID 0000:0000

I am at a loss.  I have tried everything and have not been able to get the D-Link DWL-G132 working.

Any thoughts?

Thanks,

Brett

---

