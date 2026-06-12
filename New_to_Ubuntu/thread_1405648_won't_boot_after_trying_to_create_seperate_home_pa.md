---
title: "won't boot after trying to create seperate home partition"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-12
I tried to create a seperate home partition using psychocats tutorial.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have the computer booted via live cd now and when I look in the drive it seems like everything is there.  I just get error messages when I try to boot from the drive.

[QUOTE=First error message]Your home directory is listed as: '/home/mike' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session.

No Yes[/QUOTE]

[QUOTE=If I select Yes]User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by others.

OK[/QUOTE]

[QUOTE=after selecting OK]Your session only lasted 10 seconds. If you have not logged yourself out, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

view details (~/.xsession-errors file)

OK[/QUOTE]

Most of the details seem to be...
Can't create dir /home/mike/<7 different things here>

Then if I select OK here or no earlier I go tight back to the log in screen.


I think I know what is wrong in here but I don't know what I did or how to undo it... preferably do it right.

sda1 is my original boot and home partition
sda3 is the partition I intended to be /home

When I open sda3 in the file browser all I see is 'lost+found'

[QUOTE=If I try to open that file all I get is...]The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "lost+found". [/QUOTE]

Now if I go into sda1 I see my home file and home_backup. 2 separate files in sda1.  If I open home I only find another home_backup... in there is mike, in there is desktop and documents.  This seems to have everything I'm afraid to lose.

In the other home_backup it seems like some things are missing.

Anyone have any ideas to save my system?

Thanks.

---

### Post by hortstu on 2010-02-12
I hope someone can help me with this tonight... 

Please if you have any ideas or can suggest more information that I should post please speak up.

---

### Post by hortstu on 2010-02-12
I followed the directions at the bottom of the page for starting up in recovery mode and for the first entry...

```
chown -R username:username /home/username
```

It replies something about the directory not existing or being found.

I also followed the directions at the very bottom on what to do as a last resort with a live cd.  No luck.

I'm hoping I don't have to start from scratch.

---

### Post by jken146 on 2010-02-13
OK, let me get this straight. Root is /dev/sda1 and you want /dev/sda3 to be /home. You have /home/home_backup/mike, which contains what you want to keep. You also have /home_backup, which may be incomplete.

