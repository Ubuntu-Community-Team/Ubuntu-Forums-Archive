---
title: "Dapper - Wireless doesn't work on boot"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by jimmymac on 2006-07-30
Hi guys,

My wireless won't work on bootup.  I have to take the card down and bring it back up again.  :confused: 

All the modules are loaded etc.

It just doesn't connect to the AP.

Any ideas?

TIA

Jimmy

---

### Post by costoa on 2006-07-30
Could you please post a copy of your /etc/network/interfaces please?

---

### Post by jimmymac on 2006-07-30
I certainly will when I get home from work.

Cheers,

Jimmy

---

### Post by jimmymac on 2006-07-30
/etc/network/interfaces reveals:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid galaxy
wireless-key d403f82bce4a3206eed791554d

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Cheers,

Jimmy

---

### Post by Stinger on 2006-07-30
You seem to be using the eth1 network interface , but wlan0 indicates you have ndiswrapper installed too , is this correct ?

If it's so I think you'll need to remove ndiswrapper so that it won't interfere with the build in driver , you don't seem to use it anyway.

hope it helps.:smile:

---

### Post by jimmymac on 2006-07-30
Ok, I've removed ndiswrapper.
I still have the same problem and the interfaces file is still the same.
Do I need to remove the wlan0 lines manually?

I'm using fwcutter for the BCM43xx wireless btw.

Cheers,

Jimmy

---

### Post by Stinger on 2006-07-30
> **jimmymac said:**
> 
Do I need to remove the wlan0 lines manually?
Jimmy

You can do that , but instead try recofiguring you network interface using System > Administration > Network , remember to deactivate the unused interfaces , preferably in BIOS if possible.

BTW Have a look here [ HOWTO: getting wireless BCM43xx on Ubuntu Dapper to work.]("http://www.ubuntuforums.org/showthread.php?t=180936")

---

### Post by jimmymac on 2006-07-31
The wlan0 interface wasn't in System -> Administration -> Networking
I removed the wlan0 line from the /etc/network/interfaces file.
I also worked out that if I take the card down and bringing it back up by:

sudo ifconfig eth1 down
sudo ifconfig eth1 up

the wireless doesn't work.

I have to deactivate it and activate with the GUI interface.

Any other ideas?

TIA

James

---

### Post by Stinger on 2006-07-31
> **jimmymac said:**
> 
Any other ideas?

TIA

James
Did you check out the link to the Howto on my previous post ?
There seems to be two ways to setup your card , one using the build in driver and another method using ndiswrapper.
Have a look , if you haven't been there already.

Hope it helps.

---

### Post by costoa on 2006-08-06
Instead of:

```
auto eth1
iface eth1 inet static
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid galaxy
wireless-key d403f82bce4a3206eed791554d
```

Try this instead:
```

iface eth1 inet static
pre-up ifconfig eth1 up
pre-up ifconfig eth1 down
pre-up ifconfig eth1 up
pre-up ifconfig eth1 down
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid galaxy
wireless-key d403f82bce4a3206eed791554d
auto eth1
```

It's quite ugly but is similar to what I use.

---

### Post by jimmymac on 2006-08-09
Cheers for that but it didn't do the trick!  I can manage as is, it is just driving me absolutely insane!!

Any other ideas?

TIA

Jimmy

---

### Post by jimmymac on 2006-08-12
Alright guys,

Just so you know I ended up doing a fresh install of Ubuntu (for other reasons not this!)
I followed the instructions on the HowTo to get ndiswrapper to work, and it now works like a dream.  At 54Mb/s and straight from boot.:D 

Cheers for all the help!

Jimmy

---

### Post by K.Mandla on 2006-08-22
This is weird. I have the same problem with a 4306. It's activated at startup, but won't sign on. I can't do *ifconfig down*, *ifconfig up* either -- it only resets through the GUI, and sometimes I have to deactivate/acknowledge the preferences/then reactivate.

I'd prefer to stick with the bcm43xx-fwcutter method than tinker with ndiswrapper. Any suggestions?

---

### Post by K.Mandla on 2006-08-22
Well, I *think* I got it. I edited my /etc/network/interfaces file to look like this:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
pre-up ifconfig eth0 down
pre-up ifconfig eth0 up
wireless-essid XXXXXXX
wireless-key XXXXXXXXXX

auto eth0

```
That *seems* to do the trick. I've rebooted two or three times now (I'm pecking away at the Xpress 200M in this thing), and it reconnects each time.

Cheers, all.

---

