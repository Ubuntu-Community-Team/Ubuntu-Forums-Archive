---
title: "Using 32-bit grub to boot an 64-bit image via ipxe (Mad idea i know)"
date: 2018-10-30
forum: Networking &amp; Wireless
---

### Post by chrislucas on 2018-10-30
Hello,

I've recently bought a Windows tablet (32-bit UEFI and 64-bit CPU +  using a usb-ethernet dongle). I installed Ubuntu 64-bit using this [tutorial]("https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec").  Everything works perfectly fine. Now, I would like to step it up a  notch and try and boot via ipxe (usb-ethernet dongle) to a server with  an 64-bit image. The issue is that when I add 64-bit efi script in my  bootloader it doesnt work but if I add a 32-bit efi scripts it finds the  server but can't load the image.

My idea would be to try and use grub to boot ipxe. So far, I get the  same results as if I would do it through UEFI. I tried installing grub  on a USB stick + bootia32.efi but no success.

I was wondering if I could use this bootia32.efi script to be able to  boot a 64-bit efi script and if somebody has tried this mad system.

Help is much appreciated. Any suggestion I'm up to test.

---

