---
title: "ndiswrapper module not loading at boot?"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by AJL on 2007-04-30
I have had this connection working fine until recently.

I have  Broadcom bcm43xx with ndiswrapper and until the other day it has been flawless.

Over the weekend, I went to a place that had free wifi, and had to enter in the essid manually in order to get on.  That worked fine, but upon my next boot it seemed like ndiswrapper module was not loading.

The reason I say that is that if I do a '**sudo modprobe ndiswrapper**' my wlan0 comes to life, I see networks, etc.

The weird thing is, I do a '**sudo ndiswrapper -m**' and get the message:
"**module configuration already contains alias directive**"

My ndiswrapper -l output:
[B]bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)[/B]

I have tried to fumble my way through this, (thats how I discovered that it works if i load the module manually) but I would love to know where to look for WHY this isn't working at boot.

Thanks in advance!

---

### Post by AJL on 2007-04-30
Oh, also...

my /etc/modprobe.d/ndiswrapper contains
"alias wlan0 ndiswrapper"

---

### Post by AJL on 2007-04-30
Interestingly...my /etc/network/interfaces does not contain any mention of the wlan0 device

I tried adding it by hand, but it seems it was overwritten.

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

---

### Post by bmt on 2007-04-30
> **AJL said:**
> ... if I do a '**sudo modprobe ndiswrapper**' my wlan0 comes to life, I see networks, etc.
Make sure that the file /etc/modules contains an entry```
ndiswrapper
```

---

### Post by AJL on 2007-04-30
that did the trick

Thanks for your help!

---

### Post by m0p on 2008-01-15
sorry to bump an old topic 
but i'm having the exact same problem with gusty 

except that 
when i run 
sudo modprobe ndiswrapper
the command hangs 

everything else is pretty the same 

it used to work few weeks ago 
nothing changed in the configuration 

now 
i have to restart a couple of times to get it to work 
i just dont know why this happens 

everything is fine 


ndiswrapper is in /etc/modules

/etc/network/interfaces DOES contain the wlan0 device

sudo ndiswrapper -m' get the message:
"module configuration already contains alias directive"

---

### Post by m0p on 2008-01-16
help anyone ...

sometimes the (( wireless )) disappears from the network manager

after a couple of restarts 
it appears again and works fine 

i just can't figure out why this happens 

help would be apperitiated

---

