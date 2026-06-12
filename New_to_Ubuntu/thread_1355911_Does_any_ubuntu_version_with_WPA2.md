---
title: "Does any ubuntu version with WPA2?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Poketown on 2009-12-15
I am new to Ubuntu, but have managed to set up my laptop to dual-boot Vista and Ubuntu Jaunty.  The most frustrating part of this process is trying to setup a wireless connection in Jaunty.  I use WPA2 and can see my SSID when in Launty.  When I type in the requested password, I get an infinite loop asking for the password again and again and again.  I have seen a number of postings talking about problems with WPA2 and a lot of suggested workarounds.  I don't want to have to go into Terminal and fix a lot of script to try to get Ubuntu to allow a wireless connection.  
 
Is there any Ubuntu version that works with WPA2 without having to fix it first?  If not is there any other version of Linux that will work with WPA2 without having to do a lot of script writing?

---

### Post by bshosey on 2009-12-15
What is your wireless card?

---

### Post by rustutzman on 2009-12-15
Try going into the Network Manager and check the box to make your connection automatic. Reboot and see if it then connects. That's what worked for me.

Russ

---

### Post by Poketown on 2009-12-15
I have a Marvell Topdog card and I see my network so I don't think it is the card.  Based on the large number of posts about Ubuntu not working with WPA2 and asking infinitely for the password, I suspect this is a bug in Ubuntu.  Several of the other forums say this has been addressed in previous and current versions of Ubuntu, but from the continuing number of posts I don't think it is fixed.
 
All I want is a version of Ubuntu that will work with WPA2.  Is there such a thing?

---

### Post by coffeecat on 2009-12-15
> **Poketown said:**
> Based on the large number of posts about Ubuntu not working with WPA2 and asking infinitely for the password, I suspect this is a bug in Ubuntu.

You suspect wrong, and your reasoning is upside-down. Sorry. WPA2 works just fine in Ubuntu with wireless devices where there is no driver issue. Works fine for me with 5 different devices. Your problem is...

> **Poketown said:**
> Marvell

For anyone to be able to help, we need the precise chipset. Open a terminal and post the output of:

```
lspci
```

---

### Post by bshosey on 2009-12-15
I use WPA2 and do not have problem with any but one system. And that is my Dell Inspiron 1721. It has a Broadcom driver. Now This problem only happens if I pic the wrong Proprietary drive. There is two listed. I don't remember the name. I only remember the one that says Broadcom B43xxx and then it works fine. But if I pick the other one it will do this. So it is defiantly the driver driver issue.

---

