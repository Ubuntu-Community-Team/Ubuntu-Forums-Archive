---
title: "live cd - how long until I get focus ?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by southof40 on 2009-12-23
I've put a live CD into an Toshiba Satellite Pro 4600. Things seem to be happening - I've got a desktop with the ubuntu bird, tool bar with 'applications'/'Places'/'System'. Desktop icons 'Examples'/'Install' but I still don't actually have control of the system (after some 30 minutes).

From time to time a mouse cursor is seen. The desktop is only occupying perhaps 75% of the height and width of the screen. CD drive appears to be very busy.

I've never done this before. I presume that's something wrong but what should I do ? I don't seem to have access to anything like a log which might tell me where it's up to.

---

### Post by wil08son on 2009-12-23
Maybe you should check the integrity of your disc. There should be an option when the Live CD first boots to "Check CD for Defects". Run that and see if the process finishes and if there are any problems with your CD.

---

### Post by southof40 on 2009-12-24
Thanks I'm trying that now. As far as there is a 'normal' how long should it take to go from power on to where the user has control when using a live CD ?

---

### Post by cenzorrll on 2009-12-24
i typically can use a live cd within about 3 minutes from boot, less if i use a usb drive

---

### Post by southof40 on 2009-12-24
OK the disk check likes the CD. I've rebooted and I once again have the desktop with a visible mouse cursor but which the 'eraser mouse' in the middle of the keyboard can't move. The date/time in the top right of the screen shows a moment in time about six minutes ago (when it was first painted to the screen I guess) and does not change. 

In reading elsewhere I believe ALT-F1 should provide the applications menu and I've tried that but nothing happens.

Is there any way I can 'break through' the desktop to see what point it is at in the start up procedure ?

Is it worth taking the option to book in text mode ? (Although long term I definitely want the GUI).

Any comments welcome. Thanks.

---

### Post by running_rabbit07 on 2009-12-24
If you don't mind, could you tell us your system specs?

---

### Post by southof40 on 2009-12-24
Sure - happy to. It's a Toshiba Satellite Pro 4600 (it's my wifes old machine so not very familiar with it) as far as I can make out we're talking :

Pentium III
256Mb RAM
16Gb Free Disk
Windows 2000 installed currently
BIOS set to book first off CD 

Not sure what other specs might be of interest ? Would be happy to find out if it was significant. Thanks for your interest.

---

### Post by running_rabbit07 on 2009-12-24
> **southof40 said:**
> Sure - happy to. It's a Toshiba Satellite Pro 4600 (it's my wifes old machine so not very familiar with it) as far as I can make out we're talking :

Pentium III
256Mb RAM
16Gb Free Disk
Windows 2000 installed currently
BIOS set to book first off CD 

Not sure what other specs might be of interest ? Would be happy to find out if it was significant. Thanks for your interest.

Are you using a Ubuntu or Xubuntu LiveCD? Ubuntu prefers at least 512MB RAM.

---

### Post by running_rabbit07 on 2009-12-24
See [Xubuntu]("http://www.xubuntu.org/get")

---

### Post by southof40 on 2009-12-24
Oh OK. Hadn't thought of that ! I thought 'runs windows must be able to run Linux' ! It is indeed Ubuntu. Looks like even if I installed it for real I'd be running pretty low trying to use 256MB so I guess I'll try Xubuntu.

---

