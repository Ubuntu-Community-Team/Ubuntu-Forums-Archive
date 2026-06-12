---
title: "USB CDROM/DVD Device Problems on Ubuntu 10.10"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by SebMack on 2010-11-10
Ubuntu 10.10 seems to have troubles with cdroms...I used Ubuntu 8.04 lts and 10.04 lts with no cdrom issues. 
10.10 does not show my CDROM/DVD USB device in 'Places' and I cannot get it's UUID number via ROOT terminal , yet I did Remastersys backup of entire system, opened the Remastersys folder, right clicked the custom.iso file and burnt it using Brasero, which proves it is working on 10.10 but just not showing an icon. Inserting media of any kind does not open the Nautilus folder, yet other USB devices show immediately (USB sticks and USB harddrive appear instantly).

The CDROM/DVD USb device works in Windows on a different machine and I also attached a USB harddrive with Windows XP to my netbook which 10.10 is installed on, and the USB CDROM/DVD device shows up fine. 
I tried mounting the device in Ubuntu 10.10, but I'm not that great at understanding commands, and the hundreds of different commands other people tried across the web don't work. 

When I type 'dmesg' the USB CDROM shows up as this (is there an I/O error preventing the USB cdrom drive from displaying???):-

[ 8284.535666] scsi 9:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 0
[ 8285.098044] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 8285.098770] sr 9:0:0:0: Attached scsi CD-ROM sr0
[ 8285.099262] sr 9:0:0:0: Attached scsi generic sg3 type 5
[ 9001.878411] usb 1-8: USB disconnect, address 10
[ 9001.957325] JBD2: I/O error detected when updating journal superblock for sdc1-8.


Also typing this below showed my device:- 
'ls /dev/disk/by-id -lah' 
lrwxrwxrwx 1 root root   9 2010-11-10 09:42 usb-HL-DT-ST_DVDRAM_GSA-4084N-0:0 -> ../../sr0


I also typed 'lsusb' and my device showed up on line 6 as 'Genesys Logic, Inc . USB 2.0 IDE Adapter'

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0168:1998  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


but typing this only displayed my internal HDD UUID number on line 4:-
'ls /dev/disk/by-uuid -lah'

drwxr-xr-x 2 root root  80 2010-11-10 09:15 .
drwxr-xr-x 5 root root 100 2010-11-10 09:15 ..
lrwxrwxrwx 1 root root  10 2010-11-10 09:15 420CDBE80CDBD54F -> ../../sda1
lrwxrwxrwx 1 root root  10 2010-11-10 09:15 4c593da0-46c2-4dff-b389-a443d87792e5 -> ../../sda2

My USB CDROM/DVD device installed Ubuntu 10.10 just perfect, but then it disappeared some time without me noticing. Reinstallation does not help, the device still won't appear...It doesn't show up in fstab or mtab.
This has only been an issue since I installed 10.10 netbook edition. I am currently using GNOME because it uses less CPU power and is more configurable.

What Ubuntu 10.10 needs is a CDROM detection and installation software program...in a .deb file, so it can be downloaded, installed and opened like a normal program, and would be able to detect a CDROM or DVD attached, and create it within fstab and other files requiring the info...
If Windows has been able to detect CDROM's since the 1990's I can't see why Ubuntu suddenly has problems.. 
People shouldn't have to be subjected to a crash course in programming to add basic standard devices.

thanks for reading my whinge.

---

