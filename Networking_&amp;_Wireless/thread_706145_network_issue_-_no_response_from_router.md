---
title: "network issue - no response from router"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by arxaggelos on 2008-02-24
Hi everyone,
I've just installed Ubuntu (3 days ago) and lovin' it already, so that makes me a complete rookie, but I kinda messed sth up; everything was going finer than fine until I installed a vpn (to have remote access to my university-works on winXP) using synaptics (don't really recall the actuall components i selected); as soon as the installation was completed I lost com with the router (firefox tries to connect and stays at trying-doesn't even open the router dialogue at [http://fritz.box](http://fritz.box)).  Now I'm in Windows.

Pleeeeease
a.Is there an (easy) way to restore all networking defaults in Ubuntu, or, if not,
b.Is there an (easier) way to completely restore all Ubuntu deafults without ripping it out and re-installing it altogether?

Sorry for the word count, I wanted to be explicit

Thanks in advance!

---

### Post by Iowan on 2008-02-24
After I finish the Nagios book, I intend to get a VPN book from the library.  I suspect you have some settings to adjust. Short term, you _*might*_ be able to turn it off. Check in /etc/init.d for a VPN-type file.  Most services have a **stop** option.  No guarantees, but it's easier than un-installing VPN - or re-installing Ubuntu.

---

### Post by arxaggelos on 2008-02-24
thanx, i'll give ot a try and let u know

---

