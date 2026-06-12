---
title: "backtrack usb won't boot"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Cuil22 on 2009-10-06
Hi, I'm fairly new to the linux world. I recently installed backtrack 4 final on my usb flash drive. I formatted it to fat32 and copied the files to my flash drive using unetbootin. My only problem is that it will not boot when I restart. I have grub installed and I'm dual booting with vista home premium and ubuntu intrepid. I heard that it's most likely a faulty mbr and that I need to install one on my flash drive. I followed the directions via this link below, yet when I reboot, I still get the grub menu with the dual boot options. Help would be greatly appreciated. Thanks.

[http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/](http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/)

---

### Post by swoody on 2009-10-08
First, you're going to need to verify that your computer can be booted from a USB device. You'll need to go into your BIOS and make sure there's an option for it. While you're in your BIOS, you'll also need to set your boot priority so that your USB is higher than your hard drive. This way your computer will look to the USB for boot information before it goes to the HDD. Try this out, and let us know if it works or not for you :)

---

