---
title: "Widows 7 &amp; Ubuntu 9.10 on Separate Partitions"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by viper3ez on 2010-01-17
i'm trying to run separte partitions so windows dont see ubuntu and vice versa.

during install, i did not pick the option to istall side by side and pick one at startup, i created partions manually but it still asks me to pick one at startup.

seems like Grub takes over the whole system and it has to be my primary bootloader. i do  not want that.

so is it possible to install both OS so that grub does not take over the whole system  and be the primary bootloader? i want grub to load ubuntu in its partition aand windows loader to load windows in its partition. is that possible?

why is grub so damn invasive anyways? cant uninstall it, cant delete it, cant bypass it and go str8 to windows b ootloader. it makes no sense to me that i have to boot grub and then grub boots windows bootloader  and windows bootloader boots windows. this grub business is putting me off ubuntu slowly.

end of rant.

help please

PS, in summary, i want both Os separate, i dont want grub in charge of my whole system in a way that when it fails(it has) i cant even access windows.

---

### Post by J V on 2010-01-17
Short version: Nope
Long version: Something has to be run when the computer starts up, the computer doesn't know which you want, so it automatically loads the "MBR"

The windows bootloader won't let you start ubuntu, but grub will let you start windows, the whole reason its there is so that you can choose which OS you want to boot...

You don't understand the way OSs work yet, grub will load windows directly, not grub > win MBR > windows

Its not like its some virtual machine running them, all grub does is tell the computer which to start up, then its done, it doesn't stay in memory, it doesn't crash your system when it "fails"

similarly, windows bootloader failing would also lock you out of your computer (only then it would be much harder to get back in)

If you just keep a live disc handy you can "fix" grub any time you want...

---

### Post by viper3ez on 2010-01-17
> **J V said:**
> Short version: Nope
Long version: Something has to be run when the computer starts up, the computer doesn't know which you want, so it automatically loads the "MBR"

The windows bootloader won't let you start ubuntu, but grub will let you start windows, the whole reason its there is so that you can choose which OS you want to boot...

You don't understand the way OSs work yet, grub will load windows directly, not grub > win MBR > windows

Its not like its some virtual machine running them, all grub does is tell the computer which to start up, then its done, it doesn't stay in memory, it doesn't crash your system when it "fails"

similarly, windows bootloader failing would also lock you out of your computer (only then it would be much harder to get back in)

If you just keep a live disc handy you can "fix" grub any time you want...

thanks, i do keep a live disc handy.

so why does it show me windows 7 loader as the option on the OS list when grub starts instead of just windows 7?

now i have to figure out how to create a home partition for both OS to share. ugh

---

### Post by J V on 2010-01-17
Well mabey its just the name, mabey it is actually starting up the loader (because windows refuses to start with non microsoft bootloaders)

The point is, when the bootloaders are done, they stop existing, they tell the computer to "actually" *boot* from the OS itsself...

Sharing stuff is easy... windows won't open linux partitions, but linux can open windows partitions...

All you do is make shortcuts from the windows folders (My documents etc) and put them in your home (as "Documents") then all apps that save it to your home/Documents will actually be saving it to the other partition.

Enjoy :)

---

### Post by ajgreeny on 2010-01-17
> so why does it show me windows 7 loader as the option on the OS list when grub starts instead of just windows 7?What exactly do you mean by this?  Normally when windows starts you do not actually see the windows bootloader or MBR as it all just happens and windows starts to boot.  You seem to suggest that grub takes you to another screen where you have to make a choice, which seems unlikely to me.  I think like JV that you are not understanding how grub and the boot process works.

If you have two OSs installed, there has to be some way of chosing between them at boot time, you can not run windows and then choose to run ubuntu from within that unless you use a virtual machine system, such as VirtualBox, but that is not a dual boot system at all.

If you want windows to start automatically that can be arranged easily, but you can not have that happen and still be able to boot ubuntu if you wish to some times without the grub system to do it for you.  You can hide the grub menu if you want to, and only show it if you press a key at boot (which key depends on grub version), but you can't choose from both OSs without grub to allow you to do so.

Finally, you can not share a full /home partition between windows and ubuntu because the ubuntu home can not be on any of the windows file systems; they do not allow for linux permissions which are essential for a working /home partition.  You can, however, use a shared /data partition for your docs, music, videos, photos, etc etc, which can be fat32 or preferably ntfs.  That can then be mounted at boot and given read/write permissions in ubuntu using ntfs-config installed from the repos.

