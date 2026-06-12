---
title: "Desktop graphics"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by loubur on 2009-01-10
After installing ubuntu 8.10 and rebooting, I found the graphics will not load without putting the live disk back into the dvd player. After doing so the desktop will load. Any solutions?

---

### Post by JoshuaRL on 2009-01-10
Does it throw any errors?  Or what exactly do you see?

---

### Post by loubur on 2009-01-10
I just see tan colored screen that is blank

---

### Post by JoshuaRL on 2009-01-10
What are your computer specs?  And how long does it sit there if you just let it?

---

### Post by loubur on 2009-01-10
I have a pentium 4 1 gig of mem. Will stay blank screen until I put the cd in the player

---

### Post by JoshuaRL on 2009-01-10
What is your graphics card?

---

### Post by loubur on 2009-01-10
ATI All in Wonder

---

### Post by JoshuaRL on 2009-01-10
Alright.  I think it may be the graphics driver.  Once you have a desktop, go to System->Administration->Hardware Drivers.  See if you can activate any proprietary drivers for your system.  If so, let that finish and then restart.  See if that helps.

---

### Post by loubur on 2009-01-10
no proprietary software is available for linux system in 7500 series. I may need to upgrade.

---

### Post by JoshuaRL on 2009-01-10
> **loubur said:**
> no proprietary software is available for linux system in 7500 series. I may need to upgrade.

I couldn't remember if the All in Wonder was covered by fglrx or not.  I had a Radeon Mobilty 7500 that wasn't, and it was stupid hard to get the card working.  Not sure if things are better on that front or not, but it seems like older cards have kinda been dropped by ATI.

I always suggest Nvidia, if you really are wanting to upgrade.  Even if you just get a cheap one on eBay, Nvidia has pretty good (although proprietary) support for Linux.

---

### Post by loubur on 2009-01-11
after upgrade to nvidia card (8400 gs) and installing driver from linux, I still having the same problem

---

### Post by loubur on 2009-01-11
after installing nvidia (8400 gs) card and installing driver from linux, I am still having the same problem

---

### Post by JoshuaRL on 2009-01-11
I have that same card, and no problems.  So it must be something else.  Go to the terminal and do:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
sudo aptitude install ubuntu-desktop

```
That should clean stuff up and hopefully install anything missing from your install.

---

### Post by loubur on 2009-01-12
Issue still exists. unable to start desktop without install disk?

---

### Post by loubur on 2009-01-14
Issue still exists. unable to start desktop without install disk?

---

