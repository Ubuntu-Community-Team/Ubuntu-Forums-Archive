---
title: "HP Dv7 Grub Error 22"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by andyzammy on 2009-03-21
Hello everyone!

I'm a relatively new convert to the ubuntu cause. I'm a student and skint so you can't beat ubuntu on my budget! Also my patience with MS finally ran out after realising i shouldn't *have* to be patient with them in the 1st place lol..

I recently purchased a HP Pavilion dv7 1055em. It came with Vista ofc. I tried ubuntu out with the live cd to see how it faired, but you can't try everything on a live cd so my next move was to install ubuntu as a duel boot job. Everything worked fine, so i committed to the ubuntu changeover and reinstalled ubuntu, erasing the vista partition in the process (but keeping the recovery partition should i ever need it for something) so that all i had now on the HD was Ubuntu and vista recovery.

Today i wanted to install the virtualbox propriatery version (i wanted to run itunes in xp in a vm so i could keep my ipod in check etc). According to the installer package it had installed (though i couldn't find it in the menu's, and typing "virtualbox-2.1" into bash gave me a "command not found" or something..

I can't even remember what caused my laptop to crash, but crash it did. the screen froze and after about 5 mins of waiting i pressed and held the power button. upon restart, i got the grub error 22. I then tried to use the recovery cd but that brought up a windows error 100a (which i think has something to do with hard drive failure). I tried the cd again, but this time opted to "use a program on the hard drive", so the lappy restarted and booted from the recovery partition. Since then, the laptop only boots from the recovery partition (and the odd time i tried to recover still brings up that 100a error) and doesn't even get up to the grub anymore.

i googled and i found this, which is what i think i need but i would like someone to confirm before i try it. i can boot from the live cd so i think i can do this, though not without being walked though it step by step because i understand nothing about this (lol i know, i wan't to be walked though a walkthough.. i'm like that).
[http://ubuntuforums.org/showthread.php?p=4346162](http://ubuntuforums.org/showthread.php?p=4346162) which gave me:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

is this the fix i need to use? this laptop has 2 hard drives so i'm very unsure what that means when it comes to the setup (hdX). would someone be able to write out the commands i need to do this please?

thanks,
zammy

---

### Post by andyzammy on 2009-03-22
Fixed it with the super grub disk

:P

---

### Post by boris_1981 on 2009-06-22
hello there.

im actually having the same problem.  can you tell me how exactly did you managed to fix this error using the super grub disk?  

do i need to have an OS installed to use this program or can i boot with super grub (just like gparted)?

thanks for your help.  


PS.  bare with me, my english isnt good and im also a newbie.

---

### Post by andyzammy on 2009-06-25
hi there.
you do need to have an OS installed, but you want to boot from the super grub disk. what the super grub disk does is fix the bootloader, which will enable you to successfully boot an OS. i used this method: [http://ubuntuforums.org/showpost.php?p=1628616&postcount=3](http://ubuntuforums.org/showpost.php?p=1628616&postcount=3)

i'm a noobie myself so if you still struggle i hope others will be able to help you. good luck!!

zammy

---

