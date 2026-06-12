---
title: "Good Portable Ubuntu Installation?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by dmaxel on 2010-02-18
Hey everyone,

I've been trying to get to install Ubuntu on an external 30GB USB HDD. I used 8.10 for the installation. Although it's working on my desktop and laptop, I'm having problems with my mom's and dad's computers. On my mom's, I keep getting a GRUB Error 2. On my dad's, Ubuntu starts, but after the progress bar fills up and then goes away, the login screen doesn't appear.

I know about installing a "LiveCD" on the USB device, but I intentionally installed it on my external HDD instead of a flash drive because I wanted to have a full, portable Ubuntu system, where I would also be able to update to newer distributions when I feel like it, as long as updating packages. With the "persistent" LiveCD, that only keeps documents.

Does anyone have any tips on getting GRUB and Ubuntu to play nice with all computers I plug into? Would having to reinstall with Karmic help any?

---

### Post by mikeyphi on 2010-02-18
I think that, using Grub, there will always be a problem with this type of 'portable' system. Grub will look for drives in each 'new' PC and get confused by a 'new' list.

You might try your system without installing Grub; then you would only have to enter BIOS to assign your drive as the boot drive each time you switch PC.

---

### Post by dmaxel on 2010-02-18
I also just read somewhere that installing Ubuntu on an external hard drive would keep a certain set of drivers active, which would be the ones on the installation machine. However in the LiveUSB with persistence, it's supposed to go through the detection phase every time so that it adapts better to each machine. Question is, as long as I have enough space on the external hard drive, would the LiveUSB remember not only settings and documents, but also updated packages updated through the Update Manager?

---

