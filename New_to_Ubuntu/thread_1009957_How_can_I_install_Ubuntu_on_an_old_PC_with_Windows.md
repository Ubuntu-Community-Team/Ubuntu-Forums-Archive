---
title: "How can I install Ubuntu on an old PC with Windows ME?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Roger at CCCC on 2008-12-13
How can I install Ubuntu on an old PC with Windows ME?  

I’m an absolute beginner with Ubuntu, but would like to try Ubuntu out on an old PC with a Pentium 3 and 128 MB main memory.  There is 10 GB of free disk space AND internet access through my home network BUT:  

the CDROM drive works but the PC cannot boot from it so the Ubuntu 8.1 CDROM does not work; 
USB flash drives work but the PC cannot boot from them either; 
the floppy disk drive does not work at all and cannot be used; 
the Operating system is Windows ME (which means that WUBI does NOT work )  

What’s the easiest and quickest way to get Ubuntu working on this machine?  Thanks in advance for any simple suggestions (I’m not good at Linux/Ubuntu jargon, so if it could be avoided, that would be great)

---

### Post by ugm6hr on 2008-12-13
Do you have another computer that you could swap out the HD into.

I have heard it is possible to install on a different computer, then put it into the older computer before the first boot.  That should configure xorg properly.  If not, the following will do it:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

PS: If you can't boot from a CD, I would consider setting a separate partition to store future updated ISOs when Intrepid is no longer supported.  In fact, consider using Hardy for the extra year of support.

---

