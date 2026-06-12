---
title: "Need to Uninstall Ubuntu to Reinstall"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by djk21108 on 2009-04-23
So I have had a lot of problems with 8.10 and I'd like to start fresh with 9.04.

I believe Ubuntu is the primary partition but I'd like to get rid of it, use windows for a while, and then install Ubuntu.  How should I do this?

---

### Post by MuddBuddha on 2009-04-23
I would install 9.04 using the 8.10 partitions.  There is no reasonable way to remove 8.10 and keep Windows intact.

Dual booting creates a lot of issues like this. I don't care for it. You could try VirtualBox and run Linux within Windows or Windows within Linux.

Using the "seamless mode", you can't really tell which is the host and which is the virtual.

---

### Post by djk21108 on 2009-04-23
well the problem is...i can't boot 8.10 anymore so I'm in a tough spot.

---

### Post by MuddBuddha on 2009-04-23
You shouldn't need to.  Just boot from the 9.04 CD to install it in place of 8.10 using those partitions.

What happened to 8.10?

---

### Post by djk21108 on 2009-04-23
8.10 Got messed up when I tried to use ATI's first party drivers.  Now I just boot into random pixels, so frustrating.

---

### Post by MuddBuddha on 2009-04-23
Yeah, been there.

Can you still boot into Windows?

---

### Post by Didius Falco on 2009-04-23
You need to give more information.

Are you dual-booting with Windows now?

What is it, exactly, that you want to do? Do you just want to get rid of Ubuntu totally for a while, and have the regular Windows boot-up screen?

When you boot up, are you seeing the Grub menu?

What partitions are on your PC currently?

BTW, I respectfully disagree with MuddBuddha regarding the dual booting. All it requires is a little knowledge.

Let us know what you are trying to achieve and the current status of your PC and we can help you much more. Otherwise, it's all WAGs...

---

### Post by JK3mp on 2009-04-23
Why don't you wish to use Ubuntu as primary? I gues just windows temp until 9.04 is worked out all the way and works well? Just curiouse. :)

---

### Post by djk21108 on 2009-04-23
> **Didius Falco said:**
> You need to give more information.

Are you dual-booting with Windows now?

What is it, exactly, that you want to do? Do you just want to get rid of Ubuntu totally for a while, and have the regular Windows boot-up screen?

When you boot up, are you seeing the Grub menu?

What partitions are on your PC currently?

BTW, I respectfully disagree with MuddBuddha regarding the dual booting. All it requires is a little knowledge.

Let us know what you are trying to acheive and the current status of your PC and we can help you much more. Otherwise, it's all WAGs...

Ok right now I boot into Windows 7 no problem.  I can go to grub and boot into ubuntu but it doesn't really get anywhere.  I have a 30 gb partition for ubuntu which is primary and a 100 gb one for windows and a 5gb one that i have no idea what its doing.

As for what I want.  I want 8.10 completely wiped (i had nothing on it anyway) and i wanna reinstall 9.04

---

### Post by utnubuuser on 2009-04-23
I usually have an XP install, then use Gparted to slide/resize the right-most Windows partition leftward. then install Ubuntu on the unused space.  No muss no fuss.

PS. Beware 9.04's "ext4" file system - it's not backwards compatible with earlier versions of Ubuntu.

---

### Post by MuddBuddha on 2009-04-23
That's cool, but I'm still correct.

This is a common issue when people have issues with a distro on dual boot and then want to abandon Linux and remove it without disturbing their Windows install.  

Good grief, it comes up on the forum constantly.  

For those "tinkering" with Linux, VirtualBox is just flat out a better option.

---

### Post by djk21108 on 2009-04-23
> **MuddBuddha said:**
> That's cool, but I'm still correct.

This is a common issue when people have issues with a distro on dual boot and then want to abandon Linux and remove it without disturbing their Windows install.  

Good grief, it comes up on the forum constantly.  

For those "tinkering" with Linux, VirtualBox is just flat out a better option.

I'm not just tinkering, I have been using it as my main operating system for a while until stuff conked out on me.  I really want what I had again!

---

### Post by dizzle1234 on 2009-04-23
DJK: Have you tried booting an older version of the kernel via GRUB? I had a problem and my kernel freaked. I then just booted the option several below the most recent one and Ubuntu was working. If you are still interested!

D

---

### Post by MuddBuddha on 2009-04-23
That was a general statement; not specifically directed at you or this thread.  Apology.

---

### Post by djk21108 on 2009-04-23
> **dizzle1234 said:**
> DJK: Have you tried booting an older version of the kernel via GRUB? I had a problem and my kernel freaked. I then just booted the option several below the most recent one and Ubuntu was working. If you are still interested!

D

8.10 is the only kernel i have besides safe mode, which doesnt seem to do much

---

### Post by Didius Falco on 2009-04-23
> **djk21108 said:**
> Ok right now I boot into Windows 7 no problem.  I can go to grub and boot into ubuntu but it doesn't really get anywhere.  I have a 30 gb partition for ubuntu which is primary and a 100 gb one for windows and a 5gb one that i have no idea what its doing.

As for what I want.  I want 8.10 completely wiped (i had nothing on it anyway) and i wanna reinstall 9.04

On Edit: the 5 Gig partition is likely your swap partition. Have a look at it on the partition screen and it will tell you what type it is.

On Edit: The 5 Gig partition is probably your swap file, but it'll tell you what type it is on the partition screen.

Boot with the Ubuntu 9.04 CD and choose "install". When you get to the partitioning screen, choose the "manual" option. Click the 30 Gig "/" partition and open the "change partition" button. Change so that it uses ext3 (or ext4 if you don't mind the risk), uses the partition and set it as "/".

Proceed with the install. It should format it by default, but there is a little box on the partition screen that you can click to force it to.

It'll install it and setup a new grub menu for you that includes your Windows 7.

---

### Post by j_zhill on 2009-04-23
Maybe try making a jaunty live CD with windows 7 then pointing the installer at your 30GB partition, and select the option to use the entire partition.

---

### Post by djk21108 on 2009-04-23
> **j_zhill said:**
> Maybe try making a jaunty live CD with windows 7 then pointing the installer at your 30GB partition, and select the option to use the entire partition.

Thanks for the advice, I tried the cd but when i hit install it says I/O error cd wont boot right or something....ahhh

---

### Post by djk21108 on 2009-04-23
help!!!

---

### Post by Didius Falco on 2009-04-24
Are you seeing any error messages when it first boots?

When you boot the CD, instead of choosing "install", chose "test disk integrity" to see if the disk is okay.

Will it load the desktop if you choose the "try without making changes" option?

Does everything work okay on the desktop? Try it out for a few minutes and make sure it's compatible with all your hardware.

Try that out and see how it goes.

---

