---
title: "Lost Wireless"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by mi_were on 2007-05-01
I have just upgraded to Feisty from Edgy and have lost my wireless connection. I have a Dell Latitude C600 and using A Trendnet TEW-421PC H/W:B1.1R wireless card. I had it installed under edgy using ndiswrapper  and the mrv8000c driver.

After upgrading to feisty I lost the card. It appears as present and installed when using the ndiswrapper -l command. 

I installed Feisty to get to use the Infrared port, that also isn't work!

Any help would be welcome.

---

### Post by josephus on 2007-05-02
is the ndiswrapper loaded (lsmod | grep ndis)

if it is loaded then check dmesg to see if there are any errors. if not then load it up using 
```
sudo modprobe ndiswrapper
```

---

### Post by mi_were on 2007-05-23
> **josephus said:**
> is the ndiswrapper loaded (lsmod | grep ndis)

if it is loaded then check dmesg to see if there are any errors. if not then load it up using 
```
sudo modprobe ndiswrapper
```

Thanks for the help, I got it working by uninstalling verything (ndiwrapper) and reinstalling it over with the XP driver instad of the 2000 drivers!

---

