---
title: "How Do I Give My Self Permission to Write Files?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by mulluysavage on 2009-12-14
It wasn't happening before, but suddenly I can only open files as read-only in one of my folders. The ownership is root(root) others is greyed-out and says read-only. How do I give my user permission to read/write?

---

### Post by mulluysavage on 2009-12-14
Tried sudo chown -R user My\ Book

returned 'operation not permitted/'

---

### Post by bodhi.zazen on 2009-12-14
I ran into a similar problem in 9.10, had to set permissions with nautilus.

```
gksu nautilus
```

Set ownership and permissions via nautilus.

---

### Post by japju on 2009-12-14
It is unusual for file ownership to change to root in the normal course of work. I guess you could have opened root shell and then edited the files with whatever program and saved them. Still what are these files? It is a bit worrying unless you are in habit of running as root unnecessarily.


You want to read up on commands [FONT="Courier New"]chown[/FONT] (change ownership) and [FONT="Courier New"]chmod[/FONT] (change mode/permissions). Open an [FONT="Courier New"]xterm[/FONT] and [FONT="Courier New"]man chown[/FONT] or [FONT="Courier New"]man chmod[/FONT].

If you are really lost, post the output of the command [FONT="Courier New"]ls -la[/FONT].

---

### Post by mulluysavage on 2009-12-14
> **bodhi.zazen said:**
> I ran into a similar problem in 9.10, had to set permissions with nautilus.

```
gksu nautilus
```

Set ownership and permissions via nautilus.

This didn't do anything - no program opened

---

### Post by mulluysavage on 2009-12-14
> **japju said:**
> It is unusual for file ownership to change to root in the normal course of work. I guess you could have opened root shell and then edited the files with whatever program and saved them. Still what are these files? It is a bit worrying unless you are in habit of running as root unnecessarily.


You want to read up on commands [FONT="Courier New"]chown[/FONT] (change ownership) and [FONT="Courier New"]chmod[/FONT] (change mode/permissions). Open an [FONT="Courier New"]xterm[/FONT] and [FONT="Courier New"]man chown[/FONT] or [FONT="Courier New"]man chmod[/FONT].

If you are really lost, post the output of the command [FONT="Courier New"]ls -la[/FONT].

I tried chown - see above.

re: chmod - do I really want to change the 'file mode bits'?

---

### Post by mulluysavage on 2009-12-14
I take it the table on the left is some kind of permission table. How do I decipher it?

