---
title: "ltsp- need non-pae kernel"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by Fenderian_Mayhew on 2013-09-14
How would one tell LTSP to use/make a non PAE kernel? Im using older i386's for terminals and the kernel is the only remaining holdup.

---

### Post by Fenderian_Mayhew on 2013-09-14
I found that 10.04 (lucid) is non-PAE. so I ran...
```
sudo ltsp-build-client --dist lucid --arch i386
```

---

### Post by mörgæs on 2013-09-14
10.04 is out of support and hence a security breach. 

Here's a guide to solving the [PAE]("https://help.ubuntu.com/community/PAE") problem in a recent Buntu release.

---

### Post by sudodus on 2013-09-15
> **Fenderian_Mayhew said:**
> How would one tell LTSP to use/make a non PAE kernel? Im using older i386's for terminals and the kernel is the only remaining holdup.

What kind of processors are there in those old i386 computers?

- older than Pentium II?  - you need a non-pae kernel
- Celeron M or Pentium M? - you can use fake-pae and run pae kernels
- other processors (including Pentium II) - you can run pae kernels

You can also consider the tips from this link [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by Fenderian_Mayhew on 2013-09-15
> **sudodus said:**
>  - Celeron M or Pentium M? - you can use fake-pae and run pae kernels   These are M275's w/Pentium M's (400mhzFSB) and... whats this about "fake PAE?" All these sound like doable options including skiping Ubuntu all together (TC, Puppy, Debian etc.)   The knut of the problem is i dont know how to safely anipulate the ltsp root dir's and images to use an alternate kernel or image.   I did attempt to use --dist wheezy or --dist potato but apt attempted to call the files from the ubuntu archives.

---

### Post by Fenderian_Mayhew on 2013-09-15
I am attempting to setup a ltsp with the "ltsp-build-client" tool so my options are slim.  I cant find any way to define Xubuntu or Lubuntu as client. 
 using --dist and --mirrors options for a debian client (with approperate URL's) yeilds falures due to certen packages/folders not being available

---

### Post by sudodus on 2013-09-15
> **Fenderian_Mayhew said:**
> These are M275's w/Pentium M's (400mhzFSB) and... whats this about "fake PAE?" All these sound like doable options including skiping Ubuntu all together (TC, Puppy, Debian etc.)   The knut of the problem is i dont know how to safely anipulate the ltsp root dir's and images to use an alternate kernel or image.   I did attempt to use --dist wheezy or --dist potato but apt attempted to call the files from the ubuntu archives.

I have an IBM Thinkpad T42 with such a Pentium M CPU and a friend has a Thinkpad T41. I know that it works well with fake-PAE, because I have used it for a long time now. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by sudodus on 2013-09-15
> **Fenderian_Mayhew said:**
> I am attempting to setup a ltsp with the "ltsp-build-client" tool so my options are slim.  I cant find any way to define Xubuntu or Lubuntu as client. 
 using --dist and --mirrors options for a debian client (with approperate URL's) yeilds falures due to certen packages/folders not being available

Your method will probably give a good result but it is more complicated.

Fake-PAE gives you access to the new versions of Ubuntu flavours like Lubuntu and Xubuntu and also [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

If you are happy with a single boot system without Windows, you can use the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") to install your Ubuntu based operating system in an easy way.

---

### Post by Fenderian_Mayhew on 2013-09-15
I believe there's a misunderstanding on whats being attempted. I am trying to setup a PXE booted LTSP server on a 64bit machine w/32bit non pae systems as the thin clients.
I have been able to get the server setup but the image/kernel used contains PAE.
 its not a question of using x/l/edu/buntu beacuse ltsp-build-client won't allow any other system but ubuntu 12.04 and up to be installed in the ltsp root DIR.
every attempt at aquiring/installing/replacing ubuntu 12.04 as the LTSP system with an approperate system has failed 
10.04 resulted in a failed image creation
debian (with approperate mirror) failed due to locales-gen not existing.

---

### Post by sudodus on 2013-09-15
It is not only a misunderstanding. It seems I don't understand at all, how systems with thin clients work ;-)

Will you net-boot these thin clients, or have they got their own operating systems?

I think that there is an Ubuntu 12.04 ***mini-iso*** with non-pae kernel. It might help to start from there.

---

### Post by Fenderian_Mayhew on 2013-09-15
the mini-iso does indead have non pae kernels but without a way to set the iso as the ltsp-boot enviroment the "good idea" dies there

---

