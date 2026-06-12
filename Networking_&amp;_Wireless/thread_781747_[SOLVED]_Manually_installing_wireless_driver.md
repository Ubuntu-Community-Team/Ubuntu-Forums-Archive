---
title: "[SOLVED] Manually installing wireless driver"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by ezramorris on 2008-05-04
Hi, I got my Broadcom B43 chipset wireless card set up fine on my installed version of Ubuntu, but I had to use an ethernet connection to enable it through restricted drivers.

However, I also have a USB installation which is not persistent, so is there any way of getting the files which would be downloaded through restricted drivers, and saving them so they could be installed temporarily without having an ethernet connection?

Thanks.

-------
Ubuntu Hardy

---

### Post by Ayuthia on 2008-05-04
b43-fwcutter should be located on the liveCD or you can grab the file from your b43 installed Ubuntu computer at /var/cache/apt/archives.

As for the firmware, you will have to download them again because the installer deletes the files after the install.  The ones that they get are:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

---

### Post by ezramorris on 2008-05-04
> **Ayuthia said:**
> b43-fwcutter should be located on the liveCD or you can grab the file from your b43 installed Ubuntu computer at /var/cache/apt/archives.

As for the firmware, you will have to download them again because the installer deletes the files after the install.  The ones that they get are:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Thanks very much! One more thing, how would I install the firmware, and would I do it before or after installing the driver?

---

### Post by Ayuthia on 2008-05-04
You will need to do these steps after you install b43-fwcutter:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```

Make sure that you are in the directory where you downloaded the firmware.

---

### Post by ezramorris on 2008-05-05
> **Ayuthia said:**
> You will need to do these steps after you install b43-fwcutter:
[CODE]sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o]

Make sure that you are in the directory where you downloaded the firmware.

Thanks again, worked great!

---

### Post by wonderbriefs on 2009-01-16
I get this error.
"Cannot open input file broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o]"
What am I doing wrong?

---

### Post by ezramorris on 2009-01-16
> **wonderbriefs said:**
> I get this error.
"Cannot open input file broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o]"
What am I doing wrong?

Are you in the same directory as the place where you untarred the file to?

---

### Post by Ayuthia on 2009-01-16
> **wonderbriefs said:**
> I get this error.
"Cannot open input file broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o]"
What am I doing wrong?

Sorry, that was my mistake.  The commands were supposed to be:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```

I was apparently typing too quickly and messed up the code box so you saw the wl_apsta.mimo.o] instead of wl_apsta.mimo.o

---

### Post by dstubb on 2009-11-29
My linux skills are a little rusty, I haven't done much with Ubuntu in a couple years.  When I try to follow these directions, I get "Cannot open input file wl_apsta-3.130.20.0.o"

Can someone post some "noob" instructions, I have a feeling I am not directing Terminal to the proper directory.

---