### Post by coffeecat on 2010-11-10
From my lsusb:

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```From my dmesg:

```
[ 1853.720028] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 1853.872707] usb-storage 1-6:1.0: Quirks match for vid 05e3 pid 0701: 520
[ 1853.872776] scsi12 : usb-storage 1-6:1.0
[ 1854.872121] scsi 12:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 0
[ 1855.121964] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1855.122153] sr 12:0:0:0: Attached scsi CD-ROM sr1
[ 1855.122297] sr 12:0:0:0: Attached scsi generic sg5 type 5
```When I plug in and switch on the USB DVD drive, a second 'CD/DVD Drive' icon appears in Places > Computer (this is a Desktop system with an internal DVD drive running the standard desktop Ubuntu 10.10). But when I put a readable DVD in, the drive whirrs for a bit and then the second icon disappears. It would appear that you have uncovered a bug which I have probably reproduced, except that my dmesg shows no error after disconnecting the device.

So....

> **SebMack said:**
> What Ubuntu 10.10 needs is a CDROM detection and installation software program...in a .deb file, so it can be downloaded, installed and opened like a normal program, and would be able to detect a CDROM or DVD attached, and create it within fstab and other files requiring the info...
If Windows has been able to detect CDROM's since the 1990's I can't see why Ubuntu suddenly has problems.. 
People shouldn't have to be subjected to a crash course in programming to add basic standard devices.

thanks for reading my whinge.

... instead of "whingeing" and making assumptions about what Ubuntu might or might not "need", why not pop over to...

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

... and file a bug report?

After you. :wink:

**Edit:** The fact that I couldn't find a relevant bug on Launchpad means that this could be an obscure bug affecting only some types of USB hardware. This is quite possible. When you consider the variables of the kernel driver, the ACPI implementation in the BIOS and the USB device's firmware, the possible permutations are endless. I'll give you an example. I have a USB SATA docking station. Works just fine with every machine and OS I have except with my Sony Vaio running an earlier version of Ubuntu (can't remember which offhand). It worked fine with the same Ubuntu version on other machines, just not with the Sony. But it worked fine with Vista on the Sony. Why? Haven't a clue and life is too short for me to worry about it.

Out of interest, what is your USB CD/DVD enclosure? I assume it was a bare enclosure when you bought it because it has the same ID '05e3:0701' as mine which is a 'Hiyatek'. But googling '05e3:0701' brought up a variety of makes all with the same ID. [For example.]("http://www.qbik.ch/usb/devices/search_res.php?pattern=enclosure")

---

### Post by coffeecat on 2010-11-10
> **coffeecat said:**
> **Edit:** The fact that I couldn't find a relevant bug on Launchpad means that this could be an obscure bug affecting only some types of USB hardware.

I think I may be right. I've managed to get hold of one of those USB powered external DVD drives that use a slimline drive to try out. It is recognised and automounted in Ubuntu 10.10 just fine. Presumably then this problem must be a bug affecting...

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```... because I've tried this device with another machine running 10.10 and I get the same issue.

Is this is bug? Almost certainly. Is it irritating/frustrating? Undoubtedly. Will it get fixed? Not unless someone files a bug report. Will it get fixed then? Depends on how many people do a 'me too' on the bug report. Seeing as how this seems to be hardware-specific to a fairly uncommon piece of hardware I would guess this affects only a small minority of Ubuntu users.

---

### Post by coffeecat on 2010-11-14
I'm posting this workaround for anyone with a similar problem who's found this thread from a search. I doubt the OP is interested since they have not logged in since posting their one and only  post.

Have a look in /dev. If you have a machine without an internal optical drive, your usb CD/DVD drive will probably appear as sr0. If you have an internal CD/DVD drive, your usb one will probably be sr1. If it doesn't automount when you insert a CD or DVD, simply open a terminal and:

```
udisks --mount /dev/sr0
```... or ...

```
udisks --mount /dev/sr1
```... depending on whether you have an internal optical drive or not. Your disc will be mounted and a clickable icon will appear on the desktop with a 'disk' label.

It is not elegant but at least someone in the OP's situation will be able to read CDs and DVDs.

---

### Post by mikolune on 2010-11-15
I have the exact same problem but it is limited to Audio CDs (haven't checked Media DVDs).  Software DVDs work fine.  

I tried the workaround on an audio CD, but this didn't work:
ml@computer:~$ udisks  --mount /dev/sr1  
Mount failed: Error mounting: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: you must specify the filesystem type[/code]So then I tried this, but didn't work as well:
 ```
 
ml@computer:~$ udisks  --mount /dev/sr1  --mount-fstype cdda
Mount failed: Not a mountable file system
```I am not sure about the cdda option tho...

What am I missing ?

Many thanks!

edited for clarity

---

### Post by mikolune on 2010-11-15
OK - after browsing along some more - I got to understand that Audio CD's  are not to be "mounted", but rather accessed directly through the software. :)

Anyhow -  the problem remains that Ubuntu - or is it a problem with Gnome ? - cannot see the Audio CD's from the USB/IDE adaptor using the 05e3:0701 Genesys Logic, Inc. chip set.

---

### Post by coffeecat on 2010-11-16
> **mikolune said:**
> OK - after browsing along some more - I got to understand that Audio CD's  are not to be "mounted", but rather accessed directly through the software. :)

Tbh, I didn't check with an audio disc, so thanks for that. I'll try with a video DVD as well to see what happens.

> **mikolune said:**
> Software DVDs work fine.  

Very interesting, since both the OP and myself are having this issue with data DVDs.

> **mikolune said:**
> Anyhow -  the problem remains that Ubuntu - or is it a problem with Gnome ? - cannot see the Audio CD's from the USB/IDE adaptor using the 05e3:0701 Genesys Logic, Inc. chip set.

Good point. Or it could be related to the kernel driver. What I haven't done is to check this in Fedora 14 which, iirc, has the same version of gnome. It certainly runs Fedora's version of the 2.6.35 kernel, the same as Maverick. I'll post back when I've done some investigation. Thanks for posting. We can assume that there are at least three people in the world with this Genesys 05e3:0701 device who are running Ubuntu. :)

