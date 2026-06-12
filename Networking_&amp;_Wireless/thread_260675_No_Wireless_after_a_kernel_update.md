---
title: "No Wireless after a kernel update"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by chris_aldworth on 2006-09-19
Hi,

I am new to Ubuntu, so please bear with me.

Ubuntu has been working fine for the last couple of weeks until I had a update to the kernel which stoppped all wireless working.


Heres my settings:-

ath0      IEEE 802.11  ESSID:"OBS_NET"
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

jon@OceanBlue9:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:30:1E:CA
          inet6 addr: fe80::214:6cff:fe30:1eca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1734 dropped:0 overruns:0 frame:1734
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:e0320000-e0330000

eth0      Link encap:Ethernet  HWaddr 00:0F:FE:44:13:CD
          inet addr:172.16.98.1  Bcast:172.16.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5448 (5.3 KiB)  TX bytes:5448 (5.3 KiB)

Its a netgear WPN311 which works fine when booting from XP.

Hope You can Help!

---

### Post by kairu0 on 2006-09-19
Stopped working here at some point as well. I have a rt2500 chipset Corega pcmcia card. Power LED stays on, but Link LED doesn't blink anymore.

Have not changed any wifi settings.

---

### Post by spetko on 2006-09-20
Same here!! It seems like the whole wireless support is lost. It worked without a problem until I installed the latest updates. Now I have no wireless. I changed nothing in my configuration.

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:C2:5C:8F
          inet addr:192.168.0.16  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fec2:5c8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2772530 (2.6 MiB)  TX bytes:412935 (403.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2716 (2.6 KiB)  TX bytes:2716 (2.6 KiB)





Please help.

Spetko

---

### Post by spetko on 2006-09-20
hi again!

I resolved the problem by updating restricted modules. See:
[http://www.ubuntuforums.org/showthread.php?t=260842](http://www.ubuntuforums.org/showthread.php?t=260842)

I have no idea why this is not updated automatically.

spetko

---

