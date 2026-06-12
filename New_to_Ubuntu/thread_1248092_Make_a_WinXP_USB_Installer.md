---
title: "Make a WinXP USB Installer"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-23
I want to know how to make a Windows XP Installer on a USB Stick using ONLY Ubuntu, not wine, not virtualbox, not anything but linux and the WinXP CD I have.

Everything on the web is about using Windows to make a Windows USB Installer. But what about us who don't have a ready Windows computer?

I've already tried to dd the ISO copy of the CD to a USB Drive, but it didn't boot.

USB Startup Creator doesn't accept a WinXP ISO.

And I don't know how to convert an ISO to IMG for use with ImageWriter (I have AcetoneISO, but it doesn't have an option to convert an ISO to IMG.)

---

### Post by nhasian on 2009-08-23
am I to understand from you sig that your computer has a modem, but not a CD-Rom to install WindowsXP with?

just for fun I setup my usb thumbdrive to install windows 7.  I imagine it would be the same procedure for windows xp.

1) format your thumbdrive as FAT32 and make it bootable.
2) extract all the files from the windowsXP cd image
3) copy all the files to the root of the thumbdrive

now you should be able to boot off the thumbdrive to start the installation.

---

### Post by Seankn on 2009-08-23
Im sorry to say that it is really hard...

You have to change a ton of files and all that. 

Why are you talking about windows xp in ubuntu Forums?

---

### Post by coldReactive on 2009-08-23
> **Seankn said:**
> Im sorry to say that it is really hard...

You have to change a ton of files and all that. 

Why are you talking about windows xp in ubuntu Forums?

Cause ubuntu is all I have to make the USB Drive. I don't think windows tech help would help me when I can't use windows to make a windows install USB drive.

No, I have cable, and a router.

---

### Post by mikewhatever on 2009-08-23
> **Seankn said:**
> . 

Why are you talking about windows xp in ubuntu Forums?

+1

It's rather awkward to see Windows help requests here. If it goes on, I'll put some Ubuntu related questions on microsoftforums.com.

To the OP, there is a ton of guides for that on the web, all you have to do is google.

---

### Post by twright on 2009-08-23
Just right click on the ISO, select extract, then install gparted from add/remove and use it to partition your usb drive as to have one fat 32 partition and right click on it, select change flags and make it bootable. Now all you need to do is to copy and paste all of the files extracted from the ISO onto the USB stick - overall it is probably easier than doing it in Windows :-)

BTW. This is absolutely a Ubuntu support request as the question is how how to make the usb installer from within Ubuntu - it is the same as if he wanted to burn the ISO to CD from Ubuntu.

---

### Post by coldReactive on 2009-08-23
> **twright said:**
> Just right click on the ISO, select extract, then install gparted from add/remove and use it to partition your usb drive as to have one fat 32 partition and right click on it, select change flags and make it bootable. Now all you need to do is to copy and paste all of the files extracted from the ISO onto the USB stick - overall it is probably easier than doing it in Windows :-)

Already tried, didn't boot. All it did was boot to the first harddrive instead.

@mikewhatever: I'm absolutely terrible at google. The first 10+ pages of search terms I use are about doing this in Windows, NOT ubuntu.

---

### Post by mikewhatever on 2009-08-23
> **coldReactive said:**
> 
@mikewhatever: I'm absolutely terrible at google. The first 10+ pages of search terms I use are about doing this in Windows, NOT ubuntu.

I see, the problem is, Ubuntu is neither designed not intended for making USB windows installers. You can probably do it with a lot of hackingand much time on your hands, plus the legality of such action is very questionable. In short, it's just not worth the while.

---

### Post by hackerseraph on 2009-08-23
Does unetbootin not support XP?

---

### Post by coldReactive on 2009-08-23
> **hackerseraph said:**
> Does unetbootin not support XP?

Nope, not possible, just tried it.

---

### Post by alexlafreniere on 2009-08-23
For XP:

