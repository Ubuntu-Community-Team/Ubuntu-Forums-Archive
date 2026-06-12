---
title: "XP Compatible Drive - NTFS, Whats wrong?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by jzacsh on 2009-06-19
Hello,

I have a tower with two drives in it. Ubuntu 9.04 is installed beautifully on one of the drives.

I popped in my Windows XP CD, because I'd like to install it on the other drive, and rebooted. Once I booted from the XP install CD, using "setup" I hit "c" for "create partition" on the drive that wasn't formated (the empty one without ubuntu). Even though I partitioned that drive with Setup's help, Setup told me:
> To install Windows on the partition you selected setup must write some startup files to the following disk:
xxxxx MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP compatible partition.
To continue installing Windows XP, return to the partition selection screen, and create a Windows XP-compatible partition on the disk above. If there is no free space on the disk, delete an existing partition and then create a new one.
To return to the partition selection screen, press ENTER.

So I thought, okay maybe it can't write an NTFS from scratch. So I booted into Jaunty, and installed "gparted" and "ntfsprogs" via synaptic package manager. I then used gparted to make that drive an NTFS drive. I rebooted using the XP install cd, and still I get the same error message. What should I do? does this have anything to do with me using ubuntu? or is this my lack of understanding Windows only?

Thanks in advance for any help!

---

### Post by ohzopants on 2009-06-19
For dual booting you have to start with Windows first.  I'm not sure you can do it while still preserving your current installation.

Sorry.

---

### Post by juanoleso on 2009-06-19
I would try using gparted and create a small 100MB primary partition ntfs format before your Ubuntu ext3 partition and then try installing windows.  I'm pretty sure windows setup expects that first primary partition on the boot HDD to be ntfs.

BTW, windows setup would then overwrite the MBR on the boot HDD which you would have to "reinstall" grub.  You can follow these instructions here: [[COLOR="Blue"]https://help.ubuntu.com/community/GrubHowto[/COLOR]]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by ainsworth_t on 2009-06-19
Basically what that message is saying is that it can't update the bootloader on the first disk with the new Windows XP install entry. This is because you installed Ubuntu first, which installed GRUB as the bootloader on the first disk. Not only is GRUB not recognized by Windows as a bootloader (since Windows can only write to it's own NTLDR bootloader) but GRUB resides on an ext3 formatted partition (which is not a partition format that Windows recognizes).

So just like ohzopants said, you must install Windows first. I would recommend installing Windows first on the first disk, then coming back and installing Ubuntu on the second disk.

This way, the Ubuntu installation process will recognize the existing Windows installation and will then install GRUB to the first disk and write the appropriate bootloader entry for both Ubuntu and Windows.

---

### Post by jzacsh on 2009-06-21
wow, i totally wouldn't have known any of this, or to query for any of this on my own. awesome, thank you everyone for the explanation. especially the details about the boot loader!

:)
cheers.

---

### Post by presence1960 on 2009-06-21
switch the boot order of your disks in BIOS so that the disk you want to install windows onto is first. You probably have the Ubuntu hard disk set as first boot in the order so of course windows needs to write to that disk. You **DO NOT HAVE TO INSTALL WINDOWS FIRST!! THAT IS BOLDERDASH!** Then after you install windows switch the order back in BIOS. Then reinstall GRUB if necessary:

> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

You will probably have to add your windows entry to menu.lst manually. Don't forget to add the map lines in the entry so windows will think it is on the first boot device. Here is mine:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

I don't know where this stuff started that you MUST install windows first, but the fact remains that you can install either OS first. Some searching of our forum and some googling will turn up some info to show you how to do it. Do not limit yourself. What happens if your windows goes south on a dual boot? do you have to uninstall Linux too so you can reinstall windows? If you want to do it that way be my guest, but there is another way to do it.

P.S. I'll provide one of many topics on this subject : [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
     It's not my favorite but it is a start.

Here is one straight from our community documentation : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jzacsh on 2009-06-21
> **presence1960 said:**
> switch the boot order of your disks in BIOS so that the disk you want to install windows onto is first. You probably have the Ubuntu hard disk set as first boot in the order so of course windows needs to write to that disk. You **DO NOT HAVE TO INSTALL WINDOWS FIRST!! THAT IS BOLDERDASH**

Oh! awesome save, thanks presence1960 - I would've started my week off kind of sad tomorrow (having to re-set-up my ubuntu installation).

---

### Post by presence1960 on 2009-06-21
> **jzacsh said:**
> Oh! awesome save, thanks presence1960 - I would've started my week off kind of sad tomorrow (having to re-set-up my ubuntu installation).

No problem, I would hate for you to have to do all that work for nothing!

---

### Post by egalvan on 2009-06-22
> **presence1960 said:**
> 
**I don't know where this stuff started** that you MUST install windows first, but the fact remains that you can install either OS first

