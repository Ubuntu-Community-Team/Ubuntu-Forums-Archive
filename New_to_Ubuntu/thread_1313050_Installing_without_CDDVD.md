---
title: "Installing without CD/DVD"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Fate32 on 2009-11-03
Hi - totally new to ubuntu. Just noticed that my cd/dvd drive isnt detecting disks at all. I need to get rid of windows and was wondering if there is a way of installing without booting from or using CD/DVD - i read a few boards and it would seem there is via USB pen drive/memory stick however i dont have one of these either. Any more ideas?

Im trying to install on a laptop acer aspire 5100 series, currently has a windows xp. Have a feeling this may attract some heat but I am all out of ideas.

thanks in advance

---

### Post by howefield on 2009-11-03
There are a few ideas on this page which might help.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Bunnybugs on 2009-11-03
You can order a Disc from Ubuntu for free... or you download the .ISO-file from the ubuntu website...

after that you can restart your computer... while your startscreen (BIOS-screen) appears, enter set-up... that's most of the times F2, F10 or Del...

Go to 'Boot' and change your order of boot-priority with CD/DVD as first booting device...

Exit with Saving Changes (most of the time press F10), and start your PC with the disk inside...

For the rest of it: Follow on screen instructions...

Watch out, it&#347; probably a good plan to Back Up your files


**OR,**

Download the Wubi.exe app from Ubuntu.com

This is an Windows installer that installs Ubuntu to your computer/laptop... perfect for starting ubuntu users...

if your diskdrive doesn work in windows, doesn say that it doesn't work in Linux/BIOS

---

### Post by wilee-nilee on 2009-11-03
> **Fate32 said:**
> Hi - totally new to ubuntu. Just noticed that my cd/dvd drive isnt detecting disks at all. I need to get rid of windows and was wondering if there is a way of installing without booting from or using CD/DVD - i read a few boards and it would seem there is via USB pen drive/memory stick however i dont have one of these either. Any more ideas?

Im trying to install on a laptop acer aspire 5100 series, currently has a windows xp. Have a feeling this may attract some heat but I am all out of ideas.

thanks in advance

The link gives you great options, but if your a new user doing a command line install might not be a good idea, if you don't do it right you could completely remove the XP. It may be that this doesn't matter, but lets say worse case scenario you end up with a unbootable computer to Linux or Xp your going going to have to use a USB live cd to fix it, repartition--etc. Make it easy get a USB stick load the distro you want and use the partition manager to set it up with a open partition or just install and use the partition gui t0 partition. Ask more questions if you do anything, once you have the basic understanding of Linux to do this stuff it will be very easy. So your computer not reading CD's is this in reference to booting or in general.

---

### Post by GrantBarry on 2009-11-03
You could try installing over LAN using a PXE Boot (network boot from BIOS). Your laptop NIC needs to be PXE-complaint and that Acer did not disable the option in the BIOS/Boot menu. If it is a recent model, it should be PXE-compliant.

You will also need another PC which will act as a server. There is an open-source project called TFTPD32 ([http://tftpd32.jounin.net/](http://tftpd32.jounin.net/)) which is a PXE Service for Windows. You do not need a server edition of Windows. Windows XP, Vista or 7 will do.

Check out this thread: [http://ubuntuforums.org/showthread.php?t=327597](http://ubuntuforums.org/showthread.php?t=327597)

---

### Post by screaminfakah on 2009-11-03
Buy a new cd rom.
You can get a flash stick for $10 these days as well.

---

### Post by Bunnybugs on 2009-11-04
> **screaminfakah said:**
> Buy a new cd rom.
You can get a flash stick for $10 these days as well.

True, here in holland it&#347; usual to have 16GB for 40 euro's or some... that&#347; about 55 dollar

---

### Post by NickJones on 2009-11-04
[SIZE=7][UnetBootin]("http://www.google.com.au/url?q=http://unetbootin.sourceforge.net/&ei=A2DxSt_WMY6OkQXmtf2WBw&sa=X&oi=spellmeleon_result&resnum=1&ct=result&ved=0CAcQhgIwAA&usg=AFQjCNEsPguQz1-ufKE3td6-TBc2vZQEiQ")[/SIZE]
I cannot express how useful this App is.

---

### Post by 3rdalbum on 2009-11-04
Either borrow someone's external CD drive, or get an internal CD drive and plug it into a SATA drive enclosure (borrow both things if you like) - or buy a USB flash drive and use Unetbootin to put the disk image onto the flash drive.

You'll find lots of uses for a flash drive, don't worry about that! :-D

---

### Post by phillw on 2009-11-04
> **NickJones said:**
> [SIZE=7][UnetBootin]("http://www.google.com.au/url?q=http://unetbootin.sourceforge.net/&ei=A2DxSt_WMY6OkQXmtf2WBw&sa=X&oi=spellmeleon_result&resnum=1&ct=result&ved=0CAcQhgIwAA&usg=AFQjCNEsPguQz1-ufKE3td6-TBc2vZQEiQ")[/SIZE]
I cannot express how useful this App is.

Another great site is [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)   I guess it's just a case of personal choice :)

Phill.

---

### Post by Bunnybugs on 2009-11-04
Well, Pendrivelinux is some kind of a problem... but if you just want to use Ubuntu instead of Widdows... You might try the Wubi.exe installer....

Execute it in Widdows...

!!!Slide the bar to 30GB, this will be your space on the Ubuntu partition...!!!

Follow the instructions, and press reboot...

You might also want to check out the CD drive problem... I guess that your driver has been damaged... had the same problem on Vista

---

### Post by phillw on 2009-11-04
> **Bunnybugs said:**
> Well, Pendrivelinux is some kind of a problem... but if you just want to use Ubuntu instead of Widdows... You might try the Wubi.exe installer....

Execute it in Widdows...

!!!Slide the bar to 30GB, this will be your space on the Ubuntu partition...!!!

Follow the instructions, and press reboot...

You might also want to check out the CD drive problem... I guess that your driver has been damaged... had the same problem on Vista

Odd that you had problems with pendrivelinux - we found it good :-\

[http://ubuntuforums.org/showthread.php?t=1308359&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1308359&highlight=phillw)

(amongst others I sent to their site - mainly ones with net-books)

Phill.

---

