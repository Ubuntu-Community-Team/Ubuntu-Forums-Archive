---
title: "ubuntu netbook remix"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-30
how big a file is the netbook remix iso    ??

---

### Post by nerdtron on 2010-03-30
Same as the regular Ubuntu iso...about 695MB

---

### Post by Rex Bouwense on 2010-03-30
> **3948ctyj said:**
> how big a file is the netbook remix iso    ??

When I downloaded it (1 Jan 2010), the raw image was 680.8 MBs.  That was Karmic Koala (9.10).  It is still on my hard drive.  I never installed it.

---

### Post by ddefillo on 2010-03-31
Actually the UNR file is a bit larger, both the iso and the img file that you use to download in previous versions, but once you create the bootable image with unetbootin the file size on the usb is the same as that of the regular iso.

Hope this helps, and remember if you downloaded the file from the ubuntu.com page you have nothing to worry about, just check it with the supplied md5 if you are unsure.

---

### Post by sandwormblues on 2010-03-31
Is there any reason why the USB image isn't available for download?

It seems a little silly that the netbook remix is only available as an ISO, seeing as most netbooks don't have cd-roms...

---

### Post by 3948ctyj on 2010-04-01
if you have a netbook you always have a USB device handy and know how to use unetbootin or similar.

---

### Post by haddog on 2010-04-02
> **sandwormblues said:**
> Is there any reason why the USB image isn't available for download?

It seems a little silly that the netbook remix is only available as an ISO, seeing as most netbooks don't have cd-roms...

**Copying Files to USB Stick Using Linux**

The usb-creator utility can be installed using Synaptic Package Manager if not already present on your system. Some people have problems with usb-creator. You can also install and use UNetbootin to do the same thing.

Run usb-creator

Top pane, you will have to click "other", locate and select the ISO image
Plug the to-be-nuked USB stick into the computer, it should show up in the bottom pane titled "USB disk to use".
Make sure you have the correct device selected before proceeding to create a USB startup disk!
There may be bugs during the formatting which will show up as two partitions when booting from the USB stick. Try selecting each of them and one should work. If not, restart the computer and try booting from the USB stick again.

The following link list all the methods for creating a USB image including using a Windows PC or Mac:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

