---
title: "Ubuntu confused by floppy drive?"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-13
I just installed 9.1 on an old Dell Dimension 2400 (dual boot with winXP on separate HDs). When I booted up Ubuntu it got stuck and the splash page never loaded. I noticed that the light on the floppy disk drive stayed on the whole time until I shut down the computer, so I disconnected the drive and now things seem to work OK. Does Ubuntu not know what to do with a floppy drive when it finds one, or is this just an idiosyncrasy of my computer?

---

### Post by mlentink on 2010-07-13
Neither.

It's just that your computer BIOS is set to try and boot from a floppy first. Which you can change by changing your BIOS setup. I used to own a 2400 quite a few years back, but I don't remember the exact keys to press. But if you google 'BIOS setup' and your computer model, I'll bet you'll find it

---

### Post by Chris1274 on 2010-07-13
Actually the boot sequence is 1. CD, 2. HD. I removed the floppy from the boot sequence a while ago. It booted into the GRUB menu fine, it was just once I selected Ubuntu that things got stuck.

---

### Post by mlentink on 2010-07-13
> **Chris1274 said:**
> Actually the boot sequence is 1. CD, 2. HD. I removed the floppy from the boot sequence a while ago. It booted into the GRUB menu fine, it was just once I selected Ubuntu that things got stuck.

Sorry. Which HD?

---

### Post by Chris1274 on 2010-07-13
The Master drive, which has winXP on it.

---

