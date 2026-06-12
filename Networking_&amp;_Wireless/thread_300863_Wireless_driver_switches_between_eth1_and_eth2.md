---
title: "Wireless driver switches between eth1 and eth2"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by calvmari on 2006-11-16
Hi All,

   First thank you for your help if you're looking here, it's much appreciated! Anyways, on to the problem. When I boot up my computer in to Ubuntu Dapper 6.06, there's a chance the wireless driver will either be eth1 or eth2. When the driver is eth1, everything works fine and I can access the internet, but when the wireless driver boots as eth2 the wireless driver won't work.

   My knowledge of Linux networking is limited so let me explain what I mean by not working: The network icon in my task tray will have a red minus symbol on it, and when I click on it, it gives me the error that no network driver (eth1) is found. I try to go to System --> Administration --> Networking, and eth2 appears as my wireless driver, and it does say it's working fine. However, the text at the bottom: "Default Gateway Device: " will be blank. I can select eth2 as my default gateway and click OK, but it'll hang for a bit, exit, and when I go back in "Default Gateway Device: " will be blank again!

Here's a look at my ifconfig when the computer is working, you'll notice eth1 is present as my wireless...

```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:82:78:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

eth1      Link encap:Ethernet  HWaddr 00:13:CE:63:78:C2
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe63:78c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1530 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1422097 (1.3 MiB)  TX bytes:174520 (170.4 KiB)
          Interrupt:10 Base address:0x8000 Memory:e0206000-e0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.214.1  Bcast:192.168.214.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.11.1  Bcast:172.16.11.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Here's ifconfig when my wireless doesn't work, you'll notice eth1 is gone and in it's place there's eth2...

```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:82:78:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

eth2      Link encap:Ethernet  HWaddr 00:13:CE:63:78:C2
          inet6 addr: fe80::213:ceff:fe63:78c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:10 dropped:10 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2448 (2.3 KiB)
          Interrupt:10 Base address:0x4000 Memory:e0206000-e0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.214.1  Bcast:192.168.214.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.11.1  Bcast:172.16.11.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

My system is a Dell 700m Inspiron, Dapper 6.06.
Device manager says my wireless card is an Intel 82801 Mobile PCI Bridge, and under that it's sub classified as PRO/Wireless 2200BG.

Any help is appreciated. Right now it's a crap shoot if wireless works in Linux or not, which is a pity since I have to boot in to my Windows partition and use the wireless from there (where it works perfectly). Any help is appreciated, thank you!

---

### Post by hal10000 on 2006-11-16
Hello calvmari,

first thing you can try is to look into the file /etc/network/interfaces:

```
sudo nano -w /etc/network/interfaces
```

and look if there is an entry for the eth2 device. It may look like ```

auto eth2
iface eth0 inet static
...

```

or something similar.
If there is such an entry, then you should comment out these lines (with #).
if there us no such entry then you can run the program "network-admin" or "wlassistant" (from console or menu) and delete or deactivate your "eth2"-device. I think you can remove it, because both your eth1 and eth2 devices have the same MAC-Address (HWaddr 00:13:CE:63:78:C2), which indicates that it is the same Hardware.

Hope it can help you.

---

### Post by FrodoB on 2006-11-16
You can permanently lock a particular device to a name using /etc/iftab:

Edit /etc/iftab and assign your device to a permanent name.

Here is a typical file:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:f0:13:43:23:45 arp 1

Just put in a record with the MAC identifier for the device that you wish to be eth0 in this case.

---

### Post by calvmari on 2006-11-16
Thank you for your advice! :) 

Once I get home in the afternoon I'm going to give that advice a shot, then I'll edit this post to say how it went.

---

### Post by calvmari on 2006-12-09
Hey All,

I still have no real luck on this issue. The wireless driver still switches between eth1 and eth2, and I can't force it to be eth1 when it "wants" to be eth2.

The good news is that when it becomes eth2, I can double click on the network icon in my task tray, set it to eth2, and it will show up as full signal strength. If I set it up in network settings, eth2 now says it has a full connection and it's full connected. However, no internet. It says it's fully connected, but I can't ping anything. This is a large issue because now, especially since I've switched to edgy, it likes to be eth2. Anyway I can do anything to connect to the internet? When it's eth1, it accesses the internet just fine, when it likes to be eth2, it says its connected and reports that it's second and receiving packets, but it doesn't let me ping outside of localhost.

Any further advice is appreciated, thank you.

---

