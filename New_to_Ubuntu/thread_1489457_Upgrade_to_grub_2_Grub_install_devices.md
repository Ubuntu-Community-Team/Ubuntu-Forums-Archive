---
title: "Upgrade to grub 2: Grub install devices?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by KIAaze on 2010-05-21
Hi,

I recently upgraded a friend's PC to Ubuntu 10.04 and am about to upgrade to grub 2 using "upgrade-from-grub-legacy".

It now asks me to select "Grub install devices".
Should I give the device containing the boot sector or the device where Ubuntu is installed and where the grub2 config files should go?

df -h
```
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda6             227G   14G  202G   7% /
none                 1001M  320K 1000M   1% /dev
none                 1005M  248K 1005M   1% /dev/shm
none                 1005M  204K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw

```

sudo fdisk -l

```
Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0xb31eb31e

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1       30401   244192256    7  HPFS/NTFS
/dev/sda2           30402       60801   244188000    5  Etendue
/dev/sda5           60437       60801     2931862+  82  Linux swap / Solaris
/dev/sda6           30402       60435   241248042   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

```

I think selecting /dev/sda6 is the right choice, but just want to be sure, so I don't break anything. :)
(chain-loading works without issues)

---

### Post by warfacegod on 2010-05-21
Assuming that 10.04 is the only OS on the system then sda would most likely be the proper choice. No partition number at all.

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

This is a GRUB2 Guide. Extremely useful.

---

### Post by KIAaze on 2010-05-21
No, it's a dual-boot with Vista.

---

### Post by warfacegod on 2010-05-21
I just saw that NTFS partition. If that's Windows, you *may* be correct in choosing sda6.

This GRUB multi-boot will be useful as well: [http://ubuntuforums.org/showthread.php?t=1462617]("http://ubuntuforums.org/showthread.php?t=1462617")

---

### Post by KIAaze on 2010-05-21
Apparently, the "*" is just a boot flag and doesn't matter to grub:
[http://ubuntuforums.org/showthread.php?t=900885](http://ubuntuforums.org/showthread.php?t=900885)

Can the MBR even be somewhere else than at the beginning of the disk?

I don't remember having that problem myself when upgrading to grub2. Maybe I did a new install. I don't really remember.

---

### Post by warfacegod on 2010-05-21
MBR *can* be where ever you want it.

My advice is to go with sda6 and if that doesn't work, use the GRUB2 Basics guide to reinstall to sda.

---

### Post by SlugSlug on 2010-05-21
i'd stick with the old grub!

---

### Post by KIAaze on 2010-05-21
> **SlugSlug said:**
> i'd stick with the old grub!
Why? I never had problems with Grub2. Any drawbacks?

---

### Post by SlugSlug on 2010-05-21
I prefer the /boot/grub/menu.list way of things rather than this /etc/default/    & update-grub    stuff

---

### Post by philinux on 2010-05-21
@kiaaze, where is grub installed now? Or have you still got the windows bootloader.

---

### Post by KIAaze on 2010-05-21
Well, the grub config files (menu.lst & co) are installed on /dev/sda6.
I have no idea where the MBR is, but I think it's on /dev/sda1.
I'm not on the corresponding PC at the moment, but I can check it this evening (by using the dd command and checking the contents with a hex editor?).

My main problem is that it's not clear what the config dialog is asking for when it says "Grub install devices". I'm not that familiar with grub installation.

---

### Post by annie71307 on 2010-05-21
hi
i have ubuntu10.04 which i upgraded from 9.10. after upgrading i installed window vista.both are in different drives.
but after installing vista i am not able to see ubuntu in boot menu.
please help me.

---

### Post by KIAaze on 2010-05-22
Ok, after rerunning (after aborting previous attempt) upgrade-from-grub-legacy, the explanation seemed more detailed.
It seems to ask for the argument to give to grub-install, which apparently should be the MBR.

So I gave /dev/sda as argument and it's working now.

Just for reference, the different boot sectors of each partition:
```
[^_^][21][~/MBR]$  hexdump -C MBR-sda
00000000  eb 48 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.H....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 03 02  |.....V.U.F...F..|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  1e b3 1e b3 00 00 80 20  |............... |
000001c0  21 00 07 fe ff ff 00 08  00 00 00 28 1c 1d 00 fe  |!..........(....|
000001d0  ff ff 05 fe ff ff 81 45  1c 1d c0 06 1c 1d 00 00  |.......E........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[^_^][22][~/MBR]$  hexdump -C MBR-sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 27 1c 1d 00 00 00 00  |.........'......|
00000030  00 00 0c 00 00 00 00 00  7f c2 d1 01 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c6 02 ee 30 32 ee 30 6c  |...........02.0l|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200
[^_^][23][~/MBR]$  hexdump -C MBR-sda6
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
[^_^][24][~/MBR]$  hexdump -C MBR-sda5
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
[^_^][25][~/MBR]$  hexdump -C MBR-sda4
hexdump: MBR-sda4: Aucun fichier ou dossier de ce type
[^_^][26][~/MBR]$  hexdump -C MBR-sda3
hexdump: MBR-sda3: Aucun fichier ou dossier de ce type
[^_^][27][~/MBR]$  hexdump -C MBR-sda2
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 93 8d  c2 1c 2d 79 59 00 00 fe  |..........-yY...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 d1 4e c2 1c 00 00  |...........N....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[^_^][28][~/MBR]$  

```
MBR-* files made with dd: [http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/](http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/)

---

### Post by KIAaze on 2010-05-22
> **annie71307 said:**
> hi
i have ubuntu10.04 which i upgraded from 9.10. after upgrading i installed window vista.both are in different drives.
but after installing vista i am not able to see ubuntu in boot menu.
please help me.

You will need to reinstall grub to the MBR as far as I know.
This might help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Having 2 separate drives might complicate things a little bit. I never had such a setup.

I suggest creating a new thread for your problem.

---

### Post by warfacegod on 2010-05-22
Have you tried both Ubuntu and Vista to see if they boot?

---

### Post by KIAaze on 2010-05-22
> **warfacegod said:**
> Have you tried both Ubuntu and Vista to see if they boot?

You talkin' to me? O.o
Yes, of course I did. Vista not booting was my main fear. Everything works perfectly. :)
I even created a little reboot_into_windows.sh script:
```
#!/bin/bash
/usr/sbin/grub-reboot "Windows Vista (loader) (on /dev/sda1)"
/sbin/reboot

```
Had to set UID on /sbin/reboot and /usr/bin/grub-editenv to be able to use it without sudo.

---

### Post by warfacegod on 2010-05-22
> **KIAaze said:**
> You talkin' to me? O.o
Yes, of course I did. Vista not booting was my main fear. Everything works perfectly. :)
I even created a little reboot_into_windows.sh script:
```
#!/bin/bash
/usr/sbin/grub-reboot "Windows Vista (loader) (on /dev/sda1)"
/sbin/reboot

```
Had to set UID on /sbin/reboot and /usr/bin/grub-editenv to be able to use it without sudo.

Yep, talking to you. You might want to share that script. I've seen a few threads about doing just that. Maybe write a tiny How To: thread and post it in General Help.

---

### Post by warfacegod on 2010-05-22
> **annie71307 said:**
> hi
i have ubuntu10.04 which i upgraded from 9.10. after upgrading i installed window vista.both are in different drives.
but after installing vista i am not able to see ubuntu in boot menu.
please help me.

Most likely, you need to reinstall GRUB. This will help: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

KIAaze is right though, you should start your own thread.

---

