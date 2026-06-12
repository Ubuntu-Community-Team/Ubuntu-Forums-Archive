---
title: "Making bootable USB flash drive for 10.10 in Ubuntu 10.04"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by tesex167 on 2010-12-12
I currently have Ubuntu 10.04 installed - would it be possible to make a bootable USB flash drive for version 10.10 using 10.04 and what would I need to do this (i.e. live CD for 10.10?)...

---

### Post by Wobblybob on 2010-12-12
Yep, you can use a Live Disc to boot up the PC in the correct version then make your bootable USB from the Live session, see [[COLOR="Blue"]http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/[/COLOR]]("http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/")

---

### Post by amjjawad on 2010-12-12
> **tesex167 said:**
> I currently have Ubuntu 10.04 installed - would it be possible to make a bootable USB flash drive for version 10.10 using 10.04 and what would I need to do this (i.e. live CD for 10.10?)...

1) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
then go to no.2 
> Burn your CD or create a USB drive 
Click USB Stick, Ubuntu then Show me how

OR

2) [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


You don't need to boot using any Live media. Just login to Ubuntu and use one of the above methods (either 1 or 2).
What you really need beside these tools is the .iso file for Ubuntu 10.10 and that's all.

Enjoy ;)

---

### Post by C.S.Cameron on 2010-12-13
If you are already running 10.04, download 10.10 iso to desktop and go to System/Administration/Startup Disk Creator.
If you want the flash drive to save changes use Stored in reserved extra space

---

### Post by beew on 2010-12-13
> **Wobblybob said:**
> Yep, you can use a Live Disc to boot up the PC in the correct version then make your bootable USB from the Live session, see [[COLOR=Blue]http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/[/COLOR]]("http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/")

Rather complicated. You only need to download the 10.10 iso,  insert a usb formatted to FAT, Go to System > Administration > Start Up Disk Creator and open it, choose the downloaded iso image as the source and the usb as the target (usually dev/sdb or dev/sdc) and start. There is an option to make the usb persistent (remembering changes) and that's it. 

Pendrivelinux is mainly for people with Windows, OP already has Ubuntu 10.04 installed so most of those tutorials don't apply.

Edited: Just see that C.S.Cameron has beaten me to it.

---

### Post by beew on 2010-12-13
> **amjjawad said:**
> 1) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
then go to no.2 

Click USB Stick, Ubuntu then Show me how

OR

2) [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


You don't need to boot using any Live media. Just login to Ubuntu and use one of the above methods (either 1 or 2).
What you really need beside these tools is the .iso file for Ubuntu 10.10 and that's all.

Enjoy ;)

Hi, how are you? Just want to mention that OP wants to be able to save changes, so I am afraid unetbootin won't work because it doesn't support persistence. But it is a good recommendation if someone just want to create a live usb mainly to install.  Incidentally, unetbootin appears to be the only easy to use gui tool to create a live usb for Fedora 14 (no persistence), Fedora's own live usb creator only works up to 13, go figure.

---

### Post by amjjawad on 2010-12-13
> **beew said:**
> Hi, how are you? **Just want to mention that OP wants to be able to save changes**, so I am afraid unetbootin won't work because it doesn't support persistence. But it is a good recommendation if someone just want to create a live usb mainly to install.  Incidentally, unetbootin appears to be the only easy to use gui tool to create a live usb for Fedora 14 (no persistence), Fedora's own live usb creator only works up to 13, go figure.

Hello my friend :) I'm fine, thanks for asking :)

Well, I didn't see that anywhere in his post ;)
However, method 1 will do the job as long as he's using Ubuntu.
Method 2 is an alternative. So, he got 2 methods.

As for Fedora, let's talk about that somewhere else :)
I'm thinking to create a group and invite all my friends (you'll be the first) and open such discussion. I love discussion :)

---