### Post by mikeyphi on 2008-12-13
Have a look at this guide - it should do what you need:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by philinux on 2008-12-13
Ubuntu wont run very well at all with 128meg ram. Xubuntu would be better. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by theozzlives on 2008-12-13
if you have internet access go to [http://www.virtualbox.org]("http://www.virtualbox.org") and download the  VirtualBox for Windows, then install Ubuntu into a  VirtualBox using the *.ISO as a  cd drive. Ubuntu will run in a VirtualBox under Windows (you can even make it "full screen").

---

### Post by ugm6hr on 2008-12-13
> **theozzlives said:**
> if you have internet access go to [http://www.virtualbox.org]("http://www.virtualbox.org") and download the  VirtualBox for Windows, then install Ubuntu into a  VirtualBox using the *.ISO as a  cd drive. Ubuntu will run in a VirtualBox under Windows (you can even make it "full screen").

Probably not so well with 128MB RAM.

---

### Post by theolster on 2008-12-13
Although it is quite difficult installing Ubuntu on < 128MB is possible, but I had to do it using the Alternative CD (I used hardy I think and uninstalled a whole buch of stuff from the command line).

It would be much easier to use Xubuntu!

---

### Post by ugm6hr on 2008-12-13
> **theolster said:**
> It would be much easier to use Xubuntu!

Actually, 128MB will be a little low even for Xubuntu.

I'd suggest a minimal installation (see the LXDE link below for an example).

The main problem is no CD / USB / floppy booting options.

---

### Post by theozzlives on 2008-12-13
you might be able to install [Damn Small Linux]("http://damnsmalllinux.org/dsl-hd-install.html") if you don't wanna go with VirtualBox

---

### Post by Roger at CCCC on 2008-12-13
Wow, thanks to everybody for all your suggestions.  I will be studying them in the coming week.  Here are a few quick comments: 

1.  I am a little surprised that Ubuntu doesn&#8217;t run well on 128 MB when Windows ME is adequate.  I don&#8217;t know anything about Xubuntu but wonder if I should try it.  

2.  I forgot to say that I hope Win/ME can dual boot with whatever version of Linux I finally try.  If anybody has any further comments about that, I would appreciate it.  

Thanks again for your help.  

PS The first time I put this comment on, the system rejected it with an error message.  This is the second try.

---

### Post by Kareeser on 2008-12-13
The GRUB bootloader should have no problem booting into Windows ME. Windows won't even know Ubuntu is on the computer :)

Are you sure the computer is not bootable with the CD-ROM? Check your BIOS settings.

---

### Post by ugm6hr on 2008-12-13
> **Roger at CCCC said:**
> 1.  I am a little surprised that Ubuntu doesn&#8217;t run well on 128 MB when Windows ME is adequate.  I don&#8217;t know anything about Xubuntu but wonder if I should try it.  

2.  I forgot to say that I hope Win/ME can dual boot with whatever version of Linux I finally try.  If anybody has any further comments about that, I would appreciate it. 

Remember, the current era of Ubuntu is from 2008.  Windows ME is from 2000.  The basic hardware from those eras are generations apart.  Ubuntu's requirements are similar to XP, but significantly less than Vista.  The main difference is that Ubuntu can be installed with lighter desktop environments, which no Windows OS can.  Hence 128MB is too low for Ubuntu, borderline-OK for Xubuntu, and fine for a custom lightweight *buntu.

Ubuntu can dual boot with anything (inc W-Me).  Although if you go online, I would consider removing W-Me due to lack of support (and significant security risk).

EDIT: Also, remember that installing a dual-boot requires repartitioning unless you have 2 HDs.  Repartitioning runs the risk of data loss or corruption.  Normally, I merely advise a backup to safeguard.  However, since you have no floppy / CD boot options, reinstalling W-Me would likely be impossible if you were unfortunate enough to have a problem.

---

### Post by richaoj on 2008-12-13
> **ugm6hr said:**
> Remember, the current era of Ubuntu is from 2008.  Windows ME is from 2000.  The basic hardware from those eras are generations apart.  Ubuntu's requirements are similar to XP, but significantly less than Vista.  

Ditto.  Linux can be great for bringing back life to old hardware, but it is not a windows-from-8-years-ago equivalent.  I've found the best way for beginners to enjoy ubuntu is to install it on current hardware and see how versatile and fast it is compared to vista/xp.

I use ubuntu because i love it-not because i just can't install vista on the machine (actually my machine came with vista that lasted about an hour--long enough for me to download and burn an iso of 8.10 the day it came out).

But if you want to run it on that machine, why not buy a some ram (RAM is soo cheap these days) and give ubuntu a fair shot?

---

### Post by egalvan on 2008-12-13
> **richaoj said:**
> Ditto.  Linux can be great for bringing back life to old hardware, but it is not a windows-from-8-years-ago equivalent.  I've found the best way for beginners to enjoy ubuntu is to install it on current hardware and see how versatile and fast it is compared to vista/xp.

Maybe not Ubuntu, but PuppyLinux can run wonders on older, slower machines.


> But if you want to run it on that machine, why not buy a some ram (RAM is soo cheap these days) and give ubuntu a fair shot?

Yeah, DDR2 RAM is cheap as dirt, but unfortunately, older RAM is not always "soo cheap". 
I bought 4 sticks of 2Gig DDR2 for $78 shipped from Newegg last week. :)

The cheapest I've seen DDR is $50 for 2 sticks of 1Gig

As for PC133 stuff...

And of course, older machines take older-style RAM.

ErnestG

---

### Post by richaoj on 2008-12-14
d'oh.  didn't think about it.

---

### Post by kansasnoob on 2008-12-14
I'd suggest Puppy:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

I've tried both Damn Small and Puppy. Puppy is the winner!

---

### Post by egalvan on 2008-12-14
> **kansasnoob said:**
> I'd suggest Puppy:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

I've tried both Damn Small and Puppy.** Puppy is the winner**!

+1

Absolutely!

Puppy is great. Especially the latest 4.12 version, on newer machines...

There is always the Retro versions for the older stuff.

And of course, v2.14R.

ErnestG

---

### Post by theozzlives on 2008-12-14
ME is like Vista, nothing but problems. I'd suggest either going backward to 98 or up to 2000/XP.

---

### Post by Roger at CCCC on 2008-12-14
Thanks again to everybody who has responded and commented.  Thanks, in particular, for the comments about PuppyLinux.  I looked at it and it looks like a real possibility.  In addition, the user forums appear to be much more active than Damn Small Linux.  

But I’m still uncertain about the easiest and quickest way to install, hopefully as a dual-boot, with Win/ME.  I tried my two CDROM drives again and neither one (one is a CDROM drive and one is a DVD drive, I think) will boot, even though the Windows setup screen lists “ATAPI CDROM” as the first boot option.  I’m not interested in trying to figure out what this problem is if I can boot/install over the network, which does work.  

But I’m still uncertain how to do this.  The PuppyLinux website has a webpage about downloading from the network at:  	 [http://www.puppylinux.com/thin-puppy.htm](http://www.puppylinux.com/thin-puppy.htm) 	but this page has yet to be written and the main link on the page doesn’t work. 

The only page that I could find that actually mentions Win/ME and booting from the network (The Netboot approach) is: 	[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)  (mentioned by mikeyphi ) 
This appears to be exactly what I am looking for in terms of booting, but this page appears to be specific for Ubuntu and so apparently Puppylinux won’t work here.  
In addition, one of the essential weblinks mentioned on this page:
[ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/](ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/)	doesn’t work either.  

So I’m back to square one in finding something that actually works.  Does anyone have any suggestions about how I can proceed, and/or what I should do about the links mentioned above that don’t work?  

Thanks again for all of your comments and suggestions.

---

### Post by handydan918 on 2008-12-14
Here are two suggestions.

Replace the cdrom that you said doesn't work.

Double the amount of RAM (at least).

That should fix you up. 

If finances are too tight, try looking up a local LUG (Linux Users Group) and see if you can find either some advice or some hardware, or both.

---

### Post by ugm6hr on 2008-12-15
> **Roger at CCCC said:**
> I’m not interested in trying to figure out what this problem is if I can boot/install over the network, which does work.  

The only page that I could find that actually mentions Win/ME and booting from the network (The Netboot approach) is: 	[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)  (mentioned by mikeyphi ) 
This appears to be exactly what I am looking for in terms of booting, but this page appears to be specific for Ubuntu and so apparently Puppylinux won’t work here.  
In addition, one of the essential weblinks mentioned on this page:
[ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/](ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/)	doesn’t work either.

I have never done this, but it looks promising: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

The Netboot manual option for W-Me looks reasonable.  As you say the Loadlin download link is miising - but appears to be available here now: [ftp://ftp.sunet.se/pub/Linux/distributions/slackware/slackware-current/kernels/loadlin16c.zip](ftp://ftp.sunet.se/pub/Linux/distributions/slackware/slackware-current/kernels/loadlin16c.zip) (searched from [http://en.wikipedia.org/wiki/Loadlin](http://en.wikipedia.org/wiki/Loadlin)).

With that, and the intitrd.gz and linux files from: [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/) (just change intrepid to hardy if you prefer - the documentation wiki links to outdated gutsy files).

Then follow the advice as given.  Hopefully that should create a netboot installation successfully.  Please note that if loadlin doesn't work as expected on W-Me, it may be because of Me's special case ([http://marc.herbert.free.fr/linux/win2linstall.html#loadlin-or-grub-for-nt](http://marc.herbert.free.fr/linux/win2linstall.html#loadlin-or-grub-for-nt)).

Feel free to add any lightweight environment on top.  My description of LXDE should suit you: [http://ubuntu-lxde.wikidot.com](http://ubuntu-lxde.wikidot.com) (amongst others on the Ubuntu wiki).

Good luck!

---

### Post by mikjp on 2008-12-15
128 Mb is not enough for a usable installation of Ubuntu or Xubuntu. Try some lightweight distribution that is tailored for old systems. See the links in my signature :-)

Greetings,

mikko

---

### Post by theozzlives on 2008-12-15
> **Roger at CCCC said:**
>  the Windows setup screen lists “ATAPI CDROM” as the first boot option.

You want the CMOS setup to say that, not Windows. Also check yor jumpers, both drives might be set to master (or slave)

---

### Post by Roger at CCCC on 2008-12-15
> **mikjp said:**
> 128 Mb is not enough for a usable installation of Ubuntu or Xubuntu. Try some lightweight distribution that is tailored for old systems. See the links in my signature :-)

Greetings,

mikko

Mikko, the link to "Top 10 Lightweight Distros" at the bottom of your signature does not work.  The other ones do, and I got to that page via the other links.  Thanks for the info.

---

### Post by philinux on 2008-12-15
The link in case anyone needs it is
[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

I think the link before had http twice.

---

### Post by AndyCooll on 2008-12-15
> **theozzlives said:**
> You want the CMOS setup to say that, not Windows. Also check yor jumpers, both drives might be set to master (or slave)
Agree with this. This seems to me to be a BIOS settings issue. Have you tried changing the BIOS settings on your pc? These are independent of any OS.

It is likely that the priority on your pc is that when your pc boots up it is saying check the floppy drive first (if you have one) and then go to the HDD, i.e. at the moment no matter what you do it won't look at your CD drive for bootable media. You need to change your BIOS settings to look at the CD-drive before your HDD.

To get to your BIOS settings, _as soon as you switch your pc on_, i.e. before your OS booting up kicks in, you need to press a key (or a combination of keys). It's different on each pc but it is often the DLTE key, F7 or F8. This should bring up your BIOS settings. Look through the various screens for the boot priority, make the changes, and save the settings. The pc will reboot as normal. Now however if you have a bootable CD in the drive it should try to boot up from that first. 

:cool:

---

### Post by snowpine on 2008-12-15
Try a google search for "puppy linux frugal install". All you need to do is copy a few files to the root directory of your C drive. I agree with the other posters who recommended against Ubuntu/Xubuntu on a computer of that era. Good luck!

---

### Post by mikjp on 2008-12-15
> **Roger at CCCC said:**
> Mikko, the link to "Top 10 Lightweight Distros" at the bottom of your signature does not work.  The other ones do, and I got to that page via the other links.  Thanks for the info.

Thanks, got to check it :-)

Corrected :-)

mikko

---

