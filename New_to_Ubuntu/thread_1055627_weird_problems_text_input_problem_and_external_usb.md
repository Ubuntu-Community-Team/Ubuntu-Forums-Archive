---
title: "weird problems: text input problem and external usb hdd permission denied to copy dat"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by nandan on 2009-01-30
Hi

Have been a user of ubuntu for quite some time now, though am not good at programming.

Yesterday, bought a 320 GB USB external drive (Maxtor Basics) to create backup of files. However, while the HDD was recognized and mounted (its icon was visible on the desktop and I could view some of the basic files), I am unable to write anything on the hdd. I get messages like "you do not have permission to write on this". 

The stranger thing happened while I was searching this forum and internet for solution to this (I have not really found it yet.) While trying out some text commands on the terminal window, suddenly, text input started stalling and when I enter the letters a, b, c, d, e, f, the letters are underlined and a small strip with some options is shown below. Those options are all garbled and when i press escape, it removes the strip from view, but also deletes the text that was typed.
This happens in the terminal window, firefox and open office text files. Opera has not suffered from this, so thankfully, I can stilll write this in ubuntu.

The reason why I have put in these problems in the same thread (external hdd and text) isbecause they seem to be related.

Could somebody please help me with both issues?
(About the hdd, it has ntfs filesystem. I thinjk the rights to make changes are with root user, and so it does not allow me to write.)

Thanks!

---

### Post by unutbu on 2009-01-30
Let's try to fix the terminal first, since it may be useful for setting up the USB hdd later. (Getting the USB set up should be relatively easy, too.)

How about try typing 

```
reset
```

in the terminal. Does that return it to normal?
Maybe it won't, since you mentioned firefox is also affected.

If you type 
```
history
```
can you see the command which caused the terminal (and other apps) to start behaving badly? Posting the output of the history command, or the contents of ~/.bash_history might give us a clue as to what's causing the text input problem.

Finally, how about try a reboot. Does that fix the terminal?

---

### Post by nandan on 2009-01-30
> **unutbu said:**
> Let's try to fix the terminal first, since it may be useful for setting up the USB hdd later. (Getting the USB set up should be relatively easy, too.)

How about try typing 

```
reset
```

in the terminal. Does that return it to normal?
Maybe it won't, since you mentioned firefox is also affected.

If you type 
```
history
```
can you see the command which caused the terminal (and other apps) to start behaving badly? Posting the output of the history command, or the contents of ~/.bash_history might give us a clue as to what's causing the text input problem.

Finally, how about try a reboot. Does that fix the terminal?

Thanks for your reply! I could not type 'reset' since it contains 'e', so I copied the command.That did not really help, since again, the 'e' of reset was underlined and further typing input was not shown. Have rebooted today (have been facing this since yesterday), so that doesn't seem to have helped.here is the output of the history command:

```

    1  glxinfo | grep direct
    2  chmod 0700/ home/nandan
    3  chmod 0700/home/nandan
    4  run nautilus
    5  sudo nautilus
    6  sudo gnome
    7  gnome
    8  sudo gnome
    9  nautilus --help
   10  -c
   11  --cgeck
   12  --check
   13  display
   14  --display
   15  quit
   16  exit
   17  startx
   18  exit
   19  sudo apt -get install -y msttcorefonts
   20  sudo apt-get install -y msttcorefonts
   21  quit
   22  sudo fc-cache -f
   23  mplayer -v ypuvideo.avi
   24  vlc -v yourvideo.avi
   25  vlc -v experienceubuntu.ogg
   26  vlc -v experience ubuntu.ogg
   27  home
   28  go home
   29  vlc -v experience ubuntu.ogg
   30  hal
   31  apt-get clean
   32  /usr
   33  \usr
   34  apt-get autoremove
   35  yes
   36  root
   37  nandan
   38  goto nandan
   39  admin
   40  gksu "sh /cdrom/cdromupgrade"
   41  gksudo &#8220;sh /mnt/cdromupgrade&#8221;
   42  gconf-editor
   43  winecfg
   44  root
   45  su
   46  gdm
   47  openbox
   48  openbox-gnome-session
   49  openbox
   50  exit
   51  gdm
   52  kill
   53  xfce
   54  kde
   55  exit
   56  run kde
   57  exit
   58  nandan-r
   59  nandan -r
   60  uname -r
   61  sudo pico/boot/grub/menu.lst
   62  sudo pico /boot/grub/menu.lst
   63  uname -r
   64  sudo pico /boot/grub/menu.lst
   65  uname -r
   66  sudo pico /boot/grub/menu.lst
   67  uaname -r
   68  uname -r
   69  /boot/grub/menu.lst
   70  sudo update grub
   71  sudo update-grub
   72  read menu.lst
   73  gksudo gedit /boot/grub/menu.lst
   74  sudo grub
   75  exit
   76  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
   77  gksudo gedit /boot/grub/menu.lst
   78  sudo gedit
   79  sudo gedit/emnu.lsrt
   80  sudo gedit/menu.lst
   81  pwd
   82  gksudo gedit /boot/grub/menu.lst
   83  exit
   84  desktop
   85  exit
   86  start desktop
   87  sudo desktop
   88  sudo exit
   89  sudo quit
   90  quit
   91  gdm
   92  sudo fdisk-l
   93  sudo fdisk -l
   94  sudo fdisk -lu
   95  sudo apt-get install ntfs-3g ntfs-config
   96  quit
   97  exit
   98  fdisk -l
   99  sudo chown -R nandan:nandan media/disk
  100  ls -l /media
  101  sudo apt-get install ntfs-3g
  102  sudo mkdir /media/60Gig
  103  reset
  104  history

```

