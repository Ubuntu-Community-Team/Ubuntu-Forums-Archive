---
title: "Help creating live USB!"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by boblettoj99 on 2011-07-01
Hi, I am trying to create a live usb thing to install ubuntu. I downloaded UNetBootIn but it won't recognise my usb stick. I formatted it to fat32 but still no luck...

I seem to remember being able to click a button before which said "display all drives - be careful" or something along those lines, pretty sure that worked for me last time but the version I have now doesn't have it.

Does anyone have a link to the old (or maybe it's the new) version?

Taaaaa

---

### Post by Scunnered on 2011-07-01
You will need to provide a bit more info to assist.  What version are you using?

I recently created a USB using the Startup Disk Creator to load 11.04. I found that there was a problem with the stored in reserved space not being able to be adjusted.  It was necessary to copy 11.04 to my desktop and when the source disk image was displayed I then selected 11.04 from the desktop.  This let me make the required adjustment to the reserved space.

I am now working with the USB as a test bed to see how much I like Unity.

Give this method a try and if you still have more problems get back to the forum with more info to enable them to assist

---

### Post by sam_delta on 2011-07-01
[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating a bootable Ubuntu USB flash drive](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating a bootable Ubuntu USB flash drive)

check the section which says "From windows" if your on windows

any questions, just ask

sam

---

### Post by mastablasta on 2011-07-01
or you could try LiLi found at Linuxliveusb.com

---

### Post by I2k4 on 2011-07-02
This is the official download page and the "Show Me How" steps are bulletproof:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Unfortunately, Step 2 doesn't go on to Show Me How to install Persistence, which allows the Live USB user to save settings between boots.  It's pretty clear on the PenDrive installer itself, which has a slider control to set it.  (The installer does have a "display all drives" choice on the dialog.)

For 11.04 I'm using a 4GB drive with around 2.5GB set for Persistence.  (I'm running Lubuntu 10.10 very nicely on a 2GB Live USB with 1.3GB set for Persistence.)

---

### Post by beew on 2011-07-02
> **I2k4 said:**
> This is the official download page and the "Show Me How" steps are bulletproof:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Unfortunately, Step 2 doesn't go on to Show Me How to install Persistence, which allows the Live USB user to save settings between boots.  It's pretty clear on the PenDrive installer itself, which has a slider control to set it.  (The installer does have a "display all drives" choice on the dialog.)

For 11.04 I'm using a 4GB drive with around 2.5GB set for Persistence.  (I'm running Lubuntu 10.10 very nicely on a 2GB Live USB with 1.3GB set for Persistence.)
 
How do you create the live usb, in Windows or Ubuntu? If you are in Ubuntu the startup disk creator would create a live usb with persistence (I have created a live usb with persistence for 11.04 in Mav so I am sure it works,--or worked) In Windows LiLi (see mastabasta's post above) should work but I haven't tried it as I have not been using Windows for quite some time.

Unetbootin by the way does not support persisrence.

---

### Post by wildmanne39 on 2011-07-02
Hi, here is a guide for creating a persistent usb stick.
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

