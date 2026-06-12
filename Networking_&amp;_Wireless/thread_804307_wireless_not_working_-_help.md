---
title: "wireless not working - help"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by ubuman80 on 2008-05-23
hi guys, can't get my wireless card to work, please help, my guess it's something to do with either ID or card memory:



lshw
 *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:81:bc:f9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wire 




iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:38:0e:24:69  
          inet addr:192.168.200.6  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe0e:2469/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:656154 (640.7 KB)  TX bytes:84677 (82.6 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99700 (97.3 KB)  TX bytes:99700 (97.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:81:bc:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-81-BC-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



dhclient wmaster0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


thanks

---

### Post by superprash2003 on 2008-05-23
go to system->administratoin->restricted drivers manager and enable any WLAN drivers if  available

---

### Post by ubuman80 on 2008-05-23
thanks for replying

I don't have any restricted driver manager under system administration, I do have "hardware drivers" but no restricted drivers over there

---

### Post by ubuman80 on 2008-05-23
the only driver listed on system>administration>"hardware drivers" is Nvidia graphics

---

### Post by mapes12 on 2008-05-23
What kernel version are you running?

```
echo `uname -r`
```

This may help get your driver initialised:

[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)

---

### Post by ubuman80 on 2008-05-23
Ubuntu 8.04 - the Hardy Heron - released in April 2008.

---

### Post by ubuman80 on 2008-05-23
2.6.24-16-generic

---

### Post by ubuman80 on 2008-05-23
thanks mapes12 question is are drivers downloaded from the compat wireless project will work or should I use an older kernel version?

---

### Post by ugm6hr on 2008-05-23
Please repost the lshw - you have missed the final line.

How are you online at the moment? Wired on same laptop?

The useful commands for us to see:
```
lshw -C network
route -n
iwlist scan
```

---

### Post by ubuman80 on 2008-05-23
lshw -C network


 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:81:bc:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:0e:24:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.200.6 latency=0 module=tg3 multicast=yes


route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.200.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.200.254 0.0.0.0         UG    0      0        0 eth0


iwlist scan


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

---

### Post by ugm6hr on 2008-05-23
The driver is installed OK : **driver=iwl3945**

It appears you are online with ethernet (wired).

wlan0 is your wifi.  It is apparently "unavailable" according to iwlist scan.  Don't know why.

Is there a hardware or BIOS switch?  If so - is it ON?

Do you dual-boot with Windows?  If so - it may be a power-saving issue with Windows.  Although I would anticipate that would be on for both wired and wireless ([http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14))

Not sure what else it could be.  That Intel chipset is one of the best supported in Linux.

---

### Post by ubuman80 on 2008-05-23
thanks ugm6hr

no dual booting only ubuntu on my laptop
what does it mean that on "lshw" the wireless is identified as "wmaster0" and not "wlan0" is that might be the problem?

lshw

 *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:81:bc:f9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by ugm6hr on 2008-05-23
Not sure.  I suspect it isn't that though.

Maybe try searching for 3945ABG on the forum to see if anyone else has a similar problem.

---

### Post by ubuman80 on 2008-05-23
if my wifi is wlan0 how come my wireless interface is called wmaster0?

---

### Post by mapes12 on 2008-05-23
I apologise in advance for stating the blindingly obvious BUT

**have you removed the ethernet cable from your machine? **

If not then do so and restart Ubuntu.

Does the wifi come alive?

---

### Post by ubuman80 on 2008-05-23
obviously, no more than a few hundred times....

---

### Post by mapes12 on 2008-05-23
> obviously, no more than a few hundred times....

BUT you have tried a restart with the thing removed?

> wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
> eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 Failed to read scan data : Resource temporarily unavailable

Disable the wmaster device:

```
ifdown wmaster0
```

and rescan

```
iwlist scan
```

---

### Post by ubuman80 on 2008-05-23
I can't disable wmaster0
ifdown returns ifdown: interface wmaster0 not configured

---

### Post by mapes12 on 2008-05-23
Try stopping all network services:

```
sudo /etc/init.d/networking stop
```

Remove the ethernet cable.

Then restart everything:

```
sudo /etc/init.d/networking start
```

Run another scan:

```
iwlist scan
```

Any luck? If not have another go at:

```
ifdown wmaster0
```

---

### Post by ubuman80 on 2008-05-23
I tried network restarting and no luck got:

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable



tried again ifdown wmaster0 and got:

without sodu:
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
with sudo:
ifdown: interface wmaster0 not configured

---

### Post by ubuman80 on 2008-05-24
gentlemen, problem solved, thanks to postings of Zorael and BoardWorld
thanks again to all of you, the following worked for me, don't forget to restart: 


>  Originally Posted by Zorael  View Post
Intel's new driver is open source! :>

Small note though; my 3945ABG card wouldn't work at all until I created a file named iwl3945 and placed it in /etc/modprobe.d/, with the following contents:
Code:

```

alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1

```

If you see any networks at all then you likely don't need to do this. Mine couldn't see any, and by extension, I couldn't connect to any.


To perform a network scan in a terminal, enter this.
Code:

```
$ sudo iwlist scan
```



---

