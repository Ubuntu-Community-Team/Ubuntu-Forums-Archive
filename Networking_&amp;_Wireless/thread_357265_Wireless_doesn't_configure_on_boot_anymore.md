---
title: "Wireless doesn't configure on boot anymore"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Tonren on 2007-02-09
I have a wireless card - bcm4318 running with ndiswrapper.  Up until a few days ago, it was able to successfully configure itself on boot with the follogin /etc/network/interfaces:

```
auto wlan0 inet dhcp
   wireless-ap any
   wireless-essid any
```

Now, however, when I boot up, it hangs on "Configuring network interfaces" for about eight years.  When I check daemon.log, I see that dhclient unsuccessfuly tries to connect during boot.

When I get into KDE, however, I can do "sudo iwconfig wlan0 essid any; sudo dhclient -1 wlan0" and
it works perfectly.  What is happening when I log in that ISN'T happening during boot?

---

### Post by spd106 on 2007-02-09
The interfaces file should look like this
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid any
```
Make sure you have an iface line and the auto line is separate from the the other stanza. See **man interfaces** for more details.

---

### Post by Tonren on 2007-02-10
spd - Sorry, I mis-typed before.  This is the actual contents of my /etc/network/interfaces:

```
auto lo wlan0

iface lo inet loopback
iface eth0 inet dhcp

iface wlan0 inet dhcp
	wireless-ap any
	wireless-essid any
```

---

### Post by Tonren on 2007-03-13
Can anyone help me out here?  I'm sure there's a way to get this working.  Why doesn't this work on boot?  Is it because ndiswrapper doesn't get loaded in time, or something?  What could be wrong?

---

