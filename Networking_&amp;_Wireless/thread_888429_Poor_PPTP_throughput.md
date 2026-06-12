---
title: "Poor PPTP throughput"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by SteveTPearce on 2008-08-13
Hi,

I'm trying to configure a VPN on my newly configured Hardy server. So far, I've managed to be able to get the thing up and running and can ping the server on the remote network, connect via ssh, etc. Pings have a dropped rate of about 10%.

The problem comes when I try to browse the Samba shares from a Windows Vista client. The shares are all visible, but refresh slowly and trying to download anything can cause a delay of several seconds before the download starts, and a download rate much slower than the upload rate of the ADSL modem that connects the server to the internet.

Worse is trying to open even a small file on the remote server. The application (e.g. Word) will hang for a minute or more, and often fails to open the file at all. Saving causes much the same problem. This is really my entire reason for setting up the VPN in the first place: to access files on my server from different locations.

My basic question is this: is this as good as it gets? I've limited experience of VPN so I don't know if this is the kind of performance that's typical across VPN, but it seems unlikely. Certainly it compares poorly with ssh or webdav.

I've tried shutting down the firewall at both ends, connecting via two different (wifi) networks and a 3g mobile network, and more internet research than I can bring to mind. Anyone got any comments or suggestions?

Some relevant config details (truncated):
/etc/pptp.conf
```
localip 172.16.0.101-200
remoteip        172.16.254.1-100

```

/etc/ppp/pptp-options
```
ms-dns 172.16.0.1
ms-wins 172.16.0.1
proxyarp

```

ifconfig (with a VPN connection running)
```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:9f:69:36
          inet addr:172.16.0.1  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:8dff:fe9f:6936/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2639964 (2.5 MB)  TX bytes:11083780 (10.5 MB)
          Interrupt:247 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:60:97:d9:21:9c
          inet addr:10.0.0.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::260:97ff:fed9:219c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270613 errors:4049 dropped:0 overruns:0 frame:4101
          TX packets:335645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:71994375 (68.6 MB)  TX bytes:159774123 (152.3 MB)
          Interrupt:18 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:378770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:120973217 (115.3 MB)  TX bytes:120973217 (115.3 MB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:172.16.0.101  P-t-P:172.16.254.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:1115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:98438 (96.1 KB)  TX bytes:154043 (150.4 KB)

```

Thanks in advance,
Steve

---

### Post by SteveTPearce on 2008-08-13
Since my original post, I've modified my network a bit with some interesting results:

I have placed my wireless access point on a network switch connected directly to my ADSL modem. The switch is in turn connected to the server (DMZ). I can now connect to the server via the wireless access point through VPN and it works flawlessly, producing a throughput pretty much in line with that of the wireless router itself, suggesting that the VPN configuration is not at fault.

However, when I access the VPN from outside the ADSL modem (say from my 3g modem or iPhone), problems persist as before. Here's an excerpt from my logs for the connection from the iPhone (via 3g, i.e. passing through the ADSL modem):
```
Aug 13 22:55:41 caliban pptpd[23789]: GRE: accepting packet #293
Aug 13 22:56:07 caliban pptpd[23789]: GRE: accepting packet #294
Aug 13 22:56:33 caliban pptpd[23789]: GRE: buffering packet #296 (expecting #295, lost or reordered)
Aug 13 22:56:34 caliban pptpd[23789]: GRE: buffering packet #297 (expecting #295, lost or reordered)
Aug 13 22:56:54 caliban pptpd[23789]: GRE: timeout waiting for 1 packets
Aug 13 22:56:54 caliban pptpd[23789]: GRE: accepting #296 from queue
Aug 13 22:56:54 caliban pptpd[23789]: GRE: accepting #297 from queue
Aug 13 22:56:54 caliban pptpd[23789]: GRE: accepting packet #298
Aug 13 22:57:04 caliban pptpd[23789]: GRE: accepting packet #299
Aug 13 22:57:14 caliban pptpd[23789]: GRE: accepting packet #300
Aug 13 22:57:34 caliban pptpd[23789]: GRE: accepting packet #301
Aug 13 22:57:35 caliban pptpd[23789]: GRE: accepting packet #302
Aug 13 22:57:54 caliban pptpd[23789]: GRE: accepting packet #303
Aug 13 22:58:04 caliban pptpd[23789]: GRE: accepting packet #304
Aug 13 22:58:23 caliban pptpd[23789]: GRE: buffering packet #306 (expecting #305, lost or reordered)
Aug 13 22:58:35 caliban pptpd[23789]: GRE: timeout waiting for 1 packets
Aug 13 22:58:35 caliban pptpd[23789]: GRE: accepting #306 from queue
Aug 13 22:58:35 caliban pptpd[23789]: GRE: accepting packet #307
Aug 13 22:58:37 caliban pptpd[23789]: GRE: accepting packet #308

```

These lost or re-ordered packets do not seem to be anything like as common for the WiFi connection, i.e. when they're not passing through the ADSL modem. Hence I assume the ADSL modem is causing the trouble, or something further upstream. Is this likely to be the case? Is the MTU size likely to be an issue, and will my ADSL connection suffer if I were to make it bigger? Anyone got any thoughts of anything I could try to further diagnose the problem, or had a more positive experience with PPTP VPN over ADSL so I know I'm not wasting my time trying?

Any thoughts or comments most welcome,

Steve

---

### Post by john_navarro on 2008-11-02
Check out this thread I created - it may help you out.

[http://ph.ubuntuforums.com/showthread.php?p=6087873#post6087873]("http://ph.ubuntuforums.com/showthread.php?p=6087873#post6087873")\

You also may want to consider lowering your MTU for your eth0 as well. I have DSL and have my eth0 MTU set to 1468.

---

