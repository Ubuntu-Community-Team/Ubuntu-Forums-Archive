---
title: "cdrom"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by LadyA on 2010-08-22
Cdrom will not mount when I put a blank cd in, but I can mount it manually when I put a picture cd in. How can I fix this? This is a new installation. I have been using ubuntu on another computer and did not have this problem.

---

### Post by jtarin on 2010-08-22
Do you see.....Main Menu>Places>Blank CD-RW Disc....if yes, click on it and post the results of this action.
Also post a copy of your "/etc/fstab".
Change the boot order of your devices in bios to boot on HDD first then CD.

---

### Post by LadyA on 2010-08-22
> **jtarin said:**
> Do you see.....Main Menu>Places>Blank CD-RW Disc....if yes, click on it and post the results of this action.
Also post a copy of your "/etc/fstab".
Change the boot order of your devices in bios to boot on HDD first then CD.

In Main Menu>Places, there is no Blank CD Disc. I already tried to change the boot order and that didn't work.
I'm fairly new to Linux, so how do I find /etc/fstab and how do I copy it.
I am dual bootiing with Mint and it will not mount the CDrom either.

---

### Post by jtarin on 2010-08-22
> I'm fairly new to Linux, so how do I find /etc/fstab and how do I copy it.The same way you would find a file in Windows using Notepad only in Gnome it is called Gedit. MainMenu>Acessories>Gedit. When you have opened it.....click the open tab and make your way to the directory /etc. In that directory there is a file named fstab.Click on it and it will open in Gedit.Copy from Gedit the same way you would copy from Notepad. Paste the resulting copy to your forum post.

In addition....To find out what your optical drive is called, type in the terminal:

```
eject -n
```

It will answer you with

```
eject: device is `...'
```

The device that is shown between the quotes, let's assume it's /dev/hdc, use that in your mount command

Example:

mount /dev/hdc /mnt/hdc

You may want to remember, that the /dev folder is for devices, not for mounts.

Quite often, more then one link to the optical drive is provided, like /dev/cdrom or /dev/dvd and so on, those are usually symlinks to the actual device name, which in the above case is /dev/hdc

---

### Post by LadyA on 2010-08-22
> **jtarin said:**
> The same way you would find a file in Windows using Notepad only in Gnome it is called Gedit. MainMenu>Acessories>Gedit. When you have opened it.....click the open tab and make your way to the directory /etc. In that directory there is a file named fstab.Click on it and it will open in Gedit.Copy from Gedit the same way you would copy from Notepad. Paste the resulting copy to your forum post.

In addition....To find out what your optical drive is called, type in the terminal:

```
eject -n
```It will answer you with

```
eject: device is `...'
```The device that is shown between the quotes, let's assume it's /dev/hdc, use that in your mount command

Example:

mount /dev/hdc /mnt/hdc

You may want to remember, that the /dev folder is for devices, not for mounts.

Quite often, more then one link to the optical drive is provided, like /dev/cdrom or /dev/dvd and so on, those are usually symlinks to the actual device name, which in the above case is /dev/hdc

Copy of fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=302fca4d-f812-4dda-b7a3-ed290415008b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=657ad981-ca9e-4774-adff-d05724a0bb01 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

This is what I got in terminal for mount command.

---

### Post by jtarin on 2010-08-22
> This is what I got in terminal for mount command.So you are saying you have nothing in the terminal for the mount command as I described above?

---

### Post by LadyA on 2010-08-22
jtarin. sorry about that. I forgot to put command results in. Here they are.

ubuntu@ubuntu-desktop:~$ eject -n
eject: device is `/dev/sr0'
ubuntu@ubuntu-desktop:~$ sudo mount /dev/sr0 /mnt/sr0
mount: mount point /mnt/sr0 does not exist
ubuntu@ubuntu-desktop:~$

---

### Post by jtarin on 2010-08-22
Check if the CD-ROM device was identified correctly by the Linux kernel using the command dmesg.
If you have an ATAPI cdrom connected via IDE then this might look like:```

$ dmesg |more
.
.
.
hda: QUANTUM FIREBALL CR8.4A, ATA DISK drive
hdc: CD-ROM CDU701, ATAPI CDROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: QUANTUM FIREBALL CR8.4A, 8063MB w/418kB Cache, CHS=16383/16/63, (U)DMA
hdc: ATAPI 14X CD-ROM drive, 128kB Cache
Uniform CDROM driver Revision: 2.55 
```
If you have an SCSI cdrom then it might look like:```

