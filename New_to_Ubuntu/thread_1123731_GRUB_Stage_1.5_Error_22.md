---
title: "GRUB Stage 1.5 Error 22"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by davecrom2009 on 2009-04-12
Hello.

I have a Vista then Ubuntu dual build.  

Grub is hanging at Error 22 Stage 1.5 after I tried to remove a botched Ubuntu install.

I have searched and seen a common solution is to boot of a LIVECD, Vista CD, recovery CD etc.

My problem, is that even with my BIOS set to boot to CD/DVD first, and even using a normally boot-capable CD, I still keep getting the GRUB message before anything on the CD gets a chance to boot.

So, right now, I have a dead laptop with no means of recovering to put anything on it.

Anyone have any ideas?

Cheers,
Dave

---

### Post by lavinog on 2009-04-12
Grub only affects the MBR of the hard drive. Something is wrong with your bios if you can't boot to CD.
What I have noticed on my desktop is that if I tell the bios to boot from CD-ROM first, it wont because since my CD-ROM drive is a sata drive BIOS calls it by the manufacturer name....see if there other devices you can boot from.

Can you give some specifics about your laptop?

---

### Post by davecrom2009 on 2009-04-12
Thanks for the speedy reply, friend.

It's a toshiba satellite p100.

The thing that's odd - is that I have booted from the drive before - for instance, to boot into Acronis True Image.

It was during an attempt to remove Linux (temporarily) that the problem occurred - I dloaded an ISO linux boot image off this site, and tried to use the sudo get ms.sys approach I saw documented in one of the sticky's here.

During that, my desktop went gray, and then finally suffered a big crash where all I got was a blue, black and white zig-zag pattern on my screen.

I powered off and on, and at that point i couldn't get past error 22 even when booting to my "known-good" CD such as acronis.

Cheers
Dave

---

### Post by davecrom2009 on 2009-04-12
Just one thing to add - even though I'm not that computer literate (being of the silver-haired aged brigade!), I think I know enough to know that I can't attribute this problem to software like Grub or Ubuntu.

I;m not about to start ranting about "Ubuntu Killed My Laptop!!!!" and adorn the message with several angry-looking frownies.

I guess the law of un-correlated co-incidence may have struck me a savage blow.  Who knows, the ability of my CD/DVD drive to boot could have failed yesterday without me knowing.  :-)

Cheers
Dave

---

### Post by lavinog on 2009-04-12
Is it possible that your drive lens might be dirty.
Does the drive try and spin up when you boot?
Have you tried burning at a slower rate?

---

### Post by davecrom2009 on 2009-04-12
I'm exploring those options, thanks again.

The more I think about it, the more I think I should see this as something for Toshiba not for the good people of this forum.

I have managed to get a bootable CD to work just this second - but it didn't work the next time.

It looks like I have a dodgy drive right now.

I shall fix this first, then revert back to a backup I guess.

Thanks for the help and replies in the mean time.

Cheers,
Dave

---

### Post by beatbm on 2009-04-12
well what i ll say its not a solution but works for my pc when i get error 22

i press "e" to edit and then "c" to go to the command line
then write  geometry (hd0) then going back and like a magic thing happens i press to boot and both windows and ubuntu loading correctly. don know to explain but happens

---

### Post by lavinog on 2009-04-12
If you have ubuntu available on another computer, you could make a bootable flashdrive.

Also you should be able to boot off of a usb cdrom drive. you should be able to find a desktop cdrom drive for about $20 and a usb connector for another $20

---

