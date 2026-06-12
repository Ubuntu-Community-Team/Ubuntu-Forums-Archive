---
title: "Need help with Intel 2200BG on HP DV1000..."
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Wheelman on 2006-09-17
Hello all, I'm running the latest ubuntu live cd.  I have really wanted to convert a computer to linux for a while now, and after trying several different versions of linux live cds, I can't for the life of me get wireless  working.  This is the only thing holding me back from doing a full install on this computer.  If I had an internet connection, no other problems would bother me because I could search the answers without having to go to another computer :D 

Anyway, here is my problem.  I have a HP DV1000 with the Intel 2200BG Wireless chipset.  I am trying to connect to my 2wire dsl modem/wireless gateway.  Its set to "WEP - Open"  Here are the steps I take when I boot up the live cd in an attempt to get it to connect. 

1) Turn on wireless switch.  Both lights on my computer light up.
2) In network settings the wireless interface eth1 is active.
3) Select my SSID from the dropdown list, key type is "hexadecimal" and i enter my wep key.  It is configured for DHCP.
4) Signal is at 100% based on the bar in the top right hand corner, but yet I still cannot connect to the internet :(
5) DNS server autopopulates as does search domain "gateway.2wire.net"

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"2WIRE821"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:41:78:A1
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-26 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C2:7B:C3
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fec2:7bc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14327 (13.9 KiB)  TX bytes:161035 (157.2 KiB)
          Interrupt:201 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:12:F0:EC:3E:DA
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:feec:3eda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:935326 (913.4 KiB)  TX bytes:2688 (2.6 KiB)
          Interrupt:177 Base address:0x8000 Memory:b0107000-b0107fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6404 (6.2 KiB)  TX bytes:6404 (6.2 KiB)

```

Anyone see anything wrong here or know what else I can try next?

Thanks in advance, :D

---

### Post by sjieke on 2006-09-19
Is eth0 (wired) also connected to the gateway?

In the output of ifconfig it also has an ip-adres in the same subnet. This could result in a messed up routing table, so your pc is trying to access your gateway through eth0 instead of eth1.

It's a wild guess, but you could try disabling eth0...

---

### Post by naruto-kun on 2007-02-08
I get the same problems, ony for me, it used to be working, but now its not. The thing is, I dont remember what I did to the connection settings...my next post wiill have the file...
:(

---

### Post by naruto-kun on 2007-02-10
ok so it works now, but it does not automatically detect networks.

---

