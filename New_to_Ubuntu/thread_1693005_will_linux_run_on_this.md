---
title: "will linux run on this"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by moose579 on 2011-02-22
hi im looking at buying a cheap laptop/netbook for my son ,,,

here is the spec 

&#8226; 10" screen
&#8226; Google android 2.1
&#8226; 256MB RAM
&#8226; 16GB storage
&#8226; 1 GHZ processor
&#8226; 2 x USB ports
&#8226; Cardreader
&#8226; WiFi

will any linux run on this netbook

as its running google android 2.1 at the moment

wanting it to run kids web site and youtube//all these sites run adobe flash and needs the updated version ,,so hoping a linux will run on it [FONT=Arial][SIZE=4][/SIZE][/FONT]

---

### Post by whatthefunk on 2011-02-22
Cnat you just update flash on the android?

Some versions of Linux would probably run on it, but I would check hardware compatibility first.

---

### Post by Frogs Hair on 2011-02-22
There some choices here , but you will have to check specs.[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by kerry_s on 2011-02-22
no, flash only comes on android 2.2 on.
256mb ram is not enough.

---

### Post by seawolf167 on 2011-02-22
It should. As a netbook, you'll want a lighter weight distro with some screen (v-out) modifications for easier viewing on a small screen

[Here ]("http://www.ubuntu.com/netbook")is the Ubuntu netbook edition (being the Ubuntu forum, this is probably the one I'd suggest)

[Here ]("http://www.linux-netbook.com/linux/distributions")is a listing of all the distributions featured on linux-netbook.com

---

### Post by whatthefunk on 2011-02-22
> **seawolf167 said:**
> It should. As a netbook, you'll want a lighter weight distro with some screen (v-out) modifications for easier viewing on a small screen

[Here ]("http://www.ubuntu.com/netbook")is the Ubuntu netbook edition (being the Ubuntu forum, this is probably the one I'd suggest)

[Here ]("http://www.linux-netbook.com/linux/distributions")is a listing of all the distributions featured on linux-netbook.com

Ubunut netbook would run poorly on this machine.  Just not enough RAM.  Id go Lubuntu, Puppy, or Damn Small.

---

### Post by Ben Page on 2011-02-22
err...Android is Linux...

Ubntu will run on 256 MBs of RAM normally, just turn of compositing and give it 512 MBs of SWAP, stock Ubuntu uses ~210 MB of RAM. My recommendation would be XUbuntu, or any distro with XFCE instead of Gnome.

---

### Post by kerry_s on 2011-02-22
never mind

---

### Post by sydbat on 2011-02-22
> **Ben Page said:**
> err...Android is Linux...This.

However, if you want to run Ubuntu or any other Linux distribution, then follow the advice of the previous posters.

---

### Post by komputes on 2011-02-22
If you can, I'd recommend booting from a bootable USB drive with persistence (use usb-creator or do a full install onto a stick). Then when you are at the computer, boot ubuntu, test it out and run the following two commands to grab better specs on the hardware.

```
$ lspci -nnk > ~/lspci.txt
$ lsusb > ~/lsusb.txt

```

Upload these two files and I can have a look. Can you also point to a website for this model?

For best results use ubuntu-certified hardware:
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

