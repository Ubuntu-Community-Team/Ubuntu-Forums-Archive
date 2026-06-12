---
title: "Linksys wireless help"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by slimboarder003 on 2008-05-15
Ubuntu reads my WMP54GX4 Linksys Wireless G PCI Adapter with SPX 4000 has Airgo network Inc Agn300 802.11 a/b/g true MIMO wireless card. I did the test hardware thing off of Ubuntu on my other drive. I'm not sure how to confirm it to work or to set it up because in connection it doesn't show wireless network. I'm new to Ubuntu and would like some help if possible. Thanks if someone can help.

---

### Post by dmizer on 2008-05-15
open a terminal, enter the following command:
```
lshw -C network
```
and paste the results here

also post the results of:
```
ifconfig
```

---

### Post by slimboarder003 on 2008-05-16
lshw -c network

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)
format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0c:76:0e:dc:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:214700 (209.6 KB)  TX bytes:214700 (209.6 KB)

Hardware testing still shows this

Detecting your network controller(s):

Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)

Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)

---

### Post by slimboarder003 on 2008-05-16
bump

---

### Post by dmizer on 2008-05-16
the code needs to have and upper case C, not a lower case c.  please repost the following:
```
lshw -C network
```

this is not fixing anything, it's just getting information about your adapter.

---

### Post by slimboarder003 on 2008-05-16
ok, Ill fix that

---

### Post by slimboarder003 on 2008-05-16
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AGN300 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=24
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 82
       serial: 00:0c:76:0e:dc:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56

---

### Post by dmizer on 2008-05-16
try this: [http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

it's the only one i found that claims to work.

---

### Post by slimboarder003 on 2008-05-16
Thanks, I'll give it a try tomorrow and post back how it works. Thanks again for the help.

---

### Post by tattoo_wolf on 2008-12-21
I have the WPC54GX4 pcmcia wifi card for my old dell i2500 laptop and the way that I got it working was to download the windoze driver from linksys (WPC54GX4-v1.00.09-2.0.1.19.zip) and using ndiswrapper installing the driver.  Unzip the file in a dir of your choice and then sudo the following

ndiswrapper -i tmimo3P.inf
modprobe ndiswrapper
depmod -a
iwconfig wlan0 essid *your essid or any for any open network*
iwlist wlan0 scan
dhclient

I put the last 3 lines in my rc.local file above the exit 0 line for starting the wireless at boot and also modified my /etc/modules file to include ndiswrapper.

I hope this helps you and anybody else that might have the same card. 

Wolf

---

