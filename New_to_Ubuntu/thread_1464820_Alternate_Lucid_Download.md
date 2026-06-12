---
title: "Alternate Lucid Download"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by daniell59 on 2010-04-28
After many failed attempts, only the alternate Lucid download will boot up without errors. If I install the alternate Lucid download will the result be the same?

---

### Post by tgm4883 on 2010-04-28
Yes it should be the same.

---

### Post by Ubuntiac on 2010-04-28
Quite a few people are having boot problems caused by Kernel Mode Setting (KMS) which can be easily fixed by turning it off. The exact command you use depends on the manufacturer of your video card, for example if you have an ATI card adding "radeon.modeset=0" to the kernel boot line.

While I don't know what your problem is, there's a good chance that it's this. Googling your card maker plus "modeset=0" and lucid will likely turn up good results.

---

### Post by daniell59 on 2010-04-28
> **Ubuntiac said:**
> Quite a few people are having boot problems caused by Kernel Mode Setting (KMS) which can be easily fixed by turning it off. The exact command you use depends on the manufacturer of your video card, for example if you have an ATI card adding "radeon.modeset=0" to the kernel boot line.

While I don't know what your problem is, there's a good chance that it's this. Googling your card maker plus "modeset=0" and lucid will likely turn up good results.

Please expand upon this.
How can I change the kernel boot line? I cannot even get to a screen.

---

### Post by daniell59 on 2010-04-28
> **daniell59 said:**
> Please expand upon this.
How can I change the kernel boot line? I cannot even get to a screen.

 ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card

---

### Post by Ubuntiac on 2010-04-29
I was kind of waiting to hear back what make your video card is so we can tell you what you need to type first. That said, here's what you would need to do, assuming you're using an ATI card. If you're not, you'll just need to replace the word "radeon" with the one correct for your card (which can be googled very easily as per what I wrote above).

Anyway, to business:

**ADDING A PARAMETER TO THE KERNEL LINE:**

1. When you first turn on your computer, hold down the shift key.

That should take you into a black and white, text only menu with a number of entries that look something like:

"Ubuntu 10.04, 2.6.32-11-generic"



2. using the up/down arrow keys on your keyboard, make sure the top one is hilighted.

Push the "e" key to edit it's options. That will take you to a new screen where you can edit around 4 lines of text.



3. Find the line that starts with "linux". Usually it looks something like:
linux /boot/vmlinuz-2.6.32-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro quiet splash

Replace "quiet splash" with the modeset tag (eg radeon.modeset=0 if you're on ATI)



4. Push ctrl plus x to boot. If it works, let us know and I'll give you a pointer as to how to make it permanent.

---