To sort out the hdd issue, was trying out commands by copy-pasting them from this forum into the terminal...

---

### Post by unutbu on 2009-01-30
Nothing in your history output jumped out at me as the culprit.
If you had more than one terminal open, only one terminal's history gets saved, so maybe that is why the bad command is not apparent. 

Whatever the case, let's try this: Turn off Compiz special effects, and keyboard shortcuts if you are using any. Open a Nautilus file browser.
Press Ctrl-h to show hidden files. 
Rename 
```

.gconf --> .gconf-ol
.gnome2 --. .gnome2-ol
```
(ol stands for old, but you have no 'd's eh?).

Log out and then log back in. 
GNOME will find ~/.gconf and ~/.gnome2 are missing, and will create new directories with those names. Your GNOME settings (such as background, and preferences) will all be reset to pristine conditions -- like when you first installed Ubuntu.

Let's see if this fixes the text input problem.
If it works, you'll have to redo your GNOME settings, but hopefully that will be relatively easy.

If it does not work, the change is easy to revert: Simply delete the new ~/.gconf and ~/.gnome2 folders and rename

```

.gconf-ol --> .gconf
.gnome2-ol --. .gnome2
```
Log out, and log back in.

Hopefully this will solve the text input problem. I have to go now. Will be back tomorrow. If the above does not work, hopefully there will be another forum reader who can jump in.

Good luck.

---

### Post by nandan on 2009-01-30
Hi Unutbu

I am writing this in firefox :)
I was able to sort it out myself...I just did a shift+ctrl+V in the address bar of firefox and it sorted itself out! There must be some command which I toggled. I don't know which, but it has worked!

Thanks a ton for your help!! Appreciate.

---

