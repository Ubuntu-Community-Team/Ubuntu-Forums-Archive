---
title: "No net connection means severe system lag"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by victorgreen on 2007-09-28
When I boot the computer with my Ethernet plugged in, everything runs great. I can open a terminal in about a second and programs open as they should on a 2.2ghz core 2 duo with 2gbs of ram. 

Then I pull the ethernet!
 
And the system dies...

I will tell it to open a terminal. System monitor shows the process of gnome-terminal running. But no terminal comes up. If I wait for 5 minutes, the terminal window will come up. This goes for every program I open. They take minutes to launch... 

When I plug back in the ethernet, everything is back to normal again. 

This is extremely problematic as taking 5 minutes to open a video when I have my laptop on a bus or plane is ridiculous. 

Any advice as to how to solve this extreme dependence on an internet connection would make my life significantly easier.

---

### Post by victorgreen on 2007-09-28
Oh, and not any connection will do. If I connect to a router that isnt connected to the internet on a LAN, the system still crawls. 

Only when the Ethernet connection is internet does the computer function correctly. 

I would assume that a wireless net connection would also mean system normality but i havnt been able to connect this thing to any wireless network yet.

---

### Post by noob12 on 2007-09-28
Can you post the output of these commands?

```

cat /etc/network/interfaces

cat /etc/hosts

```

and try to capture these while disconnected, save them and post them when connected again: 
```

ifconfig -a

route -n

```

---

### Post by victorgreen on 2007-10-02
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


#auto eth1
iface eth1 inet dhcp

#auto eth2
iface eth2 inet dhcp

#auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/airpennnet.conf

     #   Ive since deleted those extra lines under the wlan settings, its for specific conf to connect to my universities secure w2 network, which Ive never been able to do successfully, it has made no difference 



~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by victorgreen on 2007-10-02
when I disconnect the ethernet I get this:

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D3:C8:00:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82871 errors:0 dropped:1 overruns:0 frame:0
          TX packets:33761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:10549 txqueuelen:10 
          RX bytes:35853501 (34.1 MiB)  TX bytes:5695255 (5.4 MiB)
          Base address:0x1840 Memory:f8200000-f8220000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:C8:00:03  
          inet addr:169.254.4.36  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x1840 Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4840 (4.7 KiB)  TX bytes:4840 (4.7 KiB)


~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


When I reconnect and try ifconfig -a, the eth0 avah goes away

eth0      Link encap:Ethernet  HWaddr 00:16:D3:C8:00:03  
          inet addr:165.123.146.143  Bcast:165.123.147.255  Mask:255.255.254.0
          inet6 addr: fe80::216:d3ff:fec8:3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83235 errors:0 dropped:1 overruns:0 frame:0
          TX packets:34016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:10624 txqueuelen:10 
          RX bytes:36053536 (34.3 MiB)  TX bytes:5727173 (5.4 MiB)
          Base address:0x1840 Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4933 (4.8 KiB)  TX bytes:4933 (4.8 KiB)

---

### Post by noob12 on 2007-10-02
Try right-clicking your NM icon and unselecting Enable Networking either before or after you unplug.

Does performance improve?

Network manager doesn't seem to do a good job when you mix manual and roaming configurations.
If you put both the wired and wireless device in "roaming" mode, you should do better. 

You should also remove the stanzas in /etc/network/interfaces for any interfaces you don't actually have (eth1, eth2, ath0); leave just the section for your loopback in there.

---

### Post by victorgreen on 2007-10-03
Performance was normal if I first unplugged the Ethernet and then disabled networking, it seemed to respond normally. I if disabled networking but left the cable plugged in, terminal still took over a minute to open. When I disabled networking and then pulled the cable the same massive time lag was involved. 

System - Administration - Network tells me that both eth0 and wlan0 are roaming mode enabled. I haven't messed with those settings at all. 

