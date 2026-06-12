---
title: "I broke automounting of my mp3 player"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by angelsneverdie on 2008-12-24
I'll explain what I did and hopefully one of you ubuntu gods out there can help me undo what I did.  I think i'm at the phase of my learning linux that I know just enough to be dangerous.  Here's the story:

My wife has a creative zen stone that has worked flawlessly with ubuntu since we got it.  She went over to a friends house who put some music on it.  (i'm assuming her friend uses windows or mac)  She complained to me that some of it wasn't playing so I attached to my computer (ubuntu 8.04 hardy heron) and I noticed that along with the music files there were some files that were beyond gibberish.  no file extensions, and the file names were very odd symbols and characters.  worst of all, it wouldn't let me delete these files.

So this is where it goes wrong:
 It wouldn't let me delete them, so the first thing I did (stupidly) was:

sudo chown -r mitchell /media/disk

Now, this was a couple days ago, and i was at an airport, and my comp battery was about to die, so i didn't take notes on what happened . . . but somewhere in there I managed to delete all the files. I'm not sure if what i typed above allowed me to do that, i don't remember. the 'chown' is the only thing i specifically remember typing, but i do know that i played around with it for quite a while.  I also remember that at some point it mounted but wouldn't let me write anything to it.  I did a hard reset on the mp3 player.

but now when I plug in the mp3 player it recognizes it as a usb drive but doesn't mount it.  if i right click on it and choose "mount volume" - nothing happens.

so, can anyone explain to me how I F*&^&Oed sh*t up?  and what can i do to make it function like it used to?

---

### Post by taurus on 2008-12-24
Make sure it is plugged in and on.  Then, open a terminal and post the output of this command here.

```
sudo fdisk -**l**
```
That would be lower case letter L, not number 1.

---

### Post by angelsneverdie on 2008-12-24
mitchell@mitchell-laptop:~$ sudo fdisk -l
[sudo] password for mitchell: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 990 MB, 990904320 bytes
31 heads, 61 sectors/track, 255 cylinders
Units = cylinders of 1891 * 2048 = 3872768 bytes
Disk identifier: 0x00042821

   Device Boot      Start         End      Blocks   Id  System
mitchell@mitchell-laptop:~$

---

### Post by taurus on 2008-12-24
What about

```
dmesg | tail
```
Does it still work if you connect it to another machine running windows or even mac?

---

### Post by angelsneverdie on 2008-12-24
mitchell@mitchell-laptop:~$ dmesg | tail
[ 4777.634107] sd 3:0:0:0: [sdb] Write Protect is off
[ 4777.634113] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 4777.634117] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4777.639074] sd 3:0:0:0: [sdb] 483840 2048-byte hardware sectors (991 MB)
[ 4777.639705] sd 3:0:0:0: [sdb] Write Protect is off
[ 4777.639710] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 4777.639713] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4777.639719]  sdb:
[ 4777.640895] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 4777.640949] sd 3:0:0:0: Attached scsi generic sg2 type 0
mitchell@mitchell-laptop:~$ 


I'm on vacation now and don't have any windows or macs around to test it.

---

### Post by angelsneverdie on 2008-12-24
when i open gparted to look at the disk it says sdb is 235.33mb unallocated. (when it should be a 1 gig mp3 player).  when I go to new, it tells me i need to set a disklabel and it defaults to msdos.  I say okay, and then it just quits and I get the following output in the terminal:


