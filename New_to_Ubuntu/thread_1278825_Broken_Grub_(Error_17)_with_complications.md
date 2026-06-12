---
title: "Broken Grub (Error 17) with complications"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by arachnic on 2009-09-30
Hi Folks !

_**Short story:**_
Grub Error 17.
SuperGrub Disk doesn't seem to work.
Dead DVD/CD drive.
Live USB usually fails.

_**Long Story:**_

 Toshiba Satellite A-215 S4757 (AMD Turion64/200GB HDD/Vista/etc)

_HD Partition Layout before the problem:_
SDA 1 - Toshiba System - 1.5 GB - primary
SDA 2 - Vista - 50 GB - ntfs - primary
SDA 3 - Extended
-           SDA 5 - 120 GB - ntfs
                        -           SDA 6 - 1 GB - Linux Swap
SDA 4 - Kubuntu 9.04 i386 - 14 GB - primary

The system was working fine(except no usb stick detection - usb HDs work fine) until I split up SDA 5 into two - 70 GB + 50 GB - using Easeus Partition manager from within Windows. It booted up, partitioned, then rebooted, and thats when I've been stuck with Grub Error 17.

I have a working XP/Ubuntu dual boot, FYI. To make Live USBs/Burn Disks/access forums/etc.

_What did I try so far:_
_1. SuperGrub Disk:_ Since I had converted a Wubi install to permanent using LVPM, following online advice, I had made a SuperGrub Disk Live USB. I tried a lot of options, followed instructions from various excellent webpages, but no go. From the posted screen shots I saw, its apparent that SGD does not go to where its next going.
Once I select the option - boot Linux, or Windows, or repair Grub, or whatever - it gets stuck with 
selectfile /grub/stage1 /boot/grub/stage1
or
similar stuff with fstab, etc.
Doesnt go anywhere.
This is before AND after deleting the new partition using GParted Live.

I dont know if this actually made any changes at all. Very probably not. But if it did, the place is now in more of a mess than before !
[U]
2.GParted Live USB[/U] (created using UnetBootIn)
Checked out the partition state. Saw that the new partition had been successfully created. But now the state was:
SDA 1 - Toshiba System - 1.5 GB - primary
 SDA 2 - Vista - 50 GB - ntfs - primary
 **SDA 4** - Extended
             -           [B]SDA 5 - 70 GB - ntfs
             [/B]            -           [B]SDA 6 - 50 GB - ntfs
            [/B]            -           **SDA 7 - 1 GB - Linux Swap**
 **SDA 3** - Kubuntu - 14 GB - primary

Hoping things would just restore back to normal, i deleted the SDA 6, so now the swap could go to being SDA 6. No Go.

SDA 1 - Toshiba System - 1.5 GB - primary
 SDA 2 - Vista - 50 GB - ntfs - primary
 **SDA 4** - Extended
                         -           SDA 5 - 120 GB - ntfs
                         -           SDA 6 - 1 GB - Linux Swap
**  SDA 3** - Kubuntu - 14 GB - primary

Since the GParted environment has a terminal, I tried going to the grub prompt and fiddling with it. (root (hd0,3), etc combinations ) No Go.

_3.Kubuntu Live USB_.
Used the Kubuntu Iso to make a Live USB using USBuntu (mindful that my earlier UNetBootIn Live USB didnt work, See Backstory below)
Get dumped into Busybox/Initramfs prompt.

