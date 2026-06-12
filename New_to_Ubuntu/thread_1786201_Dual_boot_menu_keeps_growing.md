---
title: "Dual boot menu keeps growing"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by robertlow on 2011-06-19
On my internet machine I use Ubuntu exclusively, but on my working machine I'm dual booting Ubuntu and XP.
I've been using Ubuntu for a year or so. I decided that I'd learn to use the command line as needed to fix things, but the OS has been so reliable that this is the first thing that resembles a problem I've encountered.

Problem: Boot list keeps growing with every image update.

I followed the directions given in help to change the boot options, but the [/boot/grub] directory contains no file named menu.lst.
The contents of the [/boot] directory contains the following:

root@Base:/boot/grub# find menu.lst
find: `menu.lst': No such file or directory
root@Base:/boot/grub# cd /boot
root@Base:/boot# dir
abi-2.6.31-21-generic          memtest86+.bin
abi-2.6.32-22-generic          System.map-2.6.31-21-generic
abi-2.6.32-23-generic          System.map-2.6.32-22-generic
abi-2.6.32-24-generic          System.map-2.6.32-23-generic
abi-2.6.32-25-generic          System.map-2.6.32-24-generic
abi-2.6.32-26-generic          System.map-2.6.32-25-generic
abi-2.6.32-27-generic          System.map-2.6.32-26-generic
abi-2.6.32-28-generic          System.map-2.6.32-27-generic
config-2.6.31-21-generic      System.map-2.6.32-28-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.31-21-generic
config-2.6.32-23-generic      vmcoreinfo-2.6.32-22-generic
config-2.6.32-24-generic      vmcoreinfo-2.6.32-23-generic
config-2.6.32-25-generic      vmcoreinfo-2.6.32-24-generic
config-2.6.32-26-generic      vmcoreinfo-2.6.32-25-generic
config-2.6.32-27-generic      vmcoreinfo-2.6.32-26-generic
config-2.6.32-28-generic      vmcoreinfo-2.6.32-27-generic
grub                  vmcoreinfo-2.6.32-28-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-23-generic  vmlinuz-2.6.32-23-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-25-generic  vmlinuz-2.6.32-25-generic
initrd.img-2.6.32-26-generic  vmlinuz-2.6.32-26-generic
initrd.img-2.6.32-27-generic  vmlinuz-2.6.32-27-generic
initrd.img-2.6.32-28-generic  vmlinuz-2.6.32-28-generic
root@Base:/boot#

This list looks a lot like what I see in my boot menu, and selecting the latest version boots Ubuntu just fine.
I'm guessing that I should create the file menu.lst, but I don't want to screw things up, so I thought I'd ask the experts for advice about how I should proceed.  Suggestions would be greatly appreciated.
Thanks.

---

### Post by JRV on 2011-06-19
Use synaptic to delete the old kernels.
I usually save the latest and the one before it.
Make sure you do not delete the latest kernel.

---

### Post by Enigmapond on 2011-06-19
An easy solution is to install Ubuntu-Tweak which, among other nifty functions, has a package and kernel cleaner which will remove all previous or unused kernels. I always keep 1 previous kernel just in case.

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

---

### Post by oldfred on 2011-06-20
This is a link to a command line version. It mentions menu.lst but the sudo update-grub is the same command to update grub2.

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

Tweak or synaptic are easier.

---

### Post by _0R10N on 2011-06-20
Try cleaning your system up by deleting no longer needed kernels.

First: look for all the kernels installed by running

```
aptitude purge linux-image
``` + TAB TAB to get a list of all the available kernels you have.

Second: make a list of everyone of them but the last one or two. After that, run the previous command for every kernel you're going to delete, completing the correct version each time.

Third: after that, also delete the linux-headers, using the same command, but replacing linux-image for linux-headers

Forth: make sure you don't leave garbage behind, cleaning your system.
```
aptitude autoclean
```

Obviously every command previously mentioned has to be executed as superuser.

---