At the log in screen, press ctrl+alt+F1 to get a text login prompt. You should be able to log in there. Then you should mount the new partition and move over your files.
```
sudo mkdir /mnt/sda3 && sudo mount /dev/sda3 /mnt/sda3 && sudo cp -r /home/home_backup/* /mnt/sda3/
```
Check that everything copied over ok ```
ls /mnt/sda3/mike
```
(that's a bit superficial but I hope you get the idea)

Then move things out of the old /home directory.
```
sudo mv /home/home_backup /home_backup2
```

Now re-mount sda3 in the correct place
```
sudo umount /dev/sda3 && sudo mount /dev/sda3 /home
```

Then add an entry in /etc/fstab
```
sudo nano /etc/fstab
```

Add a line like this:
```
/dev/sda3 /home/ ext3 defaults 0 0
```

---

### Post by hortstu on 2010-02-13
Thanks jken,

I'll be back in a few moments to let you know what happened.

---

### Post by hortstu on 2010-02-13
OK i tried the first few commands and I don't think I explained the file hierarchy clearly enough.  This is what I can see from the boot disk.

sda1 aka boot> home > (nothing...empty now)

sda1> home_backup> home

sda1> home_backup> home-backup> home_backup> mike(user name)> desktop and documents (doesn't appear to be complete)

sda1> home_backup> mike> desktop+ others (appears to be complete)

Sorry for the misunderstanding.  Completely my fault and I'm thinking I screwed this up with a bunch of typos?

---

### Post by hortstu on 2010-02-13
> **jken146 said:**
> OK, let me get this straight. Root is /dev/sda1 and you want /dev/sda3 to be /home. You have /home/home_backup/mike, which contains what you want to keep. You also have /home_backup, which may be incomplete.

```
sudo mkdir /mnt/sda3 && sudo mount /dev/sda3 /mnt/sda3 && sudo cp -r /home/home_backup/* /mnt/sda3/
```

I wrote this instead since I think this is what you're trying to get me to accomplish, I wrote all of them separate...

```

sudo mkdir /mnt/sda3 
sudo mount /dev/sda3 /mnt/sda3
sudo cp -r /home_backup/mike/* /mnt/sda3/
```

Now it's hanging here without a prompt.

just realizing that /home_backup/mike/* exists in two places and both seem to be different.  I think I'm going to have to come back to this after some sleep.

---

### Post by jken146 on 2010-02-13
It's copying. Give it time.

By the way, the && just means that the first command has to be successful before the second one will start.

---

### Post by hortstu on 2010-02-13
> Can't create directory.  No space left on device.
  This is starting to make a little sense to me now.  I'm thinking I should resize the partitions and/or delete some of these files that are duplicated.  Can I do that from the live CD?

---

### Post by jken146 on 2010-02-13
Yes, you can. Use gparted (it's in the System menu as Partition Editor).

---

### Post by hortstu on 2010-02-13
Where and what is the system looking for when I boot, that isn't there?  Where should it be and what should it be named?

---

### Post by Girya on 2010-02-13
> **hortstu said:**
> Where and what is the system looking for when I boot, that isn't there?  Where should it be and what should it be named?

I've had this problem before. I think you have a permission problem with your home directory. I think it came from running some ofthe commands from the psychocat tut. as the wrong user: as root instead of <user> or vice versa.

what does your /etc/fstab look like? is the hoem dir getting mounted? 

I **think** this worked for me.

> 

	
I solved the problem by running the follwing...

>>>as root
chown <myusername> /home/<myusername>
>>>as <myusername>
chmod 700 /home/<myusername>



from: [http://http://www.linuxquestions.org/questions/linux-general-1/users-home.dmrc-file-is-being-ignored.-589557/]("http://www.linuxquestions.org/questions/linux-general-1/users-home.dmrc-file-is-being-ignored.-589557/")

---

### Post by hortstu on 2010-02-13
Thanks Girya,

I'll try that after I'm done resizing the partitions

---

### Post by hortstu on 2010-02-13
> **Girya said:**
> 
I **think** this worked for me.



from: [http://http://www.linuxquestions.org/questions/linux-general-1/users-home.dmrc-file-is-being-ignored.-589557/]("http://www.linuxquestions.org/questions/linux-general-1/users-home.dmrc-file-is-being-ignored.-589557/")

I think I'm going to need some clarification.  I went to the login page.  Then <ctrl+alt+f1>

logged in and I'm looking at 
```
mike@mike-laptop:/$
```
How do I get to root from here?

I think I got there... cd root resutled in...

mike@mike-laptop:/root$

---

### Post by hortstu on 2010-02-13
so I entered the first line you suggested...

chown <myusername> /home/<myusername>

and got this result

missing operand after mike/home/mike

---

### Post by jken146 on 2010-02-13
> **hortstu said:**
> I think I'm going to need some clarification.  I went to the login page.  Then <ctrl+alt+f1>

logged in and I'm looking at 
```
mike@mike-laptop:/$
```
How do I get to root from here?

I think I got there... cd root resutled in...

mike@mike-laptop:/root$

The root of the file system is just /
There is also the /root directory, which is like a home directory for the user root. You can ignore /root

It doesn't matter which directory you're in if you give the full path to files you want to use. So, (this is just an example): ```
mike@mike-laptop:/$ cd /etc/apt
mike@mike-laptop:/etc/apt$ cat sources.list
``` would do exactly the same as ```
mike@mike-laptop:/$ cat /etc/apt/sources.list
```

> so I entered the first line you suggested...

chown <myusername> /home/<myusername>

and got this result

missing operand after mike/home/mike 

It looks like you missed out a space. ```
chown -R mike:mike /home/mike
```

---

### Post by hortstu on 2010-02-13
```
chown -R mike:mike /home/mike
```

Entered that and it says 

cannot access no such file or directory

I think everything got renamed funny when I tried following psychocats tutorial and maybe misspelled things.

This is what I see when I'm looking at the drive from the live cd.

---

### Post by hortstu on 2010-02-13
OK so now via the live cd I've learned that I've moved something to sda3

Here's what I have, again I don't know what the system is looking for when it boots so I don't know what to change the name of in order to make this happen properly.

I'm using the A1,A2,A3,A4,B1... just for easy reference purposes

A1  sda1> home > (nothing visble to me)

A2  sda1> home_backup> home> (nothing visible to me)

A3  sda1> home_backup> home-backup> home_backup> mike(user name)> desktop and documents (doesn't appear to be complete)
<~everything in here is in A4 +some so I imagine I could delete this but I'm not allowed to via point and click.  How do I do it via terminal?>

A4  sda1> home_backup> mike> desktop+ others (appears to be complete)
<this is the one that has all the stuff I don't want to lose.>

Now here is what I have on SDA3, the partition I intended to be the new home.

B1  sda3> home_backup> mike> desktop+ others
<this is the one that has all the stuff I don't want to lose.  It is the same as A4>

B2  sda3> home_backup> home-backup> home_backup> mike(user name)> desktop and documents
<This is the same as A3, don't think I need anything in it but what do I know?>

---

### Post by oldfred on 2010-02-13
You need to have the correct entry in fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

to see your UUID's which are used by fstab.
blkid 

You may want to make a copy before editing:
sudo cp /etc/fstab /etcfstab.backup
Then look for your /home entry and update with the correct UUID
gksudo gedit /etc/fstab

---

### Post by hortstu on 2010-02-13
Thanks oldfred,

Dont get everything you just said but I'll look at the fstab link and then I'll come back

---

### Post by hortstu on 2010-02-13
> **oldfred said:**
> You need to have the correct entry in fstab.

How do I know what the correct entry is?

> Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

What I'd really like to see is some example of what fstab is supposed to look like.  Mine doesn't say anything about UUID's.

> to see your UUID's which are used by fstab.
blkid 

I see the 4 partitions here with some long id numbers.  

> 
You may want to make a copy before editing:
sudo cp /etc/fstab /etcfstab.backup

Done thank you.

> Then look for your /home entry

I know how to find home by point and click but not via terminal and it seems like I have multiple homes now.

 > and update with the correct UUID
gksudo gedit /etc/fstab

So I'm going to update fstab with the UUID of the partition that has home on it.

My fstab is 3 lines
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Maybe this is the fstab of the live cd the system is running on?

---

### Post by hortstu on 2010-02-14
Well it looks like I should reinstall and start from scratch.

There are some files in here I'd like to save for my fresh install but I don't seem to have permission to move them.  

can anyone tell me how to move the contents of 

sda1/home_backup/mike

to an external with a newly created ext3 partition recognized sdb8 via the terminal?

After I'm sure I have that saved I'll just start from scratch.

---

### Post by hortstu on 2010-02-14
I think I figured it out thanks to an earlier post in this thread from jken...

sudo mkdir /mnt/sdb8 
sudo mount /dev/sdb8 /mnt/sdb8
sudo cp -r /media/disk/home_backup/mike/ /mnt/sdb8

unfortunately the drive ran out of space.

---

### Post by louieb on 2010-02-14
Sorry but I'm really confused. Its real hard to tell what went wrong. Or what you need to to fix it. But try the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

As far copying files you can use use the live CD and the file browser - Nautilus to cut and paste to your backup drive.

In the terminal the copy command would look like 

```
cp -a <source directory> <dest directory> 
```

the -a switch tells cp to copy recursively and to preserve ownership and permissions.

---

### Post by hortstu on 2010-02-14
> Sorry but I'm really confused.

Don't be sorry louie... I appreciate all of the attempts to help me... I've really gotten myself into one though.

 > Its real hard to tell what went wrong. Or what you need to to fix it. But try the Boot Info Script: How to and put the results.txt file in your next post.

THanks again but don't know how to get that text file.
just realized that was a link... really tired last night. get back with that later.


In the terminal the copy command would look like

> cp -a <source directory> <dest directory>

the -a switch tells cp to copy recursively and to preserve ownership and permissions. 

Thanks that will come in handy

---

### Post by hortstu on 2010-02-14
Here's the boot script if anyone has any suggestions.

```
Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bfd06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   165,148,199   165,148,137  83 Linux
/dev/sda2         300,415,500   312,576,704    12,161,205   5 Extended
/dev/sda5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris
/dev/sda3         212,266,845   300,415,499    88,148,655  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x531d9fcc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   320,159,384   320,159,322  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74e3c250-12d0-4313-ae9c-1d6e7b2f63bb   ext3                                     
/dev/sda3        5ec01415-5915-4e99-8d9c-f91c2262a279   ext3                                     
/dev/sda5        300acce5-0b6b-409a-a1f8-a463045a0e2d   swap                                     
/dev/sdb1        a8ae8287-4ef1-4ba5-87f4-9c43744b04d6   ext3       data                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/data              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1        /mnt/sdb1                ext3       (rw)
/dev/sda3        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=300acce5-0b6b-409a-a1f8-a463045a0e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

/dev/sda3 /home/ ext3 defaults 0 0


=================== sda1: Location of files loaded by Grub: ===================


  34.1GB: boot/grub/menu.lst
  34.1GB: boot/grub/stage2
  34.1GB: boot/initrd.img-2.6.24-23-generic
  34.1GB: boot/initrd.img-2.6.24-23-generic.bak
  34.1GB: boot/initrd.img-2.6.24-26-generic
  34.1GB: boot/initrd.img-2.6.24-26-generic.bak
  34.1GB: boot/initrd.img-2.6.24-27-generic
  34.1GB: boot/initrd.img-2.6.24-27-generic.bak
  34.1GB: boot/vmlinuz-2.6.24-23-generic
  34.1GB: boot/vmlinuz-2.6.24-26-generic
  34.1GB: boot/vmlinuz-2.6.24-27-generic
  34.1GB: initrd.img
  34.1GB: initrd.img.old
  34.1GB: vmlinuz
  34.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

---

### Post by louieb on 2010-02-14
1st thing I would try is comment out the /home entries in /etc/fstab (the last 2 lines) - you have 2 for some reason - should have only one at the most. Put a # in column 1 of those lines. Hopefully that will get you back to where you started before trying to create a separate home. You can get your stuff backed up and try again.   

 ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=300acce5-0b6b-409a-a1f8-a463045a0e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR="Red"]/dev/sda3 /home ext3 nodev,nosuid 0 2

/dev/sda3 /home/ ext3 defaults 0 0[/COLOR]



```

---

### Post by hortstu on 2010-02-14
Louie,

So you're saying I should add those 2 red lines to my fstab file?

> Put a # in column 1 of those lines.

Or are you saying put a # sign in front of one of those lines?

I'm sorry I know I use sudo gedit to open the file but I don't know exactly how to open a savable version of it.

> You can get your stuff backed up and try again. 

Yeah I think I backed it up to an external with the info you gave me last night... thanks again for all your help

---

### Post by louieb on 2010-02-15
Put a # sign in front.  You added the lines now you need to go back and remove or comment out both.

the file is in partition sda1.  name /etc/fstab

Open the file browser as administrator to get to it so you can edit it.

```
gksu nautilus
```

Also looking at the fdisk output seems sda3 the partition your trying to put /home in should to be larger. and sda1 your root only needs to be about 10 - 15 GB.
Don't know how much data you have but might be easiest to set your partitions up the way you want  and do a clean install.

---

