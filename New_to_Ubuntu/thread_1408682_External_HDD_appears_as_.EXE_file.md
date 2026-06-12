---
title: "External HDD appears as .EXE file"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2010-02-16
Hi all,

Just bought myself a nice shiny new 1TB HDD only to find it doesn't work with Ubuntu, it pops up as a .EXE file. It did actually say on the box that it's only compatible with Windoze and Mac, but didn't think anything of it since my 400GB said the same thing yet worked fine. As with my printer, camera, and mouse.

Moving on, I thought perhaps I need to set it up first in windoze, so rebooted, logged into windoze and there was nothing to setup, instantly recognised. So I rebooted again, logged back into Ubuntu, checked my desktop and the drive is still appearing as .EXE.

Right clicking the file gives an option to format the drive as compatible with all systems (fat) or Encrypted compatible with Linux (fat). I want to know if I should format it and if so, which option to choose, or, am I better to take it back to the shop and find a different one, such as a USB portable HDD? 

Thanks in advance all.

---

### Post by Silver40mm on 2010-02-16
How does it "pop up" as an .EXE file? When you plug in your hard drive, what exactly happens?

---

### Post by tom.swartz07 on 2010-02-16
> **T4K3Z0U said:**
> Hi all,

Just bought myself a nice shiny new 1TB HDD only to find it doesn't work with Ubuntu, it pops up as a .EXE file. It did actually say on the box that it's only compatible with Windoze and Mac, but didn't think anything of it since my 400GB said the same thing yet worked fine. As with my printer, camera, and mouse.

Moving on, I thought perhaps I need to set it up first in windoze, so rebooted, logged into windoze and there was nothing to setup, instantly recognised. So I rebooted again, logged back into Ubuntu, checked my desktop and the drive is still appearing as .EXE.

Right clicking the file gives an option to format the drive as compatible with all systems (fat) or Encrypted compatible with Linux (fat). I want to know if I should format it and if so, which option to choose, or, am I better to take it back to the shop and find a different one, such as a USB portable HDD? 

Thanks in advance all.

Well, since you just purchased it, im sure its fine to just reformat it. Use a program such as gParted to take care of it, but be careful- if you select the wrong drive you could blow away your internal drive by accident. 


Also, Check the manufacturers site to see if there are firmware updates. I saw a few with problems in the past days that got them cleared up by doing so.

---

### Post by T4K3Z0U on 2010-02-16
> **Silver40mm said:**
> How does it "pop up" as an .EXE file? When you plug in your hard drive, what exactly happens?

When I plug it in, there is like a little file icon with wee squiggles to represent text. When I click on it there is .EXE inside. 

I include screenshot, of how the file looks on desktop, and how it looks when I click it.

---

### Post by T4K3Z0U on 2010-02-16
> **tom.swartz07 said:**
> Well, since you just purchased it, im sure its fine to just reformat it. Use a program such as gParted to take care of it, but be careful- if you select the wrong drive you could blow away your internal drive by accident. 


Also, Check the manufacturers site to see if there are firmware updates. I saw a few with problems in the past days that got them cleared up by doing so.

I was thinking if formatting also don't work, it may void any warranty.

---

### Post by Silver40mm on 2010-02-16
> **T4K3Z0U said:**
> I was thinking if formatting also don't work, it may void any warranty.

Are you sure that the screen you showed wasn't just the contents of the drive? 

And formatting the drive will NOT void the warranty.

---

### Post by HarrisonNapper on 2010-02-16
Agreed, it shouldn't void the warranty, but you could read the warranty if you really wanted to do so. Also, most external HDDs have nice little compression programs and things like that in them. That may just be a file on the HDD appearing on your desktop. Open up Konqueror (jk, Nautilus if you must) and click on the external HDD on the left.

---

### Post by T4K3Z0U on 2010-02-16
> **Silver40mm said:**
> Are you sure that the screen you showed wasn't just the contents of the drive? 

Oh, good question, I am not sure. I made the assumption since the icon is not a little silver box with the USB symbol like my other HDD and smaller portable USB HDDs, and because inside has the folders and .EXE stuff. It looked to me to be some sort of windoze installation software. 

I wonder if formatting it would get me the little USB icon. So which of the 2 format options would be best?

---

### Post by Silver40mm on 2010-02-16
Try deleting the .ico file. Ubuntu might be trying to display that as the icon whenever you plug it in. I think everything is working the way it should be. (besides the icon :D)

---

### Post by T4K3Z0U on 2010-02-16
> **Silver40mm said:**
> Try deleting the .ico file. Ubuntu might be trying to display that as the icon whenever you plug it in. I think everything is working the way it should be. (besides the icon :D)

OK sounds good. I will try sending a file or 2 to that drive and see what happens. Sending the .ico file to trash didn't help. Oh well it happens. Perhaps after a reboot it might change, will let you know next time I reboot.

