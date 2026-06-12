---
title: "Grub missing boot menu backround image"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by X-Tarzan on 2010-11-03
Dear sensei , how can i enable boot menu background image in Grub 1.98+20100804 , i follow the instruction from this site :
[http://dorianpula.ca/2010/09/10/beautifying-the-boot-grub2-plymouth-themes-in-ubuntu-10-04/](http://dorianpula.ca/2010/09/10/beautifying-the-boot-grub2-plymouth-themes-in-ubuntu-10-04/)

i using 4 types of O.S , (Ubuntu,XP SP3,Win7,and OSX Snow Leopard)
and its worked in ubuntu 10.04 but not worked in ubuntu 10.10
any advice pls

---

### Post by X-Tarzan on 2010-11-04
billy@the-kid:~$ sudo update-grub Ubuntu Generating grub.cfg ... Found background image: luckyluke.png Found linux image: /boot/vmlinuz-2.6.35-22-generic Found initrd image: /boot/initrd.img-2.6.35-22-generic Found memtest86+ image: /boot/memtest86+.bin Found Windows 7 (loader) on /dev/sda1 Found Mac OS X on /dev/sda4 done  help me i still got no background in boot menu

---

### Post by ziazis on 2010-11-04
how about configure your grub.cfg on your own.

that would look like that 
> if loadfont $bootpath/grub/unicode.pf2 ; then
  set gfxmode="640x480"
  insmod gfxterm
  insmod vbe
  terminal_output gfxterm
  if terminal_output gfxterm; then true ; else
     terminal gfxterm
  fi
fi
insmod tga
background_image $bootpath/grub/$pic.tga
i hope this could help :)

Edit:
Btw. i just did it with .tga files as a newbie in this things. however i would suggest u try this or maybe someone else will help u better ;P.

---

