---
title: "clean install, but -&quot;disk does not exist!&quot;"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by nnjond on 2010-09-27
Hi,

My install went without a hitch but on reboot grub menu listed Ubuntu when I expected the new Kubuntu install to showup

Enter leads to a long pause, then a page of text which ends with:

ALERT! /dev/disk/by-uuid/xxxxxxxxxxxx does not exist. Dropping to a shell!

Can you advise me please?

Thanks for your time.

---

### Post by TeoBigusGeekus on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=987243]("http://ubuntuforums.org/showthread.php?t=987243")

---

### Post by nnjond on 2010-09-27
It worked! Thanks alot Pal,

But it didnt remember the edit on reboot

---

### Post by TeoBigusGeekus on 2010-09-27
Change the grub configuration file - menu.lst for legacy grub or whatever it's called for grub2.

---

### Post by nnjond on 2010-09-27
Sorry, I dont understand that advice. Could you break it down please.

I've re- edited the line and now at the grub prompt

---

### Post by TeoBigusGeekus on 2010-09-27
Login and open terminal.
gksu gedit /boot/grub/grub.cfg
Find the line with the newest kernel, something like
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 444539ba-ab9e-4028-94f5-c1a86b5ec7c1
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
```
and change the linux line to
```
linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
```

---

### Post by ajgreeny on 2010-09-27
> **TeoBigusGeekus said:**
> Login and open terminal.
gksu gedit /boot/grub/grub.cfg
Find the line with the newest kernel, something like
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 444539ba-ab9e-4028-94f5-c1a86b5ec7c1
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
```and change the linux line to
```
linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash [COLOR=Red]rootdelay=130[/COLOR]
```
NO! NO! NO!

I'm afraid **grub.cfg** is read only and should not be edited; even if you do change the files mode to make it writable, it will simply convert back next time you run "sudo update-grub" or there is a new kernel installed, so is pointless.

You need to edit the file /etc/default/grub with ```
gksudo gedit /etc/default.grub
``` find the line 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
```and add your boot option **rootdelay=130** after that so it looks like 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=130"
```Then run ```
sudo update-grub
```

---

### Post by TeoBigusGeekus on 2010-09-27
^^^ This...
Sorry, I'm not very familiar with grub2.

---

### Post by nnjond on 2010-09-27
Something atempts to open after
 
gksu gedit /boot/grub/grub.cfg

but then gives up.

---

### Post by nnjond on 2010-09-27
root@nnjond-den:/home/nnjond# gksu gedit /boot/grub/grub.cfg
No protocol specified

(gksu:1571): Gtk-WARNING **: cannot open display: :0.0
root@nnjond-den:/home/nnjond# gksudo gedit /etc/default.grub
No protocol specified

(gksudo:1572): Gtk-WARNING **: cannot open display: :0.0
root@nnjond-den:/home/nnjond# 

???

---

### Post by ajgreeny on 2010-09-27
Try ```
sudo nano /etc/default/grub
``` and make your edit in that terminal application.  Use Ctrl+X to exit and save after the edit.

Incidentally, I have no idea why gedit will not work in the way I told you to use it.

---

### Post by nnjond on 2010-09-27
Many Thanks

---

