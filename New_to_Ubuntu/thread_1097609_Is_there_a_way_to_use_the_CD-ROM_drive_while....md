---
title: "Is there a way to use the CD-ROM drive while..."
date: 2009-03-16
forum: New to Ubuntu
---

### Post by cludos on 2009-03-16
...booted into the Live CD version? It seems the drive is locked shut by the OS while it is booted up and it won't let me remove the Live CD in order to put in something else. I'm using Feisty Fawn btw.

---

### Post by diwas on 2009-03-16
Well, I don't think so. Sorry.

---

### Post by billgoldberg on 2009-03-16
If you have a usb stick laying around you could install Ubuntu on that and boot from it.

Then you could use your cd-rom drive while using the live usb session.

---

### Post by cludos on 2009-03-16
I was afraid of that...  Thank you for replying, diwas.

---

### Post by cludos on 2009-03-16
> **billgoldberg said:**
> If you have a usb stick laying around you could install Ubuntu on that and boot from it.

Then you could use your cd-rom drive while using the live usb session.

I do have USB sticks lying around. How do I install Ubuntu on those?

---

### Post by orethrius on 2009-03-16
Hold Alt and hit F2, then:

```
xterm -e 'gksudo apt-get install usb-creator'
```

After you've done that, it'll be under "System > Administration > Create a USB startup disk".

---

### Post by skymera on 2009-03-16
There are many guides on Pendrivelinux.com

Also there's a program called USBuntu that can create persistent Ubuntu USB installs.

---

### Post by cludos on 2009-03-16
> **orethrius said:**
> Hold Alt and hit F2, then:

```
xterm -e 'gksudo apt-get install usb-creator'
```

After you've done that, it'll be under "System > Administration > Create a USB startup disk".

When I entered that command, the window opens and closes too quickly. I tried  the same command inside a terminal window. This is the output, I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Couldn't find package usb-creator

```

I had modified my **sources.list**. This is how
my **sources.list** currently looks:

```
deb cdrom:[Xubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://old-releases.ubuntu.com/ubuntu feisty main restricted
deb-src http://old-releases.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com/ubuntu feisty universe
deb-src http://old-releases.ubuntu.com/ubuntu feisty universe

deb http://old-releases.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu feisty-security main restricted

deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
```

---

### Post by orethrius on 2009-03-16
Oh, Feisty.  Sorry man, I figured you were on at least Hardy, due to the lack of OS type on your userbar. ;)

---

### Post by cludos on 2009-03-16
> **skymera said:**
> There are many guides on Pendrivelinux.com

Also there's a program called USBuntu that can create persistent Ubuntu USB installs.

Thanks, skymera. I'll give those guides on pendrivelinux a try. 

> **orethrius said:**
> Oh, Feisty.  Sorry man, I figured you were on at least Hardy, due to the lack of OS type on your userbar. ;)

Yea, I'm on Feisty. I had mentioned it in my original post. I have the **Intrepid Ibex** ISO sitting on a hard drive that I can access, but cannot boot from presently. That's why I want to access my CD-writer, while booted into the Live CD; so I could burn it to CD.

Thanks for all the help everyone. :)

---

### Post by billgoldberg on 2009-03-16
> **cludos said:**
> Thanks, skymera. I'll give those guides on pendrivelinux a try. 



Yea, I'm on Feisty. I had mentioned it in my original post. I have the **Intrepid Ibex** ISO sitting on a hard drive that I can access, but cannot boot from presently. That's why I want to access my CD-writer, while booted into the Live CD; so I could burn it to CD.

Thanks for all the help everyone. :)

Oh, you can easily install Ubuntu 8.10 using a usb stick instead of a cd.

Google for "unetbootin", install the .deb package.

When you open the program, point to the 8.10 iso and the flash drive, it will write the needed stuff to the stick.

Then you can boot from the USB and install Ubuntu to your HDD.

---

### Post by cludos on 2009-03-18
> **billgoldberg said:**
> Oh, you can easily install Ubuntu 8.10 using a usb stick instead of a cd.

Google for "unetbootin", install the .deb package.

When you open the program, point to the 8.10 iso and the flash drive, it will write the needed stuff to the stick.

Then you can boot from the USB and install Ubuntu to your HDD.

Thank you very much for that tip, billgoldberg. I tried "**unetbootin**" and it seemed to work brilliantly. It extracted the ISO onto the USB stick and installed a boot loader on it. I'm now able to boot into **Intrepid** using the USB stick, but it seems the X server on **Intrepid** does not like my onboard graphics (**i845**), but I guess that's a separate problem and deserves a thread of it's own. I'll search the forums for threads that might offer possible solutions. Thanks to everyone who chipped in on this thread. :)

---

