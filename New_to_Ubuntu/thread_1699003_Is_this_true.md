---
title: "Is this true?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-03
I'm dual booting Ubuntu 10.10 and Xp, I was talking to a friend of mine couple of mins ago. He told me that 
If I reinstall xp (which happens every now and then) it will wipe ubuntu totally is it true pls tell me it is not ...
I dont want to loose my Ubuntu installation.

---

### Post by Telengard C64 on 2011-03-03
Reinstalling XP won't wipe out Ubuntu unless you explicitly tell the XP installer to delete the partition which contains Ubuntu. So it kind of depends on how you do the install.

What the XP installer will do is overwrite Ubuntu's boot sector leaving you with no grub menu at startup. It would then appear that Ubuntu is gone, but in reality you can actually restore Ubuntu's boot sector and the grub menu. I've had to do this before, but don't recall exactly how I worked it out.

The rule of thumb is to install Windows first and Ubuntu second. Ubuntu will always preserve the boot sector of your old operating system and give you the option of choosing it from the grub menu. The Windows installer is not so kind.

---

### Post by beew on 2011-03-03
This is probably true as XP doesn't care about whether there is something else on the hard drive, but then one guy on the Forum said that XP can't see the Linux file system (ext4) and hence can see the Linux partition so it won't (the context was someone wanted to remove Ubuntu and he said reinstalling XP wouldn't do)

But what is the reason that you want to reinstall XP every now and then? This is not even an option for people who don't have a disk (say you have a laptop) so I really can't see the necessity of it.

---

### Post by Hedgehog1 on 2011-03-03
If you reinstall you XP properly (and post when you need to so we can help) it will not wipe out your Ubuntu install.

It does overwrite the MBR (**M**aster **B**oot **R**ecord), so there is an extra step to put the Grub boot loader back so you can boot XP ***and ***Ubuntu.

We will help you when the time comes.

---

### Post by Th3W1z4rD on 2011-03-03
If you install Windows after Ubuntu it overwrites the MBR(Master Boot Record) so that only Windows will boot by default. As long as you don't mess with the partition that Ubuntu is on you shouldn't overwrite the actual ubuntu install

This [thread]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should help you get the Grub bootloader working again so you have the option to choose your OS on boot

---

### Post by JRV on 2011-03-03
When Windows is re-installed it will overwrite the Master Boot Record which will destroy grub.
The rest of the Ubuntu installation is still there, but you will need to re-install grub.


To fix it download the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know of to fix Grub2.

---

### Post by Hedgehog1 on 2011-03-03
> **beew said:**
> 
But what is the reason that you want to reinstall XP every now and then? This is not even an option for people who don't have a disk (say you have a laptop) so I really can't see the necessity of it.

Hey - Beew is right!

Once you use Ubuntu mostly and XP a little, the reload of XP to improve performance wont be needed any more!

Think of the time you will be saving!!!

---

### Post by migrate from windows on 2011-03-03
Thank you guys that was very comforting....  My windows dies now and then because of viruses. Will take your advise before reinstalling if such a situation arises.. for now I guess I need not worry.

---

### Post by Hedgehog1 on 2011-03-03
Because of virsus, use XP as little as possible.

MS does now offer a **free** Anti Virus program for XP and above called 'Windows Defender'.  It does a decent job (did I mention it was **free**?)

Run Ubuntu for web surfing and such.  ***Linux is the ultimate antivirus***.  Hey - that can be our new slogan!

---

### Post by migrate from windows on 2011-03-03
Well said Hedgehog!  Think I will wean out off  Windows soon ( still clinging to it for I use vba macros a lot for work ).the links you guys gave solved my problem even before it happened!!!

---

### Post by YesWeCan on 2011-03-03
Try installing this: [http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)

---

### Post by Ertwong on 2011-03-03
Ugh, im kinda new to this and it might sound like a dumb question, but if i install Ubuntu does my files on my microsoft office 2007 get wiped too? or does it gets transfered to unbuntu? or do i have to keep both windows 7 and run Ubuntu? Thanks for the help guys
-Eric

---

### Post by mastablasta on 2011-03-03
> **migrate from windows said:**
> I'm dual booting Ubuntu 10.10 and Xp, I was talking to a friend of mine couple of mins ago. He told me that 
If I reinstall xp (which happens every now and then) it will wipe ubuntu totally is it true pls tell me it is not ...
I dont want to loose my Ubuntu installation.
 
 
**YES** **it will destroy/overwite Ubuntu if you installed it via Wubi** (in which case you instaleld it whithin windows). If you have it on separate partition then you will be fine you will just need to restore GRUB.
 
[QUOTE=Ertwong]
Ugh, im kinda new to this and it might sound like a dumb question, but if i install Ubuntu does my files on my microsoft office 2007 get wiped too? or does it gets transfered to unbuntu? or do i have to keep both windows 7 and run Ubuntu? Thanks for the help guys
-Eric 
[/QUOTE]
 
yes the files will be overwritten if they are on the same partition. otherwise they simply remain where they are. just files using a different file system. (partition is one part of disk - in windows they are often marked as C: drive, D: Drive...)
 
Windows uses NTFS file system while Linux uses EXT3 or EXT4. and to make this filesystem, the disk (or partition) needs to be formated which means also erasing all files. a CD for example usually uses some ISO standard file system.
 
It is possible to create a new partition on which you can install ubuntu. that way you files are safe. you can even keep windows on another partition and have a menu on start asking you what system you want to boot.
 
Linux can read NTFS file system, windows can't read EXT file system (without propper tools installed). as a result windows will not even knwo a linux is installed :D

---

### Post by wizard10000 on 2011-03-03
> **Hedgehog1 said:**
> If you reinstall you XP properly (and post when you need to so we can help) it will not wipe out your Ubuntu install.

