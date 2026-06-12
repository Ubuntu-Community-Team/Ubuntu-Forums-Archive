---
title: "[SOLVED] wmaster0???"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by craiggale on 2008-10-23
could somebody please tell why it is that when i run lshw -C network the logical namme of the interface is wmaster0 and on the connection i am using now the interface is wlan0.  Shouldn't the logical name also be wlan0?

```
craig@craig-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:64:72:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.4 latency=0 module=
```

```
craig@craig-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"zoom"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:01:38:8E:01:95   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
craig@craig-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:68:c4:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65900 (64.3 KB)  TX bytes:65900 (64.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:64:72:79  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe64:7279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2510215 (2.3 MB)  TX bytes:379140 (370.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-64-72-79-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```



any explanation please?

---

### Post by caleb12 on 2008-10-23
Explanation... It is normal. 

"The master device wmaster0

mac80211 creates creates one master device and as many other secondary devices as requested to represent interfaces for the wireless card you have. mac80211 asks for the master device to appear as named as wmaster%d, and wlan%0 for the interfaces. udev may override the naming convention used though. wmaster%d is an internal master device used only by mac80211. It is currently visible only because it uses netdevice structure which we must allocate and use for for QoS. It also serves as a holder for all interfaces we have, and represent the underlying hardware. For example, when TXing your wlan0 STA interface will actually add IEEE-802.11 header data to a frame with just Ethernet headers, and then pass it down to the master device for actual transmission using the low level drivers.

The wlan%d devices (interfaces) are the devices you would use to configure your wireless settings. "

More here:

[http://linuxwireless.org/en/developers/Documentation/mac80211](http://linuxwireless.org/en/developers/Documentation/mac80211)

---

### Post by juje on 2009-04-29
ok, i have exactly the same problem...i setup my network according wieman01 ([http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)) and still can't get this to work...how do i fix the logical name of my network?

---

### Post by internalkernel on 2009-04-30
What do you mean the same problem? The OP in this thread didn't know why he had a wmaster0 - this is normal... 

What logical name do you want to change?

---

### Post by ben3896 on 2009-06-27
OK, but explain to be this:
Even though they supposed to be the same, when I run packet capture, I receive different captures for the wmaster0 and the wlan's interface.

Not that this is a problem, it's just curious.

---

### Post by roger97123 on 2010-02-21
I have discovered on my HP laptop that WMASTER0 is the _BUILT IN WIF_I adapter.  It is different than the added wifi (WLAN) cards and wired internet (ETH0) connections in other computers.

Any ideas how to configure Ubuntu Studio 9.04 to use the built in WMASTER0 hardware?

> **craiggale said:**
> could somebody please tell why it is that when i run lshw -C network the logical namme of the interface is wmaster0 and on the connection i am using now the interface is wlan0.  Shouldn't the logical name also be wlan0?

```
craig@craig-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:64:72:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.4 latency=0 module=
``````
craig@craig-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"zoom"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:01:38:8E:01:95   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
craig@craig-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:68:c4:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65900 (64.3 KB)  TX bytes:65900 (64.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:64:72:79  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe64:7279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2510215 (2.3 MB)  TX bytes:379140 (370.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-64-72-79-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

any explanation please?

---

### Post by internalkernel on 2010-02-21
Im not sure what you mean when you say it's different. The wmaster0 is simply the master device for the wlan0, you don't configure wmaster0 directly. 

What is the brand and chipset of your wireless card? I used to have an HP too, and they are notorious for using Broadcom's proprietary crap.

Post the output of the following commands, and maybe we can figure something out... 
```

sudo lshw -C network 
ifconfig
iwconfig

```

---

### Post by roger97123 on 2010-02-21
It is a built in card and the system calls it a networking wireless control interface. My laptop is a HP Pavilion dv2000

---

### Post by internalkernel on 2010-02-21
So... how bout the out put of those commands above? That would help a lot more than the model of your computer.

---

### Post by roger97123 on 2010-02-21
here is what the first command renders:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:3c:c3:ad
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

ifconfig renders

eth0      Link encap:Ethernet  HWaddr 00:16:d3:a2:5f:8a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fea2:5f8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:338240940 (338.2 MB)  TX bytes:9438933 (9.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45960 (45.9 KB)  TX bytes:45960 (45.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:3c:c3:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:77:3c:c3:ad  
          inet addr:169.254.8.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-3C-C3-AD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig renders

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"onh28"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by roger97123 on 2010-02-21
to get on here, I am using my ethernet cable.  Wireless will not work even with switch on.

I am using Ubuntu Studio 9.04
Ubuntu Studio 9.10 locks up ubuntu so I will not upgrade to it

---

### Post by internalkernel on 2010-02-21
> **roger97123 said:**
> here is what the first command renders:

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:3c:c3:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     IEEE 802.11abg  ESSID:"onh28"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So, that's kind of a trip. You wlan0 interface is up, and seems to be working but won't associate... 

What happens when you try to connect to your wireless router? Do you get any errors? 

Try opening a terminal, and typing:

sudo tail -f /var/log/syslog

and then try to connect your wireless, you should see some output that will hopefully be useful. 

Also, post the results from the command: lsmod

&

dmesg | grep iwl3945

~~~~~~
Looks to be similar to this issue: 
[http://ubuntuforums.org/showthread.php?t=1312086](http://ubuntuforums.org/showthread.php?t=1312086)

They are saying to install linux-backports-modules and use WICD instead of Network Manager... 

It's getting late over here, so if you don't hear back from me immediately I'm getting some rest...

---

### Post by roger97123 on 2010-02-21
When I try to use the wireless, the message comes back that internet or server connection is not found.  This is in spite of using network connection and setting up the wireless connection... which seems to connect.  Just not found by firefox or wifi location programs.

---

### Post by internalkernel on 2010-02-21
Here's some more links I came across with similar problems:

[http://ubuntuforums.org/showthread.php?t=813937](http://ubuntuforums.org/showthread.php?t=813937)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226411)

At least you're not alone...

---

