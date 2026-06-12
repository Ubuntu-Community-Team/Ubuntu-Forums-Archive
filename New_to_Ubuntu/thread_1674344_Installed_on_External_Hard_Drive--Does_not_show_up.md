---
title: "Installed on External Hard Drive--Does not show up in BIOS bootloader"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Missing_Number on 2011-01-23
Hi. I installed Ubuntu 10.10 on my WD Elements 500 GB USB 2.0 External Hard Drive. I am running XP on my main drive. The installation went fine and the hard drive wasn't bricked or anything like that.

However, whether the USB drive is plugged in or not, the option to load Ubuntu from the drive does not appear in the standard BIOS when I boot up. By the way, I am using the bootloader that comes with XP, not GRUB.

I know I haven't give much information, but does anyone have any advice on what to do? I still have the CD, if that helps.

---

### Post by MartyBuntu on 2011-01-23
> **Missing_Number said:**
> Hi. I installed Ubuntu 10.10 on my WD Elements 500 GB USB 2.0 External Hard Drive. I am running XP on my main drive. The installation went fine and the hard drive wasn't bricked or anything like that.

However, whether the USB drive is plugged in or not, the option to load Ubuntu from the drive does not appear in the standard BIOS when I boot up. By the way, I am using the bootloader that comes with XP, not GRUB.

I know I haven't give much information, but does anyone have any advice on what to do? I still have the CD, if that helps.

If GRUB is installed on the external, try setting that as your first bootable device in the BIOS.

---

### Post by Missing_Number on 2011-01-23
You're speaking to an absolute neophyte here. How am I to do that without preventing me from booting my XP partition? Can you tell me or link me to a guide that can show me?

---

### Post by MartyBuntu on 2011-01-23
Assuming that GRUB was actually installed to the removable USB drive, try accessing the BIOS by tapping F2...DELETE...(this depends on the computer/motherboard brand) and find the setting for boot order ie: CDROM first...USB first...hard disk first...

Set the USB HDD as first in the boot order.

---

### Post by GabrielYYZ on 2011-01-23
when you turn on your computer, press the delete key a couple times to enter the BIOS setup (it'll look like an ugly, low resolution big box, usually blue) in there, go to advance setup or something along those lines and look for "1st boot device", change that to your external HD, then save and exit.

edit: as MartyBuntu said, the key should be F2 or delete, it depends on the computer/mobo brand, i missed that.

---

### Post by Missing_Number on 2011-01-23
I tried that. I hit "ESC" on BIOS, it told me to "Select a Boot First device", I selected "Removable", and it said "no bootable device found". What do I do now?

EDIT: Tried GabrielYYZ's advice, didn't work.

---

### Post by MartyBuntu on 2011-01-23
> **Missing_Number said:**
> I tried that. I hit "ESC" on BIOS, it told me to "Select a Boot First device", I selected "Removable", and it said "no bootable device found". What do I do now?

Quite possibly GRUB was not installed.

Maybe someone here with more knowledge can assist you with installing GRUN using your live CD.

---

### Post by Missing_Number on 2011-01-23
> **MartyBuntu said:**
> Quite possibly GRUB was not installed.

Maybe someone here with more knowledge can assist you with installing GRUN using your live CD.

Anyone know how to do this?

---

### Post by Markn951 on 2011-01-23
As I do not know exactly how you ran your setup, I don't know which options, etc. you ticked, but I can tell you for certain that installing and running Ubuntu off of an external drive is completely possible (I'm doing it right this second :P) Honestly, I would recommend just wiping the hard drive and starting over. If you know what I'm doing at any point and know you can skip the step, go right ahead.

1) Boot into Windows. Plug in your drive after logging in, etc. and then go into Start -> Administrative Tools -> Computer Management. Go into Disk Management in the menus (should be on the left) and you should see a graphical representation of all your available logical drives. Right click on the one that is your external, and click delete. The graphical representation should now be grey and say something to the effect of Unallocated Space (no format, etc.).

2) Insert your Ubuntu Live/Install CD, reboot, start up from the CD. You did that the first time, right? I ask because if you can't boot from an external hard drive you may not be able to boot from CD. Anyways, just make sure your CD is in while the computer is starting up, and if it starts from the CD, great.

3) Go through the prompts of the installation until you get to the part where it says something to the effect of "Install Alongside the other OS, Replace the other OS, Manually Configure (Advanced)" or something like that. Check the Manual option and continue.