It does overwrite the MBR (**M**aster **B**oot **R**ecord), so there is an extra step to put the Grub boot loader back so you can boot XP ***and ***Ubuntu.

We will help you when the time comes.

Although I don't build dual boot machines any more I'm a big fan of using a Windows bootloader to call grub instead of the other way around, since using Windows to start grub will allow you to reinstall either OS without bothering the other one.

Here's whatcha do for a clean install of both OS - you can't do this with an existing Linux installation unless you're willing to relocate grub  ;)

1.  Partition your machine the way you want - let's say sda1 is Windows, sda2 is Linux root, sda3 is swap and sda4 is /home just for fun.  Linux will be installed to sda2.

2.  Go ahead and install Linux to sda2 - but when prompted where to install grub **put it on the first Linux partition** instead of the boot partition.  This is critical.

3.  Go ahead and boot into Linux.  Make a copy of the linux partition's boot sector like this -

dd if=/dev/sda2 of=bootsect.lnx size=512 count=1

4.  Copy bootsect.lnx to a thumb drive.

5.  Install Windows.  This will break your Linux installation for the time being.

6.  Boot into Windows and copy bootsect.lnx to the root of your c:\ drive.

7.  Edit c:\boot.ini (note this is a read-only, hidden file and you'll have to replace those attributes after you're done) and add an entry for Linux that looks something like this -

```
c:\bootsect.lnx "Ubuntu 10.10"
```

Your boot.ini will look something like this -

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows" /fastdetect
c:\bootsect.lnx "Ubuntu 10.10"

```

8.  Save and enjoy - as you can now reload either OS without bothering the other one.  If you do reinstall Linux you have to remember to install grub to the first Linux partition and not the boot partition, though.

Some people use bootpart to do all the work for you but I've heard that bootpart doesn't like grub.  YMMV, of course  :)

Also, this *doesn't* work for Vista or Windows 7 - you have to use EasyBCD instead.

---

### Post by philinux on 2011-03-03
> **YesWeCan said:**
> Try installing this: [http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)

+1 for this. Better than the free virus scanners and less bloated than AVG. And it's free.

---

### Post by grahammechanical on 2011-03-03
Hi Ertwong

You are posting a new question on someone else' thread. This is not the way to get your question answered. No one will notice your question. This thread should be marked solved, anyway. Then no one will post answers as the problem is solved.

I am trying to be a nice person today, so I will give an answer. It is all up to you. The Ubuntu installer program does some tricky things automatically and gets it done well.

If you tell it to use the entire disc it will wipe out your Windows installation and all the documents that you have created and saved in Windows.

If you tell the installer to install alongside Windows it will do exactly that and give you a menu so that you can choose which OS to boot from. Ubuntu will be able to read what is in your Windows installation. You can copy files from Windows into Ubuntu. Windows will not see files in Ubuntu. You cannot copy files from Ubuntu to Windows.

Backup all the data that you want to keep. Decide if you want to keep Windows. This is allowed. You will not be a traitor to the cause. If you decide that you want to remove Windows, then it will be gone. There is no going back unless Microsoft supplied you with install CDs. It do not think that they did.

With Ubuntu we get Open Office, soon to be changed to LibreOffice. This program will read the Microsoft Office 2007 files. It is possible to convert from a Microsoft environment to Linux. You do not need to run Windows and Ubuntu unless there are Windows programs that you use and that do not have a Linux equivalent. In this case you will need to study a Linux program called WINE.

My advice is to run both operating systems until you get everything they way you want it. You can do a reinstall in a few months or years when you are convinced that you do not need anything from Microsoft.

Regards.

---

### Post by migrate from windows on 2011-03-03
That was a great idea Wizard10000! never thought of using the windows bootloader..... I dont think I should mark this thread solved still great ideas are pouring in.

---

### Post by Kixtosh on 2011-03-03
> **philinux said:**
> +1 for this. Better than the free virus scanners and less bloated than AVG. And it's free.I'll add my vote to that too (I might as well, since I nearly always agree with philinux anyway). AVG and others really slowed down my XP system, especially on startup. M.S.E. is much lighter and ... did anyone mention that it's free?! One other thing though that you should check if you're using any Windows, especially if you keep getting viruses, is to see if you have "secured" the Administrator profile. 

Frequently, Windows (especially XP and W2K) gets installed for a single user with Administrator privileges. Usually (I hope) that profile gets assigned a password, and then becomes the default startup profile. Nobody bothers to check the default Administrator profile, that is hiding in the background, with NO PASSWORD! The first thing to do to check this is Log Off whatever user profile you regularly use in XP and see if you can log on to the Administrator profile without even entering a password. If so, create a good password and secure that profile! W2K is not supported any more, so I hope nobody is using that anyway, and I won't mention it further.

Windows Vista and 7 have attempted to cure this oversight, by creating User Authentication Control, but in that case, too many people continue to use a profile with administrative privileges so that they don't have to put in a password so often when they want to do anything. This weakens the security of the system as a whole. Anyone using those operating systems should separate the Administrator profile from their regular user profile, and protect both with different passwords.

1) Get a fresh install of XP. 
2) Check that the Administrator profile is "secured" (as well as it's ever going to be anyway).
3) Install M.S.E.
4) See if you still have to install every six months or not.

I do all my browsing and e-mail messages in Ubuntu now, and XP hasn't even slowed down yet, much less required a fresh installation.

In any case, if you backup your Home folder, it's so simple to re-install Ubuntu that it's not even that big of a deal in my opinion. Yes, it does take some time (and some careful planning to make sure you didn't forget anything), and yes, you will have a large update the first time you check for updates, but after that, you'll be right back up to cruising altitude.

---

