---
title: "Installing ubuntu fully on a usb hard drive"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Truemedia on 2010-07-25
After having a harsh time with wubi, and still trying to fix the problems that it caused aswell as windows, I have decided to have 2 operating systems on 2 different hard drives, and have a way of keeping ubuntu as far away from windows as physically possable.

I still need windows for a few services I payed a lot of money for, where wine is not an option, so my idea was to keep my windows installation the same on the main computer hard drive with no modifications.

For ubuntu, I know you can boot from a usb drive, and I'm not sure how easy it would be to do but basically I have an external usb hard drive with a lot of space that could be plugged in before I turn on my pc if I wanted to boot ubuntu and have an entire installation setup on the external hard drive, with no need to touch the main computer drive thqt is completely windows.

I'm not sure how to do this since I hqve only used wubi and havn't seen a post yet suggesting this idea, but how could I make this plan work and setup?

---

### Post by Goolie on 2010-07-25
> **Truemedia said:**
> After having a harsh time with wubi, and still trying to fix the problems that it caused aswell as windows, I have decided to have 2 operating systems on 2 different hard drives, and have a way of keeping ubuntu as far away from windows as physically possable.

I still need windows for a few services I payed a lot of money for, where wine is not an option, so my idea was to keep my windows installation the same on the main computer hard drive with no modifications.

For ubuntu, I know you can boot from a usb drive, and I'm not sure how easy it would be to do but basically I have an external usb hard drive with a lot of space that could be plugged in before I turn on my pc if I wanted to boot ubuntu and have an entire installation setup on the external hard drive, with no need to touch the main computer drive thqt is completely windows.

I'm not sure how to do this since I hqve only used wubi and havn't seen a post yet suggesting this idea, but how could I make this plan work and setup?


[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Check it out, pick the option for the USB stick, and follow the instructions.  Hope that works out for you.

EDIT: not sure if that will work for an entire USB external hard drive, but I think it should

---

### Post by nerdtron on 2010-07-25
> **Truemedia said:**
> After having a harsh time with wubi, and still trying to fix the problems that it caused aswell as windows, I have decided to have 2 operating systems on 2 different hard drives, and have a way of keeping ubuntu as far away from windows as physically possable.

I still need windows for a few services I payed a lot of money for, where wine is not an option, so my idea was to keep my windows installation the same on the main computer hard drive with no modifications.

For ubuntu, I know you can boot from a usb drive, and I'm not sure how easy it would be to do but basically I have an external usb hard drive with a lot of space that could be plugged in before I turn on my pc if I wanted to boot ubuntu and have an entire installation setup on the external hard drive, with no need to touch the main computer drive thqt is completely windows.

I'm not sure how to do this since I hqve only used wubi and havn't seen a post yet suggesting this idea, but how could I make this plan work and setup?

From the Live CD, you can fully install Ubuntu on a USB flash drive with a capacity of 8GB or more since the full install will take about 4GB. This will format the flash drive to a linux file system since this is a full install and note that there will be some performance issues since flash drives has slower reads/write speeds than hard drives. Try experimenting on different file systems and see which one will give you the best performance. Try selecting ext4 or XFS file systems on the installation to the flash drive.

---

