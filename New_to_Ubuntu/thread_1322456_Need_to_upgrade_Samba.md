---
title: "Need to upgrade Samba"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-10
Hi everyone,

Whilst trying to share files between my desktop PC (9.04) and my laptop (9.10), I need to upgrade the version of samba on my PC from 2.3 to 3. 
EDIT: I need to update from 3.3.2 to 3.4

Note my PC is not connected to the internet. 

Is there a single deb I can install Samba from, or do I need to manually transfer over smbclient, samba_2, samba-common, and all their dependencies one at a time?

Thanks! If I can get an answer here it would save me a lot of time :popcorn:

---

### Post by Paqman on 2009-11-11
Assuming you're patched up to date, your 9.04 computer has Samba 3.3.2 and your 9.10 machine has 3.4.

The Ubuntu package names seem to start with 2:, which is probably where you're getting confused.

---

### Post by asuastrophysics on 2009-11-11
The reason I have to update it is because I shared this folder from my updated laptop:

/var/cache/apt/archives
This folder contains all the .DEB files stored on the system after updates.

and I installed this file which broke my samba on the desktop computer:
system-config-samba_1.2.63-0ubuntu4_all.deb

This file wasn't included in the earlier version (for good reason, bc it doesn't work with the earlier release)

so the only real way to "fix" the break I made would be to do a full update on the Samba service. 

So I guess I'm asking if there is an easy way to update it? (E.G. a DEB package containing all dependencies)

---

### Post by Paqman on 2009-11-11
Have you tried uninstalling system-config-samba? Then if that doesn't work, try reinstalling or removing then reinstalling Samba.

---

### Post by asuastrophysics on 2009-11-11
I kinda already (stupidly) started the Samba update on that computer. :rolleyes:

This means the older packages associated with Samba have already been removed in preparation for newer ones. 

Now I've got to download all the newer files for the samba package. I just wish they were all included in one DEB. :lolflag:

---

### Post by Paqman on 2009-11-11
> **asuastrophysics said:**
> I just wish they were all included in one DEB. :lolflag:

They are: [samba]("http://packages.ubuntu.com/jaunty/samba"). That's a meta-package for the Samba server. If you're just connecting to a remote share you'll only need [smbfs]("http://packages.ubuntu.com/jaunty/smbfs").

---

### Post by asuastrophysics on 2009-11-11
> **Paqman said:**
> They are: [samba]("http://packages.ubuntu.com/jaunty/samba"). That's a meta-package for the Samba server. If you're just connecting to a remote share you'll only need [smbfs]("http://packages.ubuntu.com/jaunty/smbfs").

:popcorn: wow hey i googled around for that but i couldn't find anything

Thanks! 

Now if I could get my iPod to connect and not just charge, i'll put it on my ipod and transfer it over to the desktop

---

### Post by Paqman on 2009-11-11
Browsing or searching in Synaptic gives you a full picture of everything that's in the repos. They're also available on this website: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Generally all major systems like this will have one top-level meta-package that you can install, and which will pull in all the required dependencies. Linux package management rocks like that.

What sort of iPod have you got? You should be able to get most of them to connect to any of the main media players (Rythmbox, Banshee, Amarok, etc...)

---

### Post by asuastrophysics on 2009-11-11
> **Paqman said:**
> Linux package management rocks like that.

That it does! 

It's an iPod video from ~2005-2006. It seems that if I want it to connect to Ubuntu, I have to restart my machine with the iPod already attached. Otherwise, when I plug it in, it just shows a charging icon. 

Output of dmesg:
```
[96581.860088] usb 6-2: new full speed USB device using uhci_hcd and address 26
[96581.992631] usb 6-2: device descriptor read/64, error -71
[96582.230205] usb 6-2: device descriptor read/64, error -71
[96582.460094] usb 6-2: new full speed USB device using uhci_hcd and address 27
[96582.599555] usb 6-2: device descriptor read/64, error -71

```
Note how it says address 26. It started at 1, and the longer it's connected, the more addresses it tries without success. 

I tried booting the iPod in disk mode, but it just shows a check mark saying "ok to disconnect"

hmm...

---

### Post by Paqman on 2009-11-11
What music player do you have installed? Does it take control of the iPod when you start up the player? Older iPods like that should just work, AFAIK.

---

### Post by asuastrophysics on 2009-11-11
Solved!!!!

(I use songbird or banshee. BTW)

It was a broken iPod USB cable. That's what was causing that bizarre message. Who knew?

anyway, I copied over that DEB but I get:

Error: Dependency is not satisfiable: samba-common 3.2

When I try to install samba-common 3.2 I get:

Error: Breaks existing package 'libpam-smbpass' 

so it looks like this may yet take a little while ;)

---

