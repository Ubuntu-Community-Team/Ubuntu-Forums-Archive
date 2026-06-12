---
title: "DWL G-520M not recognized"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Famicommie on 2007-01-04
Running 32bit Dapper

This is the second wireless card I've tried to get running on Ubuntu. It's a D-Link DWL G-520M. It has the atheros architecture. Router information is accurate.

My very first problem with it is that neither the madwifi drivers seem to recognize it, and ndiswrapper doesn't seem to be doing any good either.

I'm a graduated newbie (been reading a LOT lately :D ) But this wifi stuff has me in completely over my head. All I can give you at the moment is the output of lspciI:

```
0000:02:08.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0020 (rev 01)

```

I'm certain that's the device.

Is there a conflict between madwifi and ndiswrapper? Why isn't the system recognizing it? Is there a way to "tell" ubuntu what it is? What do I have to do after I have it identified?

EDIT: Followed the help wiki ndiswrapper guide and no luck. Here are the outputs of various commands:

tail /var/log/messages
```
Jan  4 06:28:58 localhost kernel: [17180898.148000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  4 06:29:43 localhost gconfd (root-7205): starting (version 2.14.0), pid 7205 user 'root'
Jan  4 06:29:43 localhost gconfd (root-7205): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  4 06:29:43 localhost gconfd (root-7205): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan  4 06:29:43 localhost gconfd (root-7205): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  4 06:29:43 localhost gconfd (root-7205): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  4 06:29:43 localhost gconfd (root-7205): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  4 06:29:52 localhost kernel: [17180952.420000] skge eth0: disabling interface
Jan  4 06:30:13 localhost gconfd (root-7205): GConf server is not in use, shutting down.
Jan  4 06:30:13 localhost gconfd (root-7205): Exiting
```

sudo ifdown wlan0
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1928 (1.8 KiB)  TX bytes:1928 (1.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:1C:DA:6D  
          inet6 addr: fe80::213:46ff:fe1c:da6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:f5000000-f5020000
```

sudo ifup wlan0
```
wlan0     IEEE 802.11b  ESSID:"Ordinance"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ndiswrapper -l tells me that both the device and driver are present.

---

### Post by spd106 on 2007-01-04
Madwifi doesn't appear to support this card yet [http://madwifi.org/wiki/Compatibility#DWLG520M](http://madwifi.org/wiki/Compatibility#DWLG520M), so you will have to use ndiswrapper. Maybe try downloading the latest version 1.33 from the ndiswrapper website on sourceforge. You will also need to install the build-essential package.

The madwifi driver is in the linux-restricted-modules package, remove this to get rid of it or add ath_hal to the disabled modules in /etc/default/linux-restricted-modules-common file

---

### Post by Famicommie on 2007-01-05
I added ath_hal to the disabled modules, did a complete reinstall of ndiswrapper, downloaded the latest drivers for the card from D-Link's website, and lost complete sight of wlan0.

output of tail /var/log/messages
```
Jan  5 01:52:44 localhost gconfd (fami-5234): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  5 01:52:44 localhost gconfd (fami-5234): Resolved address "xml:readwrite:/home/fami/.gconf" to a writable configuration source at position 1
Jan  5 01:52:44 localhost gconfd (fami-5234): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  5 01:52:44 localhost gconfd (fami-5234): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  5 01:52:44 localhost gconfd (fami-5234): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  5 01:52:47 localhost gconfd (fami-5234): Resolved address "xml:readwrite:/home/fami/.gconf" to a writable configuration source at position 0
Jan  5 01:56:18 localhost kernel: [17179838.048000] ndiswrapper version 1.33 loaded (preempt=yes,smp=no)
Jan  5 01:56:18 localhost loadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver version 1.9 
Jan  5 01:56:18 localhost last message repeated 8 times
Jan  5 01:56:18 localhost kernel: [17179838.084000] usbcore: registered new driver ndiswrapper
```

What's wrong now? ifconfig and iwconfig don't even list the device, whereas I could see it before...

---

### Post by spd106 on 2007-01-05
Check you completely removed the old version of ndiswrapper before building the new one, a few details [here]("http://www.ubuntuforums.org/showthread.php?t=190614")

---

### Post by Famicommie on 2007-01-06
Completely reinstalled ndiswrapper again, following the directions in the link you posted to the T. 

output of tail /var/log/messages:
```
Jan  6 01:55:15 localhost kernel: [17266169.784000] ndiswrapper: driver net5513 (D-Link,09/12/2005,1.0.0.56) loaded
Jan  6 01:55:15 localhost kernel: [17266169.788000] **** SET: Misaligned resource pointer: dc4cb9c2 Type 07 Len 0
Jan  6 01:55:15 localhost kernel: [17266169.788000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Jan  6 01:55:15 localhost kernel: [17266169.788000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
Jan  6 01:55:15 localhost kernel: [17266169.820000] ndiswrapper: using IRQ 217
Jan  6 01:55:15 localhost kernel: [17266169.820000] ndiswrapper (ExAllocatePoolWithTag:1009): Windows driver allocating 171840 bytes in interrupt context: 0, 0, 0
Jan  6 01:55:16 localhost kernel: [17266170.320000] wlan0: ethernet device 00:13:46:1c:da:6d using serialized NDIS driver: net5513, version: 0x10000, NDIS version: 0x501, vendor: '', 168C:0020.5.conf
Jan  6 01:55:16 localhost kernel: [17266170.320000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Jan  6 01:55:16 localhost kernel: [17266170.328000] usbcore: registered new driver ndiswrapper
Jan  6 01:55:16 localhost kernel: [17266170.824000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

EDIT: never mind, wlan0 just showed up in ifconfig and is apparently ready now >_<

---

### Post by Famicommie on 2007-01-07
UPDATE:

I finally got ndiswrapper to work. Taking advice from someone in the Ubuntu IRC channel, I also installed the GNOME Network Manager. Now this is where things get really odd.

I can see the network of someone else in the neighborhood (she lives two houses down), but my own network doesn't show up. I have a linksys router that I've set to broadcast, so I don't understand why it wouldn't show up in the list. Even after putting the ESSID and WEP hex into the GNM I still can't access my router. The laptop I have sitting right next to me has a full connection, though. What's wrong now? (I'm two floors above the location of the router).

---

### Post by spd106 on 2007-01-08
Have you tried **sudo iwlist wlan0 scan**, to scan for nearby APs?

---

### Post by Famicommie on 2007-01-09
No scan results. I could try moving the computer down to the basement where the router is kept to see if I can find it then, if that would be helpful/necessary. But I still don't see how a tiny laptop wifi card could find the AP (and my FAILdows partition can also find it) while Ubuntu can't.

---

