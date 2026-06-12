---
title: "&quot;GDM could not write to your authorization file&quot;"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by mlnease on 2009-10-02
Hello,

My missus has a dual-boot Windows/Hardy setup that's worked well for years.  Yesterday, though, Hardy started to slow down, graphics got shaky etc.  I did an Sbackup Restore and, since then, have received the error message "GDM could not write to your authorization file" each time I've tried to log in under any username.

I've spent several hours today troubleshooting this, found a great many suggestions via Google and Ubuntu Forums but have found nothing that seems to help.

I gather that this message is often the result of no more disk space being available; I've attached a screenshot of Disk Usage Analyzer if it's of any use.

I'm able to view all her files by booting to a (Jaunty) install disk but seem unable to affect any of them from there--that is, delete or whatever.  I'm also able to log in as root via the grub 'recovery' option but don't know where to go from there.

I'd be most grateful for any suggestions.

By the way, deleting Hardy and installing Jaunty is a perfectly acceptable alternative, but I've never reinstalled in a dual-boot setup before, have no real experience partitioning and find the partitioning process for installation daunting--after the point of being asked to edit or delete the Ubuntu partition I find I don't know the answers to any further questions.

Sorry this is vague and possibly redundant; thanks again in advance for any assistance.

mike

---

### Post by arrange on 2009-10-02
First go to the *recovery mode* and run these options [LIST]
[*]fsck
[*]clean
[*]dpkg
[/LIST]Reboot.

If you still have the same problems, check (in *recovery* or via LiveCD & mounting your Ubuntu partition) you have enough free space ```
df -h
```If you don't see any numbers (in "Used") near 100%, then your problem is not free space. Post the output of ```
ls -la /home/<your_username>
ls -la /

```(change the path if using LiveCD, probably something like */media/disk/home/...*)

---

### Post by mlnease on 2009-10-02
Arrange,

Thanks *very* much for the quick response.  I am working on it and will get back to you ASAP.  I had some unexpected (and somewhat alarming) results from the first three options (especially fsck)--maybe because I logged in as root?  I'll see if I can make another user work and try again.

For df -h I did receive a line reading 100%.  Unfortunately on that system I'm unable to connect to the internet (except via the LiveCD) so can't--so far--post output.  It does look, though, like free space *is* the problem, don't you think?  Can you tell me how to select and delete files via the command line in recovery mode (pardon my ignorance)?  I'm accustomed to doing this via GUI.  Is it possible to do this (delete files) while logged in via LiveCD?

Thanks again and for your patience.

mike

---

### Post by mlnease on 2009-10-02
> **arrange said:**
> First go to the *recovery mode* and run these options
[LIST]
[*]fsck
[*]clean
[*]dpkg
[/LIST]
Reboot.

If you still have the same problems, check (in *recovery* or via LiveCD & mounting your Ubuntu partition) you have enough free space ```
df -h
```If you don't see any numbers (in "Used") near 100%, then your problem is not free space. Post the output of ```
ls -la /home/<your_username>
ls -la /