$ dmesg |more
.
.
.
Detected SCSI removable disk sdc at scsi0, channel 0, id 5, lun 0
Vendor: PLEXTOR Model: CD-ROM PX-12TS Rev: 1.03
Type: CD-ROM ANSI SCSI revision: 02
Detected scsi CD-ROM sr0 at scsi0, channel 0, id 6, lun 0
scsi : detected 1 SCSI cdrom 3 SCSI disks total. 
```

---

### Post by jtarin on 2010-08-22
> **LadyA said:**
> jtarin. sorry about that. I forgot to put command results in. Here they are.

ubuntu@ubuntu-desktop:~$ eject -n
eject: device is `/dev/sr0'
ubuntu@ubuntu-desktop:~$ sudo mount /dev/sr0 /mnt/sr0
mount: mount point /mnt/sr0 does not exist
ubuntu@ubuntu-desktop:~$Go into your /mnt directory and make the required directory (sr0) by right-clicking on the file manager window and creating a new folder called sr0. Then try the mount cammand again. ```
sudo mount /dev/sr0 /mnt/sr0
```Try it without sudo also if sudo doesn't work.You shouldn't have to be root to mount a cdrom.
EDIT: CAVEAT:In Linux, mount points can be mounted permanently or temporarily. For security purposes, you should only Mount your devices under root's privileges.

---

### Post by LadyA on 2010-08-22
jtarin, I don't know too much about the terminal. Is this the code I'm supposed to put in -
$ dmesg |more  ?
When I put that code in it has Linux version 2.6.32 - 24 - generic and some bios lines. At the bottom there is a white flashing box that says more, but I don't know what I'm supposed to do from there.

---

### Post by jtarin on 2010-08-22
> **LadyA said:**
> jtarin, I don't know too much about the terminal. Is this the code I'm supposed to put in -
$ dmesg |more  ?
When I put that code in it has Linux version 2.6.32 - 24 - generic and some bios lines. At the bottom there is a white flashing box that says more, but I don't know what I'm supposed to do from there.
Use your down arrow. When you want to quit use Ctrl+c.

---

### Post by LadyA on 2010-08-22
Here is the code it gave me and when I use the down arrow it doesn't give any more.

ubuntu@ubuntu-desktop:~$ dmesg |more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4
.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu
 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe70000 (usable)
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe72000 - 000000007fe93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe93000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
--More--

---

### Post by LadyA on 2010-08-22
> **jtarin said:**
> Go into your /mnt directory and make the required directory (sr0) by right-clicking on the file manager window and creating a new folder called sr0. Then try the mount cammand again. ```
sudo mount /dev/sr0 /mnt/sr0
```Try it without sudo also if sudo doesn't work.You shouldn't have to be root to mount a cdrom.
EDIT: CAVEAT:In Linux, mount points can be mounted permanently or temporarily. For security purposes, you should only Mount your devices under root's privileges.

I found the /mnt directory, but then I don't understand where I'm supposed to right click and make a new folder. Do I open the mnt directory? Sorry I'm not getting this, but it is all so confusing to me. I guess it's because I'm so new to this.

---

### Post by Sef on 2010-08-22
> I found the /mnt directory, but then I don't understand where I'm  supposed to right click and make a new folder. Do I open the mnt  directory? Sorry I'm not getting this, but it is all so confusing to me.  I guess it's because I'm so new to this.

You are doing fine.  Take a deep breath and focus.  We all can get a bit frazzled when learning something new.

---

### Post by LadyA on 2010-08-22
> **Sef said:**
> You are doing fine.  Take a deep breath and focus.  We all can get a bit frazzled when learning something new.

Thankyou so much for the boost. When you're 74 it's a little harder than when you're 18. I really want to learn this, but I know it's frustrating to the teacher.

---

### Post by LadyA on 2010-08-22
Ok, I took a deep breath and went to the mnt directory and clicked on file, but the create folder was grayed out.

---

### Post by jtarin on 2010-08-22
> **LadyA said:**
> Ok, I took a deep breath and went to the mnt directory and clicked on file, but the create folder was grayed out.
OK...you have a cdrom and Linux recognizes it after boot, at least.Before we create the sr0 directory in /mnt, look in your /media directory and make sure the directory sr0 does not exist there first. If it does then we will use that....if not proceed with.....
In the /mnt directory right-click an **empty space**,** NOT** another file, to create a new folder and name it sr0. Rename is also availble by right-click.