Thanks all.

---

### Post by T4K3Z0U on 2010-02-16
> **T4K3Z0U said:**
> Sending the .ico file to trash didn't help.

But sending the Autorun.inf file to trash did work. I noticed the text on that file said "[auto icon= open=" So figured deleting that might work, and it did, now I have the right icon.

I do feel a little stupid that I didn't realize it was my drive. Transferring a file worked also.

Thanks again.

---

### Post by Methuselah on 2010-02-16
There are some new weirdo technologies like [http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)
These actually include .exes that expect windows.
Not sure if that's the case here but it could be something similar.

---

### Post by zeroseven0183 on 2010-02-16
I assume you have a Buffalo hard drive. The DriveNavi.exe and the autorun.inf are legitimate files that will run on Windows as soon as you plug it (except if you disabled autorun external media in registry). DriveNavi is a utility software, that is.

So as long as you are able to copy, paste, delete files from it and to it then there's no need to worry.

By default, your hard drive is formatted as FAT32 but you have the option to reformat it to NTFS or XFS  or whatever file system you prefer. But be sure to backup everything before wiping off the hard drive's content. And remember that if you format it to other than FAT32 and NTFS, you will not able to open it on Windows.

---

### Post by T4K3Z0U on 2010-02-16
> **zeroseven0183 said:**
> I assume you have a Buffalo hard drive. 

You assume correct, it is Buffalo.

---

### Post by tom.swartz07 on 2010-02-17
> **T4K3Z0U said:**
> You assume correct, it is Buffalo.

Great- so as you could see, the 'crapware' that was included on the drive was just simply making things muddled. 

You could definitely format your drive to another filesystem for convenience if you so wish (it would also get rid of the stuff that was on there to begin with). 

Just please note: 

If you plan to only use the drive for Linux systems, you should use ext or FAT, both are less prone to file fragmentation. EXT is only recognized by Linux systems, and certain FAT formats have a file size limit of 4gb. 

If youre using it on both Windows and Ubuntu, Use FAT32 or NTFS. This will allow you to see the files on either OS, at the expense of having fragmentation problems. 


Hope this helps!

---

### Post by mastablasta on 2010-02-17
also fat has a limit on partition (i think arround 130 GB), so with 1 Tb you will need about 4 or 5 partitions made. also if it's FAT32 and you are changing it into ntfs it will be painless. if partitions stay the same you don't overwrite/destroy the data that is on disk. you can't change as easy form NTFS to fat32 though.
 
Some drives have soem software "preinstalled" (for windows i think). My WD has some backup system, so that it basically automatically backs up the systems and data. it got removed (i.e. copied someowhere else) after first hour of disk use and disk got reformatted.

---

### Post by zeroseven0183 on 2010-02-17
> **tom.swartz07 said:**
> the 'crapware' 

So that's how it's called. Haha! :D

---

### Post by tom.swartz07 on 2010-02-17
> **zeroseven0183 said:**
> So that's how it's called. Haha! :D

HAHA! yep! More specifically, the programs on the drive are called 'craplets' 
[http://en.wikipedia.org/wiki/Crapware](http://en.wikipedia.org/wiki/Crapware)
:popcorn:

Anyway- to the OP, Just so that you are aware- the programs installed on the drive are not needed in any way, nor is the original filesystem. The only difference between your external drive and a full-fledged internal is that yours comes with a filesystem and files pre-registered on it.

---

### Post by mcduck on 2010-02-17
> **mastablasta said:**
> also fat has a limit on partition (i think arround 130 GB), so with 1 Tb you will need about 4 or 5 partitions made. also if it's FAT32 and you are changing it into ntfs it will be painless. if partitions stay the same you don't overwrite/destroy the data that is on disk. you can't change as easy form NTFS to fat32 though.
 
Some drives have soem software "preinstalled" (for windows i think). My WD has some backup system, so that it basically automatically backs up the systems and data. it got removed (i.e. copied someowhere else) after first hour of disk use and disk got reformatted.

Axctually FAT32 can handle much larger partiutions than that, it's just that Microsoft has decided to limit the size f FAT partitions they allow you to make in Windows VIsta or later.

As long as you format the partition Linux or OSX (or with some third-party software on Windows) you can use the full supported partition size of 2TB (or 8TB if you use 32bit clusters, but that would waste a lot of disk space).

So the only really important limitations with FAT are the 4GB file size limit, and lack of support for file/directory permissions as they are used on Linux.

Still, it's pretty easy to come up with stuff that needs larger than 4GB files, and FAT isn't realy that great fielsystem inany other way either. USe it if you ened to be able to use the drive on any operating system, otherwise go for Ext3/Ext4. (If you need some other filesystem than these you'l surely know that wthout even asking... ;))

---

