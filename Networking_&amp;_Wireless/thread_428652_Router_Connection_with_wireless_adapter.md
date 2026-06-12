---
title: "Router Connection with wireless adapter"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by RobKan on 2007-04-30
I have installed ndiswrapper for my adapter. with lshw I sow that the driver is loaded. after I check  in iwconfig and see all my wlan1 configuration. ther was this - Access Point: Not Assoiated. 

What sould I do to connect to my Router.:)

---

### Post by Floppyjoe on 2007-04-30
> **RobKan said:**
> I have installed ndiswrapper for my adapter. with lshw I sow that the driver is loaded. after I check  in iwconfig and see all my wlan1 configuration. ther was this - Access Point: Not Assoiated. 

What sould I do to connect to my Router.:)

Are you one of God's chosen people? If you are then Lucky you!

What version of Ubuntu are you using? Have you set up the /etc/network/interfaces file?

---

### Post by brizzlepop on 2007-04-30
Hi!  I'm having the same problem.  Infact, Floppyjoe, it was your tutorial that made my wireless card finally function!  I set up the interfaces file but I'm not really sure I did it right.. 

Before I set it up-- it would say that I'm connected even though I couldn't actually go on the internet, but when I run iwconfig it says "access point: not-associated"
After I set it up--  I'm not able to connect with the network manager but when I run iwconfig it shows an access point

I'm very confused..

---

### Post by Floppyjoe on 2007-04-30
> **brizzlepop said:**
> Hi!  I'm having the same problem.  Infact, Floppyjoe, it was your tutorial that made my wireless card finally function!  I set up the interfaces file but I'm not really sure I did it right.. 

Before I set it up-- it would say that I'm connected even though I couldn't actually go on the internet, but when I run iwconfig it says "access point: not-associated"
After I set it up--  I'm not able to connect with the network manager but when I run iwconfig it shows an access point

I'm very confused..

What does your /etc/network/interfaces file look like?
```
sudo gedit /etc/network/interfaces
```

I'll be back in a little while(Job interview-wish me luck).

---

### Post by brizzlepop on 2007-04-30
Hope the interview went well.  Here is what my interface file looks like:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto eth0

wireless-essid mib1
wireless-channel 11
wireless-mode managed
```


The channel was just a guess, which most likely the problem since I really know nothing about networking!

---

### Post by Floppyjoe on 2007-04-30
Make the file look like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-essid mib1
wireless-channel 11
wireless-mode managed

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
You need to know your router channel number.It can be found in your routers configuration.

---

### Post by RobKan on 2007-05-01
My interface file looks the same like in case of brizzlepop. And will try to do like you said. But why to enter essid and other info to line **auto eth0** and not to **auto wlan0**. I have wireless adapter.

---

### Post by brizzlepop on 2007-05-02
Thank you so much for the help.. my internet is FINALLY working!

I hope that yours will work too RobKan.  Best of luck!

---