### Post by nandan on 2009-01-31
hi
The other problem still remains. I still can't copy files on to the external hard disk. Am attaching a screenshot for the error message.Have gone thru many threads on the forum and tried to solve it, but most of the solutions have not worked.
(this is a brand new external usb hdd. Maxtor basics is the brandname. Am on 7.04 right now. It has ntfs filesystem. From previous thread, this output may be of use:
command-
sudo fdisk -l

```


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        3624     8626905    f  W95 Ext'd (LBA)
/dev/sda3            3625        4865     9968332+  83  Linux
/dev/sda5            2551        2920     2971993+   b  W95 FAT32
/dev/sda6            3564        3624      489951   82  Linux swap / Solaris
/dev/sda7            3529        3563      281106   82  Linux swap / Solaris
/dev/sda8            2921        3467     4393746   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


```


output for "df -h"

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.4G  5.9G  3.1G  67% /
varrun                248M  112K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb            248M  120K  248M   1% /proc/bus/usb
udev                  248M  120K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             299G   74M  299G   1% /media/disk


```

Thanks a lot!

---

### Post by unutbu on 2009-01-31
I'm glad you solved the text input problem. I doubt I would have guessed Shift-Ctrl-V in a million years. LOL! :)

To get the USB hard drive set up, follow drs305's guide on using pysdm:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197). Read the "5 Minute Guide".
That should be all it takes to set up your hard drive. 
Let me know if you run into any trouble.

---

### Post by nandan on 2009-01-31
> **unutbu said:**
> I'm glad you solved the text input problem. I doubt I would have guessed Shift-Ctrl-V in a million years. LOL! :)

To get the USB hard drive set up, follow drs305's guide on using pysdm:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197). Read the "5 Minute Guide".
That should be all it takes to set up your hard drive. 
Let me know if you run into any trouble.

Hi
Well, it was actually a shift+space combo..some SCIM utility was inadvertently activated.

I downloaded the program and tried to make those changes. I was able to make them, but I am still facing the same problem. No difference. :(
Am I missing a step? Is there some other workaround? This thing works fine in M$ Windoze, complete with a snazzy icon! A lot of my data is in Ubuntu and I may not be able to upgrade to 8.10 otherwise. :(

Thanks a lot for your help...

---

### Post by unutbu on 2009-01-31
Try changing the Options text field to 
```
ntfs-3g defaults
```

According to drs305's guide:
> 
NTFS Note: An ntfs partition fstab entry should work with a simple 'ntfs-3g defaults' entry. The mountpoint will be owned by root, as will subfolders and files. However, the user can write and save these files. If the uid/gid etc are added to fstab, the mountpoint will still be owned by root but the subfolders and files will show they are owned by the user (uid=).

If you see an "Apply" button, click that.
Then click the "Mount" button.
(This might just be my craziness, but clicking "Unmount", and then "Mount" might help too. The point is to get /dev/sdb1 re-mounted, so the operating system re-reads /etc/fstab with the new Options).

---

### Post by nandan on 2009-01-31
> **unutbu said:**
> Try changing the Options text field to 
```
ntfs-3g defaults
```

According to drs305's guide:


If you see an "Apply" button, click that.
Then click the "Mount" button.

Hi!
you mean options in the 'storage device manager', right? Tried that, still no luck...as seen in the screenshot.

---

### Post by unutbu on 2009-01-31
Okay, time to roll up our sleeves. Please post the output of the following commands:
```

mount
cat  /etc/fstab
ls  -ld  /media
ls  -ld  /media/backup

```

---

### Post by nandan on 2009-01-31
> **unutbu said:**
> Okay, time to roll up our sleeves. Please post the output of the following commands:
```

mount
cat  /etc/fstab
ls  -ld  /media
ls  -ld  /media/backup

```

1. cat command output:

> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda3
UUID=fba01e45-3407-4dd8-8def-cfc973d04474  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda6
UUID=27117ca5-f8ca-49ba-8df5-202fe8a952de  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sdb1                                  /media/backup   ntfs         ntfs-3g,defaults            0  0  



2. ls  -ld  /media output:

> 

drwxr-xr-x 6 root root 4096 2009-01-31 19:34 /media



3. ls  -ld  /media/backup output

> 

dr-xr-xr-x 1 root root 4096 2009-01-31 12:54 /media/backup



Sleeves rolled up for action!

---

### Post by unutbu on 2009-01-31
Okay, I should have paid more attention when you said you were using Ubuntu 7.04.

According to, [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions),
the ability to write to NTFS is in a Beta (experimental) state in Ubuntu 7.04. 
In more current versions of Ubuntu, writing to NTFS is no problem, and I think the instructions on drs305's guide would work fine for you if you upgrade to Hardy or Intrepid.

Here are instructions for enabling write access to NTFS using Ubuntu 7.04:
From [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions:](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions:)
```

**How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access **

Warning: The software you will use is still in Beta. You should not enable it on production machines

    * Read #General Notes 
    * Enable universe. Read #How to apt-get the easy way (Synaptic) 
    * Applications -> Add/Remove -> search for 'NTFS', you should find NTFS Configuration Tool, install it. 
    * Applications -> System Tools -> NTFS Configuration Tool -> Enable Write Support (depending on your device internal/external) 
    * Further troubleshooting is listed at this comprehensive howto thread. 

```

By the way, if you plan on installing Hardy or Intrepid and your BIOS can boot external USB drives, I recommend you do a fresh install into an empty partition on the external USB drive rather 
doing a "dist-upgrade" of your current OS. People sometimes run into strange problems doing that. We can talk more about that if you are interested.

---

### Post by nandan on 2009-01-31
Thanks! The archives do not seem to have all the files required for this...tried installing thru CLI as well as thru add/remove, but get messages like:

>  Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb)  404 Not Found [IP: 91.189.88.40 80]


or:
> 
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


So, I guess I can't download it. :( I think I will get a pen drive (which I know works with 7.04) and get it done.

Thanks a ton for the tremendous help and cooperation...

---

### Post by unutbu on 2009-01-31
Another option would be to reformat sdb1 with a FAT32 filesystem.
This would allow you to share data with Windows, and Ubuntu 7.04 would have no problems reading and writing to it too.

---

