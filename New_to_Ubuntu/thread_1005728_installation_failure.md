---
title: "installation failure"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mat429 on 2008-12-08
Hi,

i'm new to Ubuntu and wanted to give it a try. After succefully running it from the cd i attempted installation alongside windows xp.

The installation was succesful and gave no warnings

unfortunetly when i try to boot now Ubuntu fails :(   
i get the initial splash screen with the increasing amber bar - then the screen begins to flash with a various corrupted colours. My Windows installation still works fine

is there anytthing i can do to remedy / troubleshoot this.

Thanks

Mat

---

### Post by lovelyvik293 on 2008-12-08
> **mat429 said:**
> 

unfortunetly when i try to boot now Ubuntu fails :(   
i get the initial splash screen with the increasing amber bar - then the screen begins to flash with a various corrupted colours. My Windows installation still works fine

is there anytthing i can do to remedy / troubleshoot this.

Thanks

Mat
Please post the error which ubuntu shows at boot time.

---

### Post by binbash on 2008-12-08
are you using ati card?

---

### Post by mat429 on 2008-12-09
Hi,

thanks for the responses:
in answer to the queries above.
1) there is no error message - everything seems to be running fine, until the entire screen corrupts into a pink screen.

2) i am using a Nvidia geforce 5200 fx, drivers are up to date.

Thanks

Mat

---

### Post by davidbilla on 2008-12-09
I too have GeForce 5200FX. And I get the same screen always. I get the same screen during shutdown too. Just wait for a few seconds. Ubuntu will boot. It's actually the Ubuntu splash screen. I hope it's not hanging. To check this, try pressing Ctrl+Alt+F1 when you see the pink screen. You'll get the text boot and the command prompt.

If you don't want the splash screen, just do the following. You don't necessarily need to do this. The garbled screen is harmless, at least in my case!

```
$ cd /boot/grub/
$ sudo vi menu.lst
```

In 'menu.lst' find your Ubuntu entry. It'll be easy to find. You'll normally have 3 entries - one for normal boot, one for recovery and another one for memtest (in that order). The first few lines that start with a '#' are comments in shell script. These are examples for 'menu.lst' entries. The part you need to change is at the very last, normally.

Find your boot entry that looks like this (It may not be exactly the same, but something similar):
```

title          Ubuntu x.xx, kernel 2.6.xx-xx-generic
root           (hd0,0)
kernel         /vmlinuz-2.6.xx-xx-generic root=UUID=<some no.> ro quiet splash
initrd         /initrd.img-2.6.xx-xx-generic
quiet
```

In the 'kernel' option change 'splash' to 'nosplash' and save the file by typing Esc, then ':wq'. Now reboot to boot without splash screen.

Note: You have to do 'sudo' and enter your password. This file is not normally editable. When you do 'sudo' you are granted root privileges.

---

### Post by linux_tech on 2008-12-09
To get more info try:
```
lspci | grep -i nvidia
```
To get video any error or warning messages from xorg.conf is:
```
cat /var/log/Xorg.0.log | grep EE
```

Here is a link with some good information about nvidia drivers for ubuntu
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mat429 on 2008-12-16
Hi, 

thanks for the responses.

i have succesfully logged in using the ctrl- alt f1 route  - and managed to find the menu.lst however i'm struggling with the text display beyond that - my screen does not scroll through the menu and to refresh it i have to switch to another instance (ctrl-alt-f2,3, etc. 

is this a problem with my display in text mode - or am i doing something wrong?

thanks
 
mat

---

### Post by Tatty on 2008-12-16
There is an easier way to temporarily disable the splash screen for a specific boot.

At grub, select the entry you want to boot from, then press "e" to edit it.  Go down to the line beginning "kernel" then press e to edit it.  Delete the words "quiet splash" from the end of the boot string.  This will make Ubuntu boot without the splash screen and with verbose output.

Press enter, then press "b" to boot the kernel.

[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

The changes are not permanent, the next boot will have the splash screen again.

---