[http://lifehacker.com/141290/boot-windows-from-a-usb-drive](http://lifehacker.com/141290/boot-windows-from-a-usb-drive)

And Vista:

[http://lifehacker.com/240308/install-vista-from-a-usb-flash-drive](http://lifehacker.com/240308/install-vista-from-a-usb-flash-drive)

---

### Post by coldReactive on 2009-08-23
> **alexlafreniere said:**
> For XP:

[http://lifehacker.com/141290/boot-windows-from-a-usb-drive](http://lifehacker.com/141290/boot-windows-from-a-usb-drive)

And Vista:

[http://lifehacker.com/240308/install-vista-from-a-usb-flash-drive](http://lifehacker.com/240308/install-vista-from-a-usb-flash-drive)

Bart PE needs Windows to run itself, I don't have windows.

---

### Post by hansdown on 2009-08-23
Hi coldReactive.

This should** help**.

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by gali98 on 2009-08-23
Have you tried dding the iso onto the flash drive?

Also you could check out syslinux.
Kory

---

### Post by coldReactive on 2009-08-23
> **hansdown said:**
> Hi coldReactive.

This should** help**.

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

ubootin isn't compatible with the WinXP ISO.

> **gali98 said:**
> Have you tried dding the iso onto the flash drive?

Also you could check out syslinux.
Kory

How can syslinux help me make WinXP Install boot from usb?

Yes, I have tried dd'ing the WinXP ISO to the usb drive, however it wouldn't boot.

---

### Post by nhasian on 2009-08-24
seriously, you guys are making it very difficult.  look how easy it is to do with this video:

[http://mschnlnine.vo.llnwd.net/d1/edge/2/1/3/2/Win7onUSB_edge.mp4](http://mschnlnine.vo.llnwd.net/d1/edge/2/1/3/2/Win7onUSB_edge.mp4)

---

### Post by coldReactive on 2009-08-24
> **nhasian said:**
> seriously, you guys are making it very difficult.  look how easy it is to do with this video:

[http://mschnlnine.vo.llnwd.net/d1/edge/2/1/3/2/Win7onUSB_edge.mp4](http://mschnlnine.vo.llnwd.net/d1/edge/2/1/3/2/Win7onUSB_edge.mp4)

Problem: I don't have a windows machine available, so I can't use diskpart. (Even if I did, it would be Windows XP, not vista not Windows 7.)

Plus, I only have a 2 GB Drive available, (not that the Windows XP Setup Disk takes up more than 600 MB.)

Also, that Windows 7 disk has a Boot folder, which is not normally visible on a CD.

---

### Post by coldReactive on 2009-08-24
Okay, now that's strange.

I did exactly what he did in gparted and nautilus (made a FAT32 partition only, etc. and then just copy over the files raw.)

But when I boot from the USB Drive:

**CDBOOT: Cannot boot from CD - Code: 5**

Google is unhelpful because everyone wants it solved for Windows 7 and NOT a netbook.

---

### Post by The Cog on 2009-08-24
I don't know the answers, but I did notice that most solutions offered so far are for installing XP on a USB stick, which is nto what was asked for. What was wanted was to create an XP installer on a USB stick, so that for instance, one could use the USB stick to install XP to a CD-less netbook.

I do feel that this should be easier than installing XP to a USB stick. It's just a matter of getting the installer to boot, and making it think all the files are on a CD.

---

### Post by gn2 on 2009-08-24
Have you confirmed that the BIOS is correctly configured to boot from your USB stick?

---

### Post by coldReactive on 2009-08-24
> **gn2 said:**
> Have you confirmed that the BIOS is correctly configured to boot from your USB stick?

Yep, it is. Even if it wasn't, there's no way to turn on that function, no way to turn off, and no way to configure what it boots to manually.

---

### Post by Seankn on 2009-08-24
I agree ill help

---

### Post by coldReactive on 2009-08-24
> **Seankn said:**
> I agree ill help

Help with what? Getting your own postcount up?

---

### Post by gali98 on 2009-08-24
> **coldReactive said:**
> Yep, it is. Even if it wasn't, there's no way to turn on that function, no way to turn off, and no way to configure what it boots to manually.
Okay... Explain what you mean here...

As far as syslinux, it can boot a bunch of stuff... perhaps with memdisk included you can boot the cd boot files. 

Kory

---

### Post by coldReactive on 2009-08-24
> **gali98 said:**
> Okay... Explain what you mean here...

What I mean is, it's on by default, and no way to turn it off (or on for that matter). You also cannot configure what USB device boots first without it plugged in before the computer starts.

I can't use syslinux if I don't know which file on the WinXP Setup CD I need to boot with.

---

