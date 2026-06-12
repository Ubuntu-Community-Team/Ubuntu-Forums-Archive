---
title: "Ubuntu-Vista dualbooting: Error 23"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Flakz on 2009-12-03
Hey all,

I've been having issues configuring GRUB for dualbooting(I've been meaning to play a game for 3 hours now:P) I've tried various different things, but a newbie like meself can't seem to find anything. I have gotten different messages, such as GRUB saying Starting Up... And staying there.

These are the contents of my menu.lst:
```

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=540aaba4-f146-4d12-a5e0-4e1144710f0c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=540aaba4-f146-4d12-a5e0-4e1144710f0c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        540aaba4-f146-4d12-a5e0-4e1144710f0c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=540aaba4-f146-4d12-a5e0-4e1144710f0c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, memtest86+
uuid        540aaba4-f146-4d12-a5e0-4e1144710f0c
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
title        Windows Vista
root        (sd0,0)
savedefault
makeactive
chainloader    +1

```And this is my fdisk:
```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15791578

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd73a19ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

---

### Post by kansasnoob on 2009-12-03
Can you boot Ubuntu?

Or nothing at all?

---

### Post by Flakz on 2009-12-03
> **kansasnoob said:**
> Can you boot Ubuntu?

Or nothing at all?
Ubuntu boots up just fine.

It's where I'm posting this from :)

---

### Post by kansasnoob on 2009-12-03
Just wanted to be sure.

To edit the menu.lst run the command:

```
gksudo gedit /boot/grub/menu.lst
```

I think your Windows entry should be changed to:

> title        Windows Vista
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


I'd also comment out the hidden menu option like below (used red only for visibility):

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu



---

### Post by Flakz on 2009-12-03
> **kansasnoob said:**
> Just wanted to be sure.

To edit the menu.lst run the command:

```
gksudo gedit /boot/grub/menu.lst
```I think your Windows entry should be changed to:



I'd also comment out the hidden menu option like below (used red only for visibility):

I've been using sudo instead of gksudo :P.

Well, I made the changes you recommended, and while I now have a nifty border around my bootmenu, I still can't start Vista. :(

I don't get an error message now, but when I press enter on Vista it just flickers for a millisecond, showing me it registers the press of the button, but nothing happens.

---

### Post by hal10000 on 2009-12-03
Maybe you have to set the boot-flag to boot from /dev/sdb1

---

### Post by lidex on 2009-12-03
Have a look here:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by Flakz on 2009-12-03
> **hal10000 said:**
> Maybe you have to set the boot-flag to boot from /dev/sdb1
Does that mean I have to reinstall and add it there? Or if there's another way, could you explain please?

---

### Post by kansasnoob on 2009-12-03
> **Flakz said:**
> I've been using sudo instead of gksudo :P.

Well, I made the changes you recommended, and while I now have a nifty border around my bootmenu, I still can't start Vista. :(

I don't get an error message now, but when I press enter on Vista it just flickers for a millisecond, showing me it registers the press of the button, but nothing happens.

Well, as I look at your fdisk -l again:

> Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15791578

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd73a19ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

I notice that there is no boot flag set on the only Win partition shown (sdb1).

Look at my multiboot:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       14879    36772753+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17870     6160896   83  Linux
/dev/sda12          17871       19457    12747546   83  Linux


So **I think** install gparted if it's not installed:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor. Toggle to sdb in the upper right hand corner then right click on sdb1 and click on Manage Flags.

The following screenshot should describe the rest better than words:

[ATTACH]138447[/ATTACH]

Be sure to check on Boot, then close, then click on Apply (the big green check mark).

Hopefully that will work, if not I'll need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by hal10000 on 2009-12-03
> Does that mean I have to reinstall and add it there? Or if there's another way, could you explain please?

No, you can use a partitioning tool (e.g gparted, parted, fdisk etc.) to do that.

---

### Post by kansasnoob on 2009-12-03
> **hal10000 said:**
> Maybe you have to set the boot-flag to boot from /dev/sdb1

+1!

I missed that on his fdisk -l and only looked at the errors in the menu.lst.

---

### Post by Flakz on 2009-12-03
> **kansasnoob said:**
> Well, as I look at your fdisk -l again:



I notice that there is no boot flag set on the only Win partition shown (sdb1).

Look at my multiboot:



So **I think** install gparted if it's not installed:

```
sudo apt-get install gparted
```It'll then show up in System > Administration > Partition Editor. Toggle to sdb in the upper right hand corner then right click on sdb1 and click on Manage Flags.

The following screenshot should describe the rest better than words:

[ATTACH]138447[/ATTACH]

Be sure to check on Boot, then close, then click on Apply (the big green check mark).

Hopefully that will work, if not I'll need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Well, I installed Gparted, and there is a boot flag at sdb now, but I still can't boot into Vista.

So I did that bootscriptthing and here it is : [http://pastebin.com/m4471971b](http://pastebin.com/m4471971b)

---

### Post by kansasnoob on 2009-12-03
OK, you still have some problems in your menu.lst, but it's going to take me a little while.

Please be patient.

---

### Post by Flakz on 2009-12-03
> **kansasnoob said:**
> OK, you still have some problems in your menu.lst, but it's going to take me a little while.

Please be patient.
Hey, not gaming isn't going to kill me!(Soon, at least)

---

### Post by kansasnoob on 2009-12-03
You must be cautious editing system files!

Look at this section (none of the stuff in red should be there):

> ## timeout sec[B][COLOR="Red"]title Windows Vista
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 [/COLOR][/B]
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

That section should look like:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

Also at the very bottom change this (you left off the "chainloader +1" but lets be picky):

> ### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows Vista
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)

To this (exactly):

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows Vista
root  (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

BTW you can actually use either sudo or gksudo for that specific file. Just be sure to click on Save, then File > Quit.

To double check your work just run:

```
cat /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2009-12-03
If this entry:

