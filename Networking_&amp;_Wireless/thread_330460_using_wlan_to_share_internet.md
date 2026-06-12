---
title: "using wlan to share internet"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-01-03
I'm sure that there are similar answers somewhere here and i have looked around but i need definitive help.  I want to achieve something that was pretty easy in XP but is proving a pain and i'm sure i'm not the only one. 
My desktop (ubuntu edgy) is connected to the net via sagem fast usb I have a netgear wg311v3 card which communicates, ad-hoc, with my laptop (ubuntu edgy) which has a built-in broadcom bcmwl5. I want to use the net on my laptop. I got the cards to ping each other successfully, i set up both wlan devices with ndiswrapper (which has to reconfigured each time with iwconfig). 
there's got to be a simple way to do this or maybe i'm the simple one. I'm really enjoying my time with ubuntu, i always wanted to get away from windows, but when i'm not fiddling i need to use the things to do something more constructive than making stuff work.        

I know you can lead me to the light.... somebody... please

---

### Post by spd106 on 2007-01-03
I recommend that you dump the sagem and buy a wireless router with ADSL modem, they are dropping in price all the time and you don't need the latest and greatest.

If not then maybe try adding the command you use to the /etc/network/interfaces file. Assuming you have already set up packet forwarding or a bridge, you use static addresses and WEP, they should look something like this.

For the desktop
```
iface eth1 inet static
pre-up iwconfig eth1 mode Ad-Hoc
address 192.168.0.1
wireless-essid temp
wireless-key xxxxxxxxxx
```

For the laptop
```
iface eth1 inet static
pre-up iwconfig eth1 mode Ad-Hoc
address 192.168.0.2
gateway 192.168.0.1
wireless-essid temp
wireless-key xxxxxxxxxx
```

It should be easily adaptable to WPA or maybe Network Manager could be instead.

---

### Post by fugative on 2007-01-03
No, I'm not dumping hardware. It works fine and it took me two weeks to find out how to make it work and why should i? If windows could do it and it's not a point of hardware support them the sagem stays. 
I've done the /etc/network/interfaces file and that's ok but packet forwarding and stuff no i haven't. shouldn't need a bridge should it , didn't in XP.
suggestions please.

---

### Post by spd106 on 2007-01-03
Try this wiki page [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

I recommend the firestarter method if your new to the terminal since it has a gui, even if it is a bit clunky. Configuring iptables directly isn't too difficult, it's making sure that the changes are persistent if you will be shutting the server/router down regularly. 

Having a DHCP server won't be necessary if you're happy setting static addresses and routes, but it will make things easier if you plan on letting others have temporary access in the future.

---

