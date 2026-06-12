---
title: "[SOLVED] Let me know if this would work, and how to go about it"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by halberdier25 on 2009-01-05
Hi,

I really am not good at what I'm doing with Linux, but it has it's perks.  I really appreciate all ubuntuforums has helped me with.  You've fixed more than one computer and more than one occasion.


I have and Acer AspireOne that I carry with me everywhere.

I would like to install something like Damn Small Linux or Really Tiny Linux on a 4GB thumbdrive, then use it on my Acer netbook.  Problem is, I would also like to get wireless internet while using Linux, and wouldn't know how to connect Linux to the wireless card in the netbook.

Is this a pipe dream?  If not, how would I go about it?

Thanks so much!

I know this isn't necessarily Ubuntu, but the same principles apply.

---

### Post by gettinoriginal on 2009-01-05
Do some research, there are special "light weight" distros out there, I think Puppy Linux is one :confused:  And for the wireless, you can try these:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[http://beginlinux.wordpress.com/2008/11/01/solving-wireless-issues-with-ubuntu-810-intrepid-ibex/](http://beginlinux.wordpress.com/2008/11/01/solving-wireless-issues-with-ubuntu-810-intrepid-ibex/)

---

### Post by new4me on 2009-01-05
You could also try [www.pendrivelinux.com](www.pendrivelinux.com), its pretty much one of the best sites out there.

---

### Post by halberdier25 on 2009-01-05
The bigger question was getting Linux to talk to the wireless card in my laptop.  When I've done it in the past, I haven't gotten it to work.  Does anyone know of a good way to get it done?

---

### Post by terrysolid on 2009-01-05
I have an Aspire One 150 currently running Ubuntu 8.10. Regardless of which distro you wish to install - there are a few issues with the Aspire One that you will need to iron out post install. The card readers, wireless, and sound all have some issues. There is some good information at [http://help.ubuntu.com/community/AspireOne]("http://help.ubuntu.com/community/AspireOne") and also at [http://aspireoneuser.com/forum]("http://aspireoneuser.com/forum")

---

### Post by tuxxy on 2009-01-05
You could get a new compatible USB wifi adapter if the card fails, d links seem to be a good choice

---

### Post by terrysolid on 2009-01-05
> **tuxxy said:**
> You could get a new compatible USB wifi adapter if the card fails.

In Ubuntu 8.10, there's 3 different ways you can get the onboard wireless to work:

1. use ath5k from backports
2. install modified kernel
3. make and use madwifi drivers

Edit: Also, why is it you wish to use a compact distro. The 150 has the Atom N270 and 1GB of ram which is fine for Ubuntu, even with gnome. You would probably get a little more speed out of xfce, but if you have one of the newer Aspire Ones, there's really no reason to go with anything but Ubuntu :-)

---

### Post by halberdier25 on 2009-01-05
Well, the intent is to install it on a thumbdrive and boot via USB.  I am too much of a wimp to attempt partitioning my harddrive while I still have stuff on it I want to keep.

---

