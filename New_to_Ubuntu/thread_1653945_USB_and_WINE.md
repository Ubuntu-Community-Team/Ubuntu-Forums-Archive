---
title: "USB and WINE"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Bunnies on 2010-12-27
I have a camera which is compatible only with Windows and Mac. However, with WINE installed, I was able to also install the software that goes along with the camera. I only have one issue.

When I try to extract pictures or videos using the software from my camera, it claims there is no camera hooked into the USB drive. I assume this is because Linux isn't reading the Windows-based programs that the camera uses.

Is there a fix for this?

Thanks.

---

### Post by MartyBuntu on 2010-12-27
What does the software that came with the camera provide that you can't do natively with Ubuntu?

It should at least show up as a storage device, allowing for extracting images and video.

---

### Post by davidmohammed on 2010-12-27
no - wine doesnt support USB.

I'm surprised that ubuntu doesnt see your camera - for the vast majority of cameras, it just sees them as removable media that you can browse to - look in your Places menu option.

---

### Post by Bunnies on 2010-12-27
> **MartyBuntu said:**
> What does the software that came with the camera provide that you can't do natively with Ubuntu?

It should at least show up as a storage device, allowing for extracting images and video.

I figured the same thing, but the way it works is you install the software, and by using the software you can access the camera. The camera hooks to the computer with a usb cord but it seems the connection between the software and the usb connection isn't intact? I'm not sure.

Other things, such as a keyboard, microphone, headphones, flashdrives and mouses all work, though.

---

### Post by MartyBuntu on 2010-12-27
Are you saying that the camera doesn't show a removable storage icon on your desktop when plugged in, without the software?

What camera is this?

---

### Post by Bunnies on 2010-12-27
> **MartyBuntu said:**
> Are you saying that the camera doesn't show a removable storage icon on your desktop when plugged in, without the software?

What camera is this?

It doesn't, no. The camera is a Vivitar ViviCam 25.

---

### Post by MartyBuntu on 2010-12-27
Check to see if there is a "USB MODE" or "MSC/MTP" selection in the camera's system setup.

---

### Post by Bunnies on 2010-12-27
> **MartyBuntu said:**
> Check to see if there is a "USB MODE" or "MSC/MTP" selection in the camera's system setup.

There isn't. :/

---

### Post by MartyBuntu on 2010-12-27
Has this camera ever worked for you on a computer before?

Are you using the USB cable supplied with the camera?

...and lastly...

Have you tried **F-Spot** for managing camera pictures?
It's in the software repositories. Try that.

---

### Post by sandyd on 2010-12-27
wont work in ubuntu
from the drivers for your camera that i found, your camera seems to use TWAIN, which is a no-go in ubuntu unless your scanning something.

Have you tried virtualbox?

---

### Post by Bunnies on 2010-12-27
> **MartyBuntu said:**
> Has this camera ever worked for you on a computer before?

Are you using the USB cable supplied with the camera?

...and lastly...

Have you tried **F-Spot** for managing camera pictures?
It's in the software repositories. Try that.

It has not, no.

I am using the one which came with the camera.

I just tried it, but it can't detect the camera.

---

### Post by Bunnies on 2010-12-27
> **sandyd said:**
> wont work in ubuntu
from the drivers for your camera that i found, your camera seems to use TWAIN, which is a no-go in ubuntu unless your scanning something.

Have you tried virtualbox?

It tried virtual box, but couldn't get it to work properly. (The box, not in conjunction with the camera).

---

### Post by madjr on 2010-12-28
oh twain, also called wincams... (like the cheap winmodems, back in the day..)

hopefully someone will be able to reverse engineer this.

---

### Post by lkraemer on 2010-12-28
Your camera should have a memory card installed,  Just remove the memory
card, and insert it into a Card Reader (that supports your memory card)
installed in any USB Port on your Computer.  The memory device should be
recognized and files easily accessed.

Have you tried this?

lk

---

### Post by crazee64 on 2011-01-25
> **lkraemer said:**
> Your camera should have a memory card installed,  Just remove the memory
card, and insert it into a Card Reader (that supports your memory card)
installed in any USB Port on your Computer.  The memory device should be
recognized and files easily accessed.

Have you tried this?

lk

Came here looking for the same fix as the OP...

I bought one of these pathetic things for my kids (won't let them touch the dSLR). It does indeed seem to use TWAIN to upload the photos to the windows software. 

f-spot does indeed see the camera and it shows up in lsusb but there are no photos shown. 

Further it does not have a memory card, it stores the photos (max 15 in high quality mode!) on board in some sort of volatile storage and depletes the batteries even when turned off to keep the photos alive. These are lost when the batteries are dead or removed.

Guess for the price you can't complain but as far as usung them in linux goes I hold out no hope :(

---

