---
title: "The Screen Is Black after Boot load"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Phareouh on 2010-11-03
Hi there , after i installed using Wubi the 64 version, on my Win 7 , 

when i get the boot loader screen i choose Ubuntu , and then i get to  choose recovery mode or Normal mode , in either , i get some sort of a  list , and then i Get a Black Screen , Nth ,

But i hear a sound of May be Ubuntu starting ...:confused::confused:

so what can i do to see my Ubuntu ????

is there is away for help , i just need to run Both my Original Reinstalled Win 7 64 bit ,
and my Ubuntu.. So i used Wubi as an easy answer :smile:


so Can any help 

thankx

---

### Post by Hippytaff on 2010-11-03
It might be worth uninstalling Wubi in windows and doing a 'real' dual boot (seperate partition) for ubuntu if you have nothing important on your wubi ubuntu.

---

### Post by Phareouh on 2010-11-03
> **Hippytaff said:**
> It might be worth uninstalling Wubi in windows and doing a 'real' dual boot (seperate partition) for ubuntu if you have nothing important on your wubi ubuntu.


How ? but i still need my Win 7

PLEASE help me

thankx

---

### Post by P4man on 2010-11-03
I agree with the suggestion of not using wubi and do a proper install (dual booting is handled automatically), but the problem you have is probably not related to wubi, but rather a videocard (nvidia?) needing nomodeset until you install the nvidia drivers.

I would suggest booting from the installation CD (or USB stick) and you will probably face the same issue. IF so, when you see the keyboard logo at the bottom right after the bios, press any key to bring up a menu. In that menu select nomodeset from the F6 menu. Then try ubuntu without installing. If that works, then report back, then we can solve it for a full install, or the wubi install if you must.

---

### Post by Phareouh on 2010-11-03
I do have Nvidia Card , the GT 330M

What 2 do about that ?

---

