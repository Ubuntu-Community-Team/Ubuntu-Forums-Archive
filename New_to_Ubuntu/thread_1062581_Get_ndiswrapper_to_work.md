---
title: "Get ndiswrapper to work"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-02-07
I formatted my Ubuntu partition today because somehow changing my GPU and updating to 8.10 ****** it up. That's another story altogether.

I had ndiswrapper working before for my Netgear WG311T in both 8.04 and 8.10. Yes, this is an Atheros based card but as an Ubuntu user since 6.10 I can assure you the drivers are utterly pathetic with my card. ndiswrapper however has always been rock solid.

Anyway I can't get it to work. I've installed it, it installed the driver fine but once I disable the Atheros chipset, there's no way for me to 'connect' with ndiswrapper. I installed the Network configuration program from add/remove and that comes up when I hit configure in ndiswrapper's gui but it only shows two ethernet connections (which is odd as I only have one ethernet port, I'm guessing its showing my wifi as ethernet).

Anyway help would be greatly appreciated because I'm quite frustrated at the moment.

---

### Post by Pas_sa on 2009-02-07
If this helps:

```
andrew@andrewdesktop:~$ ndiswrapper -l
wg311t13 : driver installed
	device (168C:0013) present (alternate driver: ath_pci)
andrew@andrewdesktop:~$ 
```

---

### Post by walkerk on 2009-02-07
Did you blacklist ath_pci?
```
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

Now
```
sudo modprobe ndiswrapper
```

Check
```
iwlist scanning
```

?

---

