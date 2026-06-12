---
title: "Minor problem with Update Manager"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by UUUnicorn on 2011-05-14
Thank you for all advice and help people here kindly have offered me; I really appreciate it.

I found a minor problem when I run Update Manager. Whenever I run it, I get this:

Failed to download repository information

Check your Internet connection.

Details

W:Failed to fetch cdrom://Xubuntu 11.04_Natty Narwhal_ - Release i386 (20110427)/dists/natty/main/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, W:Failed to fetch cdrom://Xubuntu 11.04_Natty Narwhal_ - Release i386 (20110427)/dists/natty/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, E:Some index files failed to download. They have been ignored, or old ones used instead.

I opened up Terminal and typed in "apt-cdrom", and this is what I got:

elizabethanne@elizabethanne-U90-U100:~$ apt-cdrom
apt 0.8.13.2ubuntu3 for i386 compiled on Apr 26 2011 17:43:16
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM’s to APT’s source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
        add - Add a CDROM
        ident - Report the identity of a CDROM

Options:
       -h  This help text
       -d  CD-ROM mount point
       -r  Rename a recognized CD-ROM
       -m  No mounting
       -f  Fast mode, don’t check package files
       -a  Thorough scan mode
       --auto-detect Auto detect drive and mount point
       -c=? Read this configuration file
       -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
elizabethanne@elizabethanne -U90-U100:~$

I have an LG external optical drive (CD-ROM/DVD-ROM). Do I need to download and install driver(s) for this?

Thank you very, very much.

Sincerely,

UUUnicorn

---

### Post by corrytonapple on 2011-05-14
You should not need to install drivers for it if it works as is.  Ubuntu comes loaded with drivers for common types/brands of CD/DVD players.
Do you have an internet connection at that computer?  I assume so, but I do not know why it is not connecting to the internet to grab these updates.

---

### Post by NoNameWill on 2011-05-14
I use a external io magic on my laptop because my internal is failing. I just connect it turn it on and it shows up through the GUI. So I would say no on needing drivers.


Go into setting in Update Manager>Settings>Ubuntu Software and uncheck install from CD-Rom

---

### Post by wildmanne39 on 2011-05-14
> **UUUnicorn said:**
> Thank you for all advice and help people here kindly have offered me; I really appreciate it.

I found a minor problem when I run Update Manager. Whenever I run it, I get this:

Failed to download repository information

Check your Internet connection.

Details

W:Failed to fetch cdrom://Xubuntu 11.04_Natty Narwhal_ - Release i386 (20110427)/dists/natty/main/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, W:Failed to fetch cdrom://Xubuntu 11.04_Natty Narwhal_ - Release i386 (20110427)/dists/natty/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, E:Some index files failed to download. They have been ignored, or old ones used instead.

I opened up Terminal and typed in "apt-cdrom", and this is what I got:

elizabethanne@elizabethanne-U90-U100:~$ apt-cdrom
apt 0.8.13.2ubuntu3 for i386 compiled on Apr 26 2011 17:43:16
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM’s to APT’s source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
        add - Add a CDROM
        ident - Report the identity of a CDROM

Options:
       -h  This help text
       -d  CD-ROM mount point
       -r  Rename a recognized CD-ROM
       -m  No mounting
       -f  Fast mode, don’t check package files
       -a  Thorough scan mode
       --auto-detect Auto detect drive and mount point
       -c=? Read this configuration file
       -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
elizabethanne@elizabethanne -U90-U100:~$

I have an LG external optical drive (CD-ROM/DVD-ROM). Do I need to download and install driver(s) for this?

Thank you very, very much.

Sincerely,

UUUnicorn
Hi, all that is telling you is that it is trying to also get updates from the cdrom but there is not a cd in the cdrom or not the livecd anyway, if you follow the person instructions in the previous post you should not have any trouble.:)

---

### Post by UUUnicorn on 2011-05-15
Thank you, thank you, thank you!

You archangels ROCK--'nuff said (*bowing repeatedly*)!

Hugs,

UUUnicorn! :D

---

### Post by corrytonapple on 2011-05-15
Wow, thanks.  You are welcome.  :)
Since this thread is solved, please go up to "Thread Tools" in the top right hand corner and click "Mark Thread as Solved" so others know that there is a solution here.
Happy Ubuntu-ing!

---

### Post by zeeboos on 2012-02-09
There is also a similar check box under settings/software sources/Ubuntu Software
Down in lower left corner "Cdrom with Ubuntu 11.10 Oneiric Ocelot.  I unchecked that box and it did not fix the problem.However the directions above did.  Thank You.

Just thought I would give this information in case someone else gets confused like I did.

---

### Post by thumbtak on 2012-03-07
I can't find this option in "Xubuntu 11.10".

Edit: I found out that the issue was with "XBMC" and "WIICAN". Issue resolved.

---

