---
title: "Make a new partition for windows without reinstalling ubuntu?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Max Williams on 2009-07-26
hey all

I have a laptop with a 70gb HD, which currently has ubuntu 8.04 on it.  I need to take 20gb for a new partition, into which i want to install windows, so the laptop will be a dual boot.  Can i do this without affecting my current install of ubuntu?  

When i installed ubuntu i had windows already, and ubuntu offered me the option of keeping the existing windows install and basically taking some of the hard disk space for a new ubuntu partition.  So i guess what i need to do now is the reverse of that.

Can anyone point me at some instructions or give me some guidance?  I have the windows install disk already, obviously.

thanks
max

---

### Post by milton1 on 2009-07-26
Use the live cd or parted magic live to resize your ubuntu partition. then you can install windows on the new open space. Once windows is installed, you will need to use the live cd to reinstall grub; the windows installer will break your boot loader. There are many guides on this forum for reinstalling grub.

---

### Post by Liolikas on 2009-07-26
Windows will nuke your Ubuntu more or less.

You have to install and use gparted and create partition ntfs type.
Also remember partition size and be sure it is not something like 100Gb and 100Gb.
Also get ready Ubuntu liveCD.
Then install Windows into that ntfs partition it will nuke GRUB, be sure DO NOT format other partitions windows install may suggest this.
Then be sure windows work and boot into Ubuntu liveCD.
Do not start Ubuntu install just install GRUB. More info howto:
 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Basically just install-grub command.

---

### Post by Michael.Godawski on 2009-07-26
I like this guide for dual-booting linux and vista (linux installed first):

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[/LIST]
It explains pretty much every step. If questions arise do ask, and make a back up of your important data first in case something might go wrong.

---

### Post by Max Williams on 2009-07-26
> **Michael.Godawski said:**
> I like this guide for dual-booting linux and vista (linux installed first):

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[/LIST]
It explains pretty much every step. If questions arise do ask, and make a back up of your important data first in case something might go wrong.

Thanks michael, i'm looking at that right now.

It and other replies refer to the Ubuntu Live CD.  Looking on the ubuntu site, this is for ubuntu 9.04.  I have 8.04 installed, will i still be able to use the cd?  I already tried putting my 8.04 installer disk in and booting with that, but it didn't give me any partitioning options - just the option to install ubuntu.

thanks
max

---

### Post by Michael.Godawski on 2009-07-26
You have to choose the "Try Ubuntu..." option and go into the Live Mode, so running Ubuntu from the CD /DVD completely. 

There you will have the Partition Editor under System > Administration I guess.

---

### Post by Max Williams on 2009-07-26
> **Michael.Godawski said:**
> You have to choose the "Try Ubuntu..." option and go into the Live Mode, so running Ubuntu from the CD /DVD completely. 

There you will have the Partition Editor under System > Administration I guess.

Thanks -i used the partition manager which i downloaded on a seperate cd in the end.  So, i have my new 20 gig ntfs partition for xp, and a 4 gig fat32 partition for swapping files between windows and ubuntu.  About to install windows now....may be back if it all goes horribly wrong :)

cheers
max

---

### Post by Max Williams on 2009-07-26
> **Max Williams said:**
> Thanks -i used the partition manager which i downloaded on a seperate cd in the end.  So, i have my new 20 gig ntfs partition for xp, and a 4 gig fat32 partition for swapping files between windows and ubuntu.  About to install windows now....may be back if it all goes horribly wrong :)

cheers
max

as i feared, it's gone horribly wrong...after a load of mucking around i managed to get windows installed, now i'm trying to get back into ubuntu.  i've tried the 8.04 and 9.04 install disks and can't work out how to get to the console in my linux partition so i can start sorting the grub stuff out.  kinda lost and tired and desperate :(

---

### Post by Max Williams on 2009-07-26
> **Max Williams said:**
> as i feared, it's gone horribly wrong...after a load of mucking around i managed to get windows installed, now i'm trying to get back into ubuntu.  i've tried the 8.04 and 9.04 install disks and can't work out how to get to the console in my linux partition so i can start sorting the grub stuff out.  kinda lost and tired and desperate :(

panic over, i worked it out, all good now thanks to this post 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

:)  tfft, i have to get up and go to work in 6 hours and i need my ubuntu partition back in order to do that.  i have it now, relieved.  thanks, everyone, for your help.

max

---

### Post by Max Williams on 2009-07-27
Actually i have one more question - since doing the grub setup stuff ("setup (hd0)"), when i boot it goes straight into windows - i'd like to have a choice, with it going to ubuntu by default (eg after 10 seconds or something). 

Does hd0 refer to my primary partition (which is the one with ubuntu)?  If so then i guess i need to do setup(hd1), or setup(hd0,1) or something?  Don't want to just start randomly doing stuff though.

thanks 
max

---

