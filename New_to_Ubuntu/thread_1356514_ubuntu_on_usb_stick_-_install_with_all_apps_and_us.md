---
title: "ubuntu on usb stick - install with all apps and users?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by gorgon on 2009-12-16
Hi all,

I made a usb stick version of ubuntu (well, xubuntu really, very useful to put on friends old windows machine to show them how snappy things get with xubuntu :)).

What Im wondering is if it is possible to install the system from the usb stick to a computer and have all the installed applications, files, preferences etc follow in the install? Or is this something that is possible to do (easily) after a fresh install?

It would be really nice.

cheers,
g

---

### Post by Roger Allott on 2009-12-16
Do you mean that you've installed Xubuntu onto your memory stick or that you've created a USB Startup Disk?

---

### Post by KeLa on 2009-12-16
Have you checked this.

[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

There is good guide to create LiveCD on usb stick.

---

### Post by gorgon on 2009-12-17
KeLa:> Have you checked this.

[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

yes, sorry if im being unclear - i have made already an installation of xubuntu on my usb stick (using UNetbootin). What Im wondering now is if it is possible to install the system FROM the usb stick TO a computer AND have all the installed applications, files, preferences etc follow in the install?

I have already made an installation from the usb stick, which was smooth, but it would be great to have all the special tweaks and files I have on the usb stick to go into the hd installation as well..

---

### Post by KeLa on 2009-12-17
I have done it with 9.04 unr and 9.04 desktop.
Get iso image of the live cd and put it to the stick with unetbootin and boot your
pc with from the stick and install the system (it works as live cd)

---

### Post by gorgon on 2009-12-18
@KeLa:
So, you on your install to the HD you got all the extra applications and users preferences that you had stored on the usb stick? Did you get prompted with the option of doing this or to do a 'clean' install? This is strange since I did not see it when I was actively looking for it..

Are you sure you got my problem right? The difference with the live usb and live cd is offcourse that you can make changes to the live usb that will not change on reboot, i.e. install applications, store files and so on, while booting from the live cd all the apps that you install will not be there on reboot (since you cannot write more to the disk). What I want is that all my stored apps, files and preferences also gets installed when I choose to install to another harddrive from the usb stick.

---

### Post by PaulReaver on 2009-12-18
No

when you install from a usb start up disk its a fresh install.

all settings will go back to default.

---

### Post by ukripper on 2009-12-18
> **gorgon said:**
> 

What Im wondering is if it is possible to install the system from the usb stick to a computer and have all the installed applications, files, preferences etc follow in the install? Or is this something that is possible to do (easily) after a fresh install?

It would be really nice.

cheers,
g

you would need your usb stick/drive to boot using persistent mode to be able to do that- [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by KeLa on 2009-12-18
> **PaulReaver said:**
> No

when you install from a usb start up disk its a fresh install.

all settings will go back to default.

Yes that's true, it's like fresh install from cd-rom.

---

### Post by gorgon on 2009-12-18
@ukripper
ah! still learning! I didnt know about 'Persistence Mode', I just thought my usb stick had xubuntu with some additional packages but seems that the [pure:dyne team]("https://launchpad.net/~puredyne-team") goes a lot deeper.. and uses 'persistence mode'.

I did not however see any option of installing from the usb stick with all the saved data that i got on my stick, but I guess it's better to take this directly with them. Thanks for all the responses!

---

