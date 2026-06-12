---
title: "Auto Mounting a USB flash drive"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Singer9 on 2009-10-07
Hi everyone, I'm a total newbie to Kubuntu Jaunty, and not that computer savvy but trying to learn.

I use a lot of files on a USB stick, which I can mount an unmount manually through commands in the terminal to get access.  That's fine for me, however, when my wife uses the computer she can't be bothered with having manually mount the drive to use it.

I think I should be able to make it automount, but don't really understand how to make it work.

I have tried adding users to pludev in KUSER, but that doesn't seem to help, what else do I need to do?

Thanks in advance.

---

### Post by rippin on 2009-10-07
> **Singer9 said:**
> 

I use a lot of files on a USB stick, which I can mount an unmount manually through commands in the terminal to get access.  That's fine for me, however, when my wife uses the computer she can't be bothered with having manually mount the drive to use it.

I think I should be able to make it automount, but don't really understand how to make it work.

I have tried adding users to pludev in KUSER, but that doesn't seem to help, what else do I need to do?

Is HAL installed?

---

### Post by Temposs on 2009-10-07
Most USB flash drives do automatically mount in Ubuntu.

If you're having issues, please post the exact models of USB flash drives you're using that don't work, if you can.

Another thing you might try is to use different USB ports on the computer. For instance, if you're using a desktop, there are usually a few USB ports in front and in back of the computer. If you've only been trying USB ports in front, try the ones in back. Sometimes some USB ports act wonky in Ubuntu.

---

### Post by CaptainMark on 2009-10-07
The files /etc/fstab is what lets ubuntu know what can and cant be automounted, youll need to run this to edit it ```
sudo nano /etc/fstab
``` and then youll need to add a line for the usb stick, you should google 'using fstab' to get a better idea of the options/ if you want a quick and easy option then adding this line the bottom of fstab should work 90% of the time```
/dev/sdb1 /media/usb vfat defaults 0 0
```the first part you should make sure you enter the path assigned to your usb the second part tells ubuntu where to mount it so make sure its a path the exists already the third part tells ubuntu that the usb is fat32 filesystem the fourth part tells ubuntu to use default options, lastly the numbers are best not to worry about. I think you have to tab between each section? im not sure can anyone confirm??

---

### Post by Singer9 on 2009-10-07
Thanks, for the replies. I've no idea what HAL is, but it is installed.

The stick I am using is a Sandisk Cruzer 2GB.

---

### Post by rippin on 2009-10-07
> **Singer9 said:**
> Thanks, for the replies. I've no idea what HAL is, but it is installed.

The stick I am using is a Sandisk Cruzer 2GB.

HAL is "Hardware Abstraction Layer". 

"This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request."
  
Are "usbutils" and "udev"installed? What messages do you read in dmesg when the USB is plugged in/out ( I prefer using xconsole)? Plus, to which 'groups' do your wife and you belong? BTW, whenever changing one's groups affiliation, they must log out/in to have affect. 

Example of getting your groups from a terminal:

cmo@codybeau:~/Desktop$ groups pam cody cmo
pam : pam adm lp cdrom video plugdev staff users nogroup
cody : cody lp cdrom video plugdev staff users nogroup
cmo : cmo adm lp cdrom video plugdev staff users nogroup lpadmin sambashare

BTW, which kernel is in use?

cmo@codybeau:~/Desktop$ uname -r
2.6.28-15-generic

Oh, and another question: is your system up to date?

---

### Post by Singer9 on 2009-10-12
I still can't get this to automount,  I tried adding the line to the fstab file, didn't seem to make any difference.
 

 usbutils" and "udev"are installed.
 

 I don't know what dmesg is?  When I plug in the device I get a notice from the “device notifier widget” saying device plugged in... volume (vfat).
 

 Groups we belong to are :
 

 jc adm lp dialout cdrom video plugdev staff users nogroup lpadmin admin sambashare
 

 and  
 

 lc lp cdrom video plugdev staff users nogroup sambashare
 

 Kernel in use is
 

 2.6.28-15-generic
 

 Yes, I think my system is up to date, I have instaled all available updates using kpackage.
 

 Any more idea please?

---

### Post by gib2800 on 2009-10-19
I'm using a Cruzer 2 gig with ubuntu 9.04 and cannot get it to mount at all. How do you manually mount it?

---

