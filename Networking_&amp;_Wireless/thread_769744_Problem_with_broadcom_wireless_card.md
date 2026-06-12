---
title: "Problem with broadcom wireless card"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Tristanm1 on 2008-04-26
Well, I recently upgraded to Hardy, and now I have come across a bit of a problem. My wireless card doesn't work. I think the problem is that the firmware is missing. In Gustsy the firmware could be installed through the hardware manager, though now it is no where to be found. I have ndiswrapper set up, but no go.

My card, as listed by lspci is Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

If anyone has any clue how to get this working, please help.

EDIT: My laptop that this wireless card is part of is specifically an HP Pavillion dv9408nr

---

### Post by brew1brew on 2008-04-26
I have the BCM94311MCG wlan mini-PCI (rev 02), I had to compile ndiswrapper to make it work in feisty, after upgrading to Hardy it quit working. I found the solution [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). Page down to "Hardy bug Fix".

---

### Post by Tristanm1 on 2008-04-26
that section at the bottom fixed it. It was that offending ssb. Thanks for the help.

---

