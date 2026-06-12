---
title: "Seeking to permanently fix a &quot;bandaid&quot; solution"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by SWcisel on 2007-10-15
Hi guys,

I was previously unable to get my wireless card to access my network, but am now able to connect by manually entering the following at the command line:
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NetworkName"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
```

When I do this, I can get online, but I still get a "No network connection" icon on my screen. Additionally, I can't use wireshark (it doesn't show any interfaces), though I'm not positive that this is related. Could someone please help me find a more permanent fix (it's mildly inconvenient having to enter those lines every time I need to log on).

I'm using ubuntu 7.04, and the network is unsecured.

---

### Post by openaddict on 2007-10-15
You can add any user configuration to /etc/rc.local and it will be executed every time your computer boots.  If you don't want to do that, create a shell script containing those commands and just run that every time you log in.

---

### Post by SWcisel on 2007-10-15
well sure, but that isn't the standard way of going about it (a wireless adapter and ndiswrapper, etc). Long story short, I'd like that icon in the top-right corner of my screen (Gnome) to indicate that I'm online. Using this hack isn't going to do that for me :).

---