drwxr-xr-x 67 phil phil   4096 2009-12-14 18:52 .
drwxr-xr-x  5 root root   4096 2009-03-10 23:53 ..
drwx------  2 phil phil   4096 2009-02-23 23:33 .AbiSuite
drwx------  3 phil phil   4096 2009-02-24 10:19 .adobe
drwxr-xr-x  2 phil phil   4096 2009-11-10 11:52 .audacity1.3-phil
drwxr-xr-x  4 phil phil   4096 2009-11-10 11:52 .audacity-data
drwxr-xr-x  3 phil phil   4096 2009-10-26 10:33 .avidemux
-rw-r--r--  1 phil phil   2134 2009-02-25 14:17 AV Theory of Change.dia~
-rw-------  1 phil phil   9744 2009-12-14 18:52 .bash_history
-rw-r--r--  1 phil phil    220 2009-02-23 14:18 .bash_logout
-rw-r--r--  1 phil phil   2940 2009-02-23 14:18 .bashrc
drwx------  6 phil phil   4096 2009-02-28 16:04 .BitTornado
drwxr-xr-x  2 phil phil   4096 2009-06-23 00:20 .blueman
-rw-r--r--  1 phil phil    510 2009-06-11 23:20 Blueman Package Key~
drwx------  5 phil phil   4096 2009-02-23 14:38 .cache
-rw-------  1 phil phil  31096 2009-12-02 07:09 Cash%20Flow%202010.xls_0.ods
drwx------ 16 phil phil   4096 2009-12-07 23:06 .config
drwx------  2 phil phil   4096 2009-10-27 11:26 .cups
drwx------  3 phil phil   4096 2009-02-23 14:37 .dbus
-rw-r--r--  1 phil phil     55 2009-12-07 19:02 .DCOPserver_mediabot__0
lrwxrwxrwx  1 phil phil     34 2009-12-07 19:02 .DCOPserver_mediabot_:0 -> /home/phil/.DCOPserver_mediabot__0
drwxr-xr-x 10 phil phil   4096 2009-12-14 18:19 Desktop
drwxr-xr-x  5 phil phil   4096 2009-02-25 13:09 .dia
-rw-------  1 phil phil     28 2009-12-14 08:45 .dmrc
drwxr-xr-x  8 phil phil   4096 2009-12-09 14:46 downloads(temp)
drwxr-x---  2 phil phil   4096 2009-02-28 18:21 .easytag
drwx------  2 phil phil   4096 2009-12-03 07:33 .filezilla
drwxr-xr-x  2 phil phil   4096 2009-11-18 22:21 .fontconfig
drwxr-xr-x  2 phil phil   4096 2009-03-15 11:52 .fonts
-rw-r--r--  1 phil phil   1201 2009-02-26 10:21 foundations of youth programming.dia~
drwx------  2 phil phil   4096 2009-08-22 18:55 .fr-xMCTRK
drwx------  5 phil phil   4096 2009-12-14 08:45 .gconf
drwx------  2 phil phil   4096 2009-12-14 19:00 .gconfd
drwxr-xr-x 22 phil phil   4096 2009-12-14 08:46 .gimp-2.4
-rw-r-----  1 phil phil      0 2009-12-14 10:01 .gksu.lock
drwx------  9 phil phil   4096 2009-12-14 18:52 .gnome2
drwx------  2 phil phil   4096 2009-02-23 14:37 .gnome2_private
-rw-r--r--  1 phil phil   4334 2009-08-29 11:25 .gnumericrc
drwxr-xr-x  3 phil phil   4096 2009-02-24 22:30 .google
drwxr-xr-x  2 phil phil   4096 2009-06-26 04:57 .gstreamer-0.10
-rw-r--r--  1 phil phil    457 2009-12-09 23:59 .gtk-bookmarks
drwxr-xr-x  3 phil phil   4096 2009-07-13 09:25 .gtkpod
drwxr-----  2 phil phil   4096 2009-12-14 18:21 .hplip
-rw-------  1 phil phil   9638 2009-12-14 08:45 .ICEauthority
drwxr-xr-x  4 phil phil   4096 2009-03-15 20:59 .java
drwxr-xr-x  2 phil phil   4096 2009-10-07 21:27 jungledisk
drwx--x--x  3 phil phil   4096 2009-10-07 21:27 .jungledisk
-rw-------  1 phil phil      6 2009-12-10 00:02 .junglediskinstance
drwx------  3 phil phil   4096 2009-02-26 21:12 .kde
drwx------  3 phil phil   4096 2009-08-23 09:50 .kxmame
drwx------  3 root phil   4096 2009-03-08 17:43 .lightscribe
drwxr-xr-x  3 phil phil   4096 2009-02-23 14:37 .local
drwx------  3 phil phil   4096 2009-02-24 10:19 .macromedia
drwxr-xr-x  3 phil phil   4096 2009-02-26 21:20 .mcop
-rw-------  1 phil phil     31 2009-11-10 12:04 .mcoprc
drwx------  4 phil phil   4096 2009-02-25 11:30 .mozilla
drwx------  3 phil phil   4096 2009-02-25 11:30 .mozilla-thunderbird
drwxr-xr-x  2 phil phil   4096 2009-12-07 23:06 .mplayer
-rw-------  1 phil phil      0 2009-02-25 08:26 .mysql_history.TMP
drwxr-xr-x  2 phil phil   4096 2009-12-07 23:06 .mythtv
-rw-r--r--  1 phil phil    332 2009-06-23 19:05 .nvidia-settings-rc
drwx------  3 phil phil   4096 2009-12-14 18:40 .openoffice.org2
drwxr-xr-x  2 phil phil   4096 2009-09-15 10:40 .Picasa3Temp
drwxr-xr-x  2 phil phil   4096 2009-02-25 11:26 .Picasa3Temp_1
drwxr-xr-x  2 phil phil   4096 2009-02-25 11:38 .Picasa3Temp_2
drwxr-xr-x  2 phil phil   4096 2009-10-13 23:45 .Picasa3Temp_3
drwxr-xr-x  2 phil phil  12288 2009-09-28 15:58 .Picasa3Temp_4
drwxr-xr-x  2 phil phil   4096 2009-02-28 13:57 Pictures
-rw-r--r--  1 phil phil    586 2009-02-23 14:18 .profile
drwxr-xr-x  2 phil phil   4096 2009-08-27 11:06 .pulse
-rw-------  1 phil phil    256 2009-02-26 21:18 .pulse-cookie
drwx------  4 phil phil   4096 2009-03-16 09:45 .purple
drwxr-xr-x  2 phil phil   4096 2009-10-28 09:05 .qt
drwxr-xr-x  2 phil phil   4096 2009-11-10 12:06 .quodlibet
-rw-------  1 phil phil  48623 2009-12-14 18:39 .recently-used
-rw-r--r--  1 phil phil 376027 2009-12-14 18:52 .recently-used.xbel
drwxrwx---  3 phil phil   4096 2009-11-18 22:22 .sane
drwx------  3 phil phil   4096 2009-02-28 12:39 .scim
drwx------ 13 phil phil   4096 2009-06-16 06:09 Songbird
drwx------  4 phil phil   4096 2009-03-11 09:33 .songbird2
-rw-r--r--  1 phil phil      0 2009-02-23 14:39 .sudo_as_admin_successful
drwx------  2 phil phil   4096 2009-02-23 23:28 .synaptic
drwxr-xr-x  4 phil phil   4096 2009-03-03 21:20 .thumbnails
drwxr-xr-x  5 phil phil   4096 2009-03-02 09:08 .transmission
drwxr-xr-x  2 phil phil   4096 2009-02-23 20:01 .update-manager-core
drwx------  2 phil phil   4096 2009-02-24 22:29 .update-notifier
drwxr-xr-x  3 phil phil   4096 2009-08-27 12:42 .vlc
drwxr-xr-x  2 phil phil   4096 2009-08-27 09:22 .wapi
-rw-------  1 phil phil    119 2009-12-14 08:45 .Xauthority
drwxr-xr-x  2 phil phil   4096 2009-02-26 21:18 .xine
drwxr-xr-x 10 phil phil   4096 2009-08-22 19:03 .xmame
-rw-r--r--  1 phil phil    146 2009-02-24 10:45 .xscreensaver-getimage.cache
-rw-r--r--  1 phil phil 200148 2009-12-14 18:37 .xsession-errors

