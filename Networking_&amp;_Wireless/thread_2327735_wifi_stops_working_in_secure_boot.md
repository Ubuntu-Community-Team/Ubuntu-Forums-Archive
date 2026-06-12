---
title: "wifi stops working in secure boot"
date: 2016-06-13
forum: Networking &amp; Wireless
---

### Post by mfox on 2016-06-13
I am running Ubuntu 16.04 on a Dell xps 13 - 9343, which uses a Broadcom wifi. Once I installed the Broadcom driver, the wifi worked fine until the other day when I messed around with some settings, trying to get a live usb recognized in it. I didn't touch it for several days and when I went back to it last night, wifi was not working. When I say not working, I mean it didn't recognize the wifi connection at all in the Network connection manager on the Unity panel; not in Gnome either. I checked Additional Drivers and the Broadcom driver was installed. I confirmed that it was still working in Windows 10. I next connected my Dell to ethernet, updated the software and reinstalled the Broadcom driver. Still no recognition of wifi at all. Next, I restarted the Dell and disabled secure boot- the wifi came back. I reconfirmed that the cause was the secure boot setting by restoring secure boot and then removing it. I can certainly live without secure boot, but I'd like to know how this causes a problem with Broadcom wifi, and whether there is a solution that would allow me to enable secure boot and have my wifi back.

---

### Post by Hadaka on 2016-06-13
Hi, your computer's Dell xps 13 - 9343 wifi card uses the "wl" driver.
currently there are several others in your same situation and a bug report has been filed
```
https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1572659
```
so, you can add your name to the list or replace the card with an intel card that does have
linux support.

good luck to you.

---

### Post by mfox on 2016-06-13
Thanks for that, Hadaka. I added my name to the bug report.

---

### Post by chili555 on 2016-06-14
Our esteemed colleague Wild Man wrote a tutorial about how to create your own signing key. [http://ubuntuforums.org/showthread.php?t=2304607&page=9](http://ubuntuforums.org/showthread.php?t=2304607&page=9) Please note that he refers to the driver rtl8723be. We don't know if the same process works with your driver wl. Are you willing to try it and give us your report?

---

### Post by mfox on 2016-06-14
Thanks for the suggestion, chili555. What are the risks if it doesn't work? I'm not usually squeamish, but I recently made a stupid mistake cutting and pasting instructions that resulted in four hours to restore a computer.  The instructions look straightforward, but the blue screen makes MOK look like a firmware patch of some sort. Can I bork my xps 13 trying this, or could it render my wifi card unusable even with secure boot disabled? If all I am risking is the time to try this, then no problem.

---

### Post by chili555 on 2016-06-14
Judging by the other thread, it either works or it doesn't. You can always, I assume, give up secure boot until this bug is resolved.

I don't use secure boot. I've never tried this and I haven't a Broadcom device so I don't know for absolutely sure, but I highly doubt is can "bork" your computer. It is merely an attempt to create a key to let your driver into the locked door that is secure boot.

If you have any doubts, turn off secure boot and wait.

---

