---
title: "How to force boot from USB using bootable CD"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by dshosu on 2009-06-24
Hi,
I'm trying to make my HP TX2500 boot from USB but it will not. I've set the BIOS to boot from USB first and even select the USB device option from the list of boot options.

I know there is a CD image out there that I can burn and boot from that will allow me to then boot from my USB device.

What is it called?

---

### Post by zvacet on 2009-06-24
Read [this.]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by C.S.Cameron on 2009-06-24
Following shows how to make a CD to boot a USB drive for computers whose BIOS won't do so.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by dshosu on 2009-06-24
> **C.S.Cameron said:**
> Following shows how to make a CD to boot a USB drive for computers whose BIOS won't do so.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

That's it! I may have to resort to that.

Late last night I discovered the root of the problem though. 

My computer will only NOT boot a linux USB, but it has no problem booting a windows install USB.

---

### Post by LewRockwell on 2009-06-24
> **dshosu said:**
> That's it! I may have to resort to that.

Late last night I discovered the root of the problem though. 

My computer will only NOT boot a linux USB, but it has no problem booting a windows install USB.

If it will function properly with the windows bootable then I would suspect that you have a problem with the other "non-booting" device

stick or external HDD?

---

### Post by dshosu on 2009-06-25
> **LewRockwell said:**
> If it will function properly with the windows bootable then I would suspect that you have a problem with the other "non-booting" device

stick or external HDD?
Both are USB sticks. But here's the catch, I can plug the linux USB into another computer and it boots fine.

Any other ideas?

---

### Post by Sir Jasper on 2009-06-25
Hi,

This may well be a foolish thought and a complete waste of time but you might try using Gparted to label the stick say, "bootup" and then try again.

The reason for this suggestion is that before I labelled all my USB sticks the media references (probably umimportantly) were often to a previously used stick rather than the currently inserted stick.

My regards

PS I'm happy to be educated.

---

