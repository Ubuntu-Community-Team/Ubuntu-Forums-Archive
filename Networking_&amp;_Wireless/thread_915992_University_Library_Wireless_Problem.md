---
title: "University Library Wireless Problem"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by vaiden on 2008-09-10
Hi there!

I know this forum is for Ubuntu, but I think the solution may be similar when using other distributions as well. I have Fedora 8 with Ratpoison as the only WM installed on a Macbook Pro. Wireless works with Ndiswrapper and Windows drivers for the Apple Airport card.

I usually connect the laptop to open WiFi networks as well as encrypted ones without problems. But the university on which I study has a WiFi network which, when I use Mac OS X, require login through the web browser. There are no problems when I use the OSX partition - I just pick the network called GoteborgsUniversitet and open my browser. Then I log in with my password and everything works.

When I connect with my Fedora partition

```
sudo /sbin/iwconfig wlan0 essid GoteborgsUniversitet
```

it seems to connect without problems. 

```

wlan0     IEEE 802.11g  ESSID:"GoteborgsUniversitet"  Nickname:"macbookpro.johansson"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:7D:BD:8C:B7   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But when I launch Firefox, it tells me that "the server wasn't found".

I don't understand why it doesn't automatically redirect me to the login page. Help is much appreciated!

/Vaiden

---

### Post by vaiden on 2008-09-12
Anyone? :(

---

### Post by coppercow on 2008-10-12
I'm having the same problem, it worked for a while, now it simply fails redirect correctly.. 

Sucks i have to rely on windows to connect to my university wireless network..

I'm using latest Kubuntu hardy..Won't work in Konquerer or Firfox.

---

### Post by coppercow on 2008-10-13
Has anyone come across this problem and fixed it? could the school be blocking the mac? I ping the redirect site and get no response I ping my gateway and get a response. 

Any Ideas? Help? Support? anything? :)

---

### Post by lhansen on 2008-11-11
I am also having the same problem with no solution. According to System Monitor I am actively transfering data, but Firefox won't redirect. This did work for me in Hardy, but I was using wicd instead of network manager. Intrepid, ipw2200, Network Manager, University of Minnesota wireless.

---