EDIT:
I have just thought about this a bit more.  If you have two disks, not partitions but separate hard disks, you can do what you want, less conveniently perhaps, depending on your system.  Some machines show a key to press to change the boot order, eg F2, and if so you can put grub on the second disk, by hitting Advanced at the appropriate point of the ubuntu install, and choosing sdb, instead of sda.  I am pretty certain this is only possible with separate discreet hard disks, not partitions on a single disk, which I presume is your position.  Then when you boot you just choose Disk 1 or Disk 2 and you get the OS on that disk.  I do not really see how that is any better than grub doing it for you.

---

### Post by J V on 2010-01-17
I understand how it works... The problem is that with vista + its listed on grub as "Windows Vista loader (/dev/hda1)"

And you *can* use symlinks to share data (its stored on the NTFS anyway so both OS can access)

---

### Post by Mark Phelps on 2010-01-17
The "best" solution (in my experience) is to install the two different OSs on two different drives, and boot from the Ubuntu drive -- since its GRUB will find Windows and add the necessary entries.

As to sharing the same home partition, I will enhance the previous advice -  DO NOT DO IT!  Links aside, it's a bad idea.  Windows doesn't understand Linux permissions, and trying to do this is likely to end up with filesystem corruption.

---

### Post by viper3ez on 2010-01-18
> **J V said:**
> I understand how it works... The problem is that with vista + its listed on grub as "Windows Vista loader (/dev/hda1)"

And you *can* use symlinks to share data (its stored on the NTFS anyway so both OS can access)


correct. its listed as Windows 7 loader on my system. and from what i can see, windows 7 saves its loader on a 100mb seperate partition during installation. hence i was wondering why grub is accessing that system reserved 100mb partition of windows 7 loader when it could just go and load windows 7 from its partition. at least thats how it worked wen i had ubunto 9.04 with vista ... i think.

as far as runing them seperately, my question has kinda been answered. i ppretty much was trying to know if 2 seperate partitions could be treated like 2 seperate drives but the answer is no from ajgreeny's reply.

now about the shared data space, i have a 3rd partition on my drive and from what i've read NTFS is best but i still dont know how i would be able to point both OS to that partition to save files especially cos windows usually does not see my other partitions but ubuntu does. its windows i'm mostly worried about cos with ubuntu, i can even read and write to my windows partion folders.

i'm wanting to do sepaarate so i can reinstall both OS anytime i want without losing my files cos its a PITA downloading a 10gb torrent over and over again

---

### Post by viper3ez on 2010-01-18
> **Mark Phelps said:**
> The "best" solution (in my experience) is to install the two different OSs on two different drives, and boot from the Ubuntu drive -- since its GRUB will find Windows and add the necessary entries.

As to sharing the same home partition, I will enhance the previous advice -  DO NOT DO IT!  Links aside, it's a bad idea.  Windows doesn't understand Linux permissions, and trying to do this is likely to end up with filesystem corruption.

ook, maybe i should not have used "home"

i have space for a 3rd partition and i want to save all my files from both OS to thaat 3rd partition so i dont lose them whenever i reinstall either OS. is that a bad idea also?

and as far as seperate partitions, i'm getting a 32gb USB drive and i'm going to install ubuntu on that and leave my hard drive for windows  to crash as many times as it wants

---

### Post by OrangeCrate on 2010-01-18
> **viper3ez said:**
> i'm trying to run separte partitions so windows dont see ubuntu and vice versa.

during install, i did not pick the option to istall side by side and pick one at startup, i created partions manually but it still asks me to pick one at startup.

seems like Grub takes over the whole system and it has to be my primary bootloader. i do  not want that.

so is it possible to install both OS so that grub does not take over the whole system  and be the primary bootloader? i want grub to load ubuntu in its partition aand windows loader to load windows in its partition. is that possible?

Edit:

Though Grub will control the operating systems, you can choose which boots first by either manually editing the Grub menu, or by installing the "startupmanager" package from Synaptic, and making your choice there. 

why is grub so damn invasive anyways? cant uninstall it, cant delete it, cant bypass it and go str8 to windows b ootloader. it makes no sense to me that i have to boot grub and then grub boots windows bootloader  and windows bootloader boots windows. this grub business is putting me off ubuntu slowly.

end of rant.

**help please**

PS, in summary, i want both Os separate, i dont want grub in charge of my whole system in a way that when it fails(it has) i cant even access windows.

This should help...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

They are the instructions I used when I set up my dual boot with Windows 7.

(The instructions mention Vista, but since Windows 7 is just a re-skinned version of Vista, they work just fine.)

Edit:

Grub will control the operating systems, but you can change the boot order either by manually editing the file, or (much easier IMO), by installing the "startupmanager" package from Synaptic, and controlling which one boots first from there. (That's what I do.)

---

