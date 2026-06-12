---
title: "Non bootable boot disk"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by WU8V on 2009-01-21
I have been wanting to try to escape from Micro$haft for a few years, and finally have an older box that I can try experimenting without tampering with my current machine.

I downloaded and burned a CD of Ubuntu, and made sure that it would boot on my current machine. Fine. I then tried to boot the raw machine (120 Gb unformated drive) with the CD, No joy, no boot device found. I assured myself that the CD was first in the boot order (it was) and that it would boot from another (windows ugh) disk that I had recently burned. it did. but the new/old machine will not boot the ubuntu disk from the CD.

Is there something that I am missing?

Thanks for any advice that you can give.
regards,
Kurt

---

### Post by emarkd on 2009-01-21
So if I understand, your computer will boot from a Windows CD, but not from the Ubuntu CD you burned, correct?  If that's the case, there may be errors on the disk.  Try burning another copy at a slower rate, like 2 or 4x.  Also, use the 'compare burned data' feature of your burner software if it has it.

---

### Post by mrbiggbrain on 2009-01-21
windows disk = CD-ROM
Ubuntu DIsk = (possibly) DVD-/+R

is this correct?

---

### Post by Vaedrah on 2009-01-22
I have encountered the same behavior on a number of occasions. I had an older notebook that I reformatted completely. Ubuntu would not install (no operating system error message etc).

The notebook's installation disks also failed (but then notebook recovery disks seem to only recover from minor fault problems.)

I installed XP from a standard PC CD and this went OK.

Then I installed Ubuntu over this XP OS and then this worked OK. I can only guess that Ubuntu assumes some remnant of windows is on the new disk. But then again, that's only my guess.

I checked the hard disk using windows and it didn't show any errors. :D

---

### Post by WU8V on 2009-01-22
I do not want ANY microsoft on the Ubuntu machine. The new/old machine has a Hard drive that is new out of the box. no data, no partition.

I burned both the windows CD and the Ubuntu CD on the same drive and I have checked the Ubuntu CD with its error checker on my current machine.

The new/old machine WILL boot from a windows botable CD that I rcently created with the same drive that I created the Ubuntu CD.

Vaedrah, I am not sure what you are getting at... are you saying that I should partition and format and install XP, then install Ubuntu over that?

As I said, I am trying to get completely away from Micro$haft.

This is an experimental machine, and I can pretty much do whatever I want with it... (no data to lose) so I am up to try most anything except windows. Do I need a bigger hammer for this thing?

Machine details...500Mhz P3 120Gb IDE IDE CD reader (not sure of speed 256 MB ram It's an old Dell manchine.

Thanks guys....

---

### Post by spcwingo on 2009-01-22
Have you tried the alternate (text-based) install disc?  I have found that some machines just will not boot from the standard live disc.  Give it a shot and let us know if it works or not.  You can download it here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Vaedrah on 2009-01-22
Yes WU8V. A pragmatic approach would be to install XP then install Ubuntu on top. This will remove windows to all intents and purposes - assuming this does work it is just a means to an end.

Again, I have had the same experiences; once Ubuntu is installed you never need the XP CD for any other reinstalls. I don't understand the technical reasons so I can only report personal experience. Good luck!


p.s. It might pay to check that your CD actually has a single *.iso file. Windows may break this iso file into separate files - the CD won't then boot!. You can use a small windows s/w file ir045_unicode.exe to make the iso copy. Ubuntu will direct copy iso files as standard but Windows copy to CD usually fails to make a bootable disk - it may work well for XP copy but not for "iso" files.

---

### Post by bumanie on 2009-01-22
Are you sure you burned the ubuntu .iso as an image - it won't work if burned as a data disc. It is a common mistake that people make. If so, try the alternate cd, it is text-based and often installs when the live cd won't.

---

### Post by Nero147 on 2009-01-22
another option would be to partition it first with something like gparted. It's pretty user friendly and has a nice interface. I've had stuff like that happen to me before and quite often just having a partition to delete fixed it. 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Hope that helps.

---

### Post by WU8V on 2009-01-22
I have made a bit of progress...bad kind... I found that I have only 128M of "good" memory, so I am now in the middle of burning a copy of the alternate installation in the hopes that I can avoid cluttering up the system with windoze. If that fails, I will try the partition program, and as a last resort put Windoze on the thing and try it that way.

Thanks again for all of your advice, I will let you know how it goes...probably tomorrow if this takes too much longer...

Best regards,
Kurt

---

### Post by blackmail on 2009-01-22
Also please try to set your bios to fail safe settings, if it has such an option, some times there are options that are not suitable for a boot cd or another, and please try to boot the cd at a friend that has a machine that is somewhat similar to your test "subject" .
To be onest i had the same problem on my machine just that in mycase it was frustrating cuz some times it would boot and some times it would not boot whereas XP was working just fine.
And do try a text based install disk cuz maybe your machine does not support a newer version on bootable disk...hence XP is around since 2000 or so, and ubuntu 8.04 or 8.10 since a feew months

---

### Post by bumanie on 2009-01-22
That that amount of ram, you will need to install the alternate xubuntu cd - ubuntu won't work with that amount of ram, but xubuntu should  - just. You may have to look at puppy linux or damn small linux. Alternatively you could look at a light window manager such as fluxbox. You may have to do a bit of searching.

---

### Post by WU8V on 2009-01-22
Thanks everyone who helped this poor evil machine gain a new life....The problems that I encountered....
1) bad CD burn of both the desktop and alternate
2) memory going flakey (the machine, mine has been gon a long time)
3) flakey CD reader in the new.old machine

After clearing all those up... Shazam! Evil has a new life as a Ubuntu machine.

I still have more questions, but I will post a new thread, because with all your help, this one is put to bed.

Thanks again and regards,
Kurt

---

