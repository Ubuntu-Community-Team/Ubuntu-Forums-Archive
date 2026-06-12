---
title: "Wireless Signal Strength"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by DannyG on 2006-11-22
Hi,

I successfuly managed to get my Wireless card up and running flawlessly using a guide I found on here, with ndiswrapper. The card itself is a Broadcom Corporation BCM4318, found in a Dell Inspiron 1300.

The only problem i'm having, which isn't hugely important but it bugs me, is that the Network Manager Icon always shows me as having a 100% connection to my Access Point. Now I know from using Windows on the laptop that this is not the case in the room that i'm in.

Here are the following outputs for common commands:

```
sudo ifconfig
``` gives 
```

eth1      Link encap:Ethernet  HWaddr 00:16:CE:70:5F:A6
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe70:5fa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:84182414 (80.2 MiB)  TX bytes:5682410 (5.4 MiB)
          Interrupt:209 Memory:dfbfe000-dfc00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
```

```
sudo iwconfig
```

gives

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"BTHomeHub-3BDB"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:48:07:5B
          Bit Rate:24 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:11E4-7DDF-36   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-83 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
cat /etc/network/interfaces
```

gives

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid BTHomeHub-3BDB
wireless-key 11e47ddf36

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BTHomeHub-3BDB
wireless-key 11e47ddf36
```

I'm using WPA to connect my AP, and I am well aware that you can see my Access Key here.

Thanks,
Daniel.

---

### Post by DannyG on 2006-11-23
Anyone?

---

### Post by Spin Doctor on 2006-11-23
Danny,

Well, I kind of have the same "problem". But since I worked for a whole weekend to even get my wireless network up running with WPA-PSK, I really dont care if it says 100%. Either you have a working connection or you dont. If it is 10 % or 90 % for me doesnot matter, I guess bandwidth is being affected.

As far as Ndiswrapper driver goes. I read there is a bug with the driver that I have for my DlinkCard. The bug is that does exactly what you say, show signal quality 100% all the time. Since you use a Dlink card, with  Ndiswrapper, you could be using the same driver and therefore experience the same bug.

My wireless networkcard is a D-Link AirPlus g+ (DWL-G650+)

---

