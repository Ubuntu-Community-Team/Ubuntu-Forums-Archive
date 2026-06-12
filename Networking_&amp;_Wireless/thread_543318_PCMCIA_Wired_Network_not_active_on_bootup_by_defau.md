---
title: "PCMCIA Wired Network not active on bootup by default"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by tallthom on 2007-09-05
New Ubuntu user question;

Are PCMCIA network cards not automatically activated on bootup by default?:confused:

I have a XIRCOM PCMCIA Ethernet card which works properly, but every time I reboot the machine, I have to click on the network monitor in the taskbar and enable the network adapter manually before it comes to life.

Using Ubuntu 7.04 on a DELL Inspiron 8100.

---

### Post by noob12 on 2007-09-05
Do you have an **auto** directive line for that interface in your **/etc/network/interfaces** file?

For additional help, you should post the output of these two commands
```

ifconfig -a

cat /etc/network/interfaces

```

---

### Post by tallthom on 2007-09-12
Sorry so slow...  here is the requested output:

sam@Samwise:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A4:C2:E2:F9 
          inet6 addr: fe80::210:a4ff:fec2:e2f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:20664 (20.1 KiB)
          Interrupt:10 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:15:00:48:EB:0F 
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe48:eb0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:1 dropped:1 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:631472 (616.6 KiB)  TX bytes:53016 (51.7 KiB)
          Interrupt:10 Base address:0x8000 Memory:f8ffd000-f8ffdfff

eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:C2:E2:F9 
          inet addr:169.254.12.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5628 (5.4 KiB)  TX bytes:5628 (5.4 KiB)


sam@Samwise:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