> Unable to open /dev/sdb - unrecognised disk label.
Device /dev/sdb has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Unable to open /dev/sdb - unrecognised disk label.
*** stack smashing detected ***: gparted terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7310138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb73100f0]
/lib/libparted-1.7.so.1[0xb7f37614]
/lib/libparted-1.7.so.1[0xb7f26c18]
[0x0]
======= Memory map: ========
08048000-0810a000 r-xp 00000000 08:01 3702868    /usr/bin/gparted
0810a000-0810c000 rw-p 000c1000 08:01 3702868    /usr/bin/gparted
0810c000-0844a000 rw-p 0810c000 00:00 0          [heap]
b5210000-b5314000 rw-p b5210000 00:00 0 
b5314000-b538f000 r--p 00000000 08:01 2523195    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b538f000-b5493000 rw-p b538f000 00:00 0 
b5493000-b551a000 r--p 00000000 08:01 2523140    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b551a000-b5529000 r-xp 00000000 08:01 1654865    /lib/libbz2.so.1.0.4
b5529000-b552a000 rw-p 0000f000 08:01 1654865    /lib/libbz2.so.1.0.4
b552a000-b5589000 r-xp 00000000 08:01 2310936    /usr/lib/libgio-2.0.so.0.0.0
b5589000-b558b000 rw-p 0005e000 08:01 2310936    /usr/lib/libgio-2.0.so.0.0.0
b558b000-b56a4000 r-xp 00000000 08:01 2311567    /usr/lib/libxml2.so.2.6.31
b56a4000-b56a9000 rw-p 00119000 08:01 2311567    /usr/lib/libxml2.so.2.6.31
b56a9000-b56aa000 rw-p b56a9000 00:00 0 
b56aa000-b56dc000 r-xp 00000000 08:01 2311586    /usr/lib/libcroco-0.6.so.3.0.1
b56dc000-b56df000 rw-p 00031000 08:01 2311586    /usr/lib/libcroco-0.6.so.3.0.1
b56df000-b570f000 r-xp 00000000 08:01 2311430    /usr/lib/libgsf-1.so.114.0.7
b570f000-b5712000 rw-p 0002f000 08:01 2311430    /usr/lib/libgsf-1.so.114.0.7
b5712000-b5713000 rw-p b5712000 00:00 0 
b5713000-b5743000 r-xp 00000000 08:01 2311827    /usr/lib/librsvg-2.so.2.22.2
b5743000-b5744000 rw-p 00030000 08:01 2311827    /usr/lib/librsvg-2.so.2.22.2
b5755000-b5756000 r-xp 00000000 08:01 2376102    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5756000-b5757000 rw-p 00000000 08:01 2376102    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5757000-b5758000 ---p b5757000 00:00 0 
b5758000-b5f58000 rw-p b5758000 00:00 0 
b5f58000-b5fb8000 rw-s 00000000 00:09 2097169    /SYSV00000000 (deleted)
b5fb8000-b624a000 r--p 00000000 08:01 2637894    /usr/share/icons/hicolor/icon-theme.cache
b624a000-b69ba000 r--p 00000000 08:01 2638286    /usr/share/icons/gnome/icon-theme.cache
b69ba000-b6a65000 r--p 00000000 08:01 2558642    /usr/share/icons/Tangerine/icon-theme.cache
b6a65000-b6bcb000 r--p 00000000 08:01 2557072    /usr/share/icons/Human/icon-theme.cache
b6bcb000-b6ccf000 rw-p b6bcb000 00:00 0 
b6ccf000-b6d60000 r--p 00000000 08:01 2523139    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6d60000-b6d62000 r-xp 00000000 08:01 2442710    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6d62000-b6d63000 rw-p 00001000 08:01 2442710    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6d63000-b6d69000 r--s 00000000 08:01 2474363    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6d69000-b6d6c000 r--s 00000000 08:01 2474346    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6d6c000-b6d6d000 r--s 00000000 08:01 2474341    /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b6d6d000-b6d71000 r--s 00000000 08:01 2474366    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6d71000-b6d74000 r--s 00000000 08:01 2474343    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6d74000-b6d7b000 r--s 00000000 08:01 2474416    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6d7b000-b6d7e000 r--s 00000000 08:01 2474379    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6d7e000-b6d86000 r--s 00000000 08:01 2474347    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6d86000-b6d8e000 r--s 00000000 08:01 2474364    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6d8e000-b6db0000 r--s 00000000 08:01 2474405    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6db0000-b6db3000 r--s 00000000 08:01 2474360    /var/cache/fontconfig/de9486f0b47a4d768a594cb419Aborted


I try to mount using:  sudo mount /dev/sdb /mnt/usb and it says that i need to specify the file system. 

any ideas?

p.s.
i also just looked at the device's properties and for type, size, volume,modified and accessed it says "unknown"

---

### Post by angelsneverdie on 2008-12-27
anyone else have any ideas?

---

### Post by angelsneverdie on 2008-12-30
i just put a thumb drive in my comp and it auto mounted and opened as usual, so maybe the problem is with the mp3 player.  i'll try putting it into a windows machine tomorrow.

---

