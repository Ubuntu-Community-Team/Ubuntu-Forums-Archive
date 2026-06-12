---
title: "Netwgear wg111v3 wont connect to WEP network"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Tony Flury on 2009-01-08
can anyone help ? The router is using a 80 bit WEP connection, the Dongle identifies the network and i am prompted for the key, but the dongle wont connect - from what i can tell (via NDISwrapper) the drivers are loading correctly.

When the internal Broadcom B43 card works then it can connect with the same network with the same key without a problem. However the B43 card is on the way out (and can't be repaired) so I am relying on being able to get the USB dongle working.

I am posting here (as well to the networking and wireless forum), as I have found the level of support in this forum to be far far better.

---

### Post by jdelasalas on 2009-01-08
have you tried unloading and loading the drivers in a different order

for me i have to run

sudo rmmod b43 rmmod ssb rmmd ndiswrapper

sudo modprobe ndiswrapper sudo modprobe ssb

---

### Post by Tony Flury on 2009-01-08
hmmm
worryingly - according to rmmod the B43 module is not loaded at all 
```

tony@laptop:~$ sudo rmmod b43
[sudo] password for tony: 
ERROR: Module b43 does not exist in /proc/modules

```

However
```

tony@laptop:~$ modprobe -l | grep b43
/lib/modules/2.6.24-22-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-22-generic/kernel/drivers/net/wireless/b43/b43.ko

```

Maybe i should be looking at blacklisting b43 (although not sure how) - might that work?

---

### Post by jdelasalas on 2009-01-08
When I had my dongle driver and internal wireless driver installed at the same time...neither worked to well.  Have you tried uninstalling one set of wireless drivers?

---

### Post by Tony Flury on 2009-01-08
If i could deinstall the b43 drivers I would - but I am not sure how to do it.

as I posted earlier rmmod claims that the b43 drivers aren't installed.

---

### Post by jdelasalas on 2009-01-08
That's alright. Have you tried uninstalling all your wireless drivers and just reinstalling the drivers for your dongle

---

### Post by Tony Flury on 2009-01-08
how ?

The only wireless driver reported by ndiswrapper is the driver for my dongle.

How do i completely remove all my other drivers and start again ?

---

### Post by Captain_tux on 2009-01-08
Why are you using **WEP**? Its encryption is weak and can be hacked in mere minutes.

Use **WPA** instead.

---

### Post by Tony Flury on 2009-01-08
I appreciate the WPA is allegedly more secure, but changing to WPA right now is pointless as I can't even connect using WEP (although Windows XP works fine using this dongle) and changing to WAP will mean changes to a lot more than just my PC, and i prefer to be changing just one thing at once.

Once i get it working on WEP then i will think about taking a weekend out to get everything else converted to WPA.

The router cam with WEP enabled as default - and to be honest i have not bothered to change it.

---

### Post by jdelasalas on 2009-01-08
I would tinker around with blacklisting the b43 legacy driver.  You can always unblacklist it if it doesn't help.

---

### Post by Tony Flury on 2009-01-09
Ok - this may seem like a stupid question - how actually do i blacklist the old driver ?

Also when the dongle is plugged in, it does show that the right driver has seized control of the hardware, so I am guessing it wont be driver problems.

---

### Post by WitchCraft on 2009-01-09
> **Captain_tux said:**
> Why are you using **WEP**? Its encryption is weak and can be hacked in mere minutes.

Use **WPA** instead.

In my home network, I use no encryption at all. It anyway is broken fast with aircrack, whether WEP or WPA.
Never had a problem, though...

---

### Post by jdelasalas on 2009-01-09
To blacklist a driver you have to 

sudo gedit /etc/modprobe.d/blacklist

then just add the line blacklist [I]drivername


[/I]

---

