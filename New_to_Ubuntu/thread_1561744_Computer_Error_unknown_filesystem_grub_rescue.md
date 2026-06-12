---
title: "Computer Error unknown filesystem grub rescue?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Cameron Murray on 2010-08-26
I deleted a partition on my hardisk I think that had ubuntu netbook edition on it.

Now when my machine starts I get error unknown filesystem 
Grub rescue.


I want to access my windows partition please help!

I don't need Ubuntu onthat machine anymore but I need Windows (its not my machine)

---

### Post by ajgreeny on 2010-08-26
You need to restore the windows boot manager to the MBR.  How you do that will depend on the windows version, but search for it and you will find it very easily.  It does need the windows install CD, however, and if you only have a restore CD or partition to use, you may need to go to [neosmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") for recovery suite of software available as an iso to burn to disk as normal and boot.  Vista and win 7 are there.

There used to be a similar app for XP, I think but it's not mentioned on that site, so other than installing and using lilo in a live ubuntu CD, the details of which I can't find at the moment, I do not know how I can help.

OK, found it!
You can install a Windows XP equivalent MBR to your sda drive by doing the following from your Live CD:
Code:

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

Then you should be able to boot directly into Windows again if all goes well.

---

### Post by cunvegas` on 2010-11-30
Hi,

I had a dual boot:  Win XP and Ubuntu 10.04 LTS.  Then I erased the Ubuntu partition.

Restarted then, 
error:  unknown filesystem.
grub rescue>

I have a Ubuntu 10.04 LTS setup/boot CD.  Tried booting off of it and received the same error.

How do I get Win XP back?

---

### Post by Celcees on 2011-08-03
I know this is old but for ppl who are looking for a looking to fix the boot problem after deleting the linux or ubuntu partition i have a simple method that I a non pc/linux expert have found by accident. simply start up your windows recovery or installer. in Windows 7 go to the repair options and open a command prompt.

then type this: "bootrec /fixmbr" without the quotes

if your not sure this is the right command just type "bootrec" and hit enter and you will be given more instructions about boot recovery.

Note this will probably only work if windows is STILL installed.

this worked for me! again this is a solution for the problem of deleting the ubuntu/linux partition and getting a grub error when booting you dill need a windows install/recovery disc! good luck

---

