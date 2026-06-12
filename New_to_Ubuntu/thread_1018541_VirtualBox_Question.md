---
title: "VirtualBox Question"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-22
I was wondering, as I'm considering buying a Dell with Ubuntu, about VirtualBox. I'll probably need Windows for something in school. So I'm thinking of going the VBox method. I might dual boot as well, but I'm not sure if it's necessary. It depends on the following question. 

What about installing Windows software within the VM? Does it install normally? I'll probably have to work with Visual Basic in school, and I might need Microsoft Office (if I can't get by with Open Office).

Do you think I could get through school (Computer Science Associates) with just installing Windows into a VM, or should I partition the drive for dual boot as well?  
--- 

If I do decide to install Windows onto the system itself, in addition to a VM, that will delete or overwrite Ubuntu, right? Then I'd have to reinstall Ubuntu. So please let me know if my assumption here is right. That would mean I'd have to install Windows first before creating a VM, then reinstall Ubuntu, and then create the VM.

---

### Post by mozetti on 2008-12-22
There should be no problem installing and running Windows software in a Windows VM.

You can install windows after you install Ubuntu, but it is a lot more work to do it that way. If you think you're going to install Windows on the machine, then do that first and then install Ubuntu.

---

### Post by ushimitsudoki on 2008-12-22
I use VirtualBox and it has worked perfectly for me. They are only just now adding 3D support, so it's not a good replacement in that one area -- yet.

For everything else, I'm very satisfied with the results.

---

### Post by Zzl1xndd on 2008-12-22
I use a Windows VM for a few things and it works fine as long as your not doing anything too heavy. Installing is normal just make sure you have the host drive mounted. 

as for the installing Winows you could make a second partition and install windows on it without over wrting the Ubuntu side but you would still have to reinstall GRUB.

---

### Post by Sarmacid on 2008-12-22
Just VBox should do it, but as ushimitsudoki said, for things like games it's not so great yet.

In case you want to install windows anyways, you can have both OSes at the same time, just partition your hard drive accordingly, and it is suggested you install windows first, then Ubuntu because Windows likes to mess grub up.

---

### Post by Duck2006 on 2008-12-22
Virtual box will work ok for you. if you want to go with install windoze as a dual boot, this may help.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by lkraemer on 2008-12-22
sanubie,
Here is another very good site for Dual Boot Information.
http://users.bigpond.net.au/hermanzone/

Having done both, Dual Boot and VirtualBox, I'd like to make a few
suggestions.

1.  If using VirtualBox, which works fine, use the version from
    www.VirtualBox.org that has USB Support.  Also make sure your
    Computer has at least 2 Gig of RAM.  ~1 for XP and ~1 for Ubuntu
    & VirtualBox.
2.  When setting up your Virtual Disk Image (VDI ...Dynamically
    Expanding one) make sure you make it large enough.  The default
    10 Gig will fill quickly as you install XP and a few other programs
    you will be using.  I'd suggest 20 or 30 Gig as a starting point
    which will give you some room to install other required software.
    Once the VDI is sized, that is the Maximum and it can't be expanded.
3.  XP running in VirtualBox is a tad bit slow at times on my AMD 3300+
    Sempron, but I can live with it.  If you have a dual core it will
    most likely rune fine.  After all UBUNTU is the Primary use OS.
4.  Dual Boot with Windows XP on the first Partition is probably the best
    option, as it gives you the most options to expand/resize the
    partition as needed.  But it sure is nice to run XP as required in
    Linux and have everything work.  Just make sure your Drive is large
    enough for the required partitions, and install XP first.
5.  Make sure you go to www.VirtualBox.org and read the FAQ's and 
    Information on Installing the Guest Additions.  Also make yourself
    a SHARED Folder so you can access Files moved into the Shared folder
    along with Files on a USB Flash Drive.
6.  If/when you use the VDI's you will want to move the VDI to other
    Computers, which means transfering 10-30 Gig.  I'd suggest using
    Filezilla and vsftpd (FTP Server) on one machine so Filezilla can
    transfer the VDI.  All you will need is the IP Address, and the
    Login & Password to get the transfer done.  And it is easy and fast
    to transfer the VDI's.
    
So, the choice is yours.  Good Luck.  You can always try both.

lkraemer

---

### Post by sajnox on 2008-12-22
> **sanubie said:**
> If I do decide to install Windows onto the system itself, in addition to a VM, that will delete or overwrite Ubuntu, right? Then I'd have to reinstall Ubuntu. So please let me know if my assumption here is right. That would mean I'd have to install Windows first before creating a VM, then reinstall Ubuntu, and then create the VM.

No, an installation of windows will not delete the ubuntu partition, unless you overwrite on purpose.

If you install windows after installing ubuntu the MBR (master boot record) will be deleted by windows and you will not find the Grub, but there are too many guides in the web to repair it, and trust me, it's very easy to do it.

---

### Post by Sarmacid on 2008-12-22
I forgot to mention, but you can use VBox to boot an existing windows partition.

Here's the link [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

### Post by Kellemora on 2008-12-22
Hi San

Why not just pick up a used Doze XP computer to have on hand for when you need to do something on the Doze?????

A really decent newer machine can be had for from 150 to 300 bucks, depending upon what you want in it.  Sometimes you luck out and find some great deals for 75 bucks too!

I usually balk at a price over 275 bucks for a used machine, since I can get brand new machines, dual core, either AMD or Intel, etc. etc. etc. for like 255 bucks, plus another 40 bucks for a couple gigs of memory.

TTUL
Gary

---

### Post by Michaelg14 on 2008-12-22
I am using both methods.  Virtualbox running XP for most day to day needs and dual booting to play high power games. I use open office so I don't know how microsoft office does in a virtual machine but I would imagine it would work with no problems.  Get your copy of Vbox from their website and don't get the OSE version it has no usb support.

setting up usb is another story.

For dual booting you really need a separate partition so you won't overwrite Ubuntu.  However, as has already been said it's best to install windows first.

---

