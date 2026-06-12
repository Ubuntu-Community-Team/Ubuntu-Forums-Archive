---
title: "Wireless card wont configure"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by Jsgrabo on 2007-03-08
Ok heres the deal: I had Ubuntu 5.10 installed and my wireless card worked very nicely after installing the driver with ndiswrapper. Earlier today i upgraded to Ubuntu 6.06. When I go to Networking, my wireless card is still there and it just says that it needs to be configured. I click "properties" and then enable it. THis is my problem: When I click to view the availible networks, nothing shows up. I know theres nothing wrong with my basestation because my other computer is connected to it and works fine. Any suggestions? oh, and the wireless card is a Linksys WPC54GS v1.1 Broadcom 4306.

Thanks

---

### Post by jml on 2007-03-08
Several possibilities.  The newer version of Ubuntu may now recognize your wireless card and loads native drivers.  This is the case with cards using the Broadcom Chipset.  Many times these drivers do not work well and they interfere with ndiswrapper and the Windows drivers functioning.  It might be helpful if you past the output of ifconfig, iwconfig, and lspci here.  People might be able to give you more help.

Joe

---

### Post by Jsgrabo on 2007-03-08
ok thanks. Heres the ifconfig:
```
 
eth0      Link encap:Ethernet  HWaddr 00:11:5B:6C:EB:AA
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe6c:ebaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31921494 (30.4 MiB)  TX bytes:1015196 (991.4 KiB)
          Interrupt:225 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1399445 (1.3 MiB)  TX bytes:1399445 (1.3 MiB)

```

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by chili555 on 2007-03-09
Do you have any better luck with the ethernet connection off? I notice your eth0 has an IP address, but I'm not too sure you will, even with considerable tinkering, get two interfaces connected with two separate IP addresses. 

I'd try sudo ifdown eth0, then disconnect the ethernet cable, then do sudo dhclient eth1. 

I do realize if you cannot get your wireless working, you have to connect with eth0 to post replies.

---