By the way, what make of CD/DVD drive do you have in your enclosure? I'm using an LG which works fine in Maverick as an internal drive, but it's just conceivable that some obscure interaction between the firmware of the Genesys enclosure and the LG drive could be at the root of all this.

---

### Post by mikolune on 2010-11-16
Thanks for your response!

> **coffeecat said:**
> 
By the way, what make of CD/DVD drive do you have in your enclosure? 

Mine is a PHILIPS DVD+_RW SDV8820.  It is now plugged into a USB adaptor called Owltech OWL-ESODIDE(B) ....

In fact, the PHILIPS  was the internal drive of an Ubuntu 10.04 box that just died on me.  I bought a new machine (Acer Revo 3700 - 64 bit) that doesn't have an internal drive, so I recycled the old internal drive . I used the USB adapter to connect the old DVD drive to  the new box, which is running 10.10. 

Note that the  05e3:0701 chip set is in the USB adapter, and not in the DVD drive.

Thanks for the efforts!  :)

---

### Post by coffeecat on 2010-11-16
> **mikolune said:**
> Note that the  05e3:0701 chip set is in the USB adapter, and not in the DVD drive.

Agreed. The reason I thought it was worth seeing if a different make of CD/DVD drive would make a difference is that sometimes something weird can happen with certain combinations of enclosure and drive firmware. For example, I have a generic hard drive USB enclosure which behaves just perfectly with a Hitachi drive when plugged into my Mac Mini running OSX. But if I put a particular model of WD drive in it, the drive mounts OK (in MacOS) but spontaneously dismounts itself after a variable length of time. I discovered this when doing Carbon Copy Cloner backups of the system, which take several hours. Frustrating, to say the least. :|

Anyway, I have done some investigation and I have some interesting results, all done on the same multibooting machine to reduce the number of variables.

In** Maverick,** whether I put in a data DVD, Video DVD, Audio CD or blank recordable disc, the CD/DVD icon disappears from 'Computer'. I can mount a data DVD as before with the udisks command and, like you, I can use software to access an audio CD or video DVD. Except that VLC was the only media app (that I tried) that I could do this with, by going to Media > Open Disc and putting '/dev/sr1' in the Disc device field.

However, all these discs would open/play in Maverick  using the internal DVD drive or the USB-powered DVD drive I mentioned earlier.

In **Karmic,** everything works as expected with this 05e3:0701 device, with prompts for appropriate apps when the disc is put in, and a suitable icon appearing on the desktop.

Most interestingly, in** Fedora 14**, which uses the same version of gnome and kernel as Maverick, everything works just as well as in Karmic. I.e. everything works.

**Lucid** is the weirdest. A data DVD is automounted just fine. Ditto a video DVD and I can play it easily. But it does the same as Maverick with an audio CD and a blank CDR, CDRW or DVD+R. Which is different from the OP who said:

> 10.04 lts with no cdrom issues. Lastly, there's **Natty**. Everything worked with this device. Which is nice. But, of course, since it is still pre-alpha at the moment, there's plenty of time for things to get broken. :)

---

### Post by coffeecat on 2010-11-16
> **coffeecat said:**
> The fact that I couldn't find a relevant bug on Launchpad 

Wrong! My search-fu was playing up. Here it is:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/646293](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/646293)

@mikolune, do you want to add a comment to the Launchpad thread or at least do a 'me too'?

---

### Post by mikolune on 2010-11-16
OK, will do a me too to the launch pad thing - have never done it yet!  

Thanks for the exploration.  Glad to know that things seem to be working nicely on Natty. So - I understand we can be optimistic for the 11.10 version :smile:

I also just checked with Lucid - and same as you:   Data DVD and CD work, while the Audio CD goes undetected (no icon appears in Gnome) although I can play it with VLC.

I am still curious about Media DVD on Maverick - will check tonight.

---

