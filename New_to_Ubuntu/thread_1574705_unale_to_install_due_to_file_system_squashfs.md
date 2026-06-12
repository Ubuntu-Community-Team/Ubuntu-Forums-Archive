---
title: "unale to install due to file system squashfs?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-09-14
My girlfriend just bought an asus Eee Pc 1005p and she wants ubuntu. I installed the ISO and used universal USB maker to use on my memory stick and first time i got this error so i downloaded a fresh iso and tried again and it still won't work. i have googled and i can't find anything on this, help please :(

---

### Post by snowpine on 2010-09-14
I don't know what "universal USB maker" is; have you considered using the supported tools Ubuntu has developed specicfically for this purpose? 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Rave Gloves on 2010-09-14
Sorry, it's [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

which was on the ubuntu website when i installed the iso file. i have used this before to install ubutnu 10.04 desktop version so i don't see why it wont work with this?

---

### Post by bodhi.zazen on 2010-09-14
I always advise unetbootin , it is easy to use and works well.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Otherwise, how much do you know about live CD and how much do you want to tinker ?

---

### Post by Rave Gloves on 2010-09-14
> **bodhi.zazen said:**
> I always advise unetbootin , it is easy to use and works well.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Otherwise, how much do you know about live CD and how much do you want to tinker ?

One problem with a live CD there is no disk drive on this netbook, that would be the way i would do it first, so im stuck with pendrive installs :(

---

### Post by fatality_uk on 2010-09-14
UNetbootin is the best way to go. I would recommend trying this next.

---

### Post by Rave Gloves on 2010-09-14
could someone tell my how to use uniboot? i have no idea what im doing :P

---

### Post by fatality_uk on 2010-09-14
> **Rave Gloves said:**
> could someone tell my how to use uniboot? i have no idea what im doing :P

If you follow the details on this page it will get you up and running

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Rave Gloves on 2010-09-14
```
mount: mouting /dev/loop0 on //filesystem.squashfs failed invalid argument can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)on //filesystem.squashfs
```

hasnt worked again, this is the error while it's trying to boot, might this have something to do with my memory stick or would it be the netbooks harddrive? there is an option to install to hard drive on uniboot, would i be best to try that? i dunno if i could trust it. :(

---

### Post by bodhi.zazen on 2010-09-14
unetbootin is an application that runs on both Linux and Windows.

You run the application and use an iso file to configure a bootable usb. No cd or cdrom drive is involved. That is the point.

See :

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/](http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/)

[http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/)

I believe unetbootin will even download an iso if needed (select a distro from the menu).

---

### Post by jonny.milano on 2010-09-14
Ubuntu 10 and 9 both have very easy ways (graphical) of making a USB install stick/key. After you've got the OS installed, you could reformat the USB key. 

Download the netbook .iso that you need from the ubuntu site onto another computer booted with a live CD (ubuntu 9/+) and then in one of the menus (sorry on a Windoze machine right now, I think under "System") you'll find an option to use an iso to make a bootable USB stick. Select the iso that you downloaded. 

It's all graphical and you don't even need to delete files, rename files, etc. 

Sorry I don't have sceenshots. I'm not at my home computer right now..

---

### Post by bodhi.zazen on 2010-09-14
> **Rave Gloves said:**
> ```
mount: mouting /dev/loop0 on //filesystem.squashfs failed invalid argument can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)on //filesystem.squashfs
```hasnt worked again, this is the error while it's trying to boot, might this have something to do with my memory stick or would it be the netbooks harddrive? there is an option to install to hard drive on uniboot, would i be best to try that? i dunno if i could trust it. :(

That is not how to extract a squashfs

See : [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by Rave Gloves on 2010-09-14
For some reason the unetbootin website wont allow me to download the linux version, im at home now so im going to set the usb up now and use it tomorrow on windows. Any other links for the download?

---

### Post by Rave Gloves on 2010-09-14
> **bodhi.zazen said:**
> That is not how to extract a squashfs

See : [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I checked that link and i don't want to customise ubuntu :/ i just want to install the Netbook version. Why is squashfs in it if i don't need to use it?

---

### Post by Rave Gloves on 2010-09-14
> **Rave Gloves said:**
> I checked that link and i don't want to customise ubuntu :/ i just want to install the Netbook version. Why is squashfs in it if i don't need to use it?

Is it beacuse the ubuntu 10.04 version is a "remix"?

---

### Post by bodhi.zazen on 2010-09-14
unetbootin is in the ubuntu repositories

[http://packages.ubuntu.com/lucid/unetbootin](http://packages.ubuntu.com/lucid/unetbootin)

Detailed instructions are also here :

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Rave Gloves on 2010-09-14
I used the startup disk creator on the ubuntu 10.04 administration section and i tried the usb drive out and it's booted, will this work on windows?

---

### Post by bodhi.zazen on 2010-09-14
will what work on Windows ?

---

### Post by Rave Gloves on 2010-09-14
> **bodhi.zazen said:**
> will what work on Windows ?

Sorry, i made a usb start up on the disk creator that comes with ubuntu. i have booted the trial on my laptop and it's worked. Just wondering if i would get that error on the windows net book when i try to boot the pendrive.

---

### Post by bodhi.zazen on 2010-09-14
The netbook should boot from the usb.

---

### Post by jonny.milano on 2010-09-15
> **Rave Gloves said:**
> I used the startup disk creator on the ubuntu 10.04 administration section and i tried the usb drive out and it's booted, will this work on windows?

Yay! So I actually helped someone out!! :) Right?? Please say yes. 

Yes, the USB key/pendrive will boot on pretty much any computer that allows booting from a USB drive (sometimes called USB-HDD in the BIOS). Most modern computers allow this.

---

### Post by Rave Gloves on 2010-09-16
> **jonny.milano said:**
> Yay! So I actually helped someone out!! :) Right?? Please say yes. 

Yes, the USB key/pendrive will boot on pretty much any computer that allows booting from a USB drive (sometimes called USB-HDD in the BIOS). Most modern computers allow this.

yeah you did ;o the real problem was in my filesystems there was a partition called Ubuntu 10.04 netbook remix, which i had to format to allow me to install the usb pen.

---

