---
title: "How do i enable internet?????"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by sankz.21 on 2008-09-03
hey im absolutely new to ubuntu.......n i have juss installed dis 8.04 LTS Desktop Edition........n i wanna enable internet on it.......i have a cable net...........can ne1 help me......how to go about......IN DETAIL.......plz it will be a good help!!!!!!.........:guitar:

---

### Post by falcon61102 on 2008-09-03
Ok, first things first, I'm guessing that you want to use a wireless connection with your internet?  

Have you clicked on the Network Manager in the upper right-hand corner of your desktop (the two black monitors, one on top of the other) to see if you have any connections available?  

If nothing appears there it may be that you need to install drivers for your network card.  That shouldn't be a problem but we need some information so that we know what we're dealing with.

Open up a Terminal by going to Applications>Accessories>Terminal in the upper-left corner of your desktop.  That will open a window that has the Ubuntu equivilant to a command prompt.  If you could, type the following command in there and copy the results here:
```
sudo lshw -C network
```

If you need to, copy the results to a text file and save it to a USB drive so that you can read it with your Windows system.

---

### Post by Iowan on 2008-09-03
Just a hint from Ubuntu Forums Code of Conduct -  Section 1, #10:
```
Please do not cross post, or post the same thing in multiple locations. 
```

---

