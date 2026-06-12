---
title: "lockup on shutdown?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by garyed on 2009-01-06
My computer just locked up on shutdown & it seems to be working O.K. after booting back up but I'm wondering if it is a bad omen. I ask this because I've already had one HD go bad in this computer & I'm suspecting my second Drive is on its way out too. A couple months ago it would just click & not be recognized by the BIOS. After taking the case apart & checking all the connections it started working again & has been O.K. since. The error I got read as follows:

```
 
* Deactivating swap            [OK]
* Unmounting Local filesystems [OK]
Segmentation Fault  
```

Anyone have any ideas what it means?

---

### Post by jbrown96 on 2009-01-06
Not sure why it would seg fault. Unless some program is written incorrectly (doubtful) or there is a problem with its file. 

GSmartControl is a nifty program to check your drive's health. Some of the data it presents is daunting; I'm still trying to figure out how serious it is, but it may help you. You can get a download here [http://gsmartcontrol.berlios.de/home/index.php/en/Downloads]("http://gsmartcontrol.berlios.de/home/index.php/en/Downloads") to install it run ```
sudo dpkg -i /FILELOCATION/FILENAME
```

---

### Post by garyed on 2009-01-07
Thanks for the link.
So far everything has been running O.K. & shutting down O.K. but it sounds like a good program to try anyways.

---

