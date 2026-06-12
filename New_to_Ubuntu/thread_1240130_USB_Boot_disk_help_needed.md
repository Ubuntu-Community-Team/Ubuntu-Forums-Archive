---
title: "USB Boot disk help needed"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Couto on 2009-08-14
I'm on Ubuntu at the moment and I have the ISO I want to install on Ubuntu.

I cannot use the 'USB Startup Disk Creator' because the file isn't for a CD (it's to big)

I refuse to use UNetbootin, and I know syslinux is good, because its what I used to install this Ubuntu here.

I've seen [http://www.ubuntugeek.com/how-to-ins...usb-stick.html](http://www.ubuntugeek.com/how-to-ins...usb-stick.html)

I just don't understand why it's so different from the Windows method.

On windows, you extract the iso to the usb, you take the isolinux folder, drag all its contents into the root of the usb, rename isolinux.cfg to syslinux.cfg and do 1 command in cmd. Something like:
cd to the syslinux folder
cd to the win32 folder inside syslinux folder
syslinux -f :e

-- or something alone those lines.



Does anyone know how I'd do this the same way I just said using the Ubuntu Terminal?

cd Desktop
cd syslinux (The syslinux folder is on my desktop)
cd linux (I think thats the Linux version of the file?? )
syslinux -f sdb1 (My USB mount is sdb1)

---

### Post by arochester on 2009-08-14
Your link to ubuntugeek does not work.

> I refuse to use UNetbootin Why? 

Have you looked at pendrivelinux.com? 

Have you looked at "HowTo create Ubuntu Bootable USB Flash Drive - uSbuntu" on [http://linuxpoison.blogspot.com/2009/08/howto-create-ubuntu-bootable-usb-flash.html](http://linuxpoison.blogspot.com/2009/08/howto-create-ubuntu-bootable-usb-flash.html)

---

### Post by Couto on 2009-08-14
> **arochester said:**
> Your link to ubuntugeek does not work.

 Why? 

Have you looked at pendrivelinux.com? 

Have you looked at "HowTo create Ubuntu Bootable USB Flash Drive - uSbuntu" on [http://linuxpoison.blogspot.com/2009/08/howto-create-ubuntu-bootable-usb-flash.html](http://linuxpoison.blogspot.com/2009/08/howto-create-ubuntu-bootable-usb-flash.html)

ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html

I refuse to use UNetbootin because I've already tried it, and it failed during the install.
I'm not trying to install Ubuntu, I'm installing Fedora, and my friend installed it using syslinux!

---

### Post by matthewbpt on 2009-08-14
UNetbootin has never caused me any problems, and it's much easier than the method you are trying, I suggest you try it again. If it failed during the install you could have a bad iso or a bad copy to the usb, it happens.

---

### Post by Couto on 2009-08-14
> **matthewbpt said:**
> UNetbootin has never caused me any problems, and it's much easier than the method you are trying, I suggest you try it again. If it failed during the install you could have a bad iso or a bad copy to the usb, it happens.

I'll use syslinux again in Windows.

Thanks for the input though!

---

