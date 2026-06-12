---
title: "Help!  Major Problems with Partial Upgrade in Jaunty!"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by amor0fati on 2009-05-06
After tackling many sound and video problems after upgrading to Jaunty, I still had problems with VLC (skipping sound and video) and Rhythmbox (asking to update plugins every time it starts).  I noticed that some updates were being offered in the form of a partial upgrade, so I went ahead with it hoping these problems would be fixed.

After rebooting, I found myself stuck in low-graphics mode and my mouse wouldn't work.  After all that work, a simple update leaves me worse off than ever!  I guess this will teach me to never ever upgrade Ubuntu, especially when I've got a term paper due.

Anyway, I'm at a different computer, and I just thought about trying to my mouse directly into USB and also trying
```
sudo apt-get install xserver-xorg-input-all
```
in the console.  Not sure if any of that will work, but I definitely need immediate help on this.

---

### Post by amor0fati on 2009-05-06
So USB works, but I've discovered that my problem is that there's something wrong with my grub.  For some reason, it's booting me into my backup ide drive, rather than my main sata drive, so I ammended this to menu.lst
```
title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

We'll see if that works.

---

### Post by amor0fati on 2009-05-06
Well, somehow I've managed to compound my problems but discover something new.  After another reboot, the mouse stopped working in USB, as well.  I found out that the list I had editted wasn't the list that it was currnetly booting from, but the old list that actually worked.  It also appears that though the kernels in the current list are jaunty kernels, their uuids are appear to be different, if I'm not mistaken.  They appear to be those of my ide, rather than my sata.

I'm not sure how to access the  menu.lst that keeps showing up, but perhaps I should just edit the menu entry directly from the grub with the proper uuid's?

---

### Post by amor0fati on 2009-05-06
That solved one problem, but my mouse still doesn't seem work in it's regular port...maybe after another reboot.

I'm setting my current menu.lst to this:
```
title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		b88ff7eb-9158-4db9-aefa-653f7f22293a
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b88ff7eb-9158-4db9-aefa-653f7f22293a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		b88ff7eb-9158-4db9-aefa-653f7f22293a
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b88ff7eb-9158-4db9-aefa-653f7f22293a ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b88ff7eb-9158-4db9-aefa-653f7f22293a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b88ff7eb-9158-4db9-aefa-653f7f22293a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b88ff7eb-9158-4db9-aefa-653f7f22293a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b88ff7eb-9158-4db9-aefa-653f7f22293a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b88ff7eb-9158-4db9-aefa-653f7f22293a
kernel		/boot/memtest86+.bin
quiet
```

I really need to get my mouse problem fixed, as in I need to get it working on my ide and get it's regular ps/2 port working on my sata.  It seems kind of jumpy on my usb, and I don't have enough usb ports to spare.  Plus, I don't feel very gauranteed that it will work after another reboot.  These seem like simple fixes, so any advice?

Also, my volume keeps going to zero and muting after every startup.

---

### Post by MysticGold04 on 2009-05-06
I really hate to tell you this, but Jaunty works much better on a clean install if you can swing that.  Hopefully you have your /home on a separate partition, as that should make it even easier.  I tried to update my 8.10 install on my laptop, but ran into issues with some of the software packages I had installed, so I just bit the bullet and did a clean re-install of Jaunty.  My laptop runs better than ever now, btw!

---

### Post by amor0fati on 2009-05-06
No, that's definitely not an option at the moment.  At the very least, I just need my ps/2 mouse port working, preferrably using the console to do so (the easiest way I'd be able to do it, booting from my ide drive).  My ps/2 keyboard works just fine.

---

### Post by amor0fati on 2009-05-07
I mostly sorted it out with
```
sudo gedit /etc/rc.local
```
then typed in
```
modprobe -r psmouse
modprobe psmouse proto=imps
```
before the exit 0 line.

However, this did not work on my backup harddrive, and now my pointer moves all the way to the left of my main screen when I move it to the second screen to the right.  What's going on here?

---

