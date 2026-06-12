---
title: "Getting 2nd thoughts about a 2nd Linux"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-13
I'm thinking of partitioning the computer for a second Linux distro, I'm wondering what's the chance of the two somehow coming into conflict with each other.  My main worry is Grub.   I can see it is alredy in my Ubuntu / partition.  How is that going to work while there is a second distro to be booted?

---

### Post by avtolle on 2009-03-13
In my case, adding openSUSE 11.1 to a pre-existing 8.10/Linux Mint 6/Vista booting machine resulted in the openSUSE Grub being installed, which picked up all pre-existing OS with no difficulty.

---

### Post by Xero Xenith on 2009-03-13
The same will happen if you install any maintstream distro, not just openSUSE. But that will only update its own GRUB for its own kernel updates; if Ubuntu gets a kernel update, it won't be added.

---

### Post by avtolle on 2009-03-13
> **Xero Xenith said:**
> The same will happen if you install any maintstream distro, not just openSUSE. But that will only update its own GRUB for its own kernel updates; if Ubuntu gets a kernel update, it won't be added.
Good point, which I neglected to post. Thanks.

---

### Post by phil0stine on 2009-03-13
I have fedora and Ubuntu installed on my computer (along with windows). 
I told myself that when I got Ubuntu up and running I would kill fedora since I was having problems with it. 
I have had absolutely no reason to so, howver, and it still lives in its little corner of my hard drive. The grub manager didn't get screwy either, so I would say go for it.

---

### Post by Elfy on 2009-03-13
I've got 4 different ubuntu variants on variosu drives and partitions - I chainload so each has it's own menu list and grub gets updated

No problems here

---

### Post by andrew.46 on 2009-03-13
Hi,

Another option to consider is the use of a package such as VirtualBox. I think realistically most people have a *primary* Linux distro and others they *dabble* in so virtualisation is great solution for this.

I attach the obligatory screenshot :-).

Andrew

---

### Post by ClaytonOT on 2009-03-13
> **avtolle said:**
> In my case, adding openSUSE 11.1 to a pre-existing 8.10/Linux Mint 6/Vista booting machine resulted in the openSUSE Grub being installed, which picked up all pre-existing OS with no difficulty.

I wish it went that smooth with me :(

Installing OpenSUSE 11.1 beside XP (same Device) worked for those two OS's, but it took me a full day of troubleshooting to try to get Ubuntu running which it never did, so I ended up removing OpenSUSE.

Maybe my experience is what made it go so wrong, but everything looked right.

---

### Post by DigiTan on 2009-03-13
Well that's a coinscidence.  OpenSUSE 11.1 was the exact 2nd distro I'm thinking of getting.  So it sounds like which ever grub was the most-recent will dominate the boot process and both available...  Unless I get a kernel update?

---

### Post by 73ckn797 on 2009-03-13
> **andrew.46 said:**
> Hi,

Another option to consider is the use of a package such as VirtualBox. I think realistically most people have a *primary* Linux distro and others they *dabble* in so virtualisation is great solution for this.

I attach the obligatory screenshot :-).

Andrew

Agree here.

I, personally, have found Gnome/KDE is Gnome/KDE in whatever distro I have looked into. I have decided to stick with Ubuntu since it "just works" with my hardware and likewise on two other machines I have. Why duplicate when there is not much difference and Ubuntu works for my needs? Just my own experience and preferences, though.

---

### Post by DigiTan on 2009-03-22
On the off-chance I have to ditch this 2nd distro, what happens to grub?  Something tells me it won't be pretty when I reboot.  If a get a grub error, can I just reinstall this original Ubuntu version I'm using today?

---

### Post by 73ckn797 on 2009-03-23
> **DigiTan said:**
> On the off-chance I have to ditch this 2nd distro, what happens to grub?  Something tells me it won't be pretty when I reboot.  If a get a grub error, can I just reinstall this original Ubuntu version I'm using today?


I usually first go to terminal and edit out the 2nd distro entries then go to Gparted and delete the partition for the 2nd distro. Never has failed me yet.

---

### Post by DigiTan on 2009-03-24
Okay, openSUSE is running and it definately installed its own bootloader.  I think it's called Stage2 (they make it sound like a disease or something).  I haven't tested whether Ubuntu can overwrite this back to Grub, but I'd imagine it could.

---

### Post by raymondh on 2009-03-24
> **73ckn797 said:**
> Agree here.

I, personally, have found Gnome/KDE is Gnome/KDE in whatever distro I have looked into. I have decided to stick with Ubuntu since it "just works" with my hardware and likewise on two other machines I have. Why duplicate when there is not much difference and Ubuntu works for my needs? Just my own experience and preferences, though.

Ditto here.  Ubuntu just works for me.  And to satisfy my curiosity with other distros/OS', virtualization works just fine.

---

