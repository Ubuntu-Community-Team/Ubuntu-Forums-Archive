---
title: "Help getting on the internet"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Steelfan555 on 2008-12-30
I have been surfing around and looking for an answer of how to get the driver for a Linksys WUSB54GSC. All of the ways i have seen require going into symaptic and DOWNLOADING drivers. Im currentley running an ex-Windows 98 machine, with no ethernet port. I do have a modem, but that does not work either. I have a flashdrive so i can transfer files over, but most of the options require internet, which i do not have right now. Help would be appreciated, but please assume i know nothing, after just installing Ubuntu 8.04 Hardy Heron. I have signed up for free dialup, so i can use that if i knew how.
Steelfan

---

### Post by billgoldberg on 2008-12-30
you can download the driver from packages.ubuntu.com

Make sure you download all the dependcies as well.

Then transfer them to your ubuntu box and install them.

---

### Post by Steelfan555 on 2008-12-30
Which do i download?
I clicked on Hardy, and it didn't say anything about drivers...

---

### Post by handydan918 on 2008-12-30
> **Steelfan555 said:**
> I have been surfing around and looking for an answer of how to get the driver for a Linksys WUSB54GSC. >>>>>> I have signed up for free dialup, so i can use that if i knew how.
Steelfan

What do you intend to do with that device and dialup?

---

### Post by Steelfan555 on 2008-12-30
I was going to use the USB as internet and the dialup as a backup. I just thought thayit looked like i may need internet to get the drivers for the USB wireless adapter...

---

### Post by Steelfan555 on 2008-12-30
> **billgoldberg said:**
> you can download the driver from packages.ubuntu.com

Make sure you download all the dependcies as well.



Where do i look and what would it be called...

Can anyone help me, please? I have been up al day yesterday and today trying to figure this out...

---

### Post by Steelfan555 on 2008-12-30
Ok, this is what i have got done so far:
I have looked at the Ubuntu packages listed above, and was unable to find any linksys drivers, usb drivers or ndis Wrapper, which i have been told work. Anyone have any comments? Before installing ubuntu, the wireless card did work, so it is not an issue of the box itself (sorry if that was common knowledge, i know nothing of Linux)

EDIT: I just installed NDIS Wrapper off of my install disk. Is this good or bad, and what do i do next. All i did was double click on the package and hit install package.

---

### Post by crf on 2008-12-30
There were some threads on that usb network adapter already
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)
[http://ubuntuforums.org/showthread.php?t=459617](http://ubuntuforums.org/showthread.php?t=459617)

But the first thread says it should now function immediately. So maybe it is recognized? Does it appear in the network manager options (system --> prefs --> network configuration)? (However, if it doesn't show up here, that doesn't mean it isn't working ...)

Have you read the man page for interfaces?

---

