---
title: "black screen, live cd"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by addylad on 2008-12-29
Hi,

When i put the live cd in and choose test from the menu, i get a black screen with white writing.  It also asked for a root password, but i expected a gui.  Can you help?

Thanks.

Edit: a picture:

[[IMG]http://img135.imageshack.us/img135/6549/29122008006nn5.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=29122008006nn5.jpg)

---

### Post by nhasian on 2008-12-29
when i put the liveCD in, it prompts me for a language (defaults to english) so i hit enter.  then i have the boot options:
> 
Try Ubuntu without any change to your cmoputer
Install Ubuntu
Check CD for defects
Test memory
Boot from first hard disk

are you trying to test the computer memory or check the CD for defects?  it shouldnt ask for any passwords.  make sure your computer's bios is set to boot off the cdrom before the hard disk.

---

### Post by addylad on 2008-12-29
I get up to the try the cd option, after that it has a loading bar for ages and then it comes up almost like DOS.  I'll take a picture soon.  The boot order is fine.

---

### Post by addylad on 2008-12-29
Hi,

Below is a picture of what is going on.  I did check the CD for defects but there were no errors.  I've heard of the alternate CD; could this be what I need?  What's the difference?

[[IMG]http://img135.imageshack.us/img135/6549/29122008006nn5.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=29122008006nn5.jpg)

Thanks for your help.

By the way it's Ubuntu 8.10 I'm using.

My system specs are: laptop, 1.5GB RAM, 32bit AMD Athlon XP 2400+ CPU.  Currently have Windows XP Home installed.  If you need any more information, please ask.

---

### Post by RichardLinx on 2008-12-29
Could you please post your computer specs. From the photo you posted I can see that you are trying to install the i686 version (32Bit) I had a friend that has a 64Bit computer and would not load the 32Bit version of 8.10 no matter what he tried, It could be that you are having the same issue. Otherwise it may fall down to hardware. If you don't have sufficient RAM for example their is a good chance it will ask you to install through terminal. I believe the minimum is close to around 384MB of RAM for a GUI install.

---

### Post by addylad on 2008-12-29
> **RichardLinx said:**
> Could you please post your computer specs. From the photo you posted I can see that you are trying to install the i686 version (32Bit) I had a friend that has a 64Bit computer and would not load the 32Bit version of 8.10 no matter what he tried, It could be that you are having the same issue. Otherwise it may fall down to hardware. If you don't have sufficient RAM for example their is a good chance it will ask you to install through terminal. I believe the minimum is close to around 384MB of RAM for a GUI install.

Hi,

I had just edited my above post to show some specifications.

1.5GB PC2700 RAM
32bit AMD Athlon XP 2400+ CPU
Windows XP Home currently installed
Samsung 100GB hard disk drive

If there is anything else you need, please ask.  Should I go for it and install?  I was considering doing this but if the Live CD won't even work...

Thanks a lot for your help.

---

### Post by addylad on 2008-12-29
I just put the CD in again and booted, instead of going to the menu it went straight to the screen (pictured above) which flash several times before displaying underneath:
Broadcast messgae from root@ubuntu

I think it said something was 'unknown' as well.

---

### Post by RichardLinx on 2008-12-29
If it were me I would give the install a try even If I couldn't get it to load up as a live CD. But you already have Windows installed and I'm guessing you don't want to delete your XP partition which is something that is more likely to happen through a CLI install if you're not too sure on what your doing. Here's what I'll recommend: Backup your Windows installation (maybe even ghost it onto another hard drive if you have one available) and then proceed with installing Ubuntu, once installed you should be able to work through the problems and get it up and running nicely.

If this way is too much of a hassle for you then you might be better off trying out a distro like openSUSE (I hear 11.1 is quite an improvement!). Your hardware is more then enough to run Ubuntu.

Info on openSUSE: [http://en.wikipedia.org/wiki/OpenSUSE](http://en.wikipedia.org/wiki/OpenSUSE)
                : [http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org)

You could also try installing Wubi or Ubuntu in a virtual machine. Good luck! :)

---

### Post by RichardLinx on 2008-12-29
> **addylad said:**
> I just put the CD in again and booted, instead of going to the menu it went straight to the screen (pictured above) which flash several times before displaying underneath:
Broadcast messgae from root@ubuntu

I think it said something was 'unknown' as well.

It sounds like Ubuntu doesn't like your hardware for some reason. Your probably just better off waiting for the next version or trying a different Linux distro. Linux Mint might be another good choice, though I'm not sure you'd have any more luck then you did with Ubuntu since It is based of Ubuntu. There are a lot of distributions to choose from so If your keen to get started with Linux take a look at a few other distros, Fedora, Debian, OpenSUSE, etc. It's a shame Intrepid is giving you such a hard time, hopefully the next release will have out of the box support for your hardware. :D

---

### Post by addylad on 2008-12-29
> **RichardLinx said:**
> If it were me I would give the install a try even If I couldn't get it to load up as a live CD. But you already have Windows installed and I'm guessing you don't want to delete your XP partition which is something that is more likely to happen through a CLI install if you're not too sure on what your doing. Here's what I'll recommend: Backup your Windows installation (maybe even ghost it onto another hard drive if you have one available) and then proceed with installing Ubuntu, once installed you should be able to work through the problems and get it up and running nicely.

If this way is too much of a hassle for you then you might be better off trying out a distro like openSUSE (I hear 11.1 is quite an improvement!). Your hardware is more then enough to run Ubuntu.

Info on openSUSE: [http://en.wikipedia.org/wiki/OpenSUSE](http://en.wikipedia.org/wiki/OpenSUSE)
                : [http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org)

You could also try installing Wubi or Ubuntu in a virtual machine. Good luck! :)

Thanks.  Are there any features of Windows XP which allow me to back up.  I do have Acronis TrueImage, but I want to avoid installing if possible.  Are there any free programs that can ghost?

---

### Post by addylad on 2008-12-29
> **RichardLinx said:**
> It sounds like Ubuntu doesn't like your hardware for some reason. Your probably just better off waiting for the next version or trying a different Linux distro. Linux Mint might be another good choice, though I'm not sure you'd have any more luck then you did with Ubuntu since It is based of Ubuntu. There are a lot of distributions to choose from so If your keen to get started with Linux take a look at a few other distros, Fedora, Debian, OpenSUSE, etc. It's a shame Intrepid is giving you such a hard time, hopefully the next release will have out of the box support for your hardware. :D

If I can back up an image of the current C partition to a file then I will go for it and see what happens! :P

---

### Post by addylad on 2008-12-29
OK, so I think I may not have the correct ISO file... I'm using ubuntu-8.10-desktop-i386, which I don't think would be compatible with 32BIT AMD ATHLON CPUs - is there a version I should be using (perhaps the alternate CD)?

I'm downloading Kubuntu now to see if that helps.  I also used winMd5Sum and the ISO was fine, so I don't see what's wrong (unless I've used the wrong disc/don't have compatible hardware.

It's an Acer Aspire 1350 series laptop, if that helps...

---

