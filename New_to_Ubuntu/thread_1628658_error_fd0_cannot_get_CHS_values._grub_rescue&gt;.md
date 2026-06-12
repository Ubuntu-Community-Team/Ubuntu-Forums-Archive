---
title: "error: fd0 cannot get C/H/S values. grub rescue&gt;"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by loop444 on 2010-11-22
installed via wubi on win 7 64bit asus ul30j

worked fine **** might have hit the fan when i installed the updates in ubuntu b4 turning off the computer b4 sleeping yesterday when i woke up today all i get is:


error: fd0 cannot get C/H/S values. 
grub rescue>

ls gives hd0 and fd0

trying to load win 7 recovery (my puter has no cd and i have no usb stick) only gives some maybe 20 or 30 string of - and letters in capslock and &#324;umbers

although i dont want to have to recover or reinstall anything i figure it should be possible to somehow recover find out what went wrong

it seems otherwise my only option is to obtain an usb stick and reinstall ubuntu but how iwould recover win 7 i have no clue

well what i want is to recover my **** i am sure there is just some minor adjustment that needs to be done possible only one or a few commands

i do have usb stick but they are only on 1 gb so if u have suggestions for that im okay, let me repeat i do not want to reinstall anything i want to recover it

also b4 i tried the nvidia driver but it made by screens go black

i am willing to experiment a bit so tell me some commands and or things i can do and maybe for the 1gb usb stick

i have other computers, like this one, rite here an nc10 but yeah i guess the others are kindof unavailbe though

well bring on the help pl0xxorsz

:popcorn:

---

### Post by bcbc on 2010-11-23
It sounds like you installed ubuntu within Windows (i.e. using wubi). If this is not the case, let me know.

A recent update prompted to install grub - do you recall a screen 'continue without installing grub' followed by one where you selected to install to /dev/sda? This would have installed grub to the drive master boot record.
Wubi installs need the windows bootloader in the drive MBR.

The fix is to reinstall the windows bootloader - boot to a windows repair prompt and run "bootrec.exe /fixmbr"

Here's a link with how to get to a repair command line (step3), but note you should just have to run the command I showed above, ignore the bootsector fix etc. [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by loop444 on 2010-11-23
> **bcbc said:**
> 
Hello Good Sir, Thanks for your kind reply. I do not remember the grub and dev part, I simply installed the 200mb of various updates that was recommended, ubuntu worked b4 i  this so i suspect the cause is there somewhere.

Also, I have two internets one lan and one on a usb mobile broadband, it seems like the mobile broadband is the f0 disk because now it is unplugged and ls in rescue grub mode gives only hd0

If you still suggest I take the actions you recommend, then how do I reinstall the windows bootloader?

 
:KS

---

### Post by bcbc on 2010-11-23
Yes, put in your windows dvd and boot from it. Select Repair your computer. Click on the last option: Command Prompt.
Type "bootrec.exe /fixmbr" and press enter.

---

### Post by loop444 on 2010-11-23
> **bcbc said:**
> Yes, put in your windows dvd and boot from it. Select Repair your computer. Click on the last option: Command Prompt.
Type "bootrec.exe /fixmbr" and press enter.

It has no dvd it only has builtin partition of win 7 installation which i can normally load from when i can choose to recover or reinstall win 7 when holding the f8 or f9 key while the asus logo is showing during startup but now doing this f8 or f9 only gives me no such device in grub rescue....

I have 1gb usb stick, maybe i can use some kind of variant of linux to boot from it and run the command @sudo update grub2 something like that

or  maybe it is possible to make a rescatux usb stick?

Also this computer has a builtin second powerbutton which leads to a builtin linux? distro called asus express gate but i am not sure if it possible to reach some kind of terminal in here it is very locked down to some simple uses like skype internet music and pohots and games 

so i am on 2 puters now a netbook and an ultraportable this one

maybe i could use my lan cable to do some kind of boot via the lan cable?

so what i seem to be able to reach from this grub rescue computer is asus express gate, bios, and the grub rescue comman prompt

and the only command that i got to work is ls and it gives hd0 and i did not try many other but the ones i tried gave no such filesystem or unknown comman etc

so looking at your latest message maybe i could get some kind of other software to put on my usb stick to load the windows command prompt?

---

### Post by bcbc on 2010-11-23
If you can boot an Ubuntu live CD you can install lilo in a form equivalent to the windows bootloader.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore dire warnings as they relate to using lilo for booting linux.

---

