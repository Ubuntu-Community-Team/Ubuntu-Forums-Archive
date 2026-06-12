---
title: "Spontaneous Wireless Failure"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by your.pal.cookie on 2008-04-02
I had a working wireless connection once. Then, I came home one day, and it was gone. No idea why. I've tried to figure out what's going on, but I think I just don't know what I'm doing.

I'm running ubuntu 7.10. I have a D-Link DWA-552 wireless card installed. I am using the driver it shipped with through ndiswrapper. While I did initially have some trouble with my version of ndiswrapper, this setup was working.

Fun facts:
 - The network is unsecured.
 - My windows XP machine is able to use the wireless connection without problems.
 - Using the network icon by my clock (in ubuntu), it seems that the computer can detect and display a (good) signal strength from my wireless network.
 - When I try to connect (through the icon in ubuntu), it seems to work a long time, then fail.
 - From windows I can browse the router but not from ubuntu. This maybe makes sense because I am not connected to it.
 - From windows, DHCP is working, but not with ubuntu. My understanding of how this process works is really limited, so that might make sense too.

When I try sudo dhclient wlan0

```

There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1b:11:6f:47:9a
Sending on   LPF/wlan0/00:1b:11:6f:47:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I tried to gather info that might be relevant:

sudo lshw -C network
```

  *-network
       description: Wireless interface
       product: AR5416 802.11a/b/g/n Wireless PCI Adapter
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:6f:47:9a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 latency=128 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

ndiswrapper seems okay...

ndiswrapper -v
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.22-14-generic SMP mod_unload 586 

```

ndiswrapper -l
```

net5416 : driver installed
        device (168C:0023) present

```

I don't know if it's important, but ifconfig reports...
```

eth0      Link encap:Ethernet  HWaddr 00:0C:76:5F:AB:4F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:6F:47:9A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:ee000000-ee010000 

```

And iwconfig...

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Which I *think* is okay. I really would appreciate any help I could get. Trying to learn and all that.

Thanks.

---

### Post by your.pal.cookie on 2008-04-03
Man, I am just stumped. I just can't figure this out. If anyone can help, I would really appreciate it. I just don't know what the next step would be.

---

### Post by wieman01 on 2008-04-04
It all looks OK, but it would help if you posted these as well:
> sudo iwlist scan
> sudo cat /etc/network/interfaces
> sudo cat "canned food"
I'll try to guide you through it.

---

### Post by your.pal.cookie on 2008-04-04
wieman01,

Thanks for getting back to me about this.

I ran those commands...

sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:B7:D3:FD
                    ESSID:"Archie"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

So my "Archie" network seems visible with a 76% signal, I guess.

sudo cat /etc/network/interfaces
```

auto lo
iface lo inet loopback


```

I don't really know what this one should be saying, but there it is.

For that last one, I don't think I have a file called "canned food," so I just did sudu rm -f something something.... ;) I don't really remember, and the computer just kinda broke down too, so now we'll never know. :)

---

### Post by wieman01 on 2008-04-04
Sorry, the last one was a joke. Just found it very funny (it's harmless of course), but here we go. ;-)

Please open:
> sudo gedit /etc/network/interfaces
Now make it read:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
Now restart the PC. Any better? If not please remove the last 2 lines and restart. I'll think of something else.

---

### Post by your.pal.cookie on 2008-04-04
Okay, done and done.

Now, my network icon's menu no longer shows my network as a connection option. It only has "manual configuration..."

There's no connection improvement.
I cannot browse the admin service on the router with my browser, so I don't think that's connected.

There doesn't seem to be anything new other than the change in the menu. I didn't think it looked like a step in the right direction, so I took those lines out.

Now, the network menu is working the way it used to, showing my network, signal strength, and some other options for connecting to other wireless networks, but it still fails to connect after a long attempt.

Do you know if there is a log somewhere that might suggest what failed in the attempt?

I sure appreciate your help, wieman01.

---

### Post by wieman01 on 2008-04-04
First off, your card is a wireless G device and your router runs in mixed mode (at least wirelss G mode), is that correct? So there is no conflict?

And MAC filtering is disabled? I had that once... for a reason unknown to me my router enabled MAC filtering and I was locked out. Happens.

Please update "/etc/network/interfaces" once again so that it reads:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Archie
Save & restart the network:
> sudo ifdown -v wlan0
> sudo ifup -v wlan0
> route
Please post the output of each command.

_**EDIT:**_
I cannot explain right now what's wrong with NM, but we'll do some more testing. Also there aren't any log files I am aware of. You could run NM from command line of course and look at the output. That'd be an option.

---

### Post by your.pal.cookie on 2008-04-04
wieman01, good call.

I went over all my router configuration, and found wifi protected setup turned on.

I'm pretty remotely located, so I didn't need to turn this on (I kind of didn't know I could). I'm the only person in range of the router. Somehow this must have turned on at some point.

Anyway, I rebooted the router and the machine and presto - wireless.

I really appreciate your help, wieman01. I sure learned something today, though it's seems pretty voodoo to me that this changed, allowed my xp machine to continue to access it, but started blocking my ubuntu machine. Especially strange that it was working before.

The router is the first thing I will check next time I have problems like this. It has some pretty good logging that suggested to me that this was happening, but didn't log the change.

Sorry if it was sort of a waste of time for you, but to me it really wasn't. Thanks again.

---

### Post by wieman01 on 2008-04-04
Don't worry, it's been a pleasure. Like I said, this kind of thing happened to me a while ago for no reason, so I am happy my experience helped someone else. See you around then! :-)

---

