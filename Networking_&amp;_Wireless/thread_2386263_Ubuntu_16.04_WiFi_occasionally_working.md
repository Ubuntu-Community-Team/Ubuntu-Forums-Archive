---
title: "Ubuntu 16.04 WiFi occasionally working"
date: 2018-03-03
forum: Networking &amp; Wireless
---

### Post by daredevildas on 2018-03-03
Issue - WiFi works sometimes and sometimes it does not. 
My computer keeps trying to connect to WiFi before giving up (when it is not working). The network is up as my other devices successfully connect to it.

I have a TP-LINK TL-WN725N Ver:2.0 in addition to the inbuilt wireless card on my laptop. The same error is true for both the external and internal wireless cards. 

The solution given here - [https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing](https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing) used to work and had me satisfied for a month or so but that work around hasn't been working for the last couple of weeks inspite of restarting network-manager.

I ran this in my terminal when connected via ethernet - 

```

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

```

And got the following results - [http://paste.ubuntu.com/p/NcBb6XWY3D/](http://paste.ubuntu.com/p/NcBb6XWY3D/)

Would love some help in this regard. Thank you.

---

### Post by chili555 on 2018-03-03
Please see my answer here: [https://askubuntu.com/questions/1011458/ubuntu-16-04-wifi-sometimes-working-and-sometimes-not/1011541#1011541](https://askubuntu.com/questions/1011458/ubuntu-16-04-wifi-sometimes-working-and-sometimes-not/1011541#1011541)

---

