---
title: "Packages needed for modem connectivity?"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by durangoKid on 2007-07-23
I am setting up Fiesty Fawn for an rural user and need to configure for an external modem. What packages do I need to get them up and running? Since they do not yet have connectivity I will need to burn the packages to CDROM via aptoncd and hand deliver.

The modem they will be using is a serial-port based Trendnet TFM-560X.

Many thanks!

---

### Post by MrFSL on 2007-07-23
Alrighty... I am not familiar with your model of external modem but I think I might be able to help you.

If this modem is a true serial (i.e. RS32) connection then this is quite simple. If this modem is a USB serial modem then it might be a bit more complicated but not too bad.

I would suggest installing gnome-ppp:
```
sudo apt-get install gnome-ppp
```

which is just a front end for wvdial, wvconf, and pppd.

It should auto-detect your modem and just work. Worse case scenario your modem, phone company, or ISP require specif AT init strings in order to get things working well be that can addressed using gnome-ppp when that time comes.

Hope this helps!

---

### Post by durangoKid on 2007-07-23
Wonderful!  I read the HowTo but it didn't address true serial - if it did, I missed it. 

I will go ahead and perform and apt-get on those packages and see what the dependencies are.

many thanks,
DK

---

### Post by MrFSL on 2007-07-23
Do everyone a favor and post your results here when you are done.

External serial modems are the easiest to setup with dialup (IMHO)

---

### Post by durangoKid on 2007-07-24
Will do.  Thanks!

---

