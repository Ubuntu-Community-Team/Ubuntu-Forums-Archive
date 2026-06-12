---
title: "live usb download for lubuntu 10.04"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by dan0804smith on 2011-08-23
hey so i am trying to download lubuntu 10.04 from ubuntu 8.04 hardy.  i put the iso on a use and tried to boot from the usb but it said that there were no bootable devices. is ther a special type of iso if you are booting from usb?  and if so where can i find it?

note* my net book does not have a cd drive so my only other option is usb.

---

### Post by angry_johnnie on 2011-08-23
if you already have hardy heron installed, you could try the [ploplinux]("http://www.plop.at/en/bootmanager.html#rungrub") approach.

it's a small file you'll need to download and place in your /boot directory.  after that, a quick edit of your menu.lst, and you'll have a ploplinux entry in your grub menu.

it's basically another boot manager, with lots of nice features.  it'll let you select booting from your hard drive, or from any peripheral attached to the computer.  i use this  to boot from usb on computers where the bios does not support that.

---

### Post by angry_johnnie on 2011-08-23
by the way, just putting the iso on the usb won't make it bootable.

[here]("http://www.pendrivelinux.com/") are numerous guides on how to make a usb bootable.

other than that, isn't lubuntu just ubuntu with lxde?

why not just install it along with your current desktop environment?

---

### Post by dan0804smith on 2011-08-24
thank you both for your solutions, im sure one of the two will work

---

### Post by amjjawad on 2011-08-28
> **dan0804smith said:**
> hey so i am trying to download lubuntu 10.04 from ubuntu 8.04 hardy.  i put the iso on a use and tried to boot from the usb but it said that there were no bootable devices. is ther a special type of iso if you are booting from usb?  and if so where can i find it?

note* my net book does not have a cd drive so my only other option is usb.

Hello there,

I'd suggest to use Lubuntu 11.04. It's much better than Lubuntu 10.04 and works out-of-the box. There are some issues with 10.04 which got fixed and sorted out with 11.04.

Check: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
It's the best tool to create LiveUSB.

[http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems](http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