---

### Post by jtarin on 2010-08-22
> **LadyA said:**
> Here is the code it gave me and when I use the down arrow it doesn't give any more.

ubuntu@ubuntu-desktop:~$ dmesg |more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4
.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu
 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe70000 (usable)
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe72000 - 000000007fe93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe93000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
--More--

You could also try the "Enter" key. I'm not on my Linux machine at the moment, so I am not certain if it is the down arrow or Enter key.

---

### Post by LadyA on 2010-08-22
> **jtarin said:**
> OK...you have a cdrom and Linux recognizes it after boot, at least.Before we create the sr0 directory in /mnt, look in your /media directory and make sure the directory sr0 does not exist there first. If it does then we will use that....if not proceed with.....
In the /mnt directory right-click an **empty space**,** NOT** another file, to create a new folder and name it sr0. Rename is also availble by right-click.

In the media directory I have three folders, cdrom, floppy, and floppy0.
In my /mnt directory, there is nothing and when I click on the white space the create folder is grayed out and there is no rename.

---

### Post by LadyA on 2010-08-22
> **jtarin said:**
> You could also try the "Enter" key. I'm not on my Linux machine at the moment, so I am not certain if it is the down arrow or Enter key.

Here is the only thing I've found about the CDROM.

0.712334] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, B105, max UDMA/33
[    0.728320] ata2.00: configured for UDMA/33
[    0.799676] ata3.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    0.799682] ata3.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.842847] ata3.00: configured for UDMA/133
[    0.996010] Freeing initrd memory: 7784k freed
[    1.090762] isapnp: No Plug & Play device found
[    1.200022] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.370097] usb 2-1: configuration #1 chosen from 1 choice
[    1.372991] hub 2-1:1.0: USB hub found
[    1.374948] hub 2-1:1.0: 4 ports detected
[    1.657945] usb 2-1.1: new low speed USB device using uhci_hcd and address 3
[    1.795014] usb 2-1.1: configuration #1 chosen from 1 choice
[    1.873943] usb 2-1.2: new low speed USB device using uhci_hcd and address 4
[    2.018013] usb 2-1.2: configuration #1 chosen from 1 choice
[    2.093941] usb 2-1.3: new low speed USB device using uhci_hcd and address 5
[    2.104677] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B105 PQ
: 0 ANSI: 5
[    2.241050] usb 2-1.3: configuration #1 chosen from 1 choice
[    9.171696] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    9.171702] Uniform CD-ROM driver Revision: 3.20
[    9.171850] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    9.171940] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    9.172135] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ
: 0 ANSI: 5
[    9.172297] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    9.172398] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 
GiB)
[    9.172463] sd 2:0:0:0: [sda] Write Protect is off
[    9.172468] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.172502] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    9.172678]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    9.219003] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.219023] Freeing unused kernel memory: 660k freed
[    9.219682] Write protecting the kernel text: 4680k
[    9.219719] Write protecting the kernel read-only data: 1840k
[    9.251272] udev: starting version 151
[

---

### Post by jtarin on 2010-08-22
Ok your system is recognizing your cdrom...now we have to find out exactly why it does not automount. Have you tried a cd with data, music or a movie? Do they automount?

---

### Post by LadyA on 2010-08-23
> **jtarin said:**
> Ok your system is recognizing your cdrom...now we have to find out exactly why it does not automount. Have you tried a cd with data, music or a movie? Do they automount?

Music and pictures automount, but movies and blank cd does not.

---

### Post by jtarin on 2010-08-23
Blank CD's will not automount...because there is nothing on them to detect. Movies a different story.....are these commercially made CD movies or homemade?
Go into the /media directory and click on your sr0.....it should open a blank window. if there is something on the CD it will have a volume lablel (name)

---

### Post by LadyA on 2010-08-23
> **jtarin said:**
> Blank CD's will not automount...because there is nothing on them to detect. Movies a different story.....are these commercially made CD movies or homemade?
Go into the /media directory and click on your sr0.....it should open a blank window. if there is something on the CD it will have a volume lablel (name)

On the Ubuntu 10.04 on my other computer, when I put a blank cd in the CD/DVD window comes up and I can burn a CD. I can find nowhere to mount a blank CD. The disk utility says no media detected.
The movies are commercially made CD movies and I've played them on a computer before.

---

### Post by jtarin on 2010-08-23
> when I put a blank cd in the CD/DVD window comes up and I can burn a CD. I can find nowhere to mount a blank CDCan you not acess the blank CD through the disc burning software Main Menu>Sound and Video>Braser Disc Burner to burn?

---

### Post by jtarin on 2010-08-23
Let's see if your user is in the cdrom group...that is has permission to mount. In the terminal type this command ```
id <yourusername>
```where <yourusername> is the name you logon to Ubuntu with. Do not use the "< >".

---

### Post by LadyA on 2010-08-23
> **jtarin said:**
> Can you not acess the blank CD through the disc burning software Main Menu>Sound and Video>Braser Disc Burner to burn?

That is the problem. When I use brasero it says no disk available.

---

### Post by LadyA on 2010-08-23
> **jtarin said:**
> Let's see if your user is in the cdrom group...that is has permission to mount. In the terminal type this command ```
id <yourusername>
```where <yourusername> is the name you logon to Ubuntu with. Do not use the "< >".

ubuntu@ubuntu-desktop:~$ id ubuntu
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),121(nopasswdlogin),122(sambashare)
ubuntu@ubuntu-desktop:~$

---

### Post by jtarin on 2010-08-23
Brasero from my searches seems to be problematic for everyone.There are two **K3B **and **Gnomebaker** (you only need one) which can be found in the repositories.Main Menu>System>Administration>Synaptic. 
In the search box in Synaptic type either name in and it will show you available packages for downloading.
For **GnomeBaker **there is only one. 
For **K3B **there are several.The one you want is K3B.When you select it it will automatically select several others. That's OK. Let it.

These instructions apply to any of the software above you want to install.
> Left click on the file you want and select "Mark for installation" Then above you will see a green check mark with the word "Apply"...click it.A dialogue will appear and say"Apply the following Changes?". Click Apply and it will download and install automatically.

Personally I prefer K3B as it is more versatile, but GnomeBaker is a good burner.

---

### Post by jtarin on 2010-08-23
[How can I get my videos to play?]("https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html")

---

### Post by LadyA on 2010-08-23
> **jtarin said:**
> Brasero from my searches seems to be problematic for everyone.There are two **K3B **and **Gnomebaker** (you only need one) which can be found in the repositories.Main Menu>System>Administration>Synaptic. 
In the search box in Synaptic type either name in and it will show you available packages for downloading.
For **GnomeBaker **there is only one. 
For **K3B **there are several.The one you want is K3B.When you select it it will automatically select several others. That's OK. Let it.

These instructions apply to any of the software above you want to install.


Personally I prefer K3B as it is more versatile, but GnomeBaker is a good burner.

K3B found no optical writing device and GnomeBaker said burn failed.

---

### Post by LadyA on 2010-08-23
All the packages that it said to install in the link, How to get videos to play, were already installed.

---

### Post by jtarin on 2010-08-23
> **LadyA said:**
> K3B found no optical writing device and GnomeBaker said burn failed.It is possibly the medium that your using. I would try more than one type. CD-R,CD-RW

---

### Post by jtarin on 2010-08-23
I would suggest to repost this under a new topic.....> Disc Burning software does not detect Blank CD's. Possibly someone that has similar problems will have a fix. I'm stumped at the moment.You can tell that Ubuntu detects your CD drive upon boot and tell them it plays all but movies automatically. Make sure you mention you belong to the cdrom group and the various other things we have covered to determine that your player works in Ubuntu.

---

### Post by LadyA on 2010-08-23
jtarin, thankyou for using so much time and patience to help me with my problem. It is too bad we couldn't find a solution, but I will try to repost under a new topic.

---

### Post by jtarin on 2010-08-23
> **LadyA said:**
> jtarin, thankyou for using so much time and patience to help me with my problem. It is too bad we couldn't find a solution, but I will try to repost under a new topic.
I've researched further and have seen too many reports on this problem in Ubuntu. There are myriad fixes...I've personally never had this problem in any Linux derivitive I've had and it has me stumped for a quick fix. I would have to sit down in front of your computer to find a solution. I found in the past that the medium used has a lot to do with it.Your Welcome!

---

### Post by jtarin on 2010-08-23
[Here's a similar topic going on now]("http://ubuntuforums.org/showthread.php?t=1549545")

---

