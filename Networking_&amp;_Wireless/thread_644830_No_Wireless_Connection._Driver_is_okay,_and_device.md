---
title: "No Wireless Connection. Driver is okay, and device is recognized and turned on."
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Duffadash on 2007-12-19
Hi there.

My new lappy (Medion Model: MD 96350) have an Intel 3945 card.
Ubuntu automatically found and installed the driver (showed up in a nice big "Restricted Drivers" message, where I enabled it), and Ubuntu can easily find the actual card, which it also notes is turned on. The only problem now is... I have no wireless connection. I found a few guides which I ran through, and you can see the output of the different commands here:

```

*lshw:*
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945


*lsmod:*

Module                  Size  Used by
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211


*iwconfig:*

lo        no wireless extensions.
eth0      no wireless extensions.

```

Any idea why I have no wireless? Or more importantly; how to fix it?

Thank you for you kind help.

---

### Post by The Tronyx on 2007-12-19
Did you try running 
> 
sudo ifup wlan0 (or whatever your wlan# is)


---

### Post by Duffadash on 2007-12-19
```
duffadash@Arkhe:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

duffadash@Arkhe:~$ sudo ifup wlan1
Ignoring unknown interface wlan1=wlan1.

duffadash@Arkhe:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

duffadash@Arkhe:~$ sudo ifdown wlan1
ifdown: interface wlan1 not configured
```
nothing

---

### Post by Howl01 on 2007-12-19
I have the same problem - and I cannot figure it out.

---

### Post by jken146 on 2007-12-19
Please post the output of ```
iwconfig
```

---

### Post by Duffadash on 2007-12-19
I already have:
```
duffadash@Arkhe:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by Duffadash on 2007-12-20
Please? Anyone? Help?
(Sorry for the double update, but I'd REALLY like to get this solved...)

---

### Post by Kenny GSO on 2007-12-20
hi ...just wondering if you have tried once you enabled the driver...this

sudo apt-get install linux-restricted-modules-generic

then reboot to activate and configure...might work

---

### Post by Duffadash on 2007-12-20
linux-restricted-modules-generic is already the newest version, should I try reinstalling it, or would that be foolish?

---

### Post by Kenny GSO on 2007-12-20
not really seems fine... if your using a newer ubuntu 7.10 etc...then it might be a driver teething problems...seeing your not the only one having this issue

perhaps some of our more advanced members will know the score

sorry cannot help further... am running 7.10 gutsy on PC as main access point and dapper on my Laptop   using wireless  intel pro card... not had any problems at all with my wireless router after installing 7.10

---

### Post by Duffadash on 2007-12-20
I just downloaded and installed this version of Ubuntu 7.10 a few days ago, so might just be that, but I dunno. I'd love getting it to work though, as I use this PC every day at school and the school only offers wireless internet...

---

### Post by Kenny GSO on 2007-12-20
take a look at this thread...could be the solution to your problem

[http://ubuntuforums.org/showthread.php?t=641801](http://ubuntuforums.org/showthread.php?t=641801)

and this

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

good luck

---

### Post by Duffadash on 2007-12-20
okay, I've edited my /etc/network/interfaces from this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

To this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

# The wireless network interface
auto eth1
iface eth1 inet dhcp
```

And iwlconfig still prints:
```
duffadash@Arkhe:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

and the eth1 are nowhere to befound in the NetworkManager...

(eth1 seems to be the connection I want based on [this thread](http://ubuntuforums.org/showthread.php?t=501314))

<edit>
also tried to uninstall and reinstall the linux-restricted-modules... No difference... Just added:
```
auto wlan0
iface wlan0 inet dhcp
``` to /etc/network/interfaces... No difference at all...

---

### Post by Kenny GSO on 2007-12-21
damn its not recognizing it all is it no matter what your trying

on my dell 630m laptop the card i have is Intel Pro 2200BG and not been a problem at all eth1 shows up fine...

i will keep looking about for possible solutions for you

btw...have you checked for firmware updates for your router ?

and on a footnote...you might get some support from this place?

 ipw3945.sf.net

see thread

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

> Works perfectly on a fresh Ubuntu 6.06 (Dapper) installation. On older versions, works if you manually install the ipw3945 module (from ipw3945.sf.net), the ipw3945 daemon and the ipw3945 firmware ucode (requires ieee80211 kernel support). Not detected at all on [WWW] my system. Automatically detected and correct drivers loaded on Edgy.

---

### Post by FoxOne on 2007-12-21
try this, It worked for me

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by kevdog on 2007-12-21
What you take a look at this tutorial primer:
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

