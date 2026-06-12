---
title: "Error in booting slax with grub"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by t1nm@n on 2009-12-19
hello...

 I installed slax6.2.0 on my hdd but now it wont boot...

Here's how i did it. Any light will be looked at..pls help.. slax is as clean as it can get..

I installed ubuntu8.04 on sda9 and made swap sda8 . next i went to the slax install in slax cd.

#mkfs.ext2 /dev/sda3
#mkswap /dev/sda8
#swapon /dev/sda8
#cd /mnt
#mkdir sda3
#mount /dev/sda3 sda3
#mount 
#cp --preserve -R /{bin,dev,etc,home,lib,root,sbin,usr,var,opt} /mnt/sda3
#mkdir /mnt/sda3/{boot,mnt,proc,sys,tmp} 
#cp /boot/vmlinuz /mnt/sda3/boot 
#mount -t proc proc /mnt/sda3/proc
#mount --bind /dev /mnt/sda1/dev

This was the steps done in response to the tutorial in the below link:
[http://thanhsiang.org/faqing/node/75](http://thanhsiang.org/faqing/node/75)

now i did try going to the slax site ..but the following error was seen:

Network Timeout
          

The server at [www.slax.org]("http://www.slax.org") is taking too long to respond

The requested site did not respond to a connection request and the browser has stopped waiting for a reply.

    * Could the server be experiencing high demand or a temporary outage?  Try again later.
    * Are you unable to browse other sites? Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.
    * Still having trouble? Consult your network administrator or Internet provider for assistance.
            Eveytime for the last 2 days..... so i couldnot get grub.mo from slax.org
this was the reason why i installed ubuntu so that i can use the grub tho boot slax. heres the grub menu.ls

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ecc8a96d-d6a6-4f98-bf06-7246dc2fb5e2 ro quiet splash vga=792
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ecc8a96d-d6a6-4f98-bf06-7246dc2fb5e2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,8)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Slax6.2.0
root (hd0,0)
kernel /boot/vmlinuz max_loop=255 init=linuxrc root=/dev/sda3 ro autoexec=xconf;kdm

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
 
Now when i go to the OS selection screen and choose Slax it comes out with:
Unable to mount device
press any key to continue........

please help me.....What do you think went .. i bet it's something with menu.ls if it is pls show a correct configuration .. I really am a linux noob..

Thanks....:KS

---

### Post by t1nm@n on 2009-12-19
the smileys entered ... bummer
heres the right list


title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ecc8a96d-d6a6-4f98-bf06-7246dc2fb5e2 ro quiet splash vga=792
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ecc8a96d-d6a6-4f98-bf06-7246dc2fb5e2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,8)
kernel        /boot/memtest86+.bin
quiet
  the smiley here is eight .....why boes that happen 

Thank you

---