> title Windows Vista
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

doesn't work try adding "noverify" to "root" like this:

> title Windows Vista
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Just be careful and precise!

---

### Post by namok on 2009-12-03
You do not have some startup files of the vista. Your:> sdb1: _________________________________________________________________________
File system:       ntfs
Boot sector type:  Windows XP
Boot sector info:  No errors found in the Boot Parameter Block.
Operating System:  Windows Vista
Boot files/dirs:   /Windows/System32/winload.exe[IMG]http://www.google.pl/images/cleardot.gif[/IMG]
Original: > sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:[COLOR=Red]   /bootmgr /Boot/BCD[/COLOR]   /Windows/System32/winload.exe


---

### Post by kansasnoob on 2009-12-03
> **namok said:**
> You do not have some startup files of the vista. Your:[IMG]http://www.google.pl/images/cleardot.gif[/IMG]
Original:

Arrgh, that I don't know how to fix!

---

### Post by namok on 2009-12-03
This can be useful: [http://support.microsoft.com/?scid=kb%3Ben-us%3B927391&x=11&y=12](http://support.microsoft.com/?scid=kb%3Ben-us%3B927391&x=11&y=12)

---

### Post by Flakz on 2009-12-03
> **kansasnoob said:**
> Arrgh, that I don't know how to fix!
Yeah, I ran into some issues too. I kept getting the message NTLDR is missing, which on one hand means that the system is booting into Vista, but on the other hand means it still can't.

And for some reason I can't reinstall Vista, it keeps saying it can't find a volume that meets installation requirements :?

---

### Post by kansasnoob on 2009-12-03
Can you use the Startup Repair as explained here:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

I really don't know a lot about Vista.

---

### Post by kansasnoob on 2009-12-03
This also looks fairly "in depth":

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by Flakz on 2009-12-07
Okay, I've finally fixed it. After getting 3 new Windows 7's and whatnot, I decided to do a F'ck it move and just remove my ubuntu HDD. It worked.

Still need to edit my menu.lst so GRUB says Windows 7 instead of Vista though.

---

