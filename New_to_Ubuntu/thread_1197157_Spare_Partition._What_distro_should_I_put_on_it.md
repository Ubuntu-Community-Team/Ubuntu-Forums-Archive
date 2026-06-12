---
title: "Spare Partition. What distro should I put on it?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by eeeandrew on 2009-06-25
hi all,

I've got a little bit of free space(26Gb) on my hard drive. At the minute I have ubuntu 8.10 installed with a root partition, home partition and swap. Anyone recommend a good linux distro for me to fill that space with?

I've been using ubuntu for nearly two years now. I'm looking for something that will support games(wine hasn't really worked for me). Also anything that comes with CAD applications would be nice.

Thanks in advance for your advice,
Andrew

---

### Post by fugaki on 2009-06-25
what games?
you might be best to put xp on it if they are small.
keep in mind if you do this though, you will have to do some modifications to grub because the windows bootloader will override grub.

---

### Post by foxmulder881 on 2009-06-25
So you want a tux distro that supports games? Good luck!

Work out what exactly you want and then get back to us.

---

### Post by SunnyRabbiera on 2009-06-25
For games and CAD sadly the only thing that does them right now is windows, perhaps a dual boot should have been your option.

---

### Post by eeeandrew on 2009-06-25
Thanks all,

I had feared I may have to return to windows to get that stuff working. I can live without games but the CAD programs are starting to become necessary for my university course. I might install XP and keep it for gaming and CAD only with no internet connection. Hopefully I can keep the annoying little "quirks" to a minimum that way.

Thanks,
Andrew

---

### Post by Megrimn on 2009-06-25
If you skip the games, I would try Kubuntu.  Definitely a little challenging if you've only used Ubuntu.

---

### Post by fugaki on 2009-06-25
If your computer can support it, try to virtualize them using VirtualBox.
You can add support for 3d rendering with it, and it is really easy to use.

---

### Post by eeeandrew on 2009-06-25
@megrimm

thanks for the suggestion. I have tried kubuntu, installed the desktop package and ran it from the sessions menu.

@fugaki

Virtualbox looks like it could work. I'll need to do some more background reading and then give it a go. Thanks for the suggestion.

I suppose I'm clutching at straws but are there any custom distros/remixes designed around the electrical engineering/CAD fields that anyone is aware of?

Thanks again for all your help,
Andrew

---

### Post by Nautilus112 on 2009-06-25
OpenSUSE

---

### Post by Locutus_of_Borg on 2009-06-25
Slackware Linux, Gentoo Linux, or Linux From Scratch

Screw university courses!! :P  you can always use a VM for that too

i recommend Slackware since it is great.

gentoo is educational to install, but aggravating to maintain using

and linux from scratch is even more educational than gentoo

by educational, i mean tedious, time consuming, harrowing, seemingly obtuse and purposefully maligned, and lots of typing

---

### Post by Zzl1xndd on 2009-06-25
I can't speak for the CAD programs, but as for games I have had pretty good luck with Crossover and Cedega.

---

### Post by foxmulder881 on 2009-06-25
Quick question for the OP. If you're already running Ubuntu on the system, why do you want to install another distro of linux?

---

### Post by fugaki on 2009-06-25
lol aren't gentoo and linux from scratch distros with text mode only installers?

---

### Post by Locutus_of_Borg on 2009-06-25
as far as i recall, gentoo doesn't really have a working installer...last i tried to use it it was broken at least.

essentially you install gentoo by extracting the very basic gnu/linux components into an empty partition, then compiling every single additional component on top of that

linux from scratch is very similar, but you do not get the tools that gentoo provides in its base system (like a package manager and a compiler, and a linking tool, etc)

slackware has a true text installer, but do you really need images of stuff to help you install?  the principle is the same, just instead of sliding a bar to adjust the size of the install, you enter the number...for the most part, its really not as daunting as it might sound

plus you get the benefit of using the "best" distro of linux available (in my opinion at least)

---

### Post by eeeandrew on 2009-06-25
@foxmulder881

I'm enjoying using ubuntu but I'm starting to find there are a few drawbacks. I want to find other linux versions that beat these drawbacks. I'm also keen to learn more about computers in general. Plus all the usual reasons of cost, security etc compared to windows or mac.

Thanks,
Andrew

---

### Post by foxmulder881 on 2009-06-25
> **eeeandrew said:**
> @foxmulder881

I'm enjoying using ubuntu but I'm starting to find there are a few drawbacks. I want to find other linux versions that beat these drawbacks. I'm also keen to learn more about computers in general. Plus all the usual reasons of cost, security etc compared to windows or mac.

Thanks,
Andrew

Ok, fair enough. I've been there and done that. I've tried a lot of distros in my time and I always end up coming back to Ubuntu because it's only distro that seems to always 'just work'. But since I'm not a fan of 9.04, I'm currently running Fedora 11. Awesome version. Installs in less than 10 minutes, plymouth boots in just 20 seconds. Nothing to complain about here.

---

### Post by Zzl1xndd on 2009-06-25
> **eeeandrew said:**
> @foxmulder881

I'm enjoying using ubuntu but I'm starting to find there are a few drawbacks. I want to find other linux versions that beat these drawbacks. I'm also keen to learn more about computers in general. Plus all the usual reasons of cost, security etc compared to windows or mac.

Thanks,
Andrew

I would Probably go Suse or Fedora if this is the case.

Also Gentoo if you really wanna have some fun.

---

### Post by snowpine on 2009-06-25
Try a bunch (using Live CDs or virtualbox) before deciding. Personally I think you can learn a lot about Linux by trying Arch.

---