```(change the path if using LiveCD, probably something like */media/disk/home/...*)
OK, output of df -h:

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 218M  2.4M  215M   2% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 218M  2.4M  215M   2% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 218M     0  218M   0% /lib/init/rw
varrun                218M  108K  218M   1% /var/run
varlock               218M     0  218M   0% /var/lock
udev                  218M  160K  217M   1% /dev
tmpfs                 218M   76K  218M   1% /dev/shm
rootfs                218M   25M  193M  12% /
/dev/sr1              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 218M   12K  218M   1% /tmp
/dev/sda3              23G   22G     0 100% /media/disk
ubuntu@ubuntu:~$ 

Output of ubuntu@ubuntu:~$ ls -la /media/disk/home/rose:

total 759332
drwxr-xr-x 77 1000 1000      4096 2009-10-02 20:54 .
drwxr-xr-x 10 root root      4096 2009-10-01 22:20 ..
-rwxr-xr-x  1 1000 1000 688724608 2007-03-02 01:14 -01.ogg
-rw-r--r--  1 1000 1000   8893096 2009-07-06 19:30 12 My Heart Must Do the Crying.mp3
-rw-r--r--  1 1000 1000   9949624 2009-07-06 20:30 14 Stay (Jää Mun Luo).mp3
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 .AbiSuite
-rwxr-xr-x  1 1000 1000       791 2006-11-04 22:52 .acidriprc
-rwxr-xr-x  1 1000 1000      8378 2008-06-13 16:57 Addendum to Form 17.abw
-rwxr-xr-x  1 1000 1000       142 2007-01-20 23:31 .audacity
drwxr-xr-x  4 1000 1000      4096 2009-09-13 00:11 .audacity-data
-rwxr-xr-x  1 1000 1000      2142 2009-10-02 20:24 .bash_history
-rwxr-xr-x  1 1000 1000      2164 2009-08-24 16:40 .bash_history.before_restore_2009-08-28_13.10.12.156273
-rwxr-xr-x  1 1000 1000      2392 2009-10-01 21:41 .bash_history.before_restore_2009-10-01_15.10.52.161037
-rwxr-xr-x  1 1000 1000       220 2006-09-21 16:35 .bash_logout
-rwxr-xr-x  1 1000 1000       414 2006-09-21 16:35 .bash_profile
-rwxr-xr-x  1 1000 1000      2227 2006-09-21 16:35 .bashrc
-rw-r--r--  1 1000 1000   4019734 2009-05-25 02:43 Big Bad Bill.ogg
drwxr-xr-x  6 1000 1000      4096 2006-10-18 17:54 .BitTornado
drwxr-xr-x  6 1000 1000      4096 2008-06-13 15:58 .cache
-rw-r--r--  1 1000 1000      4796 2009-09-04 23:10 Caleb's 9th.abw
drwx------  2 1000 1000      4096 2008-12-13 02:26 .chewing
drwxr-xr-x  2 1000 1000      4096 2008-03-17 01:49 .clay
drwxr-xr-x 12 1000 1000      4096 2009-01-11 01:33 .config
drwxr-xr-x  4 1000 1000      4096 2009-10-01 22:22 Desktop
-rw-r--r--  1 1000 1000        54 2009-06-02 02:35 .devede
-rw-------  1 1000 1000        27 2009-10-01 21:24 .dmrc
drwxr-xr-x  2 1000 1000      4096 2009-08-28 22:14 Documents
drwxr-xr-x 16 1000 1000      4096 2009-07-13 00:44 .dvdcss
drwxr-xr-x  2 1000 1000      4096 2008-07-10 14:12 .dvdrip
-rwxr-xr-x  1 1000 1000     21465 2008-06-12 18:57 .dvdriprc
drwxr-xr-x  2 1000 1000      4096 2007-03-05 18:10 Empty File
-rwxr-xr-x  1 1000 1000        16 2006-09-21 23:43 .esd_auth
-rw-r--r--  1 1000 1000    124761 2009-04-27 17:40 Euboea Poseidon.jpg
drwxr-xr-x  8 1000 1000      4096 2009-09-11 05:05 .evolution
lrwxrwxrwx  1 1000 1000        26 2006-09-21 16:35 Examples -> /usr/share/example-content
-rw-r--r--  1 1000 1000      3346 2008-07-04 22:37 Firefox_wallpaper.png
-rw-r--r--  1 1000 1000  11330950 2009-09-14 18:14 FlashYYdSrD
-rw-r--r--  1 1000 1000  11330950 2009-09-14 18:38 FlashYYdSrD.1
drwxr-xr-x  2 1000 1000      4096 2009-08-19 14:53 .fontconfig
drwxr-xr-x  2 1000 1000      4096 2008-03-10 00:49 .fonts
-rwxr-xr-x  1 1000 1000      1303 2008-06-11 19:05 .fonts.cache-1
-rwxr-xr-x  1 1000 1000       516 2008-03-24 00:24 .fonts.conf
drwxr-xr-x  5 1000 1000      4096 2008-11-25 00:59 .fullcircle
drwxr-xr-x  6 1000 1000      4096 2009-10-01 21:25 .gconf
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:22 .gconfd
-rw-------  1 1000 1000         0 2009-07-16 16:34 gCTaXx
drwx------  2 1000 1000      4096 2009-07-15 02:06 .ggz
drwxr-xr-x 21 1000 1000      4096 2006-09-22 04:03 .gimp-2.2
drwxr-xr-x 20 1000 1000      4096 2009-07-24 16:19 .gimp-2.4
drwx------  2 1000 1000      4096 2009-08-18 18:13 .gimv
-rwxr-xr-x  1 1000 1000         0 2009-10-01 22:08 .gksu.lock
drwxr-xr-x  4 1000 1000      4096 2008-06-30 14:10 .gnome
drwxr-xr-x 19 1000 1000      4096 2009-10-01 22:28 .gnome2
drwxr-xr-x  2 1000 1000      4096 2006-09-22 00:37 .gnome2_private
drwxr-xr-x  2 1000 1000      4096 2009-10-01 21:24 .gnupg
drwxr-xr-x  4 1000 1000      4096 2008-06-13 17:41 GNUstep
drwxr-xr-x  2 1000 1000      4096 2009-06-28 17:07 .gstreamer-0.10
drwxr-xr-x  2 1000 1000      4096 2006-11-04 21:48 .gstreamer-0.8
-rw-r--r--  1 1000 1000       130 2009-07-16 02:15 .gtk-bookmarks
-rw-r--r--  1 1000 1000       104 2009-10-01 21:25 .gtk-bookmarks.before_restore_2009-10-01_15.10.52.161037
-rwxr-xr-x  1 1000 1000     24556 2008-03-17 01:49 .gtk_qt_engine_rc
-rwxr-xr-x  1 1000 1000        86 2006-09-21 23:43 .gtkrc-1.2-gnome2
-rwxr-xr-x  1 1000 1000       287 2008-03-10 00:49 .gtkrc-2.0
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 .gvfs
-rw-------  1 1000 1000         0 2009-10-01 22:28 .ICEauthority
-rw-------  1 1000 1000      1922 2009-08-28 19:55 .ICEauthority.before_restore_2009-08-28_13.10.12.156273
-rw-------  1 1000 1000      1427 2009-10-01 21:24 .ICEauthority.before_restore_2009-10-01_15.10.52.161037
drwxr-xr-x  2 1000 1000      4096 2008-06-30 14:10 .icons
-rwxr-xr-x  1 1000 1000         0 2007-01-25 20:57 .image.iso.8Qubar
-rwxr-xr-x  1 1000 1000         0 2007-03-05 18:54 .image.iso.AwLrcr
-rwxr-xr-x  1 1000 1000         0 2007-01-25 21:14 .image.iso.bOV2MF
-rwxr-xr-x  1 1000 1000         0 2007-01-25 21:15 .image.iso.fcZxef
-rwxr-xr-x  1 1000 1000         0 2007-01-25 20:57 .image.iso.ovgJbJ
-rwxr-xr-x  1 1000 1000         0 2007-01-25 20:58 iso
drwxr-xr-x  3 1000 1000      4096 2006-10-17 15:48 .java
drwxr-xr-x  4 1000 1000      4096 2008-03-09 23:46 .kde
drwxr-xr-x  3 1000 1000      4096 2008-03-24 21:47 .kpackage
drwxr-xr-x  3 1000 1000      4096 2006-11-04 21:47 .local
drwxr-xr-x  4 1000 1000      4096 2006-12-20 22:18 .macromedia
drwxr-xr-x  3 1000 1000      4096 2009-10-01 22:20 .mcop
-rwxr-xr-x  1 1000 1000        31 2009-10-01 15:41 .mcoprc
drwxr-xr-x  3 1000 1000      4096 2006-09-21 23:43 .metacity
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 mike
-rw-r--r--  1 1000 1000  29399040 2009-06-02 02:32 movie.iso
drwxr-xr-x  6 1000 1000      4096 2009-04-05 13:57 .mozilla
drwxr-xr-x  3 1000 1000      4096 2008-06-13 20:59 .mozilla-thunderbird
-rwxr-xr-x  1 1000 1000  12038352 2006-10-13 17:44 mozilla-win32-1.7.13-installer.exe
drwxr-xr-x  2 1000 1000      4096 2006-11-05 04:01 .mplayer
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 Music
drwxr-xr-x  3 1000 1000      8192 2009-10-01 22:28 .nautilus
-rwxr-xr-x  1 1000 1000       135 2006-10-13 17:37 .notifier.conf
-rw-r--r--  1 1000 1000      1149 2008-06-15 19:54 .nvidia-settings-rc
drwxr-xr-x  3 1000 1000      4096 2009-08-28 22:13 .openoffice.org2
drwxr-xr-x  3 1000 1000      4096 2009-07-14 20:31 .parallelrealities
drwx------  2 1000 1000      4096 2009-09-13 00:03 PDF
drwxr-xr-x  2 1000 1000      4096 2009-09-10 22:18 Photos
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 Pictures
-rw-r--r--  1 1000 1000     49512 2009-08-25 16:40 platypus.span.600.jpg
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 Public
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 .pulse
-rwxr-xr-x  1 1000 1000       256 2008-06-13 15:58 .pulse-cookie
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 .qt
drwxr-xr-x  2 1000 1000      4096 2009-07-24 16:18 .quiteinsane_gimp_plugin
-rw-------  1 1000 1000     34540 2007-01-09 01:42 .realplayerrc
-rwxr-xr-x  1 1000 1000      2577 2009-06-19 00:32 .recently-used
-rwxr-xr-x  1 1000 1000      2847 2009-08-25 00:33 .recently-used.before_restore_2009-08-28_13.10.12.156273
-rwxr-xr-x  1 1000 1000      2847 2009-08-28 22:13 .recently-used.before_restore_2009-10-01_15.10.52.161037
-rw-r--r--  1 1000 1000     24901 2009-07-15 18:01 .recently-used.xbel
-rw-r--r--  1 1000 1000     29902 2009-08-28 19:55 .recently-used.xbel.before_restore_2009-08-28_13.10.12.156273
-rw-r--r--  1 1000 1000       218 2009-10-01 16:11 .recently-used.xbel.before_restore_2009-10-01_15.10.52.161037
-rw-r--r--  1 1000 1000       237 2009-09-30 16:07 .registry
drwxr-xr-x  3 1000 1000      4096 2006-09-21 23:47 .sane
drwxr-xr-x  2 1000 1000      4096 2008-08-15 21:42 Sanjuro
drwx------  4 1000 1000      4096 2008-12-13 02:26 .scim
drwxr-xr-x  2 1000 1000      4096 2007-01-20 23:34 .serpentine
-rw-r--r--  1 1000 1000    164352 2009-09-29 17:27 setup.exe
drwx------  5 1000 1000      4096 2009-10-01 22:20 .Skype
drwxr-xr-x  2 1000 1000      4096 2008-02-04 17:32 .speedcrunch
drwxr-xr-x  2 1000 1000      4096 2009-06-02 02:16 .spumux
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 .ssh
-rwxr-xr-x  1 1000 1000         0 2006-09-21 23:52 .sudo_as_admin_successful
drwxr-xr-x  4 1000 1000      4096 2009-07-02 05:34 .sudoku
drwxr-xr-x  2 1000 1000      4096 2008-06-13 15:58 Templates
-rw-r--r--  1 1000 1000     25580 2009-09-24 18:26 The Game.jpg
drwxr-xr-x  2 1000 1000      4096 2008-06-13 22:47 .themes
drwxr-xr-x  5 1000 1000      4096 2008-03-24 16:06 .thumbnails
drwxr-xr-x  3 1000 1000      4096 2008-03-22 21:46 .thunderbird
drwxr-xr-x  2 1000 1000      4096 2006-11-06 19:26 Type name of new folder
-rwxr-xr-x  1 1000 1000       401 2006-12-06 19:44 .ubuntustudio2config
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 untitled folder
drwxr-xr-x  2 1000 1000      4096 2008-06-13 16:00 .update-manager-core
drwxr-xr-x  2 1000 1000      4096 2009-10-01 22:20 .update-notifier
drwxr-xr-x  2 1000 1000      4096 2008-07-15 18:31 Videos
drwxr-xr-x  3 1000 1000      4096 2006-12-31 21:36 .vlc
drwxr-xr-x  2 1000 1000      4096 2009-09-10 22:35 .wapi
drwxr-xr-x  4 1000 1000      4096 2009-10-01 22:20 .wine
drwxr-xr-x  2 1000 1000      4096 2006-10-12 18:23 .xine
-rw-r--r--  1 1000 1000      1918 2009-08-28 19:55 .xsession-errors.before_restore_2009-08-28_13.10.12.156273
-rw-r--r--  1 1000 1000     45056 2009-10-01 22:28 .xsession-errors.before_restore_2009-10-01_15.10.52.161037

and ubuntu@ubuntu:~$ ls -la:

total 44
drwxr-xr-x 24 ubuntu ubuntu  720 2009-10-03 00:54 .
drwxr-xr-x  3 root   root     60 2009-10-02 17:45 ..
-rw-------  1 ubuntu ubuntu  150 2009-10-03 00:53 .bash_history
-rw-r--r--  1 ubuntu ubuntu  220 2009-10-02 17:45 .bash_logout
-rw-r--r--  1 ubuntu ubuntu 3115 2009-10-02 17:45 .bashrc
drwxr-xr-x  2 ubuntu ubuntu   80 2009-10-03 00:47 .cache
drwxr-xr-x  3 ubuntu ubuntu  100 2009-10-03 00:47 .config
drwx------  3 ubuntu ubuntu   60 2009-10-03 00:47 .dbus
drwxr-xr-x  2 ubuntu ubuntu   80 2009-10-03 00:47 Desktop
-rw-------  1 ubuntu ubuntu    2 2009-10-03 00:47 .dmrc
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Documents
-rw-------  1 ubuntu ubuntu   16 2009-10-03 00:47 .esd_auth
drwxr-xr-x  2 ubuntu ubuntu   60 2009-10-03 00:47 .fontconfig
drwx------  4 ubuntu ubuntu   80 2009-10-03 00:47 .gconf
drwx------  2 ubuntu ubuntu   60 2009-10-03 00:55 .gconfd
drwx------  6 ubuntu ubuntu  120 2009-10-03 00:47 .gnome2
drwx------  2 ubuntu ubuntu   40 2009-10-03 00:47 .gnome2_private
drwx------  2 ubuntu ubuntu   60 2009-10-03 00:47 .gnupg
drwxr-xr-x  2 ubuntu ubuntu   60 2009-10-03 00:47 .gstreamer-0.10
-rw-r--r--  1 ubuntu ubuntu  112 2009-10-03 00:47 .gtk-bookmarks
dr-x------  2 ubuntu ubuntu    0 2009-10-03 00:47 .gvfs
-rw-------  1 ubuntu ubuntu  159 2009-10-03 00:47 .ICEauthority
drwx------  4 ubuntu ubuntu   80 2009-10-03 00:54 .mozilla
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Music
drwxr-xr-x  3 ubuntu ubuntu   60 2009-10-03 00:47 .nautilus
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Pictures
-rw-r--r--  1 ubuntu ubuntu  675 2009-10-02 17:45 .profile
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Public
drwx------  2 ubuntu ubuntu  140 2009-10-03 00:47 .pulse
-rw-------  1 ubuntu ubuntu  256 2009-10-03 00:47 .pulse-cookie
-rw-r--r--  1 ubuntu ubuntu    0 2009-10-03 00:49 .sudo_as_admin_successful
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Templates
drwx------  2 ubuntu ubuntu   40 2009-10-03 00:47 .update-notifier
drwxr-xr-x  2 ubuntu ubuntu   40 2009-10-03 00:47 Videos
-rw-------  1 ubuntu ubuntu  117 2009-10-03 00:47 .Xauthority
-rw-r--r--  1 ubuntu ubuntu 2436 2009-10-03 00:48 .xsession-errors
ubuntu@ubuntu:~$ 

Is this of any use?  All Greek to me, I'm afraid--

Thanks Again,

mn

---

### Post by arrange on 2009-10-03
> **mlnease said:**
> ... I had some unexpected (and somewhat alarming) results from the first three options (especially fsck)--maybe because I logged in as root?  I'll see if I can make another user work and try again.

For df -h I did receive a line reading 100%.  ...

I'm accustomed to doing this via GUI.  Is it possible to do this (delete files) while logged in via LiveCD?

1 What alarming results?
2 Did you run the *clean* option before or after the *df -h* output? (The command should have made some free space).
3 This clearly looks like an "out of space" problem.
4 If you are used to GUI, go to LiveCD again, mount your Ubuntu partition, and run Nautilus```
gksudo nautilus
```Press Ctrl+h to see hidden files, and delete the following directories (if you are able to find them; don't forget to press Shift+Del to delete them permanently, not just move them to the trash):[LIST]
[*]/media/disk/.Trash-0
[*]/media/disk/.Trash-1000
[*]/media/disk/root/.local/share/Trash/files
[*]/media/disk/root/.local/share/Trash/info
[*]/media/disk/home/rose/.local/share/Trash/files
[*]/media/disk/home/rose/.local/share/Trash/info
[/LIST]

These are all trash files, so don't worry. You could also run a command to find all large files```
sudo find -type f -size +100M /media/disk 2> /dev/null 
```This will find all larger than 100MB files on your system. If you don't need any of the files, delete them permanently too. But be careful ;-)

---

### Post by mlnease on 2009-10-03
> **arrange said:**
> 1 What alarming results?

fsck:
WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue?

I selected 'no'.  The other results weren't alarming, but for thoroughness' sake:

clean:
bash: clean: command not found

dpkg:
dpkg: need an action option [etc.]

Sorry if I misunderstood anything here.

2 Did you run the *clean* option before or after the *df -h* output? (The command should have made some free space).

Before--

3 This clearly looks like an "out of space" problem.

Yep--

4 If you are used to GUI, go to LiveCD again, mount your Ubuntu partition, and run Nautilus```
gksudo nautilus
```Press Ctrl+h to see hidden files, and delete the following directories (if you are able to find them; don't forget to press Shift+Del to delete them permanently, not just move them to the trash):
[LIST]
[*]/media/disk/.Trash-0
[*]/media/disk/.Trash-1000
[*]/media/disk/root/.local/share/Trash/files
[*]/media/disk/root/.local/share/Trash/info
[*]/media/disk/home/rose/.local/share/Trash/files
[*]/media/disk/home/rose/.local/share/Trash/info
[/LIST]
I couldn't find /media/disk/... so, once I'd figured out how to run gksudo nautilus on the mounted filesystem (thanks), I just went in and deleted a lot of old detritus.  That did the trick.  The Hardy partition is booting normally now except for bad screen resolution--another topic so I'll tackle that separately.

These are all trash files, so don't worry. You could also run a command to find all large files```
sudo find -type f -size +100M /media/disk 2> /dev/null 
```This will find all larger than 100MB files on your system. If you don't need any of the files, delete them permanently too. But be careful ;-)

So, problem solved!  Thanks a million again for your time and patience.  Seems to me I could've saved us both a lot of time if I'd learned a lot more command line commands *before *encountering this problem.  Hard to know where to begin, though, for an old GUI dependent.  Any advice would be most welcome.  Thanks yet again and

Cheers,

mike

---

