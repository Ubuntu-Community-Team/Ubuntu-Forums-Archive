---
title: "How to install another kernel?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by BigWoop on 2009-08-15
I have been using Ubuntu Studio a bit but it was randomly freezing, so I installed regular Ubuntu, that seems to run okay, no freezing yet.

I think it might be the real time kernel, I want to install the regular kernel in Studio and see if it runs without freezing, which packages do I need to add in Synaptic to achieve this?

From what I've been able to determine I think I should add linux-image-generic and linux-headers-generic, is that right?

Also, how will I boot the new kernel from Grub? (I still want to be able to boot the rt kernel as well) 

This might be complicated because I first installed Studio then normal Ubuntu, and the last install of Ubuntu installed Grub over my previous one from Studio. So do I need to add the info to Grub manually, or will Synaptic be able to do it automatically?

---

### Post by ptn107 on 2009-08-15
```
sudo aptitude install linux-firmware linux-generic linux-headers-2.6.28-14 linux-headers-2.6.28-14-generic linux-headers-generic linux-image-2.6.28-14-generic linux-image-generic linux-restricted-modules-2.6.28-14-generic linux-restricted-modules-common linux-restricted-modules-generic -y
```

---

### Post by diablo75 on 2009-08-15
Here's what you do:

1.  Go here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

2.  Select the kernel version you are looking for and open that folder/path in your browser.

3.  Download the file with the word "all" at the end of the name, then the headers deb file for your architecture (32-bit or 64-bit), and finally your image deb file for your architecture.

4.  Install them by double-clicking on them and do so in this order:

*headers.....all.deb
*headers.....i386 or amd64.deb
*image.......i386 or amd64.deb

Then restart the computer.  Grub will automatically include the new kernel in it's menu and should default to it for you.

---

### Post by BigWoop on 2009-08-15
OK thanks I got it working, but it did auto edit the wrong menu.lst file, so I just had to copy the new entry to the right one.

Thanks for the help.

---