4) Now you'll be prompted with another graphical representation of your logical drives. Typically, you'll have your computer's HDD as SDA1 and then the external as SDA2, or your computer's HDDs as SDA1,2,3,etc. and the external as SDAn+1, where n is the number of HDDs you have inside your computer. Those might start at SDA0 instead of SDA1, I don't remember, can someone verify? Anyways, so you'll see your unallocated space on the external drive down at the bottom. What you want to do is click on the space (not the group title that represents the hard drive, the actual item underneath the header that represents the empty space) and then hit Add... . You'll be prompted with another window asking two things: the size of the new partition and the file system. The file system should be ext4, leave it as is. The size should be your drive's full capacity in Megabytes. Subtract, say, two to four thousand from that, and then continue. You'll now see that partition you just created in the graphical representation, as well as the remaining two to four GB of unallocated space. Go ahead and Add... that, and this time leave the size alone (it should be the full amount of leftover space, two to four gigs) and make sure the file system is swap. Continue, and the continue again.

What is it, 5?) You'll now be prompted about the bootloader location. Make sure this is on the external drive (SDA1 or SDAn+1 from the example in #4). Continue.

6) Now, you should be done with the hard part! Fill in your time zone, account info, etc. Just follow the prompts. Go make a sandwich, play a game, watch illicit material, whatever you need to do while waiting for everything to install and you're done, sort of!

7) Try rebooting the computer, leaving the external hard drive plugged in.

8) (Yes, Number Cool Face) ) If this does not work, load up BIOS as described above, make sure something like USB Hard Drive, External Hard Drive, something like that is selected as top or at least above Primary Hard Drive, Internal Hard Drive, etc. Reboot and try it.

9) If this does not work, come back here and ask again because you will need smarter, cooler, more attractive people than me to help you :p

Good luck my friend! :D

---

