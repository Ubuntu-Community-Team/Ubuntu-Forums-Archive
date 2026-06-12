---
title: "repairing/refreshing wireless connection"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by poyner on 2005-04-11
hi all, 

my wireless connection works fine after bootup but every now and again it seems to drop out and when this happens I have to restart my computer to get it going again. Is there an easier way to repair/refresh the wireless connection? TIA

---

### Post by accuser on 2005-04-11
From the desktop menu select System -> Administration -> Networking. The network settings dialog box appears with a list of network interfaces. Select the one you want, click the deactivate button, and once deactivated, click the activate button.

You can also do this from the console:

```

$ sudo ifdown eth0
$ sudo ifup eth0

```

Assuming of course that your wireless interface is eth0. Mine isn't, it is wlan0, so beware.

Enjoy!

---

### Post by poyner on 2005-04-11
[QUOTE=accuser]From the desktop menu select System -> Administration -> Networking. The network settings dialog box appears with a list of network interfaces. Select the one you want, click the deactivate button, and once deactivated, click the activate button.

You can also do this from the console:

```

$ sudo ifdown eth0
$ sudo ifup eth0

```

Assuming of course that your wireless interface is eth0. Mine isn't, it is wlan0, so beware.

Enjoy![/QUOTE]

hmmmm ok.. thanks for the tip.... didn't seem to work though....

edit: here's my output. 

```
nathan@ubuntu:~$ sudo ifdown eth1
nathan@ubuntu:~$ sudo ifup eth1 -v
Configuring interface eth1=eth1 (inet)
run-parts /etc/network/if-pre-up.d

ifconfig eth1 192.168.1.103 netmask 255.255.255.0               up
 route add default gw 192.168.1.1  eth1
run-parts /etc/network/if-up.d
nathan@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"xxxxxxx"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
 anyone got any ideas?

---

### Post by poyner on 2005-04-12
[QUOTE=poyner]anyone got any ideas?[/QUOTE]

anyone?

---

### Post by dejitarob on 2005-04-13
It appears your wireless card is not finding your access point. Try 'iwlist eth1 scan' and then 'iwconfig eth1 essid [your essid]'. If this still isn't working you might want to check the wiki [http://www.ubuntulinux.org/wiki/WiFiWithSomeoneElsesRouterHowTo](http://www.ubuntulinux.org/wiki/WiFiWithSomeoneElsesRouterHowTo) [http://www.ubuntulinux.org/wiki/WiFiTroubleshooting](http://www.ubuntulinux.org/wiki/WiFiTroubleshooting) or [http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

---

### Post by S0rin on 2005-04-13
I have the exact same problem and its driving me crazy sometimes it can go for hours without problems then sometimes its cutting off every 30 mins.

---

### Post by poyner on 2005-04-14
[QUOTE=S0rin]I have the exact same problem and its driving me crazy sometimes it can go for hours without problems then sometimes its cutting off every 30 mins.[/QUOTE]
excellent! at least it's not me. :) 
well not really excellent for you... but you know what I mean. Next time it dies I'll be trying the tips above. thanks dejitarob

---

