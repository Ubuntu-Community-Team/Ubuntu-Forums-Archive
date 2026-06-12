---
title: "Scanning problems with hp psc 1510"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by mei0023 on 2010-01-14
Hi all. This is my first post here--I've been using Ubuntu for about 10 months now and found everything easy and generally pretty bug-free. (I'm pretty useless when it comes to tech, short of Googling for a bug fix.)

I recently connected my old hp psc 1510 all-in-one to use as a printer and scanner. The printing works great, always has--but the scanning doesn't. Using xsane, all I get is a black image, occasionally with an orange bar down the side.

I've installed hplip 3.9.12 and really am unsure where to go from here. Any ideas what to do next?

Edit: I'm getting an "Error during device I/O" message, so it's not a physical problem with the scanner. Also, I'm running dual-boot and scanning works fine on the Windows side.

---

### Post by sandyd on 2010-01-14
where did you install hplip from?
the site or repos?

---

### Post by mei0023 on 2010-01-14
> **carlee said:**
> where did you install hplip from?
the site or repos?
The site.

---

### Post by pme 72 on 2010-01-14
I have an HP PSC 1510xi All-In-One. The Scanner has worked well for me with XSane Image Scanner without having to download any additional driver files. I am using it with 9.10 now and have been using it since 7.10.

---

### Post by steveneddy on 2010-01-14
> **mei0023 said:**
> Hi all. This is my first post here--I've been using Ubuntu for about 10 months now and found everything easy and generally pretty bug-free. (I'm pretty useless when it comes to tech, short of Googling for a bug fix.)

I recently connected my old hp psc 1510 all-in-one to use as a printer and scanner. The printing works great, always has--but the scanning doesn't. Using xsane, all I get is a black image, occasionally with an orange bar down the side.

I've installed hplip 3.9.12 and really am unsure where to go from here. Any ideas what to do next?

The only thing I could suggest is to try it on a Windows machine with the latest drivers for that model and verify the outcome is the same as on the Ubuntu machine.

If it works on Windows, try an older HPLIP driver from HP or an older version of xsane.

It may be that the scanning section is inoperable.

If the scanning device is accessible, not under a piece of glass, try cleaning it with a q-tip and a little alcohol.

---

### Post by meyh on 2012-03-11
The model number **HP PSC 1510**.

**Method 1:**
You may refer to the below links and use the troubleshooters. Check if it lists and helps resolve any issues: Open the Printer troubleshooter:
[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&dlc=en&tmp_geoLoc=true&product=428800"]http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&dlc=en&tmp_geoLoc=true&product=42880...
[/URL]

**Method 2:**
You may check if you have the latest drivers installed for the device. You may refer to the below link for getting the latest drivers and check.
[HP PSC 1510 Driver]("http://www.hpdriver.net/hp-psc-1510-driver/")
 
Good Luck.

---

