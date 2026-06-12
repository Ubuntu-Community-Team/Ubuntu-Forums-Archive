---
title: "Ndiswrapper install problems"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by noahw on 2008-06-29
Hi, I'm trying to install ndiswrapper on hardy 64bit, and for some reason wlan0 doesn't show up.  I've tried everything, and ndisgtk reports everything OK.  I migrated the card from an older system also running hardy that worked, so I think the problem is unique to the 64bit version.  Can someone please help me?

---

### Post by Ayuthia on 2008-06-30
> **noahw said:**
> Hi, I'm trying to install ndiswrapper on hardy 64bit, and for some reason wlan0 doesn't show up.  I've tried everything, and ndisgtk reports everything OK.  I migrated the card from an older system also running hardy that worked, so I think the problem is unique to the 64bit version.  Can someone please help me?You might go into the terminal and type:
```
dmesg|grep ndiswrapper
```There might be an error message there about ndiswrapper.  I am guessing that you might be using a 32-bit driver for 64-bit.

---

