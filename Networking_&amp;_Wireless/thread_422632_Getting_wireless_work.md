---
title: "Getting wireless work"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Niila on 2007-04-25
The problem is, i cant get my wlan work right. Ive tried all methods i could find with google, but none of them have worked out for me. Ive reinstalled my ubuntu like 5 times in past three days. Now i decided to try kubuntu, but it doesnt look so bright for me.
 It does not connect to my router no matter what encryption i use. Even without encryption at all. Im using linksys wmp54g which uses rt61 driver. I think the driver is ok, as iwconfig says:

```
niila@niila-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-33 dBm  Noise level:-108 dBm        #Sometimes link quality is 0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Btw, i dont understand why is it called ra1 instead of ra0. Anyway, this is what lsmod |grep rt tells me.

```
niila@niila-desktop:~$ lsmod |grep rt
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
rt61                  245128  1
agpgart                35400  1 ati_agp

```

So it looks like the driver is OK. Agree?

Knetworkmanager could not connect to my router. So i downloaded kwlan, but no, all buttons and fields were greyed out, except essid field. So much for that joy.

Heres what sudo ifup ra1 says:

```
niila@niila-desktop:~$ sudo ifup ra1









RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

```

:confused: 

Every single computer in my house (with windows) works like a dream, so whats up with my linux?

---

### Post by RavanH on 2007-05-16
You have hit the BIG issue in Linux ... the cause of many still shying away from migrating to linux :(

Have you tried Wicd? Find it on [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) but you will have to uninstall Network Manager. It used to work for me without encryption, but now not anymore. Don't have a clue as to why, but you might have better luck ;)

---

### Post by Niila on 2007-05-16
I got it working right away after i installed wlan card from my second computer. I guess ubuntu likes atheros -chips more than rt61 :)

---

