---
title: "How to restore my PC back.."
date: 2010-06-02
forum: New to Ubuntu
---

### Post by KushKashyap on 2010-06-02
Hi there,

I have a PC with Ubuntu 10.04 and Windows 7 dual boot.
Recently i made a mistake of deleting the Ubuntu partition from the Windows Disk Management utility. How foolish i was, i have just realized. 
After deleting the Ubuntu partition i was trying to reinstall Ubuntu from inside my windows 7 using "Install Ubuntu along side Windows like a normal program". It was think kind of option, i don't exactly remember. Please note that i was installing from mounting an image of the Ubuntu Live CD.

Now as my bad luck, while it was almost about to finish the installation my power went off and since i had no ups so my PC shut down.
When i restarted my PC, i was left with the Grub Rescue screen.
And adding to my problems i don't have a live CD of Ubuntu but that of Knoppix...
Is there any hope for me :-)
Any help will be highly appreciated.
Thanks in advance.

---

### Post by darkdragn on 2010-06-02
The big mistake was probably trying to reinstall it... The best thing to do would've been try to get ahold of a live bootable and run test disk to try restoring your ext4 partition... uuumm, >_<. Is your HDD sata or ide?(On second thought that might not even matter) Can you not boot windows because grub didn't finish installing? If so, but grub does come up as far as the command interface try the following commands:

root		(hd0,1)
savedefault
makeactive
chainloader	+1

If it doesn't work try (hd0,1) or (hd1,1) etc

---

### Post by Ozymandias_117 on 2010-06-02
The problem is during the Dual boot, you overwrote your MBR. You need to get a Windows 7 disk and get to recovery mode and use FIXBOOT and FIXMBR.

Also, you may want to boot to an Ubuntu LiveCD and use gparted to put your hard drive's space back to Windows.

---

### Post by Bucky Ball on 2010-06-02
> **KushKashyap said:**
> ... Please note that i was installing from mounting an image of the Ubuntu Live CD.

And adding to my problems i don't have a live CD ...
Is there any hope for me :-)


Probably not unless you let us know what is going on!

---

### Post by KushKashyap on 2010-06-02
Thanks a lot darkdragn.
Well let me tell you what exactly happened.
I had first installed Ubuntu alongside windows 7 as dual boot. Then what happened was one day i was trying to login to Ubuntu but it did not proceed beyond the Ubuntu splash screen and later i got the error failed to mount drive.
Since i dint have any Live CD with me at that time, had only its image so i thought that i would delete the older partition and would reinstall it from inside the windows. And then the power tragedy happened.
Now what all i am getting is the following error

Error : Unknown File System
Grub rescue >

Now the problem is that the only Live CD i have is that of Knoppix. Is it possible to repair from it.

---

### Post by KushKashyap on 2010-06-02
I know all this may sound weird and confusing to you. So i would to clear that after deleting the Ubuntu partition i was trying to install Ubuntu by mounting an image using Power ISO inside windows 7. Then the power went off in the middle.

I don't have the Ubuntu Live CD right now with, i only had its disk image. The only live cd i have now is of another Linux distro called Knoppix.

---

### Post by cbecker78 on 2010-06-02
what do you mean you only have the disk image?  do you mean the ubuntu iso on cd?  If so, that actually IS the live cd.  Pop it in and try to boot from it if you want to check.  I don't think you have mentioned if you actually can boot windows yet, but from your posts, it seems like you cannot.  You will need to run the system restore for window (with the fix boot sector option) before you can get into windows again.

---

### Post by KushKashyap on 2010-06-02
The iso image was on my hard disk. i don't have any Ubuntu CD. I have Knoppix Live CD and i can not get in to windows. I am stuck at the grub rescue screen. So is booting and repairing from the windows the only option i have ?

---

### Post by darkdragn on 2010-06-02
Well, i'm thinking you could use grub to boot windows, and try your original idea, or use unetbootin to get the ubuntu iso on a jump drive (I'm guessing the only reason you didn't burn it from the get go, is because you don't have blanks laying around, lol)Grub is doing this because it's the default for if it's missing the config files, which were on the deleted partition. If Grub2, which was used by ubuntu is a bit too confusing to use to boot your windows os, you could try using what ever boot loader is on the knoppix disc. I was wrong, btw, and sry. Grub2 starts at 1 as opposed to 0 for the hd index values. At the grub restore > screen you can use ls to display the hd options available.

---

### Post by darkdragn on 2010-06-02
Oh, and the commands from my orig post are for grub, not grub2... I think the gurb2 commands should be

insmod chain
	set root=(hd1,1)
	devicemap -s hd0 hd1
	chainloader +1

---

### Post by cbecker78 on 2010-06-02
Oh, hang on.  If I understand power iso right, it should have been trying to mount the iso in a virtual drive...  So I'm not sure how that managed to bonk your system.  In fact, I don't think it bonked your system...  what bonked your system was deleting your ubuntu partition.  Because that was where you had grub installed to, right?.  when that partition went bye-bye... it wouln't have mattered if you had lost power or not, you would be stuck with a non-booting system.  And the good answer is yes, if the previous senario is right, you can recover your ability to boot, you just need to reinstall grub.  You can either do this with the ubuntu image cd (if you have one) or with knoppix.  Scroll down to this page for instructions (I haven't tried this with knoppix, but they seem reasonable):
[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

Ask here if you have any questions, and also, it would be a good idea to back up important windows files using knoppix before you get started.  And your ubuntu is probably toast, unless you can still mount and see that partition using knoppix...  Though there may be some trick I don't know about to recover that data, depending on how windows erased it.

Edit:  note, once you get your windows back, I'm pretty sure you cannot install ubuntu using poweriso.  Look into "Wubi" in google for a better way.  After reading the post you put up while I was writting this, I does look like your best option may be to just use the windows recovery to fix the MBR... that will give you a fresh start, more or less.

---

### Post by KushKashyap on 2010-06-02
Thanks a lot all you guys. I will go back to my PC and try all that you guys have told. Right now i am in my office.
I am sure u guys know how it feels to see your PC dead like that :-) But it was just my inexperience with Linux. But i am learning well and most of the times i use Ubuntu as my preferred OS.
And yeah my priority is to back up my windows files. I dint have much on my Ubuntu.
But thanks a lot. I will get back to you guys soon.

---

### Post by Bucky Ball on 2010-06-02
If you have the ISO image on your hard drive, make a CD from it!!! Simple.

---

### Post by darkdragn on 2010-06-03
> **Bucky Ball said:**
> If you have the ISO image on your hard drive, make a CD from it!!! Simple.

Lol, from what i gathered, the iso is on the NTFS partition for her windows OS, and currently, with grub not having the EXT3/EXT4 partition to read it's config from, the user is attempting to figure out the commands to boot into the Windows OS... So, it would be simple, if we can get it booted... and there's blank media laying around.

---

