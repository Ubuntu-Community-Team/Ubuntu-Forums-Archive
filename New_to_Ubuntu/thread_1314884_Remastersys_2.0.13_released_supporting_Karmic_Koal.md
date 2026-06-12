---
title: "Remastersys 2.0.13 released supporting Karmic Koala"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Fragadelic on 2009-11-04
I just finished working on remastersys for Karmic Koala.

Here is a link to my forum with info about it.

[http://geekconnection.org/remastersys/forums/index.php?topic=354.0](http://geekconnection.org/remastersys/forums/index.php?topic=354.0)

There were some big backend changes by the ubuntu folks which is why the older versions won't work.

If any of you have installed the older versions and let it remove grub2, you will have to put grub2 back as the installers in Karmic rely on grub2.

IMPORTANT NOTE - this version is only for Karmic and up.  I have setup a new repo area just for karmic due to this fact.

I've also attached the deb file here in case you're too lazy to go to my site - lol.

---

### Post by uusita on 2009-11-05
hello, i just test the new version in 9.10, there is still some bug, but i am not sure whether it is because of remastersys:
i try with 2.0.13 and successfully create an liveCD.iso, and test it in virtualbox and qemu, all fine. thereis no cannot find "initrid.img" error.
but i just want to make it a liveUSB.
then i found the iso cannot be recognized from usb-creator, without any warning. just cannot be load in the menu.
i just turn to 9.04's usb-creator to make it, then i get error saying it's not standard desktop live cd something, approximately, coz i am not using an english locale.
any idea?


> **Fragadelic said:**
> I just finished working on remastersys for Karmic Koala.

Here is a link to my forum with info about it.

[http://geekconnection.org/remastersys/forums/index.php?topic=354.0](http://geekconnection.org/remastersys/forums/index.php?topic=354.0)

There were some big backend changes by the ubuntu folks which is why the older versions won't work.

If any of you have installed the older versions and let it remove grub2, you will have to put grub2 back as the installers in Karmic rely on grub2.

IMPORTANT NOTE - this version is only for Karmic and up.  I have setup a new repo area just for karmic due to this fact.

I've also attached the deb file here in case you're too lazy to go to my site - lol.

---

### Post by wolfchri on 2009-11-05
> **uusita said:**
> 
i try with 2.0.13 and successfully create an liveCD.iso, and test it in virtualbox and qemu, all fine. thereis no cannot find "initrid.img" error.
but i just want to make it a liveUSB.
then i found the iso cannot be recognized from usb-creator, without any warning. just cannot be load in the menu.
i just turn to 9.04's usb-creator to make it, then i get error saying it's not standard desktop live cd something, approximately, coz i am not using an english locale.
any idea?

You may try to copy the image to the USB device with Unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope this helps!

---

### Post by Fragadelic on 2009-11-05
I made a mention of that fact in the post on my forum about it.

They changed casper-new-uuid and some of the other information needed by the usb creator tool.  I wanted to get the new version out as there have abeen a lot of people that have asked me about it.  I will be adding that function back after I've had a chance to look into it a bit more but for now you should be able to use unetbootin to put it on usb.

---

### Post by uusita on 2009-11-05
thank you Fragadelic, for your job, i'll keep following it!:D

---

### Post by uusita on 2009-11-05
> **wolfchri said:**
> You may try to copy the image to the USB device with Unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope this helps!

thx! i once have tried it, however, 

two suggestions for unetbootin:

1. customize boot menu before burn it to my pendrive -- e.g. i don't want to see "unebootin " in it.

2. persistence support -- i've tried make my own casper-rw, but still no effect took place.

for that unetbootin will be a better choice for more people!!!

---

### Post by uusita on 2009-11-10
so sorry for the post above, unetbootin, but the tool really make sense!
yes , according to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/), i just strictly follow the instruction in readme and everything works find, and an article about how to create larger casper-rw file can be found in pendrivelinux's "how to create larger ..."([http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/))

the fault i made previously is that when i using a different fat32 label for my pendrive, i mistakenly modified the syslinux.cfg :
"...file=/cdrom/***" to "...file=/mylabel/***"
and the syslinux.cfg is highliy modified to acquire customized menu, sorry, i was wrong!
i apologize!

---