### Post by pradeepjawahar on 2010-11-23
Hi I had the same problem too.
@bcbc ..your solution saved my day ..
Thanks

---

### Post by tenorx on 2010-12-22
Hey bcbc!
I've done exactly the same as you've described, and I really hope this will help :)
I'll get a Win 7 recovery CD from my friend (silly me, I've left mine in another city, where I study, and I can't even burn one with this PC), and I'll try everything the way that guide says.
Noob question #1: Is it possible that I won't be able to boot from CD? I have this question because I've tried to make things work with a Live ubuntu USB. It was working at first, but after the restart if I tried to boot from the pendrive I received this error:  error: fd0 cannot get C/H/S values.
However, if I just let the laptop load without actually doing anything, I'll get the other error.
So I really hope that I'll be able to boot from the CD and fix things.
Noob question #2: If I do fix it, will this error return if I switch to Ubuntu again? I plan to experience a bit more with Ubuntu, I would really like to be able to use it properly.

Nevermind, I could fix it, burnt the CD with my laptop using the USB Ubuntu :)
Thanks a lot man!

---

### Post by bcbc on 2010-12-23
> **tenorx said:**
> Hey bcbc!
I've done exactly the same as you've described, and I really hope this will help :)
I'll get a Win 7 recovery CD from my friend (silly me, I've left mine in another city, where I study, and I can't even burn one with this PC), and I'll try everything the way that guide says.
Noob question #1: Is it possible that I won't be able to boot from CD? I have this question because I've tried to make things work with a Live ubuntu USB. It was working at first, but after the restart if I tried to boot from the pendrive I received this error:  error: fd0 cannot get C/H/S values.
However, if I just let the laptop load without actually doing anything, I'll get the other error.
So I really hope that I'll be able to boot from the CD and fix things.
Noob question #2: If I do fix it, will this error return if I switch to Ubuntu again? I plan to experience a bit more with Ubuntu, I would really like to be able to use it properly.

Nevermind, I could fix it, burnt the CD with my laptop using the USB Ubuntu :)
Thanks a lot man!

Hey tenorx, Glad to hear you got it sorted out.

PS there's now a [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for dealing with these Wubi/grub problems.

---

### Post by loop444 on 2010-12-30
ok i now have two usb 4gb sticks or almost 4gb well here i have them and on one of them i used the universal usb installer and it seems properly put on it but when i put it in the computer and even trying various f buttons to get some kind of boot screen nothing happens but the usual grub rescue prompt

what do what do....

to remind you i have win7 and ubuntu on the computer and i want to ideally restore both to full functioning again

ktnx! :guitar:

---

### Post by loop444 on 2010-12-30
Is there some kind of command I can run to initiate the usb ubuntu distro from the grub rescue prompt or is there something elese you recommend me to put on the usb stick or do? :KS

---

### Post by bcbc on 2010-12-30
> **loop444 said:**
> Is there some kind of command I can run to initiate the usb ubuntu distro from the grub rescue prompt or is there something elese you recommend me to put on the usb stick or do? :KS

The ubuntu.com download site gives instructions on creating a usb. You can't do anything from the  wubi grub rescue prompt.
Make sure your computer is bootin first from usb devices.

---

### Post by loop444 on 2011-01-02
> **bcbc said:**
> The ubuntu.com download site gives instructions on creating a usb. You can't do anything from the  wubi grub rescue prompt.
Make sure your computer is bootin first from usb devices.

k thanks for all advice i got the usb 4gb stick installed ubuntu desktop on it and reinstalled ubuntu on the computer from choosing boot via usb because hitting esc and f1 and now i am on windows 7 i might try ubuntu later again it is still installed:guitar:

ktnx again ima mark it as solved but the problems might still be there, the causes maybe nvidia driver and some updates in ubuntu was possible some of the problems that caused all of this

now if i can just find the mark thread as solved button

tnx again!:-({|=

---

### Post by bcbc on 2011-01-03
> **loop444 said:**
> k thanks for all advice i got the usb 4gb stick installed ubuntu desktop on it and reinstalled ubuntu on the computer from choosing boot via usb because hitting esc and f1 and now i am on windows 7 i might try ubuntu later again it is still installed:guitar:

ktnx again ima mark it as solved but the problems might still be there, the causes maybe nvidia driver and some updates in ubuntu was possible some of the problems that caused all of this

now if i can just find the mark thread as solved button

tnx again!:-({|=
I didn't quite understand, but it sounds like you installed a new Ubuntu direct to partition, so you are now using the grub bootloader. But whatever you did, great you got it working again :)

---

