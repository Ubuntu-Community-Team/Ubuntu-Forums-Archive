---
title: "Is it possible to use an ISO file without burning it to a disk?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by camn on 2010-05-08
I kinda want to (totally legally) install and dual boot Windows 7 (because it was my idea!) alongside Ubuntu 10.04 but I don't have any blank disks to burn the Windows 7 ISO to, I already tried the ISO in Sun VirtualBox and it works... Help... please?

---

### Post by marshmallow1304 on 2010-05-08
[Here you are]("http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/").  No guarantees, but it looks like it should work.

Edit: From the comments, it looks as if you'll need to format the USB drive to NTFS first.

---

### Post by camn on 2010-05-08
> **marshmallow1304 said:**
> [Here you are]("http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/").  No guarantees, but it looks like it should work.

Edit: From the comments, it looks as if you'll need to format the USB drive to NTFS first.
The biggest USB drive I have is 2GB ._. I need a way without any external storage device...

---

### Post by Chiapo on 2010-05-08
I would just run the Win 7 ISO in VirtualBox.
Less malware worries.

Or get a bigger USB drive.

---

### Post by camn on 2010-05-08
> **Chiapo said:**
> I would install the ubuntu distro to hdd, then run the Win 7 ISO in VirtualBox.
That's what I did... But it's kinda slow and the internet doesn't always work...

---

### Post by CharlesA on 2010-05-08
> **camn said:**
> That's what I did... But it's kinda slow and the internet doesn't always work...

Get a bigger USB drive then. a 4GB one should work fine.

---

### Post by camn on 2010-05-08
> **CharlesA said:**
> Get a bigger USB drive then. a 4GB one should work fine.
I have no money... just 20 CAD... Which is no use in the USA... This is all I'm asking, is there a way to use ISO images without burning them to disks? ._.

---

### Post by I8NY on 2010-05-09
if you got windows 7 then they gave you a dvd to install off of.  the only reason why some one would use a iso is to install it on a netbook w/out a dvd drive or to pirate windows.  Plus i don't think there is away to do it without burning a dvd.

---

### Post by camn on 2010-05-09
> **I8NY said:**
> if you got windows 7 then they gave you a dvd to install off of.  the only reason why some one would use a iso is to install it on a netbook w/out a dvd drive or to pirate windows.  Plus i don't think there is away to do it without burning a dvd.
That's the point... It's damn expensive and the only way I could get it was "legally" from a torrent :P

---

### Post by zeekoman on 2010-05-09
What about Wubi? 
[I]"Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!"
[/I][URL="http://wubi-installer.org/"]
http://wubi-installer.org/[/URL]

---

### Post by camn on 2010-05-09
> **zeekoman said:**
> What about Wubi? 
[I]"Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!"
[/I][URL="http://wubi-installer.org/"]
http://wubi-installer.org/[/URL]
I'm running Ubuntu 10.04 now, I need to install Windows 7 for school stuff...

---

### Post by I8NY on 2010-05-09
well Wine can get some windows apps to run in linux and openoffice will read and edit .doc files

---

### Post by camn on 2010-05-09
> **I8NY said:**
> well Wine can get some windows apps to run in linux and openoffice will read and edit .doc files
Wine isn't working right... I need google sketchup, and when I run it it just closes...

---

### Post by I8NY on 2010-05-09
well Blender 3D will do pro 3d modeling and it supports many 3d format files.  google usaly makes linux version of it's apps but not sketchup.  well i bet a friend could give a blank dvd to use, i'm out of ideas. :(

---

### Post by camn on 2010-05-09
> **I8NY said:**
> well Blender 3D will do pro 3d modeling and it supports many 3d format files.  google usaly makes linux version of it's apps but not sketchup.  well i bet a friend could give a blank dvd to use, i'm out of ideas. :(
Haha, it's ok... and Blender was very confusing to use :3

---

### Post by theneoindian on 2010-05-09
Hi there , 

You can try installing windows to a harddrive partition from within Vmware (similar to virtualbox). You just have to select a physical partition in the custom creation of the virtual machine . I don't know if such an option is available with virtualbox. 

If it isn't available in virtualbox , i recommend installing vmware . You could try obtaining vmware "legally" from a torrent :popcorn: as u did with windows 7 .

---

### Post by camn on 2010-05-09
> **theneoindian said:**
> Hi there , 

You can try installing windows to a harddrive partition from within Vmware (similar to virtualbox). You just have to select a physical partition in the custom creation of the virtual machine . I don't know if such an option is available with virtualbox. 

If it isn't available in virtualbox , i recommend installing vmware . You could try obtaining vmware "legally" from a torrent :popcorn: as u did with windows 7 .
I already have Windows 7 on VirtualBox, I just want a full install so I can print stuff...

---

### Post by camn on 2010-05-09
GASP! I found a blank disk in my house! But it doesn't have enough memory... Is there any way to like, transfer memory from a USB stick to a CD or something like that?

---

### Post by freeze10108 on 2010-05-09
^I don't think that it's possible to split an iso like that.

---

In theory, I think that if you were to extract the iso to a new partition and boot from it, you could boot into the Windows 7 installer.  You'd probably need to create an NTFS partition beforehand so that Windows would have a partition to install to.  After installation, you'd need to delete the partition that contained the iso files and expand the Windows partition.

However, as with many things, what seems good in theory will be riddled with intricacies and possible errors everywhere down the line.  This is, however, a risk you run when using "legal" methods to obtain files.  ;)

---

### Post by camn on 2010-05-09
> **freeze10108 said:**
> ^I don't think that it's possible to split an iso like that.

---

In theory, I think that if you were to extract the iso to a new partition and boot from it, you could boot into the Windows 7 installer.  You'd probably need to create an NTFS partition beforehand so that Windows would have a partition to install to.  After installation, you'd need to delete the partition that contained the iso files and expand the Windows partition.

However, as with many things, what seems good in theory will be riddled with intricacies and possible errors everywhere down the line.  This is, however, a risk you run when using "legal" methods to obtain files.  ;)
Not really splitting the ISO, just transferring memory from a USB stick to a CD... So say the USB stick has 2 GB of memory... and the disk has 1 GB... Would it be possible to transfer the 2 GB of memory from the USB stick to the disk making it have 3 GB of memory?
But I shall try doing what you said...

