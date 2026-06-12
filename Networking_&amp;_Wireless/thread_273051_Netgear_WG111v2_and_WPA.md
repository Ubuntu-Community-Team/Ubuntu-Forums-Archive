---
title: "Netgear WG111v2 and WPA"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by pdania on 2006-10-07
Can someone tell me how they were able to get this to work?  I've followed all the guides out there, first of, it talks about something called network manager which I can't seem to find on my installation (by the way, how do you tell which version of ubuntu you've installed) Windows has a simple command you type in RUN called 'winver'.  I thought I installed the latest Dapper drake which is supposed to come with Network Manager in it's packages.....I haven't found this to be true.  I can get the wireless card to work without using WEP or WPA but I want to secure my connection and use Ubuntu at the same time.

---

### Post by Fass on 2006-10-07
NetworkManager is not automatically installed - you have to install it yourself. If you do it through synaptics, search for "network-manager-gnome" if you're running Gnome or "knetworkmanager" if you're running KDE.

The next thing you need to do is comment out the lines about the cards you want NetworkManager to manage in /etc/network/interfaces. If you don't comment them out, NetworkManager will ignore them. If NetworkManager doesn't work for you, then you will have to manually set up wpa_supplicant, but let's not cross that bridge until you get there, if you do.

To find our what version of Ubuntu you're running, just open a terminal and enter ```
lsb_release -a
```

---

### Post by pdania on 2006-10-08
Thanks for your help mate, I used the command you suggested and I now know that my version of Ubuntu is 5.10 Breezy which is a surprise because I though I installed the latest 6.xx.  So if this is the case I have to use wpa_supplicant which I've sort of struggled with but without success, I'll be very grateful if someone can point me in the right direction on how to do this.  Thanks for all your patience.

---

### Post by pdania on 2006-10-10
Just a quick note to say that I've succeccfully installed Ubuntu 6.06 an to get it to do Wireless was much easier that in Version 5.  I had to fall back to WEP though b/c I couldn't do WPA.  Anyway, this is the farthest I've ever gone with any flavour of Linux before I packed it up but there is something different about Ubuntu and I'm sticking with it!!!!.....It is here to stay!!!!!  Rock on guys!

---

