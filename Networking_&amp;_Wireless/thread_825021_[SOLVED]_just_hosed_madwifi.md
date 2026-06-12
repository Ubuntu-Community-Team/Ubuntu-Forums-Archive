---
title: "[SOLVED] just hosed madwifi"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by bryonak on 2008-06-10
Had madwifi on my atheros card (MacbookPro 3.Gen) working with WICD (a fairly typical setup I think).
Here's what happened...
Everything's been running fine with madwifi-ng r2756 and the latest 2.6.14-19-generic kernel. Then I checked for a new madwifi release and found that 0.9.4 has been out for awhile.
After downloading and compiling, I used **make uninstall** from the 0.9.4 source, which was probably wrong. Subsequently running **make install** and **modprobe ath_pci** didn't give me a connection. Opening WICD's gui.py produced an empty window and iwconfig just gave me eth0 and lo. Additionally, WICD was completely frozen/defunct.
Instead of trying to fix things manually I then decided to reboot and see if this "kind of defaulted" (win background, y'know ;) ).

Now I can load ath_pci with modprobe, but there are no wifi0 and ath0 interfaces on iwconfig, just eth0 and lo.
Trying **ifup ath0** or **ifup wifi0** gives me **Ignoring unknown interface **.
**modprobe ath_pci autocreate=sta** loads ath_pci, but doesn't make any difference.

Things don't get better whether I remove the new madwifi with the old madwifi's **make uninstall** or with the new source's **make uninstall** (or clean the /lib/modules/2.6.24-19-generic/net/ directory by hand...), install the old driver, remove it with the old or new make command, or just about any combination of completely or partially uninstalling madwifi and trying either the new or the old driver.
The old driver (madwifi-ng r2756) was working happily just 3 hours ago, which means that I've screwed something else in the system.

I'm pretty clueless (and wireless-less) about what to do next, short of reinstalling the system, which is something I don't really want to do.

---

### Post by bryonak on 2008-06-11
I've been messing about with ath5k, only to find out that this new driver doesn't seem to support the Macbook Pro's chipset.

As for MadWifi, things are still the same and I haven't found a clue yet...

---

### Post by chili555 on 2008-06-11
Please go into the 0.9.4 directory and try:```
make clean
make
sudo make install
sudo modprobe ath_pci
```Let us know.

---

### Post by bryonak on 2008-06-11
Did that a few times already, but I'll try once more (albeit somewhat hopelessly ;) )

After **modprobe ath_pci** i get...
```

$ lsmod | grep ath
ath_pci               107696  0 
wlan                  226336  1 ath_pci
ath_hal               220016  1 ath_pci

```

```

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```


I actually don't know where it fails, so I've tried loading the other modules installed by MadWifi... for example

```

$ sudo modprobe ath_rate_sample 

$ lsmod | grep ath
ath_rate_sample        15616  0 
ath_pci               107696  0 
wlan                  226336  2 ath_rate_sample,ath_pci
ath_hal               220016  2 ath_rate_sample,ath_pci

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by chili555 on 2008-06-12
Would you, or did you reboot? After a reboot, does:```
sudo lshw -C network
```show a logical name, such as wlan0 or ath0? does it show the driver ath_pci?

---

### Post by bryonak on 2008-06-12
Got a solution...

The problem was the new MadWifi driver. Apparently there are conflicts between the non-standard Atheros chip in the Macbook Pro 3 and MadWifi versions 0.9.3 and 0.9.4.
Luckily these are resolved in the r3717-trunk version of MadWifi, which worked after reinstalling the linux-restricted-modules. Even r2756 should work again (haven't tried).

So long and thanks for your time!

---

