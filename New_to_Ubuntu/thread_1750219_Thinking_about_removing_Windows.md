---
title: "Thinking about removing Windows"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by ubume2 on 2011-05-05
My main household computer has Windows xp in partition1, 1 FAT32 partition, 1 swap partition, 1 partition each of 10.04 and 10.10. I hardly use Windows on that computer.  It is an 80 gig HD with about 20 gig dedicated to Windows.

I would like to delete that (XP) partition.  I know how to use LiveCD and gparted and restore grub etc.  I am quite comfortable with Ubuntu (11.04 a different story).

What likely problems could I have if I deleted the XP partition(hd0,0) and replaced it with another Linux OS?

Thank you.

---

### Post by eriktheblu on 2011-05-05
You may not be able to update the BIOS. Some manufacturers only support Windows, and that isn't something you want to be doing with Wine. FreeDOS sometimes works, but you'll want to check first.

Chances are, if your computer came with XP, there isn't much BIOS updating that's going on any more.

Problem 2: Your new distro may mess with your MBR or boot loader.

---

### Post by Fedz on 2011-05-05
Problems extremely likely from removing Windows is you can't use Windows but, the psychological benefits are immensely rewarding ;-)

---

### Post by sadaruwan12 on 2011-05-05
> **Fedz said:**
> Problems extremely likely from removing Windows is you can't use Windows but, the psychological benefits are immensely rewarding ;-)

Yes I strongly agree now the apps even are coming closer to the windows ones which our most user have been using.

So I tell you to go ahead and do it.

---

### Post by lboorse2 on 2011-05-05
My question is, why delete it?  Just to say you don't have Windows installed?  Leave that 20Gig Windows partition alone (that way you still have access to any files you have saved there).  Then, just set up Grub or Grub2 to make whichever Ubuntu install is your favorite the default and reduce the countdown to like 2 or 3 seconds.  Then you'll boot, you'll see the Grub screen display very briefly (leaving you just enough time to select a different boot option if necessary), and in just a few more seconds you'll be at your Ubuntu desktop free to go on your merry way with no worry.  

If you absolutely must remove Windows... well, if it were me, I'd just grab another hard drive and start from scratch with Ubuntu only.

---

### Post by blind2314 on 2011-05-05
> **eriktheblu said:**
> You may not be able to update the BIOS. Some manufacturers only support Windows, and that isn't something you want to be doing with Wine. FreeDOS sometimes works, but you'll want to check first.
 
Chances are, if your computer came with XP, there isn't much BIOS updating that's going on any more.
 
Problem 2: Your new distro may mess with your MBR or boot loader.
 
 
Nearly every motherboard manufacturer offers a method to update/flash that doesn't involve launching something from within Windows.
 
Since he's already using GRUB (I assume), there shouldn't be any problems adding another Linux OS to it. He may have to run ```
update-grub
``` from within his Ubuntu install after, but merely adding an OS is not going to break his ability to boot into Ubuntu.
 
Caveat: This assumes that nothing stupid is done during the install of said "other OS" :)

---

### Post by ubume2 on 2011-05-05
> **lboorse2 said:**
> My question is, why delete it?  Just to say you don't have Windows installed?  Leave that 20Gig Windows partition alone (that way you still have access to any files you have saved there).  

No. I am not a GNU only type of guy. I see your point.  Probably only reason for doing it: it frees up 20 gig.  I use grub2 to boot between XP and my two Ubuntus. Thanks for your opinion.

---

### Post by eriktheblu on 2011-05-05
> **blind2314 said:**
> Nearly every motherboard manufacturer offers a method to update/flash that doesn't involve launching something from within Windows. Then I've just had really bad luck. Every system board I've tried to update BIOS on has only given me instructions and binaries for Windows/DOS.

The boot loader/MBR thing is admittedly a small problem, but really how much can go wrong from deleting Windows?

---

### Post by ubume2 on 2011-05-05
> **blind2314 said:**
>  
Caveat: This assumes that nothing stupid is done during the install of said "other OS" :)

I've done that [something stupid] many times.:P That is how I learned some important things about Linux and hard drives.

> **eriktheblu said:**
> Then I've just had really bad luck. Every system board I've tried to update BIOS on has only given me instructions and binaries for Windows/DOS.

The boot loader/MBR thing is admittedly a small problem, but really how much can go wrong from deleting Windows?

I am installing in a spare laptop with empty HD.  Everything seems to be going okay. No BIOS problems.


I will see how this goes. Mull over all your comments, and decide whether I really need to delete Windows for  that 20 gig of space and whether I really want to install 11.04 in that space. Thanks.

---

### Post by lboorse2 on 2011-05-06
Keep in mind, Ubuntu can access NTFS partitions, so that 20 Gig of space (well all except for the few Gigs taken up by Windows system files) is still  usable.

---

### Post by Frogs Hair on 2011-05-06
Just be certain you won't need or want to use Windows in the future . you may want look into installing IE in Ubuntu for future reference because there are sites that are not friendly to other browsers and User Agent Switcher does not work on many sites . An example is filling out job applications. Good Luck !

---

### Post by ubume2 on 2011-05-06
Thanks guys. Points well taken. I think I will keep XP in grub2 just in case I need it.

---

### Post by Fedz on 2011-05-06
Wise choice ... push that dusty Windows OS to the back of the shelf =D>

---

### Post by walt.smith1960 on 2011-05-06
Here's one problem with not having a Windows partition.  You buy a piece of hardware; printer, network adapter, DVD, BluRay player, whatever.  Get set it up and it doesn't work in Linux. Is it DOA hardware or is it an O.S. problem?  You did look through the paperwork that came with the device enough to find the phone number for technical support.  You call:

You-"I bought your device and it doesn't work. How can I figure out what's wrong?"

Technical Support- "Make sure it's connected properly then click 'start' in Windows"

You-  "Sorry, I don't have Windows.  I use Linux"

Technical Support-  "I'm sorry. We don't support Linux, only Windows and OSX. Sorry" <click>

Now what?  Yes you can return it but that's a pain.

Or you need to run some specialist software that barely works in Windows and certainly won't work under WINE or its variants.

---

### Post by tushargkwd on 2011-05-06
I switched completely to Ubuntu 10.04 then onto 10.10....

I use Windows XP as a VM using VirtualBox.....I can do everything in a virtual machine just as a normal XP user.

Yeah....some programs do require Windows like the bootloader for flashing BIOS...  :(

---