### Post by taygan on 2010-12-27
Thanks folks for confirming this.  I've been tearing my hair out over the past few months with this one.  I've got the same adapter.  Can manually mount CDROM, can't burn anything, won't recognize audio CDs.  I'll ditto this on the bug page.

---

### Post by TopicMapper333 on 2010-12-28
Not sure my problem is related to this one, but I suspect it may be.

I have three systems, all with identical motherboards (ASROCK X58 Extreme) and identical firmware (the latest).  Two run 10.10, one runs 10.04 (and I'm glad I never upgraded it!).  All machines have several usb disks on which they back each other up at night.  The disks are in usb enclosures from various manufacturers, and the disks themselves are several models from several manufacturers.  All are SATA-2.

About once a week, only on the 10.10 machines, one of the usb drives stops working.  But not always the same disk, enclosure model, or drive model!  It just stops working, usually with the disk-access light lit.  The ONLY way to restore access to the disk is to remove power from the disk and then restore power.  Most of the different disks seem to suffer this failure from time to time.  Sometimes /var/log/syslog says it's having Reiserfs errors on whatever disk it is (which is not surprising).  Doing an ls of the directory where the affected disk is presumably mounted hangs the terminal, and an i/o error message appears in syslog.  Sometimes "mount" says that the disk is still mounted, even when the corresponding device (/dev/sd<whatever>) no longer exists in /dev.  Power-cycling the disk causes it to appear at a different /dev/sd<something>, and then it works fine (sometimes for weeks) without a problem.

There are NO problems with the *very same* disks when those disks are moved to the 10.04 machine.  They don't lock up at all, apparently.  I repeat: the hardware of the three hosts is identical.  The only difference I know of is that the reliable machine runs 10.04, and the unreliable machines both run 10.10.

I feel I have little choice but to downgrade the 10.10 machines to 10.04.  :-(  I'm writing this to say: Dear Ubuntu Folks: There may be a serious problem with using USB disk drives under 10.10.  The problem apparently makes unattended operation impossible.  This is a bad thing.

---

### Post by coffeecat on 2010-12-28
> **TopicMapper333 said:**
> Not sure my problem is related to this one, but I suspect it may be.

No, it isn't. This thread is about the optical drive enclosure, ID:

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```Threads about problems with hard drive USB enclosures are not frequent. I have not had any problem with any of my several USB HD enclosures in Maverick. I suspect there may be an issue between your Asrock motherboards and Maverick.

---

### Post by taygan on 2010-12-30
> **taygan said:**
> Thanks folks for confirming this.  I've been tearing my hair out over the past few months with this one.  I've got the same adapter.  Can manually mount CDROM, can't burn anything, won't recognize audio CDs.  I'll ditto this on the bug page.

AH HA!  a partial workaround:

open a terminal and type:

```
sudo gnomebaker
```

Burning works through wodim using gnomebaker as a frontend in super-user mode.

---

### Post by maniqui on 2011-01-06
I'm having this very same issue with a MSI CRE52-M USB external CD drive.
Has anyone found any workaround for reading **audio CDs**? 
I can read data CDs using the ```
udisks  --mount /dev/sr1
``` workaround posted above.
Thanks.

---

### Post by WarGaleon on 2011-01-23
I also have the same problem. I can only mount it using udisks and sudo mount. Either Data CD and DVD do not work (unless manually), haven't tried audio and video yet. I haven't tried it in 10.04 and older, because I'm already in 10.10 when I got this. I can't burn using Brasero, but GnomeBaker works fine (even without sudo). I could use it in VirtualBox 4.0, in Windows XP guests, also in Windows 7 installed in my computer. I also able to reinstall Ubuntu using this drive with the enclosure. The DVD drive also works fine if installed as internal.

lsusb:
```
Bus 001 Device 002: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```

dmesg:
```

[    2.403026] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H44L  SB01 PQ: 0 ANSI: 0
[    3.397475] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.397481] Uniform CD-ROM driver Revision: 3.20
[    3.397778] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.399221] sr 2:0:0:0: Attached scsi generic sg2 type 5

