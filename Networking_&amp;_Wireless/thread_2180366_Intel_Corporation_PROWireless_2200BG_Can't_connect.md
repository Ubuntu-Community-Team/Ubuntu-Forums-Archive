---
title: "Intel Corporation PRO/Wireless 2200BG Can't connect after Distro upgrade from 10.04"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by HHhcBKQ on 2013-10-12
Hi there people i have a problem.
Ive upgraded my ubuntu laptop to 12.04 and now i can't connect to my wireless network. When i try it connects for 30 seconds and then ask for my password again. Its a WPA2 secured network.

The card is listes as  Intel Corporation PRO/Wireless 2200BG using lspci

Ive been searching forums for quite some hours the last two weeks.

my iwconfig output is this:

```

lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"ZyXEL_88DC"
          Mode:Managed  Channel:0  Access Point: FE:F5:28:1A:88:DC
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```


My lsmod looks like this.

```

ipw2200               146210  0
libipw                 46732  1 ipw2200

```


My best guess is that the system upgraded drivers does not support my old wlan card anymore.
But how do i degrade my drivers?

---

### Post by mörgæs on 2013-10-13
> **HHhcBKQ said:**
> My best guess is that the system upgraded drivers does not support my old wlan card anymore.


Unlikely. It happens very rarely that support for a wifi card is withdrawn. On the contrary, the Intel cards are known for good support.

I am not a network specialist, so I would choose the brute force and reinstall 12.04.3. I won't take offense if you keep the thread open for some time waiting for a more elegant solution.

---

### Post by HHhcBKQ on 2013-10-13
The problem with a reinstall is that it makes some mistakes on the cpu drivers and the system just doesnt work. The solution that worked for me was installing 8.04 then distro upgrade to 10.04 then sadly i upgraded after a few months to 12.04 and now i have alot of trouble.

---

### Post by mörgæs on 2013-10-13
That sounds more than strange. My guess is that your hardware is simply too weak to run a full Ubuntu, judged by the fact that a 2200BG is an old card. Have you tried a fresh install of Lubuntu 13.10?

---

### Post by HHhcBKQ on 2013-10-13
No i havent tested a lubuntu 1310. But my hardware actually works great with lubuntu right now, I have a good connection fair speed and so fourth, just not a functioning Wi-Fi connection.

---