### Post by Missing_Number on 2011-01-23
I will try your advice. Thank you. I'll report back in a bit and explain what happened. If this doesn't work, we may need to send in Strong Bad (he's cool and attractive, right?) to help.

EDIT: Yes, I was able to get the disk to boot.

---

### Post by Missing_Number on 2011-01-23
I can't create more than one partition on the external drive simultaneously. 

Also, my drives aren't numbered SDA1, SDA2, etc., but SDA, SDB, with my external drive being SDC.

---

### Post by Markn951 on 2011-01-23
> **Missing_Number said:**
> [color=red]I can't create more than one partition on the external drive simultaneously.[/color]

[color=blue]Also, my drives aren't numbered SDA1, SDA2, etc., but SDA, SDB, with my external drive being SDC.[/color]

[color=red]Make sure you're not making the first partition the whole capacity of the drive. You want enough room left over for the swap partition. I suppose it's possible WD might have done something to restrict partitioning, but I don't know how that could be possible. I "built" my external out of a 2.5" internal drive and an external SATA-USB enclosure, so I don't know what kind of limitations manufacturers set on their drives.[/color]

[color=blue]That's fine, I did this process like two weeks ago so I'm just going off of what I remember.[/color]

---

### Post by Missing_Number on 2011-01-23
I couldn't figure out how to make two separate partitions, so I made the whole drive Ubuntu. Still didn't work. Using your new advice, I'll try it again with making a smaller partition and room for the "swap drive", whatever that is. Can you explain this?

---

### Post by Markn951 on 2011-01-23
> **Missing_Number said:**
> I couldn't figure out how to make two separate partitions, so I made the whole drive Ubuntu. Still didn't work. Using your new advice, I'll try it again with making a smaller partition and room for the "swap drive", whatever that is. Can you explain this?

Sure. Basically, the computer needs a section of hard drive space where it can store data temporarily, like RAM. It's called paging, you can read more about it [here](http://en.wikipedia.org/wiki/Paging). I don't know too much about the technical details, but I know it is used when RAM runs out of space.

---

### Post by MartyBuntu on 2011-01-23
> **Missing_Number said:**
> I couldn't figure out how to make two separate partitions, so I made the whole drive Ubuntu. Still didn't work. Using your new advice, I'll try it again with making a smaller partition and room for the "swap drive", whatever that is. Can you explain this?


Don't confuse yourself with partitioning schemes if you're not familiar with the procedure. Just go with the automatic full drive setup option. You can always shrink your partitions later if you need.

---

### Post by Markn951 on 2011-01-23
> **MartyBuntu said:**
> Don't confuse yourself with partitioning schemes if you're not familiar with the procedure. Just go with the automatic full drive setup option. You can always shrink your partitions later if you need.

My concern with that when I was going through the installation was "Is it going to know that I want to install it on the external drive and not clear the internal drive?".

---

### Post by MartyBuntu on 2011-01-23
The installer doesn't lie...

...and careful detail must be paid, but it's all there.

If this is a desktop, you could always yank the power on the main drive before the installation (while the computer is powered down, of course) if you really wanted to make sure nothing was installed there.

---

### Post by Missing_Number on 2011-01-23
MartyBuntu, I tried the "Install to all hard drive" thing and it still didn't work.

I now know how to make more than one partition. However, now when I select the partition and say "install now" it says "no root file system is defined. Please correct this from the partitioning menu.

---

### Post by MartyBuntu on 2011-01-23
Trust me. Try again with the full disk option and this time, use the advanced option to select where GRUB will be installed. Choose your USB drive.

---

### Post by Missing_Number on 2011-01-23
We need to actually solve the problem: for whatever reason, when I install Ubuntu on my hard drive, it's not bootable and I don't know why.

---

### Post by Missing_Number on 2011-01-23
"Trust me. Try again with the full disk option and this time, use the advanced option to select where GRUB will be installed. Choose your USB drive."

Sorry, didn't read your post before I made mine. My bad. How do you specify where to install GRUB to?

---

### Post by Markn951 on 2011-01-23
> **Missing_Number said:**
> MartyBuntu, I tried the "Install to all hard drive" thing and it still didn't work.

I now know how to make more than one partition. However, now when I select the partition and say "install now" it says "no root file system is defined. Please correct this from the partitioning menu.

I forgot that step, it should have asked you somewhere for root file system, I think its in the same window as Partition Size and File System, and you should just choose root (it's just a / option). You won't need to choose a root file system for the swap.

---

### Post by MartyBuntu on 2011-01-23
> **Missing_Number said:**
> 
Sorry, didn't read your post before I made mine. My bad. How do you specify where to install GRUB to?

It's been a while since I've installed from the regular CD, but near the end of the installation, there's an option (advanced) that you have to tick to unhide boot options. You can choose here where to have GRUB go.
This section of the installation process comes after main system files are loaded and installed.

---

### Post by Missing_Number on 2011-01-23
I have to specify the other partition as a swap point. How do I do it?

---

### Post by Markn951 on 2011-01-23
> **Missing_Number said:**
> I have to specify the other partition as a swap point. How do I do it?

Just as the tutorial said, make sure the "file system" is swap instead of ext4 on the second (two to four gig) partition.

I'd just like to note that everything MartyBuntu has said has been correct, you don't have to do it "my" way, you could very well do it "his" way, which seems easier, and it would most likely work just as well... "My" way is just the only way I've tried/know how to do, and I know it works, which is why I suggested it, but it may very well be not the easiest or most efficient way to go about things.

---

### Post by Missing_Number on 2011-01-23
> **MartyBuntu said:**
> It's been a while since I've installed from the regular CD, but near the end of the installation, there's an option (advanced) that you have to tick to unhide boot options. You can choose here where to have GRUB go.
This section of the installation process comes after main system files are loaded and installed.

I think that option was removed in the most recent installer.

---

### Post by Missing_Number on 2011-01-23
> **Markn951 said:**
> Just as the tutorial said, make sure the "file system" is swap instead of ext4 on the second (two to four gig) partition.

I'd just like to note that everything MartyBuntu has said has been correct, you don't have to do it "my" way, you could very well do it "his" way, which seems easier, and it would most likely work just as well... "My" way is just the only way I've tried/know how to do, and I know it works, which is why I suggested it, but it may very well be not the easiest or most efficient way to go about things.

Alright, trying it out, will report back soon. Thank you both for all of your help.

---

### Post by Missing_Number on 2011-01-23
Made the swap partition room, it still didn't fix anything.

What now? I still don't know how to set up GRUB?

---

### Post by Missing_Number on 2011-01-24
Bump

---

### Post by Markn951 on 2011-01-24
When you go into BIOS (not mashing Esc, that's a one-time boot menu. Try mashing F11 or F12 or F2) and go into your boot order, can you list off what the list actually is? What's in first position, second, third, etc.

---

### Post by Missing_Number on 2011-01-24
I'll try it later; I'm away from my PC.

---

### Post by ellgor on 2011-01-24
Hi,

Just some input I experienced, when I set up one of my USB's as an operating system and as such had a boot partiton, it wasn't recognised as a USB device by the bios instead it came under as a HDD, so in looking at these options I found it listed with the choice of booting priority, hope this helps.

Regards, Ellgor.

---

### Post by Missing_Number on 2011-01-24
Tried doing all that, still doesn't work.

Would the type of file system make a difference?

---

### Post by Missing_Number on 2011-01-24
Got it working. Thanks, everyone!

---

### Post by MartyBuntu on 2011-01-24
> **Missing_Number said:**
> Got it working. Thanks, everyone!

Would you mind sharing with everyone how you made this work?

---

### Post by Missing_Number on 2011-01-24
Not much really. I realized I made a mistake in the BIOS that set up which drive was read first. So your advice was correct and I did it wrong.

---

### Post by MartyBuntu on 2011-01-24
Hey, I'm just glad your on track again!

Good going!

---