### Post by Hippytaff on 2010-11-03
Ok, so...download the ubuntu livecd [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
(theres a show me how button) follow the instructions.
 
Then reboot from cd (change the bios boot order, usually pressing one of the F (usally F8, or F9)keys at startup will open the bios menu, change the boot order so cd is at the top)
 
Once the cd has booted you get an option to install ubuntu. You can either go with the default installation, but it's probably better to do the manual partition so you can choose sizes.
 
Read this first [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
BACK UP ALL INPORTANT DATA!!!

---

### Post by P4man on 2010-11-03
slow down a bit. If my second assumption about nomodeset is also correct, the LiveCD will boot in to a black screen just as well. And if he manages to get around that with nomodeset F6 menu, and he does an install, upon booting his fresh ubuntu install he will again face a black screen. 

So lets first see if nomodeset is indeed the cure, because if it is, he will need quite a bit more guidance.

---

### Post by Phareouh on 2010-11-03
> **P4man said:**
> slow down a bit. If my second assumption about nomodeset is also correct, the LiveCD will boot in to a black screen just as well. And if he manages to get around that with nomodeset F6 menu, and he does an install, upon booting his fresh ubuntu install he will again face a black screen. 

So lets first see if nomodeset is indeed the cure, because if it is, he will need quite a bit more guidance.

Will here is what i did So far :

i Burned the iso
Booted it
then when i got the Sticky Figure Guy = Keyboard , i choose language , then i asked to try without installing

the problem happened again (Black screen), So may be it's My Vga card ??

Nvidia GT 330m

or something else

---

### Post by Phareouh on 2010-11-03
> **P4man said:**
> slow down a bit. If my second assumption about nomodeset is also correct, the LiveCD will boot in to a black screen just as well. And if he manages to get around that with nomodeset F6 menu, and he does an install, upon booting his fresh ubuntu install he will again face a black screen. 

So lets first see if nomodeset is indeed the cure, because if it is, he will need quite a bit more guidance.

Okay i Did it Now with the nomoddeset , and "Try it" option it work

although it showed me an error , something about Thermal detection of a driver or something
..

so what now

Thankx so far for your help guys ??

now i want to install it , But how ?

---

### Post by P4man on 2010-11-03
okay, so I guessed right.
We can do two things, fix your wubi install and you carry on with that, or do a native install and we will need to fix it again after installing.

Is there any particular reason you want to use wubi? If there isnt, boot windows again, remove ubuntu (assuming you have no files or anything to save in ubuntu). Then in windows disk  management resize your windows partition and make some room, that is, unpartioned space for ubuntu (this isnt strictly needed, the ubuntu installer can do it too, but its probably safest and definately fastest).

Once you did that, reboot from the ubuntu cd, do the nomodeset thing again and report back; well talk you through the installation.

Oh and make backups now. No you probably dont need it, but you never know.

PS: please dont PM me about threads like these. I subscribe to all threads I post in, I will read your posts and reply to them when I can. PM is only for private stuff.

---

### Post by Hippytaff on 2010-11-03
> **P4man said:**
> slow down a bit. If my second assumption about nomodeset is also correct, the LiveCD will boot in to a black screen just as well. And if he manages to get around that with nomodeset F6 menu, and he does an install, upon booting his fresh ubuntu install he will again face a black screen. 
 
So lets first see if nomodeset is indeed the cure, because if it is, he will need quite a bit more guidance.
 
I wasn't aware of yuor post. it wasn't there when I started posting back...sorry...looks like Nvidia problems, I'm not sure of how to resolve cthis at install stage

---

### Post by Hippytaff on 2010-11-03
Found this in another thread. If you install ubuntu you will have to do the nomodset at boot up again
 
1. During startup, keep "SHIFT" pressed until you're in the grub menu
2. Once in the grub menu, press "e"
3. Find the line with "quiet splash" and type "nomodeset" after it
4. Press "CTRL+x" to boot 

 Then install the proprietary NVIDIA driver once ubuntu is installed and reboot normally.

---

### Post by Phareouh on 2010-11-03
> **P4man said:**
> okay, so I guessed right.
We can do two things, fix your wubi install and you carry on with that, or do a native install and we will need to fix it again after installing.

Is there any particular reason you want to use wubi? If there isnt, boot windows again, remove ubuntu (assuming you have no files or anything to save in ubuntu). Then in windows disk  management resize your windows partition and make some room, that is, unpartioned space for ubuntu (this isnt strictly needed, the ubuntu installer can do it too, but its probably safest and definately fastest).

Once you did that, reboot from the ubuntu cd, do the nomodeset thing again and report back; well talk you through the installation.

Oh and make backups now. No you probably dont need it, but you never know.

PS: please dont PM me about threads like these. I subscribe to all threads I post in, I will read your posts and reply to them when I can. PM is only for private stuff.

I talk to you Now from a Cd version of the os , i did uninstall , Wubi 

and i did made a partition (40 GB) and for it .

so yes i tried Nomodeset with CD as "Try mode"

and it work , And when i tried additional drivers , it said something about Nvidia Driver . 

that is how far i came.

Now a Small Noobish advice how to subscribe to a thread ??

thanks

---

### Post by Hippytaff on 2010-11-03
THread tools at the top and subscribe to thread. You can set it to subscribe to all threads that you post on in the CP

---

### Post by P4man on 2010-11-03
> Now a Small Noobish advice how to subscribe to a thread ??


Its in "thread tools" at the top of this page. Somewhere in the options of this forum you can configure it to automatically subscribe to all threads you post in (which is usually good idea).


> **Phareouh said:**
> I talk to you Now from a Cd version of the os , i did uninstall , Wubi 

and i did made a partition (40 GB) and for it .

so yes i tried Nomodeset with CD as "Try mode"

and it work , And when i tried additional drivers , it said something about Nvidia Driver . 

that is how far i came.

thanks

Good. now double click the installer. I dont have it in front of me, so I cant give you literal explanations but it should fairly easy to figure out. When the installer asks you where to install, it will present your partitions.  Make sure it sees your windows install. If it doesnt recognize it, stop there and report back.

If it does see it, select the "advanced" or "manual" option.

Create an extended partition in the unpartitioned space (as big as the free space). Inside that extended partition, create one partition with "/" as mountpoint (that is your main partition) and set the filesystem to Ext4. And create one smaller partition as linux-swap. Make it roughly twice as big as the amount of RAM you have.

Here is a screenshot what it should look like:
[http://ubuntuforums.org/showpost.php?p=10054358&postcount=12](http://ubuntuforums.org/showpost.php?p=10054358&postcount=12)

The rest of the process I think explains itself.

edit: after it finished installing and prompt you to reboot, follow Hippytaff's post to add nomodeset to your kernel options.

---

### Post by Phareouh on 2010-11-03
> **P4man said:**
> Its in "thread tools" at the top of this page. Somewhere in the options of this forum you can configure it to automatically subscribe to all threads you post in (which is usually good idea).




Good. now double click the installer. I dont have it in front of me, so I cant give you literal explanations but it should fairly easy to figure out. When the installer asks you where to install, it will present your partitions.  Make sure it sees your windows install. If it doesnt recognize it, stop there and report back.

If it does see it, select the "advanced" or "manual" option.

Create an extended partition in the unpartitioned space (as big as the free space). Inside that extended partition, create one partition with "/" as mountpoint (that is your main partition) and set the filesystem to Ext4. And create one smaller partition as linux-swap. Make it roughly twice as big as the amount of RAM you have.

Here is a screenshot what it should look like:
[http://ubuntuforums.org/showpost.php?p=10054358&postcount=12](http://ubuntuforums.org/showpost.php?p=10054358&postcount=12)

The rest of the process I think explains itself.

edit: after it finished installing and prompt you to reboot, follow Hippytaff's post to add nomodeset to your kernel options.


Done , and i got it installed , and now instaling Nvidia Driver

had a problem first but now it's okay.

---

