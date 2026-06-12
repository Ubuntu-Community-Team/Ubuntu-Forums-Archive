---
title: "Intel Wireless-AC 7260 - intermittent connection loss"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by svenmeier on 2015-07-25
Hi all,

after much hassle with a Realtek wifi card on my notebook I switched to an Intel Wireless AC 7260 card.

Now I have new problems :(.

Intermittently the connection drops to my TP-Link mobile router. Sometimes it will re-establish after a few seconds, sometimes I can resurrect the connection by restarting the network manager service. But most of the time I have to reboot the notebook :/.

Please find attached the output of the wireless-info script, once for a successful connection and several others others for when the network manager shows dots instead of the wireless signal symbol, but cannot regain the connection.

Could anyone give me a pointer what might be the cause of the problem?

Thanks
Sven

---

### Post by weatherman2 on 2015-07-25
In the file /etc/modprobe.d/wireless.conf

try changing the option

```
11n_disable=1
```

to

```
11n_disable=8
```

Then reboot

---

### Post by svenmeier on 2015-08-01
Hi weatherman2,

many thanks for your tip, I will try out the option and report back any progress.

Meanwhile I found many reports of problems with Intel 7260 wireless cards. On my system this seems to manifest itself with the following repeated lines in syslog:

```

Aug  1 22:08:00 sandraOrange wpa_supplicant[778]: wlan1: CTRL-EVENT-DISCONNECTED bssid=c0:25:06:ea:4c:8a reason=4 locally_generated=1
Aug  1 22:08:00 sandraOrange NetworkManager[668]: <warn> Connection disconnected (reason -4)

```

Sven

---

### Post by chili555 on 2015-08-01
I suggest you try these steps: [http://askubuntu.com/questions/651462/wifi-connection-not-working-with-intel-nuc-wireless-ac-7620/651474#651474](http://askubuntu.com/questions/651462/wifi-connection-not-working-with-intel-nuc-wireless-ac-7620/651474#651474)

---

