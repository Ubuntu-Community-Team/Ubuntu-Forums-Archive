---
title: "Linksys USB WUSB54GC Issues"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by neolithic on 2007-11-17
I've tried a few of the approaches I have found on these forums but nothing seems to work.  When I first plugged the adapter in Ubuntu(I'm using the most recent version downloaded yesterday, whatever that is) recognized it and I was able to connect to my network.  However, the speed was painfully slow and Firefox always timed out.  I tried using the package that allows you to use windows drivers, and that didn't work either.  I know that the adapter works well, if conencts very fast in Windows Vista.  Now I have managed to removed the wireless device completely from my system, wlan0 no longer appears.  Is there a straight forward package available that will do all the leg work for me?  How should I fix this now?

---

### Post by neolithic on 2007-11-18
Any suggestions?

---

### Post by Blutack on 2007-11-18
sudo apt-get install ndisgtk
You will need to blacklist the driver that ubuntu loads automatically before you enable ndiswrapper.  If you need more help post back.

---

### Post by neolithic on 2007-11-18
Do I need to have an internet connection for the above method to work?

---

### Post by neolithic on 2007-11-19
Anybody?

---

### Post by Roasted on 2007-11-26
> **neolithic said:**
> Do I need to have an internet connection for the above method to work?

In my experience, anything you "sudo apt-get install" you need a connection for because the system is actually finding an outside source to grab the packages to install the said software. 

The blacklisting I am not sure about, but I doubt you need a connection then.

---

