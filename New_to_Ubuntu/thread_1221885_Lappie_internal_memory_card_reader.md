---
title: "Lappie internal memory card reader"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Shenachie on 2009-07-24
My Aspire 7720G lappie is running beautifully on Ubantu 9.04. the one thing I have found that is not working yet is the memory card reader that is built in.

Under Computer there is nothing showing with a card in?

Assistance please as I use the card a lot for picture uploading to my beekeeping forum.

Regards

Pete

---

### Post by LowSky on 2009-07-24
```
lsusb
```

cpould ytou post hte output of that code, and what kind of card, SD, Compact Flash, xD?

---

### Post by Shenachie on 2009-07-24
xD card.

---

### Post by Dougie187 on 2009-07-24
try this

```
lshw -c system | grep "xD"
```

You could even run just
```
lshw -c system
```
That will tell you if your system sees your memory card reader.

---

### Post by Shenachie on 2009-07-24
From this it seems as if the reader is "seen" so how do I see the pics as it doesn't show up under Computer or am I looking innocently in the wrong place?

Pete

---

### Post by Dougie187 on 2009-07-24
I will assume you have a card in your meida card reader now, or would this be incorrect?

---

### Post by LowSky on 2009-07-24
xD is an issue for Linux, no idea why but it is. Oddly my Camera (fujifilm finepix) uses xD but when connected directly from the camera's usb it works. Card readers dont work and I have no idea why, but if you can connect the camera dierctly it works fine

[http://www.linuxquestions.org/questions/linux-hardware-18/linux-friendly-xd-card-reader-739477/](http://www.linuxquestions.org/questions/linux-hardware-18/linux-friendly-xd-card-reader-739477/)

---

### Post by Dougie187 on 2009-07-24
You could try this in a command line, to see if you get any errors.
sdhci-pci ricoh-mmc
```
grep "sdhci-pci" /var/log/messages
grep "sdhci-pci" /var/log/dmesg
grep "ricoh-mmc" /var/log/messages
grep "ricoh-mmc" /var/log/dmesg
```

I would recommend trying this first after you boot your computer, and second after you plug in one of your xD cards. This way you can see if trying to read the card gives you any errors. I personally haven't used an xD card before, usually just sd. Also LowSky's last post might give some information.

---