### Post by mc4man on 2009-12-24
You should keep in mind that the live cd is installed to ram which @256 is leaving very little left. 
To test something the other day I** installed** ubuntu to an old laptop with only 256  ram, it ran but was very sluggish. (and this laptop had a video card, not onboard video that uses shared memory - not to say that's the case here but if so would only make things worse

Can't see how a live cd would be of much use with those specs

---

### Post by running_rabbit07 on 2009-12-24
I see where you are coming from. The thought of running a Windows machine with low memory is scary. My laptop had a 300something MB RAM with 2000 Pro and it ran much faster with Xubuntu.

Good luck and feel free to ask if you have any more questions.

---

### Post by southof40 on 2009-12-24
Thanks to all of you for your help - I appreciate it.

---

### Post by egalvan on 2009-12-24
OK, here's my nickel's worth of advice...

boot from the LiveCd and run the "memtest" optiion.

let it run at least one full cycle... may take 12-24 hours...

while the memory is being tested, borrow another machine and down-load and burn the following two mini-distro's...
(both run well in 256MB, both are small downloads)

PartedMagic LiveCD
an excellent, rather full-featured mini-distro...
it's what I use for ALL my partitioning work,
and yes, I support it with $$, I have a subscription.
main page...
[http://partedmagic.com/](http://partedmagic.com/)


puppy linux
a fast, stable, mini-distro... boots superfast, runs superfast.
(did I mention it's fast?)
main page...
[http://www.puppylinux.com/](http://www.puppylinux.com/)

download page, if you want the latest puppy (4.3.1)
[ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/](ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/)



Try your machine with Puppy. It should run well. 

If you want to install Linux, can you give it at least one extended partition,
of at least 6-8GB size?
(I don't know what you mean in your specs by **16Gb Free Disk**)

---

### Post by adam814 on 2009-12-24
If you're absolutely set on having a GNOME desktop you might have more luck installing with the alternate install CD instead of the LiveCD.  The system requirements should be lower without trying to run a full GUI during the install.  After the system is installed you'd presumably have a swap partition to cushion the low amount of memory and be able to use all the features.

I'd still think Xubuntu is a more viable option and you might even want to look into fluxbox as it should be even more lightweight than XFCE desktop.

---

### Post by southof40 on 2009-12-24
> **egalvan said:**
> OK, here's my nickel's worth of advice...

boot from the LiveCd and run the "memtest" optiion.

let it run at least one full cycle... may take 12-24 hours...

while the memory is being tested, borrow another machine and down-load and burn the following two mini-distro's...
(both run well in 256MB, both are small downloads)

PartedMagic LiveCD
an excellent, rather full-featured mini-distro...
it's what I use for ALL my partitioning work,
and yes, I support it with $$, I have a subscription.
main page...
[http://partedmagic.com/](http://partedmagic.com/)


puppy linux
a fast, stable, mini-distro... boots superfast, runs superfast.
(did I mention it's fast?)
main page...
[http://www.puppylinux.com/](http://www.puppylinux.com/)

download page, if you want the latest puppy (4.3.1)
[ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/](ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/)



Try your machine with Puppy. It should run well. 

If you want to install Linux, can you give it at least one extended partition,
of at least 6-8GB size?
(I don't know what you mean in your specs by **16Gb Free Disk**)
Well the machine has something like 20Gb of disk but it has a Windows2000 already installed on it. So it's got about 16Gb free. I was hoping (at least initially) to not blow away the W2000 but I'm sure we could a do a 10Gb partition for the use of Linux.

Thanks for your other distro suggestions. I have a friendly neighbour who uses Ubuntu and so initally I'll see if I can get Xubuntu working but I'll bear in mind Puppy as even for Xubuntu this machine isn't exactly fat. 

I should explain that I had assumed this machine had at least 0.5Gb RAM - it was only when people asked in this thread that I discovered it (what in 2009 seems) very little memory !

---

### Post by sandy8925 on 2009-12-24
256 MB RAM should be just about enough to run Ubuntu. I run it with the same amount of RAM and it's ok until I open a lot of stuff at which point  it slows down. But you have a p3 and therefore older motherboard. Your CD drive is probably too slow to use a livecd in. 

Like someone else suggested try PuppyLinux. Some other suggestions are DSL (DamnSmallLinux - approx. 50 MB) and Geexbox(media center OS - 19 MB).

Geexbox can't be used for general desktop usage. It is purely meant for playing media files.

---

### Post by southof40 on 2009-12-24
> **adam814 said:**
> If you're absolutely set on having a GNOME desktop you might have more luck installing with the alternate install CD instead of the LiveCD.  The system requirements should be lower without trying to run a full GUI during the install.  After the system is installed you'd presumably have a swap partition to cushion the low amount of memory and be able to use all the features.

I'd still think Xubuntu is a more viable option and you might even want to look into fluxbox as it should be even more lightweight than XFCE desktop.
OK thanks for your comments about the alternate install CD - I had wondered about whether part of the problem was the live CD but when I looked at the Ubuntu specs I realised I was sailing pretty close to the edge in any case. I'm downloading Xubuntu right now so I'll give that a try and see how I go.

---

