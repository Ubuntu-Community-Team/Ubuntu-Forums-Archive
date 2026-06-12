---
title: "multiple os on one machine"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by PCx86 on 2009-12-07
hi, i would like to load all my os on one machine.{all win something}. i now have ubuntu 9.04. i would prefer to have ubuntu on its own drive. when i tried to install from live cd everything seemed normal but on reboot no choice, no ubuntu, only xp. anyways my question would be: does ubuntu care which drive to install to? does grub come on the cd? i`ll be installing on a blank machine with five drives{three ide+2 sata} i`ll need to be able to swap drives with a boot manager{dos/win3.11+win 98 don`t like being on the same drive} i know jack about jack and while i am used to winX , a little advice before i start could save me lots of frustration. i had a pc with dos/win3.11/win98/win98se/winxp on it and i enjoyed playing with the different oses without digging out an old pc. i don`t want to use vm`s because half the fun is getting the software to control the hardware properly. i am simply an end user who likes to play with computers. thanks {i really know next to nothing about ubuntu but hope to learn a bit in the next year or so}

---

### Post by theozzlives on 2009-12-07
Why would you have a reason for DOS/Win 3.11? Win 98, Win98SE aren't different enough to do multiple boot. Actually unless you have a specific reason, or _old_ software to run, I see anything less than Win 2000 counterproductive. At least you're only going for one version of Ubuntu.

---

### Post by chillyomi on 2009-12-07
Not worth it dude the ideal thing would be to dual boot Windows and some other alternate OS like fedora, ubuntu etc

---

### Post by The_Pirate_King on 2009-12-07
It's not to troublesome to install Grub if you are having difficulties.  
Following these instructions should help you: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You will not need a separate CD from Grub as long as you have an Ubuntu live CD.

---

### Post by ranch hand on 2009-12-07
> **The_Pirate_King said:**
> It's not to troublesome to install Grub if you are having difficulties.  
Following these instructions should help you: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You will not need a separate CD from Grub as long as you have an Ubuntu live CD.
If you are using grub2 you need t ofollow these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Multi-booting is a lot of fun.  I would not have all that MS crap on my box.  So what.  It is your box.  Do what you want.  Take your time.

The only problem I can see is that some older MS OSs I do not think will work well on a Logical partition and you can only have 4 of them.  You could make 3 primaries and the rest of the drive as one extended.  Put your Swap and any MS OS that will work on them on there in logical partitions.

You will have to check with some one other than me about what MS OS' will go no Logical partitions.  Won't have any of them on here so I just do not know.

---

### Post by The_Pirate_King on 2009-12-07
> **ranch hand said:**
> If you are using grub2 you need t ofollow these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Multi-booting is a lot of fun.  I would not have all that MS crap on my box.  So what.  It is your box.  Do what you want.  Take your time.

The only problem I can see is that some older MS OSs I do not think will work well on a Logical partition and you can only have 4 of them.  You could make 3 primaries and the rest of the drive as one extended.  Put your Swap and any MS OS that will work on them on there in logical partitions.

You will have to check with some one other than me about what MS OS' will go no Logical partitions.  Won't have any of them on here so I just do not know.
I accidentally overwrote my boot with swap and had to reinstall, lol.  Then I just created a separate free partition for swap, works great.  Until my harddrive failed but that's a different story.

---

### Post by JBAlaska on 2009-12-07
You should use Arch......J/k honestly If I here one more "you should use Arch" comment I'm gonna sh...erm soil myself lol's (this goes for bloody mint as well..)

On a serious note, you may be able to recover data on a failed HD by putting it in the freezer for a couple of hours, then quickly boot it and copy your data..

---

### Post by oldfred on 2009-12-08
Even with old grub and now with grub2 I find mixed Sata & Pata configurations do not always identify the boot disk correctly. The BIOS is supposed to define which drive boots first. In Sata motherboards you control that with BIOS setup. Old Pata motherboards had no control and you set master/slave via jumper or cable select to control which drive boots. Mixed may have some motherboard control or not. Grub/Ubuntu may not install to the correct drive so you probably just need to change the drive order to get grub/ubuntu to boot.

---

### Post by The_Pirate_King on 2009-12-08
> **JBAlaska said:**
> You should use Arch......J/k honestly If I here one more "you should use Arch" comment I'm gonna sh...erm soil myself lol's (this goes for bloody mint as well..)

On a serious note, you may be able to recover data on a failed HD by putting it in the freezer for a couple of hours, then quickly boot it and copy your data..
I had most of my data backed up so it's really not a big deal to me.  Anything I had on there is either readily available online or backed up.  Thanks though. 

And uh... what's Arch exactly?

---

### Post by Marvin666 on 2009-12-08
For a while I ran a dualk boot of jaunty xubuntu and vista. Wouldn't recomend the vista though, it BSOD'd like carzy. If I had to install a version of windows with ubuntu, it would be server 2003. It's like a more stable, and faster version of xp.

---

