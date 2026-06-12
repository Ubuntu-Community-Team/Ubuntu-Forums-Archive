---
title: "PXE install Karmic"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by ranpha on 2010-03-19
Trying to install karmic via PXE netboot install but i get stuck when it;s loaded the initrd.gz file. After that nothing happens. Hardy boots fine, Lucid has the same problem. I read almost every PXE 9.10 out thereand it seems to work there but not with mine rigs. So what do i keep forgetting why karmic doesnt want to install over PXE ?

---

### Post by J V on 2010-03-19
Checked the bios?

---

### Post by Girya on 2010-03-19
I had no problems with karmic using these instructions: 

[http://www.debian-administration.org/articles/478]("http://www.debian-administration.org/articles/478")

I'll look at my configs and post them shortly.

---

### Post by Girya on 2010-03-19
Here's all my relevant settings for pxeboot

If you post your [COLOR="Red"]tftpboot/pxelinux.cfg/default[/COLOR] file I'll see if I see anything. thats where I'm guessing the problem is. Do you have the -- at the end of the karmic label? that tripped me up. 



**boot.txt:** 
 
> - Boot Menu -
=============

etch_i386_install
etch_i386_linux
etch_i386_expert
etch_i386_rescue
karmic_i386_install


**tftpboot/pxelinux.cfg/default:**

> DISPLAY boot.txt

DEFAULT etch_i386_install

LABEL etch_i386_install
        kernel debian/etch/i386/linux
        append vga=normal initrd=debian/etch/i386/newinitrd.gz -- 
LABEL etch_i386_linux
        kernel debian/etch/i386/linux
        append vga=normal initrd=debian/etch/i386/newinitrd.gz  --

LABEL etch_i386_expert
        kernel debian/etch/i386/linux
        append priority=low vga=normal initrd=debian/etch/i386/initrd.gz  --

LABEL etch_i386_rescue
        kernel debian/etch/i386/linux
        append vga=normal initrd=debian/etch/i386/initrd.gz  rescue/enable=true --

LABEL karmic_i386_install
	kernel ubuntu/karmic/i386/linux
	append vga=normal initrd=ubuntu/karmic/i386/initrd.gz locale=en_US skip-config --
PROMPT 1
TIMEOUT 0

---

### Post by ranpha on 2010-03-20
Thing is I used the debian tutorial first but didnt start. I had the -- after it. Then i used the default setting from the netbook.tar.gz whereevery tutorial says extract and your are ready to go. And BIOS is on because i installed lenny, testing and hardy already. Just karmic and lucid dont wanna work. So i guess am missing something?

for setting well this is mine settings [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/pxelinux.cfg/default](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/pxelinux.cfg/default)

Oh and i did install karmic once on the system but that was by USB stick which i cant use now

ALso when i come to the initrd.gz ready screen my whole keyboard freeze. no crtl-alt-delete etc

FYI i could load the vmlinuz from hd-medi .. just not the linux from the netboot

seems the pxe server is not at fault. Because on different PC it boots

---

