---
title: "grub error 17 after resizing windows XP"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-02-08
Hi don't want to screw it up any more than it already is I thought I should come to the pros here.

Dual booting XP/Ubuntu 8.10, have Live CD. I even made a Supergrub USB but something odd seems to have happened to it and  after once being able to use it (tried to boot the XP partition but got the onboard diagnostics program ran then rebooted and since I've found I can't boot from the USB drive and when I stick it into another XP system, comes as being unformatted.

Not realising that a partition editor existed already in Ubuntu, I made a new partition from some extra space in the XP partition using a Windows platform program (meaning to add it to Ubuntu later).  New partition was made, but next time I tried booting I got error 17, and can't boot either XP or Ubuntu.

I'd like to be able to return to booting from both partitions again (and eventually add the new partition I created to Ubuntu).  What do I do now?

---

### Post by paulchinnz on 2009-02-08
Here's the partition setup at the moment (using Live CD). The /dev/sda5 partition is the new one split off the XP /dev/sda2 partition.

---

### Post by CorvisRex on 2009-02-08
Well, Error 17 aint that worrying, it just means grub is confused about where to go.  Probably what happened was when you repartitioned the drive, now grub is looking in the wrong place for the partitions.  

first, check your menu.lst file is pointing everything to the right partitions.

Boot up from the LiveCD, 

go to console (or terminal app of your choice)
mount your SDA6 partition 

cd /media
sudo mkdir temp
sudo mount /dev/sda6 /media/temp

and check your /boot/grub/menu.lst file (sudo gedit /media/temp/boot/grub/menu.lst)

make sure your windows root is pointing to the right place (sda2?)
make sure your ubuntu stuff is pointing to the right place (sda6?)

if it is all ok, just reinstall grub to the MBR

in console do:
grub
root (hd0,5) [tells grub where the boot files are, in this case, the ubuntu partition]
setup (hd0) [sends that info to the first hard disk]
quit

and reboot this should reinstall your grub to the MBR...should work.

hope it helps.

---

### Post by CorvisRex on 2009-02-08
BTW, whats the fat32 partition for?

just curious.

---

### Post by paulchinnz on 2009-02-09
Thanks for your help and interest.

I'm a bit stuck on the ubuntu stuff pointing to the right place, as I can't see if it's being pointed anywhere at all. The following is a bit laborious but probably more useful than my clumsy explanation: it's a copy and paste of menu.lst contents.  As you can see the FAT32 partition harks back to the fact I'm running an Inspiron 640m.


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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=87d81434-bd60-4e1c-af69-e5abf15de2fb

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87d81434-bd60-4e1c-af69-e5abf15de2fb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by CorvisRex on 2009-02-09
Well, it looks like your menu.lst is set up right given the partition table that you posted. The UUID , BTW is a unique id for each partition that never changes, and so it should be alright,  The Windows entry look right too.  

You should be able to just reinstall grub  to the Master Boot Record (MBR) by doing what I put in the last post, 

grub
root (hd0,5)
setup (hd0)
quit

and reboot, it should then let you boot up.  If not, then there is something else wrong.  But that has worked for me EVERY TIME. Don't worry, it won't over write a partition, or wipe a drive or anything, it's safe.

Basically, any time you install windows after linux, and often times when you do any partition work in windows, it screws up the MBR,  those quick commands above just reset the mbr.  It is always a good thing to remember, i've had to do it a few dozen times, it's one of the reasons they always recommend you install linux after windows.  Just use gparted for your partitioning from now on, or use a windows partition/disk editor that knows linux partitions, like Acronis Disk Director.


Hope it helps.

---

### Post by paulchinnz on 2009-02-12
Thanks for the ongoing help. Unfortunately this is what I got:


grub> root (hd0,5)

Error 21: Selected disk does not exist


I also tried (hd0,6) with the same result. Where to now?

Also, you originally mentioned that the Ubuntu stuff should be pointing to sda6, but I can't see where on menu.lst it's indicating that (obviously I'm not looking at the right bit).

---

### Post by paulchinnz on 2009-02-12
By the way, going back to my partition table, why are sda5 to 7 subsets of sda3?

---

### Post by caljohnsmith on 2009-02-12
It looks like the problem might be that CorvisRex forgot to have you run "grub" as root user, i.e. how about trying instead:
```
[COLOR="Blue"]sudo[/COLOR] grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Please post the output of the commands before typing "quit". And by the way, your sda3 partition is what is know as an "extended" partition, meaning that it is the container for your logical partitions sda5, sda6 and sda7.

---

### Post by paulchinnz on 2009-02-12
Thanks. This is what I got:

START

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

END

By the way, could someone please point out where my Ubuntu stuff is being pointed at in menu.lst.

Going to reboot now.

---

### Post by paulchinnz on 2009-02-12
Thanks CorvisRex and caljohnsmith. Both Ubuntu and XP partitions booting.  Now if I wasn't such a noob I'd be able to lable this thread solved, but for some reason I don't have that option under thread tools.

Minor outstanding thread-related questions then:
1) Where does it say ubuntu's on sda6? in my menu.lst?
2) Where's solved gone?

---

### Post by CorvisRex on 2009-02-12
Opps, yup, forgot the sudo.  stupid brain...sorry about that.

---

### Post by CorvisRex on 2009-02-12
Actually, it doesn't...quite.  Ubuntu defaults to using UUID when it configures grub these days.  This is actually good, cause UUID is a unique ID for the partition.  Partition numbers like sda2 or sdb4 can get really messed up and confusing when you delete or create partitions.  Using the UUID, will stay the same, even after you start messing around with the partitions.  Problem is that it ain't very readable.  everything has a downside I guess.

---

### Post by paulchinnz on 2009-02-12
Thanks CorvisRex. So how could I have worked out that the UUIDs were correct?

---

### Post by CorvisRex on 2009-02-12
I always use:

ls -l /dev/disk/by-uuid/

or you can use

sudo vol_id -u device

where device is the partition you want to know about.  Like this:

sudo vol_id -u /dev/hdc3

I guess it gets created when the partition is created (??) and is never changed.  Good if you ever have to partition things, You never have to go and double check your sda? or whatever is right in the menu.lst.  Just not very readable. But I'm beginning to like it, since it solves some problems.

---

### Post by paulchinnz on 2009-02-13
Thanks again CorvisRex.

I really should start a new thread, but seeing as how you know the case pretty well now, how should I get round to combining my sda5 with sda6 partitions? Just playing around with GParted and can't find any option to do this.

---

### Post by CorvisRex on 2009-02-13
Well, your sda5 is NTFS (or so your screenshot says) I assume you want to kill the ntfs and make the sda6 bigger.There is no way to to merge ntfs it with an etx3 partition(sda6) only way is to move the contents of sda5 someplace else, it's only 64MB. Probably empty right?  Delete sda5, and resize sda6.  You'll have to do this from a live CD or something cause sda6 is your linux root patition.  

Boot from live cd
run gparted
delete sda5
Make sure sda6 is NOT mounted, if so,unmount (right click on the partition and unmount)
Resize sda6 (right click on the partition, and select "Resize/Move") should give you a nice little dialog box.

Shouldn't change you partition numbers or anything else that would screw up you boot, so you should be fine.  I've resized etc3 linux partitions all the time, never had a single problem doing it.

Of course backup anything important just to be safe.  never can be too safe.

Hope it helps

---

### Post by paulchinnz on 2009-02-13
Suffered through another grub error 17 after deleting sda5 and expanding  sda6 using gparted. Thanks to the fine instructions already available on this thread though (and my internet not being down for >48 hours this time) I was only unable to boot for a few minutes. 

Looks like what happened was that sda6 became sda5 (see the updated partition).

I had to make one change to the commands though:

grub> root (hd0,4)

rather than grub> root (hd0,5).

Questions: 
1) was there anything I could have done to prevent this second grub error 17
2) in (hd0,x), is x=partition number starting from most left-sided partition on drive

---

### Post by CorvisRex on 2009-02-13
Actually, yeah.  I guess that was why they use the UUID these days, since that doesn't ever change.If you use the UUID.  (I thought it was using the UUID), that is why I thought you shouldn't have a problem.  

without the UUID the grub entry would look like 

title Ubuntu 8.10, kernel 2.6.27-11-generic
root (0,5)
kernel /boot/vmlinuz-2.6.27-11-generic root=/dev/sda6 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

or whetever

With the UUID it would look like 

title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid 87d81434-bd60-4e1c-af69-e5abf15de2fb
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=87d81434-bd60-4e1c-f69-e5abf15de2fb ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

Notice that there are two places the UUID shows up.  Without using the UUID, it can screw with your menu.lst anytime you change the partitions.  By using the UUID instead of (hd0,5) or /dev/sda6, you totally avoid this problem, completely.  since the UUID does not change even after you fiddle with the partitions. That is why it is used these days.   Just  a pain, cause you have to find out what the uuid is, and it is not an easy id code to work with.

---

### Post by egalvan on 2009-02-14
> **CorvisRex said:**
> Actually, yeah.  I guess **that was why they use the UUID these days, since that doesn't ever change.**If you use the UUID.  (I thought it was using the UUID), that is why I thought you shouldn't have a problem.  


By using the UUID instead of (hd0,5) or /dev/sda6,** you totally avoid this problem, completely.  since the UUID does not change even after you fiddle with the partitions**. That is why it is used these days.   Just  a pain, cause you have to find out what the uuid is, and it is not an easy id code to work with.

Well, actually there ARE circumstances where the UUID can change when "fiddling around with partitions"
There was a thread last week about a user who had a terrible time getting his grub back in shape after "fiddling" with swap.
The UUID's had changed.
I remember reading a couple other threads like that...

What I use is LABELS. Similar to UUID,  but HUMAN made and applied.
Easy to see if they are changed.
Easy to see what "hardy-boot" or "8_04_home" is referring to.
(try that with *UUID=0844d680-d893-40fa-a01d-3c819f0b2zz5*
compare with *LABEL=swap*
No, they are not Unique.

Each has their place, but none are infallible.

(UUID's are truly Unique...they should never repeat... delete a partition and create it again, and it's Unique ID changes.
Useful at times.
I just don't remember if formatting a partition changes it's UUID)

---

### Post by CorvisRex on 2009-02-14
Really?  Good to know.  I know that the UUID is generated when the partition is created, or recreated.  But I didn't know if there was any time that it can be changed. A good thing to keep an eye on. And yeah, labels are a lot easier to deal with. Both cause me far less problems then the /dev/??? entries.

---

