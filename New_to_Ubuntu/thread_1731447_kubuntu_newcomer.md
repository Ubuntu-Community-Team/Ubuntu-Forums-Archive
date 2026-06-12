---
title: "kubuntu newcomer"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by joymarie on 2011-04-17
is it just OK to post kubuntu-related issues here?

---

### Post by Paqman on 2011-04-17
Absolutely. Kubuntu is just normal Ubuntu wearing different trousers.

---

### Post by oldos2er on 2011-04-17
There's also [http://www.kubuntuforums.net/](http://www.kubuntuforums.net/) but it gets much less traffic than these forums.

---

### Post by kaldor on 2011-04-17
Unless it's KDE specific, everything that applies to Ubuntu will also apply to Kubuntu.

---

### Post by mastablasta on 2011-04-17
> **kaldor said:**
> Unless it's KDE specific, everything that applies to Ubuntu will also apply to Kubuntu.


not really but OK. Kubuntu has quite a few things done differently. However, the maschine under the hood is the same.

---

### Post by joymarie on 2011-04-17
thanks..i am currently downloading kubuntu 9.10..i'll post questions here if i ever encounter problem during the installation..:)

---

### Post by oldos2er on 2011-04-18
9.10 is about to reach its end-of-life, meaning it won't be supported any longer. You might want to try 10.04 or 10.10; 10.10 with KDE 4.6.2 has worked very well for me.

---

### Post by joymarie on 2011-04-19
> **oldos2er said:**
> 9.10 is about to reach its end-of-life, meaning it won't be supported any longer. You might want to try 10.04 or 10.10; 10.10 with KDE 4.6.2 has worked very well for me.
 
 
oh. is that bad? i was just done downloading the .iso file and i am planning to install it this friday. 
 
btw, i seem to be having some difficulty understanding the process of installing ubuntu/kubuntu especially when it comes to the point when i have to partition the hard disk. i have 120GG HDD, 120 of it is for my windows seven, and i am planning to use the rest for the Kubuntu. But reading all those intructions, i am now lost. 
 
what do you mean by, "unmount/mount the file?" and "no root file is found?" and the likes? it is much different from installing windows. 
 
i need some enlightment on this. thanks. :P

---

### Post by Old *ix Geek on 2011-04-19
> **joymarie said:**
> oh. is that bad? i was just done downloading the .iso file and i am planning to install it this friday. It's not bad, per se, but it just makes more sense to use the most current stable version.
> btw, i seem to be having some difficulty understanding the process of installing ubuntu/kubuntu especially when it comes to the point when i have to partition the hard disk. i have 120GG HDD, 120 of it is for my windows seven, and i am planning to use the rest for the Kubuntu.Um...if you have 120GB and it's all going to windows...where's the "rest" of it that will be for Kubuntu? :confused:
> But reading all those intructions, i am now lost. 
 
what do you mean by, "unmount/mount the file?" and "no root file is found?" and the likes? it is much different from installing windows. 
 
i need some enlightment on this. thanks. :PNone of that should be an issue. The installation should be extremely straightforward--once you figure out how you're going to partition the drive, that is. If your entire disk is indeed being used by windows, you'll have to do something about that.

---

### Post by SeijiSensei on 2011-04-19
I'd recommend that you first try running off the CD image to get a sense of what Kubuntu looks like and whether it works for you.  It will be slow when loading things because it's constrained by the speed of the CD drive, but once everything loads it should be fine.

I've not tried booting from a USB stick instead of a CD; perhaps someone here knows whether that has better performance?  You can [create the USB boot image from Windows]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by joymarie on 2011-04-19
> **Old *ix Geek said:**
> It's not bad, per se, but it just makes more sense to use the most current stable version.
Um...if you have 120GB and it's all going to windows...where's the "rest" of it that will be for Kubuntu? :confused:
None of that should be an issue. The installation should be extremely straightforward--once you figure out how you're going to partition the drive, that is. If your entire disk is indeed being used by windows, you'll have to do something about that.
 
opppss..sorry. 100GB will be for windows7 and the 20GB will be for the kubuntu. I partitioned the drive using Gparted. And from what i saw from someone's instructions, one has to format the drive for the kubuntu as ext2, 3 or 4? then the booting option shall be "/". 
what does it mean?

---

### Post by K_45 on 2011-04-19
You'll need to partition it first, so pick ext4. You can then manually partition with Kubuntu's installer or let Kubuntu make the decision for you. / is root, the starting point of the Linux filesystem.

---

### Post by rosencrantz on 2011-04-19
> **SeijiSensei said:**
> I'd recommend that you first try running off the CD image to get a sense of what Kubuntu looks like and whether it works for you.  It will be slow when loading things because it's constrained by the speed of the CD drive, but once everything loads it should be fine.

I've not tried booting from a USB stick instead of a CD; perhaps someone here knows whether that has better performance?  You can [create the USB boot image from Windows]("https://help.ubuntu.com/community/Installation/FromUSBStick").
Running from USB is probably faster, as you don't have the drive spinning up and down all the time. Also, you can save/change stuff on the drive and you don't waste a CD, so I'd definitely recommend it. Does your computer have a boot from USB option?

---

### Post by joymarie on 2011-04-21
> **K_45 said:**
> You'll need to partition it first, so pick ext4. You can then manually partition with Kubuntu's installer or let Kubuntu make the decision for you. / is root, the starting point of the Linux filesystem.
 
 
,thanks. i'll keep that in mind. i am about to have some time off from work so i'd be able to make a fresh install of kubuntu. i'll post more questions here later. thanks guys.

---

### Post by joymarie on 2011-04-23
,guys..i really need help. i installed kubuntu 10.10 and the process was fine. Until it restarts and ask for my login ID and asking for a command. It is all black screen. I cant get past that.
I really cant get to the desktop where i am supposed to go after I entered my username and password. What am i supposed to do?

---

### Post by frup on 2011-04-23
Well X or KDE hasn't set up properly. You didn't install server edition or anything by mistake did you?

Log in to that terminal screen and at the command line try typing

startX

it may get the gui going if it is there.

---

### Post by joymarie on 2011-04-23
> **frup said:**
> Well X or KDE hasn't set up properly. You didn't install server edition or anything by mistake did you?

Log in to that terminal screen and at the command line try typing

startX

it may get the gui going if it is there.

no. i downloaded the 32-bit for my computer, desktop edition. and it's the CD only. does it make any difference? and, what do you mean by X and KDE, by the way?

---

### Post by frup on 2011-04-23
The gui runs on something called an Xserver. To start this in the command line you are getting you can type the command "startX"

KDE is the gui or desktop environment of Kubuntu. 

If you're having problems straight away with the gui after install, maybe try doing the install again and just see if that fixes it.

If that all doesn't work you might need to give us information about your computers graphics card etc.

---

### Post by joymarie on 2011-04-23
> **frup said:**
> The gui runs on something called an Xserver. To start this in the command line you are getting you can type the command "startX"

KDE is the gui or desktop environment of Kubuntu. 

If you're having problems straight away with the gui after install, maybe try doing the install again and just see if that fixes it.

If that all doesn't work you might need to give us information about your computers graphics card etc.

i have tried to enter the command startx and it only shows blank screen.
my graphic says:

00:02 0 VGA Compatible Controller: Intel Corporation Core Processor Integrated 
Graphics Controller 
(rev 18)

---

