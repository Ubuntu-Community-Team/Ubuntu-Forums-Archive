---
title: "wireless woes"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by pcnomad on 2006-08-12
I've been battling this wireless card for three days.
Linksys WMP54G PCI Adapter
Linksys WRT54GS Router....set to no encryption
Ubuntu 6.06 on Celeron 433MHz 256Mb ram

ifconfig:

ra0       Link encap:Ethernet  HWaddr 00:16:B6:9A:DA:CF
          inet6 addr: fe80::216:b6ff:fe9a:dacf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8226 errors:7 dropped:7 overruns:0 carrier:0
          collisions:40 txqueuelen:1000
          RX bytes:4733670 (4.5 MiB)  TX bytes:100954 (98.5 KiB)
          Interrupt:9

iwconfig:

ra0       RT61 Wireless  ESSID:"startrek"
          Mode:Auto  Frequency:11 MHz  Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=44/70  Signal level:-121 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ping -c 4 192.168.1.1 -b
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.924 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.791 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.86 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 0.791/1.358/1.862/0.503 ms

I have no clue at this point of what to do next.

---

### Post by wieman01 on 2006-08-12
> **pcnomad said:**
> I have no clue at this point of what to do next.

That's a though question for from what I can see you're connected. Can you outline what your problem is? Please also post the content this file:
> /etc/network/interfaces
Can you or can you not access the Internet?

---

### Post by wieman01 on 2006-08-14
Can you do me favor? Please open the file "/etc/resolv.conf" and post the content here. 

The file should look look like this:
> nameserver xxx.xxx.xxx.xxx

...whereby 'xxx.xxx.xxx.xxx' stands for your router's IP address. Could you edit this file accordingly, then save & reboot?
[U]
Example:[/U]
[http://www.faqs.org/docs/securing/chap9sec91.html]("http://www.faqs.org/docs/securing/chap9sec91.html")

The reason why your computer hangs during boot is that your system is trying to synchronize the clock through the internet. Since you don't seem to have the right name-server (DNS) configured, it fails and just hangs there.

You are connected to the router, but no DNS server is recognized. By adding it to the "interfaces" file and possibly "resolv.conf" this problem should disappear.

---

### Post by pcnomad on 2006-08-15
> **wieman01 said:**
> Can you do me favor? Please open the file "/etc/resolv.conf" and post the content here. 

The file should look look like this:


...whereby 'xxx.xxx.xxx.xxx' stands for your router's IP address. Could you edit this file accordingly, then save & reboot?
[U]
Example:[/U]
[http://www.faqs.org/docs/securing/chap9sec91.html]("http://www.faqs.org/docs/securing/chap9sec91.html")

The reason why your computer hangs during boot is that your system is trying to synchronize the clock through the internet. Since you don't seem to have the right name-server (DNS) configured, it fails and just hangs there.

You are connected to the router, but no DNS server is recognized. By adding it to the "interfaces" file and possibly "resolv.conf" this problem should disappear.
Here is the contents of /etc/network/interfaces.....
#iface ra0 inet dhcp
#wireless-essid startrek

#auto ra0

#iface eth0 inet dhcp

#auto eth0

iface ra0 inet dhcp
wireless-essid startrek

auto ra0

iface eth0 inet dhcp

auto eth0

Here is the contents of /etc/resolv.conf......
nameserver 68.238.0.12                 #(actual primary server)
nameserver 68.238.112.12            #(actual secondary server)

Both of these servers are Verizon

---

### Post by wieman01 on 2006-08-15
Everything looks fine so far actually. I assume you don't have any kind of security (WEP, WPA, etc.) enabled, correct?

However, "interfaces" seems to be incomplete. Could you add the following and restart?
> [B]auto lo
iface lo inet loopback[/B]

auto ra0
iface ra0 inet dhcp
wireless-essid startrek

auto eth0
iface eth0 inet dhcp
Since you are using DHCP, please also change "resolv.conf" (1 single line only):
> nameserver xxx.xxx.xxx.xxx

... whereas **xxx.xxx.xxx.xxx** stands for your router's IP address.

Then restart and see if you can connect.

---