Probably the same place that the "balderdash" about "32bit systems can see/use a  max of 4GB RAM" :)

It's true that it's EASIER to install Windows first, because GRUB/Linux play well with others, while MS-Windows does not.
MS-Windows expects to be the ONLY system, and it expects to be on the FIRST drive.

GRUB/Linux don't mind sharing, and don't mind being loaded onto any drive in the computer.


People often have a problem, stumble onto a solution, but don't really understand either the problem or the solution.
And then they like to think that their solution is the only one.
And it soon turns into "balderdash" :)
But many believe it!

Thanks, presence1960.

EGalvan

---

### Post by ohzopants on 2009-06-22
Opps... I misread that to read that he had 2 PARTITIONS.

Sorry to have misinformed you.  Presence's way of doing it will most definitely work with your setup.

---

### Post by presence1960 on 2009-06-22
> **ohzopants said:**
> Opps... I misread that to read that he had 2 PARTITIONS.

Sorry to have misinformed you.  Presence's way of doing it will most definitely work with your setup.

Even if it were two partitions on the same drive you can install Ubuntu first!

---

### Post by caue.rego on 2009-06-22
> **juanoleso said:**
> I would try using gparted and create a small 100MB primary partition ntfs format before your Ubuntu ext3 partition and then try installing windows.  I'm pretty sure windows setup expects that first primary partition on the boot HDD to be ntfs.

BTW, windows setup would then overwrite the MBR on the boot HDD which you would have to "reinstall" grub.  You can follow these instructions here: [[COLOR="Blue"]https://help.ubuntu.com/community/GrubHowto[/COLOR]]("https://help.ubuntu.com/community/GrubHowto")

To disagree with "windows expects to be first primary partition"...

I've got just 1 hard disk. I've installed Jaunty first, on the first primary partition, swap on an extended one, and /home on a yet third partition leaving a fourth (primary) partition for installing windows later. Once I did install windows it took over MBR as expected and it worked with no problems while leaving ubuntu inaccessible, of course.

Then all I needed to do is what **presence1960** already said, to reinstall grub.

---

### Post by jzacsh on 2009-06-22
> **presence1960 said:**
> switch the boot order of your disks in BIOS so that the disk you want to install windows onto is first. You probably have the Ubuntu hard disk set as first boot in the order so of course windows needs to write to that disk.[...]Then after you install windows switch the order back in BIOS. Then reinstall GRUB if necessary[...]
Awesome! this worked out perfectly. I changed the order of the hard disks in the bios, XP's setup ran smoothly, and when finished, I changed the bios back (*didn't have to reinstall GRUB*).

_Only one last question_: how do I create a boot menu? (something where the user can decide what disk,partition, etc. to boot into when the computer turns on, *I assume in this boot menu I'll be able to specify which is highlighted by default*). I've read in a few places that I simply need to sudo edit the file /boot/grub/menu.lst. I've also seen somewhere the mention of simply typing "grub" at the command line. If I had to edit the menu.lst file, then what will I place into that file? obviously I can't just write "windows xp" and expect the computer to know what the heck I mean. I've attached my current menu.lst for reference (don't worry, its a txt only because the forum attachment uploader gave me a "invalid file" error).

**thanks again!**

*ps. I've installed Windows XP Pro onto the second drive.*

---

### Post by caue.rego on 2009-06-22
> **jzacsh said:**
> Awesome! this worked out perfectly. I changed the order of the hard disks in the bios, XP's setup ran smoothly, and when finished, I changed the bios back (*didn't have to reinstall GRUB*).


you didn't need to redo GRUB because you've installed windows in a different disk. but you still need to configure it if you want to dual boot and have installed ubuntu before windows.

as for your question, you might want to try what **juanoleso** already told you ( [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) ) or a link from that, also already referenced by **presence1960**: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

anyway, I'll give you the most relevant part from those:
```

title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
 rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
 makeactive
 chainloader +1

```

but you'll need to figure out where is yours and change the (hd0,0), at very least.

I'm sorry I don't know an easier way to do this, as I would also expect a nice GUI for doing this.

---

### Post by juanoleso on 2009-06-22
> 
To install Windows on the partition you selected setup must write some startup files to the following disk:
xxxxx MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP compatible partition.


He has two HDD, not one, and just like the error says, because his boot HDD did not have an NTFS partition on it, windows setup won't install the MBR and errors out (for whatever closed source proprietary reason).

Switching the settings in the BIOS is easier, though and I'm glad the initial myth was cleared.

---

