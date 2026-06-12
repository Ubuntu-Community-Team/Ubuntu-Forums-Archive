---
title: "Can't Eject Disc to Put in Disc 2"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by born2live on 2009-07-08
Hey umm ye so iv had ubuntu (9.04) fora bout a week now. Still gettin used to it. 
So basically i tried installing a game today usin wine. All goes well with the installation until it asks me to insert disc 2. I try to open the disc tray to put the next disc in and i get an error and it says the disc is busy. 

i realise its probably the installer thats usin the disc still but im wondering if ther is  somthin i can do to override this. 
thnx

---

### Post by kandieyman on 2009-07-08
The problem is that wine is still using the CD even though the installer isn't. You will need to unmount the CD before you can eject it.

```
sudo umount /media/cdrom
```

---

