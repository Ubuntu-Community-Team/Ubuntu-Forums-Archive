---
title: "Configuring Wireless With Broadcom 4306"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Paul133 on 2006-08-25
I'm new to Linux. I just installed it last night, and I'm happy to report that with a few adjustments (using the server install and then downloading ubuntu-desktop) everything went very well, and I'm very pleased with Ubuntu! However, I'm having some problems with my WiFi. Ubuntu recognizes the PCMCIA card and here's the output from ifconfig and iwconfig (as a side note, can I change the "username@ubuntu:~$"?) ```
 peter@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:3F:F8:2F:F5
          inet addr:192.168.2.252  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fef8:2ff5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1383247 (1.3 MiB)  TX bytes:186688 (182.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:808 (808.0 b)  TX bytes:808 (808.0 b)

peter@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

This seems like it'll be easy, but I'm just not sure what I should do. Do I need to install ndiswrapper or what? I'm on my home network which is 802.11 g with a hex WEP encryption key and is DHCP. The router is a linksys and I know the ESSID and the IP address of the router. How should I set this up? I won't offer $50 :rolleyes: but any help is greatly appreciated!

Specs for the card: Dell 1350 external 802.11 b/g with Broadcom 4306 chipset.

---

### Post by Paul133 on 2006-08-25
Anyone? My eth0 is the wireless and my eth1 is the ethernet (how I'm online now).

---

### Post by AzraelUK on 2006-08-25
I think you're having [the same problem as me]("http://www.ubuntuforums.org/showthread.php?t=243813"); the Acces Point: Invalid. Try typing:

sudo iwconfig eth0 ap any

in the console. If it still says 'Access Point: Invalid' after that, you're having the same problem as me. If not, that might fix it.

On the side note, it is username@computername, so mine is peter@noob-PC. I'm not sure if you can change that post-install, but you can change it in the installation options while installing ubuntu.

---