---

### Post by Jacks0n on 2009-12-14
Try typing in the following in the terminal

```

sudo chmod -R 700 /home/$USER
sudo chown $USER:$USER -R /home/$USER

```


Jackson

---

### Post by mulluysavage on 2009-12-14
> **Jacks0n said:**
> Try typing in the following in the terminal

```

sudo chmod -R 700 /home/$USER
sudo chown $USER:$USER -R /home/$USER

```


Jackson

Still returns 'operation not permitted.' 

this is not a root folder it's a /media folder

---

### Post by Thocrun on 2009-12-14
should be right here:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

just use cd <path>
to change directory to the folder where the file is located then:

<command> <option (if any)> <filename (FULL)>

so in terminal type:

cd /media/ubuntu/
chmod a+w+r <full file name>
      where /media/ubuntu/ is the name of the folder(S) the file is located in. --do not close terminal halfway inbetween or you'll lose what directory you are in (it is ok to restart though)

---

### Post by mulluysavage on 2009-12-14
> **Thocrun said:**
> should be right here:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

just use cd <path>
to change directory to the folder where the file is located then:

<command> <option (if any)> <filename (FULL)>

so in terminal type:

cd /media/ubuntu/
chmod a+w+r <full file name>
      where /media/ubuntu/ is the name of the folder(S) the file is located in. --do not close terminal halfway inbetween or you'll lose what directory you are in (it is ok to restart though)

cool can I do this recursively for the entire drive? Things are getting messed up. I can't even read at this point.

---

### Post by mulluysavage on 2009-12-14
> **Thocrun said:**
> should be right here:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

just use cd <path>
to change directory to the folder where the file is located then:

<command> <option (if any)> <filename (FULL)>

so in terminal type:

cd /media/ubuntu/
chmod a+w+r <full file name>
      where /media/ubuntu/ is the name of the folder(S) the file is located in. --do not close terminal halfway inbetween or you'll lose what directory you are in (it is ok to restart though)

Thanks for that documentation link. I have a much better understanding of permissions now. But for some reason my files open as read-only, even though i have done

sudo chmod -R a+r+w+x /media/directory

---

### Post by bodhi.zazen on 2009-12-14
Is the file system ntfs or FAT (windows) ?

---

### Post by mulluysavage on 2009-12-15
> **bodhi.zazen said:**
> Is the file system ntfs or FAT (windows) ?

vfat

---

### Post by bodhi.zazen on 2009-12-15
Ah, well, that explains it.

With windows partitions (and a few others) permissions are set when you mount the partition.

mount /dev/sdxy /media/mount_point -o uid-xxx,gid=yyy,umask=zzz

or you add those options in fstab ;)

see : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by mulluysavage on 2009-12-15
> **bodhi.zazen said:**
> Ah, well, that explains it.

With windows partitions (and a few others) permissions are set when you mount the partition.

mount /dev/sdxy /media/mount_point -o uid-xxx,gid=yyy,umask=zzz

or you add those options in fstab ;)

see : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

We have a winner. Thanks bodhi.zazen. and thanks for your how-to! i understand fstab and mounting much better now.

---

