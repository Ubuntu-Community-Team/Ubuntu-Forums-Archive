---
title: "Wireless internet runs really slow in ubuntu."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by regularjoe on 2009-01-25
Hi,

I would just like to say howdy to the group as this is my first post.

For some strange reason my wireless internet runs really slowly in
ubuntu. I can't get download speeds over 3 kbps. My D-Link
Wireless G DWA-510 Network Adapter is supposedly supported in Ubuntu.
The DWA-510 uses the Atheros Chipset i believe which is supposed to be
heavily supported by Linux.

Does anybody know why my wireless internet would run slowly in Ubuntu
when it runs great on a PC using Win XP?

---

### Post by bgerlich on 2009-01-25
try setting the speed manualy: sudo iwconfig wlan0 rate 54M  or sudo iwconfig wlan0 rate 24M

---

### Post by chrisod on 2009-01-25
I had a similar issue with recently with Xbuntu 8.10 and an old laptop. Wireless worked out of the box, but not well. I solved it by switching out the wireless AP with one of my XP boxes. Sometimes the driver and the hardware just don't work well together. If you can switch out the controller with another box that may be the easiest fix.

---

### Post by spue on 2009-02-01
This solution worked!

I am running 8.10 via Wubi (only for the time being) and was only getting 40k/s doing downloads and updates.  Windows regularly got 140k/s and i would get the high speed in Ubuntu when i hooked up to ethernet.  After doing this simple fix, setting the speed with the iwconfig command, i now get 140k/s in Ubuntutoo.

THANX bgerlich!!!

---