(Note, that the simple GParted environment loads fine and works, but it doesn't allow access to the rest of the disk)

_What do I do now:_

From what my quick and forced education on this seems to tell me, the MBR now points to Grub where there is no longer any Grub, and while the Swap is back to being called what it used to be, the Linux root isnt.
Seems to me I need to reinstall Grub, and that should be it. I can even edit menu.lst manually after that if need be. But it doesnt seem to be happening.

_Options and Questions:_
a. How do I reinstall Grub and have things point to it correctly, as well as have it point to other things correctly ? Without a Live CD and Live USB, at that. (A Grub-only Live USB will probably work, its usually the full Live Installs that get dumped into Busybox)
b. Can/should I install Grub to its own tiny partition ?
c. I have an external USB HD, but it has no space (thats what I backed up onto before starting the install in the first place) Should I empty part of it and install Ubuntu/Live on that and use that.
d. I tried popping in the DVD drive of my other laptop, which works, into the problem Laptop, but while it goes fine most of the way, the front panel is a different shape so it doesnt go in all the way. Can I get some sort of connector cable that can hook up the drive to my motherboard direct or to a usb ? Then i could use the Live CD, i guess.
e. Get a new dvd drive, that is meant for this laptop, and use the Live CD.

Obviously I'd like to do this as fast and cheap as possible. There should be a software alternative here to buying more hardware.

Please help me sort this out. I am pretty new to Linux/(K)Ubuntu. Confused and unsure at times because I am new, yes. But I am willing to learn. And I am not very scared of the command line. And sorry about the length of the post.

Please refer to the Backstory below for more on How I got THIS FAR.

Thanks and Cheers
Arachnic.

__________________
**Backstory:**
I'll try to be as concise as possible, but I took a long and winding road so brevity may not be possible..

I have a Toshiba Satellite A-215 S4757 (AMD Turion64/200GB HDD/Vista/etc)
Recently installed Kubuntu : Even that was a complicated affair, because:
-Dead DVD/CD drive, so no Live CD
-Downloaded iso and used UNetBootIn to create Live USB: Kept getting dumped into Busybox/initramfs.
-Just to check if there was a problem with the iso or usb, I used the Live USB to install Ubuntu 9.04-i386 - very easily and successfully - on my other laptop(Compaq Presario/AMD Athlon/80 GB HDD/XP Pro/etc)
-Finally installed Kubuntu 9.04 i386 on Windows Vista using Wubi. Then used LVPM to convert the Wubi install to a permanent one. 
Got the error 17, looked it up and edited the menu.lst as instructed from inside the Wubi install.
Successful Vista/Kubuntu Dual Boot.
-Later uninstalled Wubi from Windows Vista.

Before I started attempting the Ubuntu install, I backed up all my stuff, repartitioned the single chunk(184 GB) into two(90 GB + 80 GB + 15 GB unallocated) Also discovered there is 1.5 GB partition containing Toshiba System or somesuch backup thing. I used Easeus Partition Maker to do this in Vista.

Next I moved more of my data from the Vista partition to the other one, intending to keep only Windows and Program files, and none of my personal media/data/etc on the Vista Partition. Then resized them to move more free space from the Vista to the other one.

I installed the From-Wubi-via-LVPM into the unallocated space (1 GB Swap/13.x GB root)

HD Partition Layout:
SDA 1 - Toshiba System - 1.5 GB - primary
SDA 2 - Vista - 50 GB - ntfs - primary
SDA 3 - Extended
            - SDA 5 - 120 GB - ntfs
            - SDA 6 - 1 GB - Linux Swap
SDA 4 - Kubuntu - 14 GB - primary

I hadnt realized SDA 1 existed, so ended up putting swap as a Logical.

In any case, the partitioning and Kubuntu install were successful, and I had a working Vista/Kubuntu dual boot system.

This is the background so far and I included it as it is probably sheds more light on the current state, and my experience level, and other such.
Thanks for reading this far.
Cheers
Arachnic

---

### Post by Cheezespread on 2009-09-30
If you are sure of the fact that you have not messed up the Windows drive , there is this last option in Supergrub which you can select from the Main Menu .

Win >>>>>>> Linux  :(((( 

Something similar to this. This fixes the mbr and loads your Windows drive.

---

### Post by arachnic on 2009-09-30
Here's what happens:

```
Booting 'WIN => MBR & !WIN!           :((((((((((((((((((((('

set aux_hd="hd0"
dd (fd0)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
```

Thats it. Cursor blinking below it.
I dont think its waiting for an input, but its not going anywhere.

Why the "fd0" Is it looking for a floppy drive ?

Thanks for the quick response.
Cheers
Arachnic

---

### Post by arachnic on 2009-09-30
Also tried the other Win ooption

```
Booting '!WIN!                     :((((('

rootnoverify (hd0,0)
```


And the cursor blinks there.

Yes, I am pretty sure I havent messed around with the windows partition. Untouched, except for initial resizing at the end of the partition. The beginning is exactly where it was.

Cheers
Arachnic

---

### Post by starcannon on 2009-09-30
Check this link out:
[http://justlinux.com/forum/showpost.php?p=869980&postcount=6](http://justlinux.com/forum/showpost.php?p=869980&postcount=6)
I think it will help you.

GL

---

### Post by arachnic on 2009-09-30
Thanks Starcannon !
Yeah it helps, in that it tells me what probably went wrong, and how to deal with it, etc. However, the method to cure it is still out of bounds for me, as I cant use a Live CD (dead CD drive) nor a live USB (dumps me into Busybox).

Should I create a 4 GB partition on my USB HD and install Ubuntu there using the Ubuntu/XP machine, then plug and boot it from the Vista/Kubuntu machine ? Once within Linux, I could probably mess around and get Grub reinstalled without actually reformatting the linux partitions.
What say ??

Edit: Or should I try the Alternate CD + UNetBootIn = Alternate Live USB ??

---

### Post by starcannon on 2009-09-30
Whatever it takes to boot into a live Ubuntu image, then you can get grub fixed. You could possible also hand edit grub from the grub screen, press esc when prompted, point grub to the correct location, once booted you can fix grub right from your install.

---

### Post by starcannon on 2009-09-30
Check this little guide out on editing grub from the grub menu at boot:
[http://ubuntuforums.org/showpost.php?p=3395958&postcount=5](http://ubuntuforums.org/showpost.php?p=3395958&postcount=5)

GL

---

### Post by arachnic on 2009-09-30
Thanks !
Will try and let know !

---

### Post by LewRockwell on 2009-09-30
you need one of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)
*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****


and an old optical drive from a desktop machine
(there are millions of these gathering dust across the globe)


we have twenty-seven of them here


.

---

### Post by arachnic on 2009-09-30
Tried the Parted Magic Live USB.

[B]The Default and SuperGrub options in the first menu take me to the Kubuntu Login Screen, but no keyboard/mouse reaction so I cant login.
[/B]
The rest of the options  dump me into shell with

```
It seems the media that contains he pmagic-4.5.sqfs could not be found.
Help us out by trying to mount the device that contains the Parted Magic media 
manually and report the results to this forum. This initramfs contains a very limited 
busybox build. Type Busybox to get a complete list of commands. Type 'reboot -f' 
to restart the system.

```:(

Edit: Yeah I am looking into the connector cable too... Thanks !

---

### Post by arachnic on 2009-10-01
Managed to put in a working dvd drive, and booted Live CD - Kubuntu 7.10

I cant see any part of my hard disk.

Going to Grub from terminal:
```
grub>root (hd0,2)

Error 21: Selected disk does not exist.
```Tried (hd0,3) as well.

```
fdisk -l /dev/hda
```this gives an output that looks like its for the CD itself (730mb, etc)

```
fdisk -l /dev/hdb
```No output, just ack to the prompt.

```
grub> root (hd1,2)

[CODE]Error 21: Selected disk does not exist.
```grub> find /boot/grub/stage1

Error 15: File not found.
[/CODE]
what seems to be the problem now ?

I dont mind reinstalling kubuntu (not happy about it, i will have to download all the packages again, but thats ok.) but i dont want to lose the other two partitions - Vista and the Data.

What do I do ? !!!

---

### Post by egalvan on 2009-10-01
> **arachnic said:**
> M, and booted Live CD - Kubuntu [COLOR="Red"][B]7.10
[/B][/COLOR]
I cant see any part of my hard disk.

Are you actually using a two-year-old distro?
If so, why?
Hardware compatibility?

> ```
fdisk -l /dev/hdb
```No output, just ack to the prompt.


use
```
[COLOR="red"]sudo[/COLOR] fdisk -l
```

> [code]grub> root ([COLOR="Red"]hd1[/COLOR],2)


That points to the second hard drive. 
Do you have two hard drives?

> I dont mind reinstalling kubuntu (not happy about it, i will have to download all the packages again, but thats ok.) but i dont want to lose the other two partitions - Vista and the Data.

What do I do ? !!!

I use PartedMagic LiveCD to partition and format and LABEL everything
before doing and install.
It's never failed me yet.
I've re-installed Linux without munging the XP.
You just have to be careful of what partitions you work with.
Make SURE you know which is which.

---

### Post by arachnic on 2009-10-01
> [quote]and booted Live CD - Kubuntu [COLOR=Red]**7.10**[/COLOR]Are you actually using a two-year-old distro?[/quote]Ok, switched to 8.10. The older one was what i got my hands on first.

> use
     Code:
     [COLOR=red]sudo[/COLOR] fdisk -l 
Gotcha.. I get full list of my partitions, etc.

Here goes:
```
Device      Boot     Start        End     Blocks     Id     System
/dev/sd                  1        192                   27     Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2  *            192     6009                    7      HPFS/NTFS
/dev/sda3            22513    24321                  83      Linux
/dev/sda4              6010    22512                    f      W95 Ext'd (LBA)
/dev/sda5              6010    22381                   7      HPFS/nTFS
/dev/sda6            22382    22512                  82      Linux Swap/Solaris

Partition table entries are not in disk order

```Looking at all possibilities before I finally go and reinstall Kubuntu.
Which also means I will have to install 8.10 not 9.04, and upgrade after that. :(

To NOT mess up the partition table, should i keep the Linux root as well as swap WITHIN the extended partition ? Because I think creating a primary AFTER the extended may cause issues (Partition table entries are not in disk order,etc) ? Or should Labeling each partition explicitly keep that from happening ?

Thanks for the help..

Arachnic

---

### Post by arachnic on 2009-10-01
```
mount /dev/sda3
mount: cant find /dev/sda3 in /etc/fstab or /etc/mtab
```contents of fstab:
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
```can I try mounting the partition ? will that work ? How do I do that ?

Using Kubuntu LiveCD 8.10.

Thanks
Arachnic

---

### Post by arachnic on 2009-10-01
Hey ! 
Mounted the Linux Partition.

```
sudo mkdir /mnt/ubuntu
sudo mout -t ext3 /dev/sdb1 /mnt/ubuntu
df -h 
```
Grub still gives me an ```
error 21: selected disk does not exist.
```

Since I CAN access my filesystem, is there a way to deal with grub (edit/reinstall) without redoing the entire Kubuntu installation ??

I hope there is !!!

---

### Post by arachnic on 2009-10-02
Thank you all !

Its done.

What I did:
1. Made GParted Live USB.
2. Took out the DVD drive from my other laptop and swapped it with the dead one from my machine (snapped off and exchanged their front panels and rear brackets so they fit their new location)
3. Booted into 8.10 Live and looked around, and rescued some of my files from the Home folder (didnt bother with installed packages, I didnt know where to rescue them from, and I could always redownload.)
4. Booted into GParted, and removed both the Linux Root and the Swap, and recreated them BOTH within the extended partition.
5. Booted into the Live CD, and installed Kubuntu 8.10 on the new partitions.

Rebooted, and Hallelujah ! Linux works, Windows works, all my data intact !

Thanks for all your help people !
Cheers

Arachnic

---

### Post by petjakob on 2009-10-19
I seem to be experiencing the exact same issue. I've tried all the steps detailed for the grub error 17 and it all seems to work, except the final steps where I do the root and setup commands, they keep giving me Selected Disk Does Not Exist.


I am creating a thread to post all specifics, thought I would bump this one in reference since this is one I used to troubleshoot so far and is fairly recent.

---