```

---

### Post by dzegarra on 2011-01-27
> **coffeecat said:**
> I'm posting this workaround for anyone with a similar problem who's found this thread from a search. I doubt the OP is interested since they have not logged in since posting their one and only  post.

Have a look in /dev. If you have a machine without an internal optical drive, your usb CD/DVD drive will probably appear as sr0. If you have an internal CD/DVD drive, your usb one will probably be sr1. If it doesn't automount when you insert a CD or DVD, simply open a terminal and:

```
udisks --mount /dev/sr0
```... or ...

```
udisks --mount /dev/sr1
```... depending on whether you have an internal optical drive or not. Your disc will be mounted and a clickable icon will appear on the desktop with a 'disk' label.

It is not elegant but at least someone in the OP's situation will be able to read CDs and DVDs.

This work for me. Thanks coffeecat.
I have Ubuntu 10.10. When I connect my usb cdrom ubuntu detects and install correctly. 
This is what dmesg show my:
```
[ 2038.373076] usb 1-2: new high speed USB device using ehci_hcd and address 19
[ 2038.512312] usb-storage 1-2:1.0: Quirks match for vid 05e3 pid 0701: 520
[ 2038.512400] scsi8 : usb-storage 1-2:1.0
[ 2039.523802] scsi 8:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A100 PQ: 0 ANSI: 0
[ 2039.547910] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 2039.550255] sr 8:0:0:0: Attached scsi CD-ROM sr0
[ 2039.550873] sr 8:0:0:0: Attached scsi generic sg3 type 5 
```
But when insert a disk the icon un My Computer disapers. 
Of course is not elegant. I go back to 10.04 because this problem, the hibernate and suspend problem and because my webcam doesnt work here and in 10.04 yes. :)

---

### Post by davidstoll on 2011-01-31
I also have this problem and the solution/workaround worked for me.  However, how do I make it mount automatically when I plug in the external drive?

---

### Post by coffeecat on 2011-02-01
> **davidstoll said:**
>   However, how do I make it mount automatically when I plug in the external drive?

To be honest, I really don't know. My first thought was to create a special udev rule, but the bug probably involves udev anyway. And please don't ask me how to create a udev rule. :| It's been a long time.

So that you don't have to open a terminal every time you want to mount a CD/DVD, you could make a panel or desktop launcher with the 'udisks --mount /dev/sr0' (or sr1) command. Not particularly elegant, but more convenient than opening a terminal and typing a command in.

The good news is that this device is still working in Natty. I tried it yesterday with a fully-updated Natty (we're just a few days off Alpha2) and data CD/DVDs, a music CD and a video DVD were all automounted. This seems to be a Maverick issue, but I am APPALLED that the bug I've linked to has been seemingly totally ignored by the dev team. I shall comment forthwith. Perhaps you'd like to comment as well.

---

### Post by davidstoll on 2011-02-01
It was suggested to me to run this...

```
sudo dpkg-reconfigure -phigh dbus hal
```

or

```
sudo reload dbus
```

It doesn't seem to help with any kind of automatic mounting of this device.  But maybe someone who understands those commands can alter the commands to help the situation...?

:(

---

### Post by manco on 2011-02-09
> **coffeecat said:**
> ```
udisks --mount /dev/sr0
```

```
udisks --mount /dev/sr1
```
^ Worked like a charm!  Thanks a million!

---

### Post by duce_85 on 2011-02-10
> **coffeecat said:**
> I'm posting this workaround for anyone with a similar problem who's found this thread from a search. I doubt the OP is interested since they have not logged in since posting their one and only  post.

Have a look in /dev. If you have a machine without an internal optical drive, your usb CD/DVD drive will probably appear as sr0. If you have an internal CD/DVD drive, your usb one will probably be sr1. If it doesn't automount when you insert a CD or DVD, simply open a terminal and:

```
udisks --mount /dev/sr0
```... or ...

```
udisks --mount /dev/sr1
```... depending on whether you have an internal optical drive or not. Your disc will be mounted and a clickable icon will appear on the desktop with a 'disk' label.

It is not elegant but at least someone in the OP's situation will be able to read CDs and DVDs.
Thank you this works perfectly ive been having the problem for months put up two posts and no replies  so thank you ver much

---

### Post by mosestruong on 2011-03-02
Workaround to play audio CDs, you can do totem cdda://

Does anyone have a workaround for ripping?

---

### Post by Rodski on 2011-05-02
Is everyone finding that the problem is solved with Natty?
On my first attempt after the upgrade (yesterday) an icon appeared on the desktop after loading an audio CD and I was able to use Rhythmbox to play and rip it.
... but today - nothing - just as previously with 10.10.
Any ideas?

---

### Post by davidstoll on 2011-05-04
Yeah, same issue on an upgrade to 11.04 32bit.

Not sure about a fresh install.

---

### Post by coffeecat on 2011-05-05
@Rodski and @davidstoll, do you get something like this from lsusb:

```
Bus 001 Device 004: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```It's the "ID 05e3:0701" that's important. This is still working for me in a fully-upgraded Natty system, but a fresh install, not upgraded from Maverick. If you have the device 05e3:0701 and it's not working properly in Natty upgraded from Maverick, that's an important observation, but if you don't have that device, please say so. Discussion of optical drive enclosures other than those with the ID 05e3:0701 confuses this thread.

---

### Post by Rodski on 2011-05-05
Thanks coffeecat.
Yes I do have that device.
Mine was an upgrade from Maverick (32 bit).
It is intermittently working for me - I have been able to play an audio CD couple of times since by having the drive connected, with a CD in, before turning the computer on. However the computer has sometimes failed to boot in this situation. Still experimenting to find out what conditions allow it to work.

---

### Post by davidstoll on 2011-05-06
All I have is the 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter.

I upgraded from 10.10 to 11.04 32bit.

Wow, this unity interface is quite a bit slower.  I get a lot of "the window isn't responding" and my HDD is working overtime.


> **coffeecat said:**
> @Rodski and @davidstoll, do you get something like this from lsusb:

```
Bus 001 Device 004: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```It's the "ID 05e3:0701" that's important. This is still working for me in a fully-upgraded Natty system, but a fresh install, not upgraded from Maverick. If you have the device 05e3:0701 and it's not working properly in Natty upgraded from Maverick, that's an important observation, but if you don't have that device, please say so. Discussion of optical drive enclosures other than those with the ID 05e3:0701 confuses this thread.

---

### Post by Rodski on 2011-06-13
Still no luck with audio CDs with a fresh install of 11.04 (64 bit this time). Worked fine with a computer running Windows 7.

I've  now given up trying to use the drive via the USB adapter and have installed it internally via the IDE cable - and it is working well without any problems.

---

### Post by coffeecat on 2011-06-13
> **Rodski said:**
> I've  now given up trying to use the drive via the USB adapter and have installed it internally via the IDE cable - and it is working well without any problems.

Yes, that bears out my experience. The optical drive is fine; the enclosure, which is really a Genesys Logic one, is the problem.

Interesting that another and different Genesys Logic device of mine should give less than stellar performance as well:

[http://ubuntuforums.org/showpost.php?p=10830882&postcount=7](http://ubuntuforums.org/showpost.php?p=10830882&postcount=7)

---

### Post by Everybody Loves Hypnotoad on 2011-06-26
I am experiencing the same problem on linux mint katya. The ide-usb2 adapter is from SPM (speed dragon multimedia) and uses a nec chipset(ID 0409:0056 NEC Corp.). I have tried all the different jumper positions on the connected drive but discs will not mount regardless of setting. But the command udisks --mount /dev/sr1 from this thread works.

```
[11970.092170] usb 1-4.6: new high speed USB device using ehci_hcd and address 11
[11970.188961] scsi7 : usb-storage 1-4.6:1.0
[11973.711964] scsi 7:0:0:0: CD-ROM PLEXTOR DVDR PX-716A 1.10 PQ: 0 ANSI: 0 CCS
[11973.851160] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[11973.851517] sr 7:0:0:0: Attached scsi CD-ROM sr1
[11973.851760] sr 7:0:0:0: Attached scsi generic sg4 type 5
```

The adapter: [http://www.speeddragon.com/index.php?controller=Default&action=ProductInfo&Id=106](http://www.speeddragon.com/index.php?controller=Default&action=ProductInfo&Id=106)

Edit: Data DVDs, data CDs and other DVD movies does show up now after maybe waking the drive up the first time with that manual mount command. The discs now show up wihout me doing anything else than placing them in the dvd drive.

---

### Post by kelpdip on 2012-08-25
This is an old thread, but since it was one of the top results in google it makes sense to update here. This command line fix solved the issue in 12.04 as well.

> **coffeecat said:**
> I'm posting this workaround for anyone with a similar problem who's found this thread from a search. I doubt the OP is interested since they have not logged in since posting their one and only  post.

Have a look in /dev. If you have a machine without an internal optical drive, your usb CD/DVD drive will probably appear as sr0. If you have an internal CD/DVD drive, your usb one will probably be sr1. If it doesn't automount when you insert a CD or DVD, simply open a terminal and:

```
udisks --mount /dev/sr0
```... or ...

```
udisks --mount /dev/sr1
```... depending on whether you have an internal optical drive or not. Your disc will be mounted and a clickable icon will appear on the desktop with a 'disk' label.

It is not elegant but at least someone in the OP's situation will be able to read CDs and DVDs.

---

