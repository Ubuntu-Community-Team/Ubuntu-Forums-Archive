---
title: "Wireless working with wpa_supplicant but not with nm-applet"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by gronbaek on 2007-04-16
I got a problem with my wireless network using feisty. It worked for a while, but not any more.
When I log in to Gnome, the network manager correctly detects any access points in my area. But I cannot get any of them to work. It looks like it actually connects, but that I don't get an IP from DHCP. This is also the case if use Wifi-radar.

If I look at /var/log/syslog I keep getting lines like this (and lots of other stuff):
```

Apr 16 22:50:54 loke ifplugd(ath0)[3671]: Executing '/etc/ifplugd/ifplugd.action ath0 up'.
Apr 16 22:50:54 loke ifplugd(ath0)[3671]: client: Ignoring unknown interface ath0=ath0.
Apr 16 22:50:54 loke ifplugd(ath0)[3671]: Program executed successfully.
Apr 16 22:51:02 loke kernel: [ 3494.457282] ath0: no IPv6 routers present

```

But eventually the network-manager dialog will appear and ask me for the passkey again. And I should note that this if exactly the same whether the access point is encrypted or completely open. So even if it is unencrypted a passkey dialog appears.

But then... if I write a wpa_supplicant.conf file with the relevant information, and use the wpa_supplicant tool
```

sudo wpa_supplicant -Dmadwifi -iath0 -c /etc/wpa_supplicant.conf &

```
followed by
```

sudo dhclient ath0

```
I can connect without any problems.

Could somebody give me some sort of hint about what to do, to get the applet working again?
I've googled this intensively and found lots of people with problems, but nothing that really was identical to this, and no solutions that I could use. Maybe I am searching for the wrong thing?

My network card is a Gigabyte type (not completely sure of the type) and I use the Atheros HAL driver accordingly to Ubuntu Resticted Drivers.

Please somebody?

---

### Post by Jouke74 on 2007-04-18
Same problem here. Also when using WIFI radar btw. (Asus Wl-138g, ndiswrapper 1.42, network-manager).

---

### Post by wyth on 2007-04-18
I'll pile on.  Since the latest NM update, I've not been able to log into any secured networks.  Quite annoying.  Has a bug been filed?

---