The new /etc/network/interfaces looks like this: [note eth0 wasn't in there when I just checked, I added it]

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by noob12 on 2007-10-03
Take eth0 and wlan0 out too.

The entire /etc/network/interfaces file can be this:
```

auto lo
iface lo inet loopback

```

This is roaming mode on those two interfaces.  If the Network menu was telling you it was in roaming mode when those two entries were there, then it was out of sync with the file.

---

### Post by victorgreen on 2007-10-03
I have cleared out the interfaces to only loopback lo. 

To get the system to run correctly, I still have to pull the cord and then hit disable networking. If I dont, it now starts automatically trying to connect to the wifi which  I cannot connect to here and certain programs I randomly tried opened, but then lagged and terminals would only actually pop open once I plugged the ethernet back in. So now its much more responsive with the cable unplugged but still enabled but still messed up... 

Im not sure what is wrong, but at least I can get it to respond normally after I disable networking. I have yet to test this from cold reboot of the laptop where it has no network cable plugged in. From my experience, that has been especially slow.

---

### Post by Alfr&#1077;do on 2007-10-16
I have the same problem, my notebook runs really slow without the network cable plugged in. Hopefully, someone can tell me what's causing this.

etc/hosts
```
127.0.0.1 localhost
127.0.1.1 p49.vub.ac.be

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

etc/network/interfaces
```
auto lo
iface lo inet loopback




iface eth0 inet static
address 134.184.119.49
netmask 255.255.255.0
gateway 134.184.119.100

auto eth0
```

**Disconnected**

ipconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:40:D0:B8:01:B6  
          inet addr:134.184.119.49  Bcast:134.184.119.255  Mask:255.255.255.0
          inet6 addr: fec0::8:240:d0ff:feb8:1b6/64 Scope:Site
          inet6 addr: 2002:86b8:777d:8:240:d0ff:feb8:1b6/64 Scope:Global
          inet6 addr: fe80::240:d0ff:feb8:1b6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14858131 (14.1 MB)  TX bytes:1326165 (1.2 MB)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10896 (10.6 KB)  TX bytes:10896 (10.6 KB)
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.184.119.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         134.184.119.100 0.0.0.0         UG    100    0        0 eth0
```

**Connected**

ipconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:40:D0:B8:01:B6  
          inet addr:134.184.119.49  Bcast:134.184.119.255  Mask:255.255.255.0
          inet6 addr: fec0::8:240:d0ff:feb8:1b6/64 Scope:Site
          inet6 addr: 2002:86b8:777d:8:240:d0ff:feb8:1b6/64 Scope:Global
          inet6 addr: fe80::240:d0ff:feb8:1b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14849580 (14.1 MB)  TX bytes:1326165 (1.2 MB)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10896 (10.6 KB)  TX bytes:10896 (10.6 KB)
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.184.119.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         134.184.119.100 0.0.0.0         UG    100    0        0 eth0
```

These are some of the errors I see in **syslog**, not sure if they're related.
```
Oct 16 12:30:45 p49 kernel: [  394.140000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000010) is beyond end of object [20070126]
Oct 16 12:30:45 p49 kernel: [  394.140000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.GFX0.DD02._BCM] (Node df844798), AE_AML_PACKAGE_LIMIT
Oct 16 12:30:45 p49 kernel: [  394.156000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000010) is beyond end of object [20070126]
Oct 16 12:30:45 p49 kernel: [  394.156000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.GFX0.DD02._BCM] (Node df844798), AE_AML_PACKAGE_LIMIT
Oct 16 12:30:45 p49 kernel: [  394.172000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000010) is beyond end of object [20070126]
Oct 16 12:30:45 p49 kernel: [  394.172000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.GFX0.DD02._BCM] (Node df844798), AE_AML_PACKAGE_LIMIT
```

---

### Post by noob12 on 2007-10-16
Does putting eth0 down after you disconnect help things?

```

# After disconnecting try this
sudo ifdown eth0

```

---

### Post by Alfr&#1077;do on 2007-10-16
Yes it does, everythings runs fine after putting eth0 down. It also runs fine if I change the connection to "roaming mode" instead of "static IP" and delete my other settings.

---

### Post by noob12 on 2007-10-16
OK.  You may also find that with the static configuration and allow-hotplug things work ok.  You can try that.  See **man interfaces** for details on that.

---

### Post by victorgreen on 2007-10-16
well I I know is whats already up there on the forum, but if you just disable networking from the network manager applet that was a good preliminary to solving my problem and the system ran normally.

---

### Post by Alfr&#1077;do on 2007-10-17
I've tried "allow-hotplug eth0" (then reboot), nothing changed. Then I tried "auto lo eth0" both and without "allow-hotplug eth0", which resulted in no Internet at all.

I know disabling the network is possible, but it's not an option for me. I move my notebook around a lot, so that means I'd have to disable the network in advance. Otherwise, I loose 5-10 minutes waiting for my laptop to boot.

---

### Post by Alfr&#1077;do on 2007-10-18
I've just ran strace, but it doesn't make any sence to me. Should I file a bug report?

```
0.000022 write(10, "\0\4\1\0\3\0\0\0\20\0\0\0\0\0\0\0\10\374V\257\352\233\333"..., 32) = 32
     0.000037 read(10, "\0\10\0\1\3\0\0\0", 8) = 8
     0.000054 read(10, "\7\0GnomeSM\0001.\6\0002.20.02747", 24) = 24
     0.000038 write(10, "\1\1\1\0\1\0\0\0\0\0\0\0\0\0\0\0", 16) = 16
     0.000033 read(10, "\1\2\0\1\6\0\0\0", 8) = 8
    40.117303 read(10, "%\0\0\000103692cb5b000119274827100000"..., 48) = 48
     0.000200 write(10, "\1\f\1\0\n\0\0\0\1\0\0\0p\361]\267\20\0\0\0CurrentDire"..., 88) = 88
     0.000212 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0p\361]\267\t\0\0\0ProcessIDre"..., 72) = 72
     0.000181 write(10, "\1\f\1\0\t\0\0\0\1\0\0\0p\361]\267\7\0\0\0ProgramIDrec"..., 80) = 80
     0.000183 write(10, "\1\f\1\0\t\0\0\0\1\0\0\0p\361]\267\f\0\0\0CloneCommand"..., 80) = 80
```

---

### Post by Alfr&#1077;do on 2007-10-21
Ok, thanks to the people over at GoT, my problem is finally solved. Turns out it's DNS related and you need to add your hostname to "127.0.0.1 localhost" in /etc/hosts. After doing that, everything runs fine. :)

---

