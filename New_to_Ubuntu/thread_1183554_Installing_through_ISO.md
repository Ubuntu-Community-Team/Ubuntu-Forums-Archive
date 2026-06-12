---
title: "Installing through ISO"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by sudeepk on 2009-06-10
I am using debian, i have downloaded the ubutu iso image. now i dont want to waste any cd's for single use. So is there any way to install the ubutu from the iso which is in my harddisk?

---

### Post by rcayea on 2009-06-10
I believe you are going to have to burn it to disk first. I have never heard of installing an ISO directly from the hard drive.

---

### Post by sudeepk on 2009-06-10
Installing can be done through iso, but i dont know the correct procedure for it.. I dint not find any articles which can give brief explanation.

---

### Post by dje on 2009-06-10
you could install via a usb drive: [unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by antoz on 2009-06-10
As far as I know you have to burn an image first onto a CD, there are ways to  make a bootable USB flash drive and install from there but I have never done it myself so you can check the forum to see if someone else can help. You will have to change the boot sequence in the BIOS to boot from USB first[depending on your computer that may not be available]. A.

---

### Post by sudeepk on 2009-06-10
i have done some experiment on booting through the kernal and initrd from the iso image.

mount -o loop ubuntu.iso /mnt
cd /mnt/live/
mkdir /temp
cp initrd1.img vmlinuz /temp
now change the menu.lst in /boot/grub/

title           ubuntu
root            (hd0,6)
kernel          /temp/live/vmlinuz1 root=/dev/sda7 ro
initrd          /temp/live/initrd1.img


this works fine.. when it booted up it used the kernel of the image file and not the debian kernal. so booting from iso can be done.. but still more experiments should be done.

---