---

### Post by theneoindian on 2010-05-09
> **camn said:**
> I already have Windows 7 on VirtualBox, I just want a full install so I can print stuff...

Yeah , dats what i'm talking about . YOu can do a full install of windows via Vmware in your linux . That is , when u install windows within vmware in  linux host , You can choose to install it in a real physical partition instead of a creating a virtual disk . So , it will install it in a real partition on your hard disk . 

I suppose that after install , you can edit the grub files and boot to windows directly . If you do this , please do it with caution . i hope u get the point .

---

### Post by camn on 2010-05-09
> **theneoindian said:**
> Yeah , dats what i'm talking about . YOu can do a full install of windows via Vmware in your linux . That is , when u install windows within vmware in  linux host , You can choose to install it in a real physical partition instead of a creating a virtual disk . So , it will install it in a real partition on your hard disk . 

I suppose that after install , you can edit the grub files and boot to windows directly . If you do this , please do it with caution . i hope u get the point .
Ohh... vairy fancy :P And I tried installing VMware first but I couldn't figure it out... I ended up loosing the registration key and forgetting which e-mail I used... so too much work :P

---

### Post by freeze10108 on 2010-05-09
> **camn said:**
> Not really splitting the ISO, just transferring memory from a USB stick to a CD... So say the USB stick has 2 GB of memory... and the disk has 1 GB... Would it be possible to transfer the 2 GB of memory from the USB stick to the disk making it have 3 GB of memory?
But I shall try doing what you said...

If I understand what you're saying correctly, no you can't transfer memory from a USB drive to a CD.  Also, the procedure I described may not work at all, and may mess up your system as well; proceed at your own peril... ;)

---

### Post by camn on 2010-05-09
> **freeze10108 said:**
> ^I don't think that it's possible to split an iso like that.

---

In theory, I think that if you were to extract the iso to a new partition and boot from it, you could boot into the Windows 7 installer.  You'd probably need to create an NTFS partition beforehand so that Windows would have a partition to install to.  After installation, you'd need to delete the partition that contained the iso files and expand the Windows partition.

However, as with many things, what seems good in theory will be riddled with intricacies and possible errors everywhere down the line.  This is, however, a risk you run when using "legal" methods to obtain files.  ;)
Ok, sorry... I'm a very-much-noob to Ubuntu, how would I partition the HD? And I'm not concerned about errors that much.. I could just re-install ubuntu...

---

### Post by freeze10108 on 2010-05-09
> **camn said:**
> Ok, sorry... I'm a very-much-noob to Ubuntu, how would I partition the HD? And I'm not concerned about errors that much.. I could just re-install ubuntu...

I haven't had to use the partition editor out of the installations for a while now, but if memory serves: booting from the LiveCD, go to System -> Administration -> Partition Editor.  From there, you'll have to fiddle around with the partitions, which I found fairly intuitive the first time I did it, and make sure you don't set your Ubuntu partition to be formatted, or you'll lose all your data.

I'll boot into my LiveCD right now to check the location of the program...

---

### Post by camn on 2010-05-09
> **freeze10108 said:**
> I haven't had to use the partition editor out of the installations for a while now, but if memory serves: booting from the LiveCD, go to System -> Administration -> Partition Editor.  From there, you'll have to fiddle around with the partitions, which I found fairly intuitive the first time I did it, and make sure you don't set your Ubuntu partition to be formatted, or you'll lose all your data.

I'll boot into my LiveCD right now to check the location of the program...
Oh, I have the partition editor up now... I just have no ****ing idea how to use it :3 EDIT: Oh... That's the disk utility... If that's the same thing ._.

---

### Post by freeze10108 on 2010-05-09
Okay, i just checked my LiveCD, and it's: System -> Administration -> GParted, which is not tbe same as Disk Utility. The program's not included with the initial install, so you will need to use the LiveCD to start the program.

---

### Post by camn on 2010-05-09
> **freeze10108 said:**
> Okay, i just checked my LiveCD, and it's: System -> Administration -> GParted, which is not tbe same as Disk Utility. The program's not included with the initial install, so you will need to use the LiveCD to start the program.
LiveCD? ._.

---

### Post by aysiu on 2010-05-09
Closed for review.

---

