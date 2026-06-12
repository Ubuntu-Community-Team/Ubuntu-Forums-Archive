---
title: "Ubuntu 9.04 LiveCD won't start up?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by ChrisMc73 on 2009-08-05
I have a 9.04 LiveCD that I downloaded and burned the iso, I know it works cause I installed fine on a PC at work with it.

Now I've come home to my Windows 7 machine that has a partition ready to install Ubuntu on, yet when I try to load this DVD with the iso of Ubuntu and even a Fedora 10 DVD, upon a restart with the BIOS ready to launch from CD/DVD drive first, it reads the DVD but then continues on into Windows 7. I can't get the LiveCD to start up? Any clues to why? Its odd that these both work on the work PC but here at home they aren't even booting into anything?

---

### Post by halitech on 2009-08-05
you say you have burned dvds with the ISOs on them, dumb question but do you have a dvd rom or dvd burner in your computer?

---

### Post by pastalavista on 2009-08-05
Did you install grub? Did you try pressing escape or some other keys to check the bootloader? Windows 7 has a bootloader... is Ubuntu or any "other" OS listed in the Windows bootloader?

---

### Post by ChrisMc73 on 2009-08-05
> **halitech said:**
> you say you have burned dvds with the ISOs on them, dumb question but do you have a dvd rom or dvd burner in your computer?

Yes, I have two DVD RW's in this PC. Its a Dell Precision 650 Workstation.

---

### Post by ChrisMc73 on 2009-08-05
> **pastalavista said:**
> Did you install grub? Did you try pressing escape or some other keys to check the bootloader? Windows 7 has a bootloader... is Ubuntu or any "other" OS listed in the Windows bootloader?

Nope, I didn't install Grub, not familiar with it, just doing what I did at work. I had Windows 7 installed where I setup two partitions on the disk, and installed W7 on one. Then once done with that I inserted this Ubuntu 9.04 disc and it loaded right into an install menu and allowed me to choose install "along side" the NTFS bla bla bla, I made the new partition FAT32 so I could see files on both and it works great, at work...

Not here at home, I can't get the disc to come up at all except once inside Windows 7 and then I have the options to install "inside" windows which I don't want, or reboot and allow it to give me the options I want "along side" but it never goes there.

Do you think the Ubuntu CD is having issues with the Windows 7 bootloader? I think at work I used GParted to create the partitions and here at home I used the Windows 7 install. But I left the 2nd partition clean so that I could use it with my Ubuntu install disc.

---

### Post by pastalavista on 2009-08-05
Wiil your computer boot from any other bootable disk?

---

### Post by ChrisMc73 on 2009-08-05
> **pastalavista said:**
> Wiil your computer boot from any other bootable disk?

It boots GParted and it boots the Windows 7 install discs, so yeah...it does.

---

### Post by ChrisMc73 on 2009-08-05
I hate to blow away to two partitions and redo them in GParted, but I can try that? I was just following what worked before at work and it seems to not be the same here.
Is there a way around the W7 bootloader with a CD program?

---

### Post by pastalavista on 2009-08-05
Well I'm stumped then.. sorry. Try cleaning the disk maybe.

---

### Post by halitech on 2009-08-05
> **ChrisMc73 said:**
> Yes, I have two DVD RW's in this PC. Its a Dell Precision 650 Workstation.

ok, just wanted to make sure it wasn't a media mismatch causing the issue

> **ChrisMc73 said:**
> It boots GParted and it boots the Windows 7 install discs, so yeah...it does. 

so we know the boot order is set right

> **ChrisMc73 said:**
> Not here at home, I can't get the disc to come up at all except once inside Windows 7 and then I have the options to install "inside" windows which I don't want, or reboot and allow it to give me the options I want "along side" but it never goes there.

Do you think the Ubuntu CD is having issues with the Windows 7 bootloader? I think at work I used GParted to create the partitions and here at home I used the Windows 7 install. But I left the 2nd partition clean so that I could use it with my Ubuntu install disc.

the cd booting should happen before the windows boot loader even comes into effect so it makes no sense that you can't boot from it on this machine. It seems to work fine once you get into windows so that is a good indication that the cd was burned properly.

I have no idea what to say as it makes no sense at all (just talking out loud here to try and make sense of things)

---

### Post by ChrisMc73 on 2009-08-05
> **pastalavista said:**
> Well I'm stumped then.. sorry. Try cleaning the disk maybe.

Well now I just burned the newest stable GParted on my laptop using an ISO recorder and its not loading up either, so maybe its the images...odd though cause they worked on the work PCs, well not this new Gparted one...but the others did.

---

### Post by razorboy5 on 2009-08-05
yea i was gonna say check boot order but it seems to be in order

and i didn't think bootable CDs needed GRUB or anything like that

perhaps disk got damaged when moving from work to home

---

### Post by pastalavista on 2009-08-05
> **razorboy5 said:**
> yea i was gonna say check boot order but it seems to be in order

and i didn't think bootable CDs needed GRUB or anything like that

perhaps disk got damaged when moving from work to home

sorry again, what I said before about grub was off the mark. I was thinking something else. It's been a long time since I dual-booted.

good-luck with your Ubuntu. damaged disk sounds about right.

---

### Post by ChrisMc73 on 2009-08-05
If they were damaged then I couldn't see the contents of them in Windows and I can...right?

---

### Post by ChrisMc73 on 2009-08-06
When I load up the Ubuntu DVD from inside W7, I get 3 options, should I do the option that offers help to boot from CD? It installs some other options in the boot menu, so this 3rd option says, should I try that?

Update: I just put the UBUNTU DVD in my laptop, rebooted and it went into the Ubuntu install, so I know it works.
For the life of me I can't figure out whats wrong with this other workstation I want to load it up on though, its stumped me as well.

When inside W7 the setup comes up and gives me the install options of "inside" windows etc...so the disc is good. Its just not loading from the CDROM off a reboot.

---