### Post by egalvan on 2009-06-22
> **jzacsh said:**
> 
_Only one last question_: how do I create a boot menu?
 (something where the user can decide what disk,partition, etc. to boot into when the computer turns on, 

You already have a "boot menu", it's just hidden....

[B]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu[/COLOR][/B]

find the above stanza and change the red line to:

[B]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#hiddenmenu[/COLOR]
[/B]

You can also press the "esc" key immedialy after GRUB starts, but it's easy to miss this....
Showing the menu is easier, IN MY OPINION.

For myself, I also change these stanzas...
totally personal choices...IN MY OPINION...

[B]# Pretty colours
[COLOR="Red"]#color cyan/blue white/blue[/COLOR][/B]

to this...

[B]# Pretty colours
[COLOR="Red"]color cyan/blue white/blue[/COLOR][/B]


and I change the timeout value to higher number...

[B]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		3[/COLOR][/B]


[B]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		30[/COLOR][/B]


There are many others... herman as an EXCELENT web site...
chekc it out

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)



As for automatically adding Windows XP, you can find some info on herman's site...

basically, you need something like the following stanza
(this is from my dual-boot... yours **WILL** be different.)

[B]title		WinXP Pro
root		([COLOR="Red"]hd0,0[/COLOR])
savedefault
makeactive
chainloader	+1[/B]

---

### Post by jzacsh on 2009-06-22
> **caue.rego said:**
> but you'll need to figure out where is yours and change the (hd0,0), at very least.

When I get home tonight, I'll look further into the articles linked here, thanks everyone. but there isn't some command I can execute to view a list of the drives and the labels assigned to each?

---

### Post by egalvan on 2009-06-22
> **jzacsh said:**
> ..isn't some command I can execute to view a list of the drives and the labels assigned to each?

This is one way...

```
sudo blkid
```


this one gives different info...

```
fdisk -l
```

that is a lower-case L, not a numeral 1

---

### Post by presence1960 on 2009-06-22
> **jzacsh said:**
> Awesome! this worked out perfectly. I changed the order of the hard disks in the bios, XP's setup ran smoothly, and when finished, I changed the bios back (*didn't have to reinstall GRUB*).

_Only one last question_: how do I create a boot menu? (something where the user can decide what disk,partition, etc. to boot into when the computer turns on, *I assume in this boot menu I'll be able to specify which is highlighted by default*). I've read in a few places that I simply need to sudo edit the file /boot/grub/menu.lst. I've also seen somewhere the mention of simply typing "grub" at the command line. If I had to edit the menu.lst file, then what will I place into that file? obviously I can't just write "windows xp" and expect the computer to know what the heck I mean. I've attached my current menu.lst for reference (don't worry, its a txt only because the forum attachment uploader gave me a "invalid file" error).

**thanks again!**

*ps. I've installed Windows XP Pro onto the second drive.*

first edit your menu.lst file and add this to the end after ### END DEBIAN AUTOMAGIC KERNELS LIST:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

to set a default OS look here in menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

zero is first OS in your OS list of menu.lst - so in mine :
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,2)
chainloader     +1
```

0 would be kernel 2.6.28-13, 1 would be kernel 2.6.28-13 recovery mode, etc. You can do it this way or use startup manager- aGUI program for this and much more. Open a terminal and run > sudo apt-get install startupmanager Once installed you can find it by going System > Administration > StartupManager or running > gksu startupmanager in terminal.

Glad you got it working and saved yourself a whole mess of work too. Now you know the truth, don't let others remain ignorant- Windows can be installed after Linux!

---

### Post by presence1960 on 2009-06-22
> **egalvan said:**
> Probably the same place that the "balderdash" about "32bit systems can see/use a  max of 4GB RAM" :)

It's true that it's EASIER to install Windows first, because GRUB/Linux play well with others, while MS-Windows does not.
MS-Windows expects to be the ONLY system, and it expects to be on the FIRST drive.

GRUB/Linux don't mind sharing, and don't mind being loaded onto any drive in the computer.


People often have a problem, stumble onto a solution, but don't really understand either the problem or the solution.
And then they like to think that their solution is the only one.
And it soon turns into "balderdash" :)
But many believe it!

Thanks, presence1960.

EGalvan

It is true what you say. The sad part is that this guy or gal almost removed a perfectly good OS for nothing. Not only are there a lot of sites turned up for a google search of this, but our own Ubuntu community documentation has info on how to install windows after Linux. I learned how to google and search our forum early on. I have never had to start a thread for any problem I have ever had ( and God knows I have them). I just read the threads turned up in the search or the sites turned up in Googling and it worked. But best of all I started to learn the nature of the problem and not only the solution- but also why the solution works.

There are some really knowledgeable people in this forum, but the bonus is a lot of them are good teachers too. You are included in there, but there are too many to name them all. A few that inspired me that I haven't seen in here for a while are meierfra, unutbu and caljohnsmith. Probably because we are lurking in different parts of the forum. 

Well anyway thanks for helping this person so he/she can now get on with enjoying & learning how great Linux can be.

---

