---
title: "Installed Wubi, But Cannot Run"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by asnbd on 2009-12-27
hi,
 
i have installed the wubi 32bit in my windows.
 
the installation was complete, but the os(ubuntu) cannot run.
 
there's a boot selection, and if i select ubuntu, i get the following error message:
 
the error message was:

try (hd0, 0) non-MS skip
try(hd0, 1) non-MS skip
try(hd0, 2) ext2

i do not know what went wrong. so any suggestions is appreciated.
 
ed

---

### Post by markjensen on 2009-12-27
That is strange.  I don't have a lot of wubi experience, having only installed it that way once to see how it works.

Anyhow, let's take a look at how Linux sees your partitions.  Can you boot the Ubuntu CD as a Live CD, open a terminal and type the following, then post the results here in this thread (you should be able to get online through the LiveCD to post back in the forum here).

**sudo fdisk -l** (that is a lowercase letter "L", not the number one)

And that will show us how your drive(s) partitioning looks to Linux.

---

### Post by asnbd on 2009-12-28
hi,
 
i have no experence using live cd. what is it? how does it use my hard disk? will it install software on my computer? and why need to use a live cd install of the .iso disc.?
 
thanks.

---

### Post by markjensen on 2009-12-28
The CD you have works as an install CD, and it can work as a "Live CD", which boots into Linux without writing to your hard drive.

So you already have your LiveCD.  No, it does not use your hard disk (though it can access it, as you please. No, it does not install anything.  And I asked you to boot it so we can take a look at your partitions as Linux sees them (as I stated in my previous post).  I think it is necessary because of the boot problems you are seeing.

---

### Post by mlentink on 2009-12-28
It would also help if you could describe precisely what you did to install, as far as you remember.
What was the first step? Did you first boot the LiveCD or did you insert the cd while in Windows? And then?

---

### Post by asnbd on 2010-01-04
> **markjensen said:**
> 
]sudo fdisk -l[/b] (that is a lowercase letter "L", not the number one)
.


hi,

i do not have a ubuntu live dvd disk, so i live booted into linux using fedora 12 live.

then in termal, i typed sudo fdisk -l

and the return message was:

#1Respect the private
#2Think before you type
#3With great power comes great responsible

very weird isn't it.

btw, i'm installing wubi 32bit on an imac, and i have been trying to it triple boot. but i'm not good at these things. so i think i have ruined my gpt partition table.

anyway, any suggestion is qppreciated.

ed

---

### Post by markjensen on 2010-01-04
Ok.   Fedora sets up their accounts a little differently.  They don't put /sbin/ in the path for the default user, so you may need to specify the system binary directory, since "fdisk" is a system level tool.   Also, Fedora doesn't set up sudo by default.  You just use "su" there.

So those are two rock-solid reasons your command didn't work.  Silly me, I thought you were going to use Ubuntu.  ;)

Let's do it this way for Fedora.
Open a terminal (so far, it is the same)
Next, type **su** to switch user (defaults to root - this replaces the sudo from my earlier post).
Finally, type **/sbin/fdisk -l** (again, that is a lowercase letter "L" there)

This should give you a good report of your hard drive partitions in Fedora.

---

### Post by asnbd on 2010-01-05
hi,

i'm not sure if these are the info you need. i used rEFIt - partition and copied the info about my gpt partitions.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    365314087  Mac OS X HFS+
 3      365576232    382353447  Basic Data
 4      382615592    466366949  EFI System (FAT)
 5      466366950    483277286  Basic Data
 6      483541032    488134983  Linux Swap

let me know if these are what you needed.

thanks.

ed

---

