---
title: "qemu network error"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by wxnker on 2007-01-26
I'm running win 98 on a virtual partition with qemu and everything is nice, but I cannot get connected to the internet. I have looked in the guides at this forum and also the link below but I cannot make it work.

[http://www.h7.dion.ne.jp/~qemu-win/HowToNetwork-en.html](http://www.h7.dion.ne.jp/~qemu-win/HowToNetwork-en.html)

I'm starting win 98 with the following command:
$ qemu -boot c -cdrom /dev/cdrom -hda /home/novak/qemu/hd.img -m 256 -net nic -net user

As far as I have understood things this should be right, or?

When I try to setup my RHINE II network card it installs fine in windows 98 but after reboot it is not working. I have attached a **screenshot** from the device manager where the network card is marked with a "!". If I reinstall the driver the installation works but after the reboot the network card is still marked with an "!" and not working. You can see the error message and the error code on the attached **screenshot**.

Can someone solve this. I'm afraid the guide in the link above is a bit complicated to me.

Thanks in advance.

---

### Post by wxnker on 2007-01-28
I chose to install Windows 2000 instead and the internet works fine. :D

---

