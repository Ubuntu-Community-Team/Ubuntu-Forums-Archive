---
title: "Do I need Samba?"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Touch.Code on 2007-02-15
Hi,

I am just wandering wether or not I need Samba, if I was to connect my Laptop(XP) and Desktop (6.10) with a ethernet cable?

Touch:confused:

---

### Post by dmizer on 2007-02-15
well, first of all, you can't directly connect two computers with a regular ethernet cable.  you'll have to use a crossover cable to connect a computer from ethernet card to ethernet card.  if you have a router, this is not a problem.

now, for your question:
for windows to view and retrieve files on your ubuntu desktop, you need to set up a samba server on your ubuntu desktop (first link in my sig)

for ubuntu to view and tetrieve files on your xp laptop, you'll need to use either smbfs or cifs (cifs is the second link in my howto).

but it really depends on what you want to do while directly connected between your desktop and laptop.  iow ... if you have a specific task you want to perform there may be an easier way.

---

### Post by Touch.Code on 2007-02-15
I want to share my wireless internet connection which is on my laptop.

---

### Post by dmizer on 2007-02-15
if that is ALL you need/want to do, then no, you do not need samba.

what you DO need is a crossover cable and you'll need to set up ICS (internet connection sharing) on your windows laptop.

the tutorial i used (way back when) when i did this my first time is here: [http://www.homenethelp.com/connection-sharing.asp](http://www.homenethelp.com/connection-sharing.asp)

edit ...
actually, here's probably a better place to start with that: [http://www.homenethelp.com/ics/ics-install-arch.asp](http://www.homenethelp.com/ics/ics-install-arch.asp)

---

### Post by Touch.Code on 2007-02-15
Thanks

I will take alook at that now!

---

