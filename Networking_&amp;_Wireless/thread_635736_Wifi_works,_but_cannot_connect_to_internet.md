---
title: "Wifi works, but cannot connect to internet"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by anon_ on 2007-12-09
i can scan for hotspots, i can what appear to be connected the to router, but it internet doesnt work
tried disabling the wired connect too, nothing

i think the screenshot pretty much sums it up

also, where is the gui what shows you the strength of the signal

---

### Post by anubhavrocks on 2007-12-09
See  the output of 
iwconfig
it says that Access Point is NOt Associated
you have to be associated to get net connection.

---

### Post by A + on 2007-12-09
I've got the same problem.  How do I get the access-point associated?

---

### Post by csat on 2007-12-09
Take those steps pointed out here:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

Check this also:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

---

### Post by anon_ on 2007-12-09
> **csat said:**
> Take those steps pointed out here:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

Check this also:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

too bad those are WPA guides, i'm on WEP

---

### Post by csat on 2007-12-09
> **anon_ said:**
> too bad those are WPA guides, i'm on WEP

Too bad, WEP is less secure than WPA-TKIP-PSK...  Anyhow, although different protocols, the method is similar to put wifi to work.  Think this way.

---

### Post by A + on 2007-12-09
I stupidly tried the WPA sequence in the links and think I switched off my Atheros wifi card!  Help!  Windows doesn't recognise it now either - ubuntu saw a wireless signal before -  and I don't seem to be able to get a driver for it through Vista...Anyway, I did something to it in ubuntu while editing this file

```
sudo gedit /etc/network/interfaces

```


this is what it looks like now after I went back in and uncommented the wpa stuff leaving the auto wlan0 command in the hope that one of the operating systems will see my card on boot-up:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto wlan0

#iface wlan0 inet dhcp
#wpa-ap-scan 1
#wpa-pairwise CCMP
#wpa-group CCMP
#wireless-key bb37b0a2aa52de03158eee3e7c
#wireless-essid eircom6213 7000

#iface wlan0 inet dhcp
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.254
#wireless-key bb37b0a2aa52de03158eee3e7c
#wireless-essid eircom6213 7000

#auto wlan0

auto eth0
```

I really don't know what I'm doing please help.

---

### Post by anon_ on 2007-12-09
well i fixed it

enable free roaming mode does it, lol manual setup

which is gay, because it start it off in free roam mode it didnt work, now it works

cant believe i had a EASIER time setting up Leopard than Ubuntu, that's just sad

---

