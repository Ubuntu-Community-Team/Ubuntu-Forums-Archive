---
title: "Network/Internet not available on login"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by mithion on 2007-03-26
Hi,
   I am having trouble with the wireless configuration stuff.  Everytime I boot up my computer, my network/internet stuff isn't working.  I configure it through the gnome applet with all the right settings, and it doesn't connect.  Even the new network-manager applet sees the access point, but is unable to connect to it for some reason.  I have found a workaround by typing:
```
sudo ifdown ra0
```
followed by
```
sudo ifup ra0
```
and then the card connects to the network and internet access is established.  How do I configure Ubuntu to connect to the right network at login?

---

### Post by will_in_wi on 2007-03-26
Use sudo nano -w /etc/network/interfaces and edit the file to use your adapter.

---

### Post by chili555 on 2007-03-26
I believe the key is:```
auto ra0
```above the ra0 stuff in interfaces. Save, close, reboot.

---

### Post by mithion on 2007-04-02
I apologize for the delay of response.  So I tried adding the auto ra0 in the interfaces file.  The problem is still present which makes no sense to me.  Here's my interface file so you can see if I did something wrong.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid Wireless
```

---

### Post by chili555 on 2007-04-02
Assuming your ethernet and wireless are the only connections you have, I would try trimming my interfaces file to just:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
```When you put in all the settings, what do you put in? Your WEP key and essid? You can certainly drop those into interfaces as well. Here is a sample:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 open
```Please amend as appropriate and reboot and let us know.

By the way, removing wlan0, eth2, ath0, etc. actually speeds up booting by a second or two.

---

### Post by mithion on 2007-04-02
Ok, I cleaned up the file and this is what looks like now.

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid Wireless
```

Speaking of network key, this is my girlfriend's wireless network, and not being very technically inclined, she never established any security for it.  So there is no WEP or WPA encryption, it is a public network.  It is very puzzling as it still doesn't work automatically at login.  I still need to deactivate and reactivate manually the interface for it to work.  What is the next step to make it work?

---

### Post by iduriduridur on 2007-04-04
The fix for this is odd I had to go to synaptic package manager and remove

network-mananger
network-manager-gnome


then sudo gedit /etc/network/interfaces 

I had to put the auto ra0 statement at the END not as BEFORE as suggested above. It works now. Oh and I have stopped updates in Synaptic since it is just an old laptop to browse the web. 



[COLOR="Red"]
auto lo
iface lo inet loopback


iface ra0 inet dhcp
wireless-essid firewalz

auto ra0
[/COLOR]

[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by mithion on 2007-04-04
Iduriduridur, thank you very much.  Your solution has worked.  The network now connects automatically from a fresh start.  This computer is for my mother, so everything has to be automatic and simple since she's not technically inclined.  Hourray for Ubuntu :D.

---

