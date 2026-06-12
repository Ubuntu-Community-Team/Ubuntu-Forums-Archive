---
title: "Dualbooting winxp &amp; ubuntu netbook 10.4"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by eyeb on 2010-08-17
Hi, can anyone help me get these two to dual boot without changing it from windows mbr?

I've tried this tutorial and it works in virtualbox but when I go do it on laptop it doesnt work. I get a message like file cant be found or something, sorry I don't remember exact message and I had to reformat to be able to post and use computer.
[http://www.linux.com/archive/articles/113945](http://www.linux.com/archive/articles/113945)

I've tried not installing grub at all and using bootpart to no success. I've followed other guides and installed grub to another partition and also no good. I've yet to try to install it to a floppy because I dont got floppy drive...

I know winxp is old but if anyone can help me dualboot it with ubuntu, I'd appreciate it. And I really have tried a few times and all the tutorials are years old. I'm not sure if ubuntu 10.4 works differently or not but I can't figure it out.

Oh, I also don't have a cd drive so I have to be able to do it all from flash drive...

edit: I tried using grub before out of having no other idea to try. I got a grub repair > message on boot and after that I had to reformat to windows again. I tried a few times thinking I did it wrong but I let ubuntu install with default settings and still that happens.

---

### Post by cariboo on 2010-08-17
If you install grub on the mbr of the first hard drive, You should have no problems with XP. Installing and using grub2 is far easier than any other solution you run into. On the last Window before you actually start the installation there should be an options button, click it and make sure grub is install to /dev/sda.

---

### Post by Paqman on 2010-08-17
> **eyeb said:**
> I tried a few times thinking I did it wrong but I let ubuntu install with default settings and still that happens.

You shouldn't need to do anything special at all to set up a simple dual boot with Windows on a single drive. The default settings should just work.

If you're having trouble then there must be some other problem. What program did you use to make your USB stick for installing Ubuntu?

---

### Post by eyeb on 2010-08-17
I used unetbootin to make ubuntu work on flash drive.

what I did was start up ubuntu from usb, partitioned single drive (left the extra space unformatted). Reboot into windows so it could see new partition space. Then went back to ubuntu usb and installed it to largest avaliable partition. It was formatted to ext4 i think and then i just kept clicking next to install it. At end it ask for reboot so I did and I got the grub repair > message.

editt: On side note, the wubi installer worked and I could dual boot from it. I liked it enough to want to have real dualboot with separate partititons since i heard it was faster.
and the thing with the grub2... I didnt see option for it on installer and i donnt know how to get to it otherwise lol. plus like I said before, I want to keep windows mbr booting with boot.ini and not grub if possible

---

