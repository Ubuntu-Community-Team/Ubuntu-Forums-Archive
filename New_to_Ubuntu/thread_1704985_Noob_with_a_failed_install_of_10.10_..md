---
title: "Noob with a failed install of 10.10 ."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by ions82 on 2011-03-11
I am in the process of learning how to use Ubuntu, so I apologize if I put things into layman's terms.  I'm definitely no expert when it comes to troubleshooting computers.  What I have is a bunch of donated computers that are to be "refurbished" and given to people in need.  The last group of systems to come in are some 3.0 GHz P4s with no hard drives.  I have been suggesting that we start using Ubuntu/Linux (instead of Win-blows XP) as the OS, but a problem I've run into isn't helping my campaign.

I am getting the following error when I tried to boot from an install disc I've created.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I made another disc and got the same error.  The hard drive is brand new.  I have no idea where to go from here.  We tried partitioning and formatting the HD.  I am now trying to figure out if I can generate the "script output."  If you can help me figure it out, please let me know.  Thank you for taking time to read through this post!

---

### Post by Hippytaff on 2011-03-11
It looks as though either the iso you burned to the disc is corrupt or it got corrupted during the burn process. I would suggest, burning the discs at the slowest possible speed, or even making a bootable usb with[ unetbootin]("http://unetbootin.sourceforge.net/")

Downloading the ubuntu Torrent will mean that you shouldn't get a corrupt iso because the checksum (to varify that it's not corrupt) is part of the torrent download process (so I'm led to believe)

---

### Post by colkey on 2011-03-11
Have you checked the MD5 sums of the .iso file you downloaded.

---

### Post by el_koraco on 2011-03-11
did you use a rewritable cd?

---

### Post by ions82 on 2011-03-11
> **colkey said:**
> Have you checked the MD5 sums of the .iso file you downloaded.


How do I go about doing that?  I have a working system with 10.10 on it (the "shop" computer), and I used it to download and create the boot disc(s).  It said it went through the checksum process.  However, I've only assumed it's OK as I don't know how to verify anything.  At the moment, I don't have an extra computer to try another boot/install.  I can get an identical system and hard drive to try it on, but it would have all the exact same specs.

So, is the "script output" something that I need to procure?  I don't even really know what it is or how to go about finding it.  As I mentioned, I just read another post where someone had generated the script output, and another forum member said it was very helpful.  Almost everything I read on this forum is completely foreign to me, so I have no idea where to start.  Thank you for the help!

---

### Post by ions82 on 2011-03-11
> **el_koraco said:**
> did you use a rewritable cd?


I didn't use re-writable CDs.  I can probably get a USB drive to try.  Do I need to use a particular format when partitioning the hard drive?  Would that make any difference for this situation?

---

### Post by Rex Bouwense on 2011-03-11
Her are two sites that you need to bookmark.  At least I have them bookmarked because I use them when ever I download a new version.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Enjoy.

---

### Post by Hippytaff on 2011-03-11
> **ions82 said:**
> I didn't use re-writable CDs.  I can probably get a USB drive to try.  Do I need to use a particular format when partitioning the hard drive?  Would that make any difference for this situation?

it should be fine as it is, but fat32 usually

---

### Post by ions82 on 2011-03-11
> **Rex Bouwense said:**
> Her are two sites that you need to bookmark.  At least I have them bookmarked because I use them when ever I download a new version.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Enjoy.


I tried doing the MD5SUM procedure, but I only made it as far as opening a terminal.  I have not been able to get it specify the download directory ("cd download_directory" just gives me a "no such directory" message.)  I'm just feeling my way around in the dark, here.  I have no background in computer programming/repair/troubleshooting.  Most of the terminology used in the forum are words for which I have no referent.  And here I thought that using a Linux-based OS would give people fewer problems than Windows.  Is there such a thing as an OS that is reliable AND simple?

---

### Post by Hippytaff on 2011-03-11
try ```
cd Downloads/
``` That's a capital D - linux is case sensitive.

It just takes a while to familarise yourself with a different OS...once you do you will see the benefit of Linux

---

### Post by Rex Bouwense on 2011-03-11
Remember that when are trying to change directories, upper/lower case makes a difference so you should have entered cd Downloads with an upper case D.  Do not get frustrated because everyone of us on this forum went through a learning curve when we installed Ubuntu on our machines.  We are here to help because we remember when we needed help.

---

### Post by Hippytaff on 2011-03-11
> We are here to help because we remember when we needed help.

Indeed I still need help sometimes, but that's not because linux is difficult, just that I am more free to learn about how it works (and sometimes break things)

---

### Post by ions82 on 2011-03-11
> **Hippytaff said:**
> try ```
cd Downloads/
``` That's a capital D - linux is case sensitive.

It just takes a while to familarise yourself with a different OS...once you do you will see the benefit of Linux


Oh, man.  Something so simple.  I could've sat here staring at the screen until the end of time and had no idea.  Thank you for the pointer!  That did the trick in getting me to the download directory.  I ran the MD5SUM for the downloaded file, and it checked out with the hash given for the version of Ubuntu I downloaded [FONT=monospace]([/FONT]ubuntu-10.10-desktop-i386.iso).  So, I guess that means that the download is good.  I'm guessing I can run the same check on the disc that I created.  I'll see if I can give that a go.  Now to figure out how to get into the directory for the CD!

---

### Post by Rex Bouwense on 2011-03-11
Hippy  You and I probably need more help than the average bear.


Rex

---

### Post by Hippytaff on 2011-03-11
> **Rex Bouwense said:**
> Hippy  You and I probably need more help than the average bear.


Rex
I am remarkably slow ;-)

```

cd media

```
do
```
ls
``` to list whats there - it will provide the name of the cd
then do ```
cd 
``` start typing the first couple of lettersof wht was returned as the name of the disc and press TAB to autocomplete. thats the path to the cd.

---

### Post by ions82 on 2011-03-11
I tried to do MD5SUm for the CD.  After almost an hour, I decided to can it.  I just let the thing run overnight some time next week.  Is it likely that there was an error in creating the disc?  It seems that issues with burning the disc are fairly common.  I'll just try to burn another one since the downloaded .iso file checked out OK.  It'll be faster than waiting for the MD5SUM on the disc I've already created.

---

### Post by Hippytaff on 2011-03-11
ok...burn at the slowest possible speed ;-)

---

### Post by milindo on 2011-03-12
> **ions82 said:**
> I tried to do MD5SUm for the CD.  After almost an hour, I decided to can it.  I just let the thing run overnight some time next week.  Is it likely that there was an error in creating the disc?  It seems that issues with burning the disc are fairly common.  I'll just try to burn another one since the downloaded .iso file checked out OK.  It'll be faster than waiting for the MD5SUM on the disc I've already created.
Try usb

---

