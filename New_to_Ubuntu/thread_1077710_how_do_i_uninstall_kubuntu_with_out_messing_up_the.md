---
title: "how do i uninstall kubuntu with out messing up the grub install?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-02-22
I am tribooted currently (vista business, ubuntu, and kubuntu)  my problem is when i try and uninstall kubuntu it crashes the grub install.  I have to much crap on my notebook and i dont have a way to back the other two installs as my externals are completely full.  All i want to do is take kubuntu out and then turn that in to a swap partition so that i can share files between windows and ubuntu.  i need help

---

### Post by taurus on 2009-02-22
I assume you installed Kubuntu last.  One way is to boot into Ubuntu and install GRUB to MBR, overwriting the version from Kubuntu so when you remove the root filesystem of Kubuntu, you don't have to worry about GRUB looking at the wrong place for /boot/grub/menu.lst.

---

### Post by trinidadflores on 2009-02-22
> **taurus said:**
> I assume you installed Kubuntu last.  One way is to boot into Ubuntu and install GRUB to MBR, overwriting the version from Kubuntu so when you remove the root filesystem of Kubuntu, you don't have to worry about GRUB looking at the wrong place for /boot/grub/menu.lst.

thank you but how do i install it to the MBR?  i know some about using ubuntu but have not grub any to messing around with the grub and moving it.

---

### Post by taurus on 2009-02-22
If all the entries in /boot/grub/menu.lst (from Ubuntu) is right, you could install GRUB to MBR with

Applications -> Accessories -> Terminal
```
sudo grub-install /dev/sda
```

---

### Post by trinidadflores on 2009-02-22
> **taurus said:**
> If all the entries in /boot/grub/menu.lst (from Ubuntu) is right, you could install GRUB to MBR with

Applications -> Accessories -> Terminal
```
sudo grub-install /dev/sda
```

will i have to move the grub installer back to the origanal location after?

---

### Post by trinidadflores on 2009-02-22
I started gpart up and noticed the partition that has my ubuntu install is actually 7  as shown on in the following screenshot.  will this change everything?

---

### Post by trinidadflores on 2009-02-22
does anyone know if i was to use my install disk for ubuntu and delete the kubuntu partition if that would mess up my grub.  I did install it to the mbr as one mentioned this evening.

---

### Post by trinidadflores on 2009-02-23
Does anyone know how to do this? I dont really want to have to reinstall everything on my computer.  

:popcorn: 
trinidad

---

### Post by trinidadflores on 2009-02-23
I need to uninstall Kubuntu but in dont want to mess up the grub install?  As i mentioned my computer is tri-booted (1st) is windows Vista business (2) is kubuntu and (3) is Ubuntu which i want to keep as well is vista.  My question is how do i uninstall kubuntu without screwing up the Grub install.  Does anyone know how to do this? I dont really want to have to reinstall everything on my computer.  

:popcorn: 
trinidad

---

### Post by trinidadflores on 2009-02-23
i'm tribooted currently (vista business, ubuntu, and kubuntu) my problem is when i try and uninstall kubuntu it crashes the grub install. I have to much crap on my notebook and i dont have a way to back the other two installs as my externals are completely full. All i want to do is take kubuntu out and then turn that in to a swap partition so that i can share files between windows and ubuntu. 

Kubuntu was actually installed first.  I have installed the grub into to the MBR to make kubuntu look in the wrong location for the grub.  It is now at  /boot/grub/menu.lst.
My questions are the following:
1.does anyone know if i was to use my install disk for ubuntu and delete the kubuntu partition if that would mess up my grub. I did install it to the mbr as one mentioned this evening
2.Because the order that the os's were installed Ubuntu (is the last one on th drive) Kubuntu being installed.
If i was to go and repartition the drive when i use the live cd will i be fine with the grub install and not get corrupted because of it being installed in the MBR?

---

### Post by Dougie187 on 2009-02-23
You will need to use your ubuntu cd to remove your kubuntu partition. It will probably mess up grub however because your grub boot info is stored on your kubuntu partition. I think you should be able to just reinstall grub and have it point to your ubuntu partition, but I am no expert with this, so you might want to read up on how to reinstall grub.

Keep in mind too this is under the assumption that what you are trying to do is the following:

Remove your Kubuntu partition
Absorb the space from the kubuntu partition back into ubuntu

Now if you are going to reinstall ubuntu over all of the new free space (in the event you don't have to save any data from either partition) you could just reinstall ubuntu and have it delete and absorb the kubuntu partition, and then it would reinstall grub for you.

This might help with the first scenario:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by trinidadflores on 2009-02-23
taurus
Run, little guy, run...
 
taurus's Avatar
 
I did reinstall the grub to the following location in the mbr.  I was told that by doing that it should confuse kubuntu and make it so that kubuntu could not find the grub.

Applications -> Accessories -> Terminal
Code:

sudo grub-install /dev/sda

---

### Post by LowSky on 2009-02-23
So wait you want to keep ubuntu, just get the Ubuntu liveCD, then go to gparted (Partion editor under System>admin), delete the kubuntu partiton, Then run the install process. Choose manual partition, then pick where ubuntu is installed to currently, relabel the / and swap and any other partition as needed. JUST DO NOT FORMAT!!! Let it run it processes, and it should reinstall grub for Ubuntu and Vista. Boot into ubuntu and run ```
sudo apt-get update && sudo apt-get upgrade
``` now all your stuff should be fine.

---

### Post by bodhi.zazen on 2009-02-23
Thread merged ;)

---

### Post by sandyd on 2009-02-23
.

---

