---
title: "DVD read and burning problems"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by DavidDJ on 2010-04-27
Hi all, once again I am trying to get my DVD to play and burn DVD. I'm not sure about the cause. It appears to me that it is a permission error or that is the message that the error screens keep telling me. I am running Ubuntu 9.10  DVD LG gh24ls50 it will read data disks on CD and DVD yet will not play any of my movie DVD's. When Burning on the drive it looks like it put data on it but the drive reports a blank disk. My CD burner is having similar problems. The DVD LG gh24ls50 is a fairly new drive is it that proper drivers have not been created. Then again the CD drive is a couple of years old and use to work fine under Windows 2000. 
I would greatly appreciate any help with this problem.

These are the logs generated when I incert a DVD int the drive and play it with MPlayer

AUTH.LOG
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

SYSLOG
Apr 27 08:42:41 david-desktop kernel: [156845.056037] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:42:46 david-desktop kernel: [156850.040045] ata3: soft resetting link
Apr 27 08:42:51 david-desktop kernel: [156855.196157] ata3.00: qc timeout (cmd 0xa1)
Apr 27 08:42:51 david-desktop kernel: [156855.196168] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 27 08:42:56 david-desktop kernel: [156860.236035] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:01 david-desktop kernel: [156865.224646] ata3: soft resetting link
Apr 27 08:43:01 david-desktop kernel: [156865.404214] ata3.00: configured for UDMA/100
Apr 27 08:43:06 david-desktop kernel: [156870.404055] ata3.00: qc timeout (cmd 0xa0)
Apr 27 08:43:06 david-desktop kernel: [156870.404064] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
Apr 27 08:43:06 david-desktop kernel: [156870.404071] ata3.00: limiting speed to UDMA/100:PIO3
Apr 27 08:43:11 david-desktop kernel: [156875.444106] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:16 david-desktop kernel: [156880.428032] ata3: soft resetting link
Apr 27 08:43:26 david-desktop kernel: [156890.584049] ata3.00: qc timeout (cmd 0xa1)
Apr 27 08:43:26 david-desktop kernel: [156890.584060] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 27 08:43:26 david-desktop kernel: [156890.584071] ata3.00: disabled
Apr 27 08:43:31 david-desktop kernel: [156895.624039] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:36 david-desktop kernel: [156900.608041] ata3: soft resetting link
Apr 27 08:43:37 david-desktop kernel: [156900.764095] ata3: EH complete
Apr 27 08:43:37 david-desktop kernel: [156900.764264] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766158] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766613] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766883] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.770492] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.785622] VFS: busy inodes on changed media or resized disk sr1

Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

---

### Post by lisati on 2010-04-27
For **playing** DVDs, look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by cuberts on 2010-04-27
> **DavidDJ said:**
> Hi all, once again I am trying to get my DVD to play and burn DVD. I'm not sure about the cause. It appears to me that it is a permission error or that is the message that the error screens keep telling me. I am running Ubuntu 9.10  DVD LG gh24ls50 it will read data disks on CD and DVD yet will not play any of my DVD's. When Burning on the drive it looks like it put data on it but the drive reports a blank disk. My CD burner is having similar problems. The DVD LG gh24ls50 is a fairly new drive is it that proper drivers have not been created. Then again the CD drive is a couple of years old and use to work fine under Windows 2000. 
I would greatly appreciate any help with this problem.

These are the logs generated when I incert a DVD int the drive and play it with MPlayer

AUTH.LOG
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

SYSLOG
Apr 27 08:42:41 david-desktop kernel: [156845.056037] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:42:46 david-desktop kernel: [156850.040045] ata3: soft resetting link
Apr 27 08:42:51 david-desktop kernel: [156855.196157] ata3.00: qc timeout (cmd 0xa1)
Apr 27 08:42:51 david-desktop kernel: [156855.196168] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 27 08:42:56 david-desktop kernel: [156860.236035] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:01 david-desktop kernel: [156865.224646] ata3: soft resetting link
Apr 27 08:43:01 david-desktop kernel: [156865.404214] ata3.00: configured for UDMA/100
Apr 27 08:43:06 david-desktop kernel: [156870.404055] ata3.00: qc timeout (cmd 0xa0)
Apr 27 08:43:06 david-desktop kernel: [156870.404064] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
Apr 27 08:43:06 david-desktop kernel: [156870.404071] ata3.00: limiting speed to UDMA/100:PIO3
Apr 27 08:43:11 david-desktop kernel: [156875.444106] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:16 david-desktop kernel: [156880.428032] ata3: soft resetting link
Apr 27 08:43:26 david-desktop kernel: [156890.584049] ata3.00: qc timeout (cmd 0xa1)
Apr 27 08:43:26 david-desktop kernel: [156890.584060] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 27 08:43:26 david-desktop kernel: [156890.584071] ata3.00: disabled
Apr 27 08:43:31 david-desktop kernel: [156895.624039] ata3: link is slow to respond, please be patient (ready=0)
Apr 27 08:43:36 david-desktop kernel: [156900.608041] ata3: soft resetting link
Apr 27 08:43:37 david-desktop kernel: [156900.764095] ata3: EH complete
Apr 27 08:43:37 david-desktop kernel: [156900.764264] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766158] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766613] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.766883] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.770492] VFS: busy inodes on changed media or resized disk sr1
Apr 27 08:43:37 david-desktop kernel: [156900.785622] VFS: busy inodes on changed media or resized disk sr1

Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 08:39:01 david-desktop CRON[4714]: pam_unix(cron:session): session closed for user root
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:40:21 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: removing removable location: /media/SUPER_SWEET_16_THEMOVIE
Apr 27 08:43:37 david-desktop gnome-keyring-daemon[1588]: no volume registered at: /media/SUPER_SWEET_16_THEMOVIE

So your computer does read DVDs?
And also are you sure that it is the right format which it has the capability to read?

---

### Post by DavidDJ on 2010-04-28
> **lisati said:**
> For **playing** DVDs, look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

hello all,
     I have done everything in the above link and I still have the same problem video DVD's will not play. does anyone have any new ideas.

---

### Post by awilkin on 2010-04-29
Hi David,

        is mplayer being started automatically when the DVD is inserted? Had similar issue with gxine. Had to disable gxine starting when loading the DVD. Once the DVD icon appeared on the desktop I started gxine from the menu and it seemed to work ok.

---

### Post by DavidDJ on 2010-04-29
> **awilkin said:**
> Hi David,

        is mplayer being started automatically when the DVD is inserted? Had similar issue with gxine. Had to disable gxine starting when loading the DVD. Once the DVD icon appeared on the desktop I started gxine from the menu and it seemed to work ok.

Hello awilkin,

mplayer does start when the disk is inserted. once mplayer gives the error message the drive stops functioning until a reboot.

How do I disable gxine?

---

### Post by DavidDJ on 2010-04-30
Hi everyone,
     This is a terminal output when I try to play a video DVD can someone give me help getting it working.
I formated a hard drive and installed ubuntu 10.04 applied all the fixes I was given before and still the DVD videos will not play. 

david@david-desktop:~$ totem
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr1 with libdvdcss.
libdvdread: Can't open /dev/sr1 for reading
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(365): rsn_dvdsrc_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: Input/output error

david@david-desktop:~$

---

