---
title: "testdisk, doesn't see SD CARD"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by ni ni on 2009-08-08
hi all,

I am trying to recover photos from an SD card that got accidentally formatted.  I have testdisk, but when i run it it only picks up the harddrive on this laptop, and not the sd card.

the sd card is in the camera, which is connected with a usb cable to the laptop, the laptop doesn't have a card reader, nor can i afford to get one :-(


any ideas?


thank you all :KS:KS:KS:KS:KS

---

### Post by Rhubarb on 2009-08-08
You could try telling your camera to act as a mass-storage device (it probably is anyway, it should come up as an extra drive on your desktop).

Then, before you can start using testdisk on it (I'd recommend using photorec instead of testdisk - it's installed with the testdisk package - so you should already have it), you should unmount the drive (right click on it, then choose unmount).

Then just run photorec / testdisk as root, and hopefully it should be recognised.

I've used photorec before, it works exceptionally well on hard disks / flash drives / SD cards.

Best of luck,
Rhubarb

---

### Post by ni ni on 2009-08-08
thanks for the reply.

my camera isn't showing as a mass storage device.  it's not on the desktop.  should i run lsusb or some little command like that?

:KS:KS

---

### Post by starcannon on 2009-08-08
> 
You could try telling your camera to act as a mass-storage device (it probably is anyway, it should come up as an extra drive on your desktop).
 ^^
This +1

There is probably a setting on the camera itself to make it act like a generic cardreader/mass storage device; go through its menu's or pull out its owners manual and see if you can find a setting like that. Once you've got it mounted proper like, your half way there. If it defaults to act like a mass storage device, you can try unplugging the cable, wait 30 seconds, and plug the cable back in, my cameras all wake up from OFF when they get USB power, and they go right into card reader mode.

---

