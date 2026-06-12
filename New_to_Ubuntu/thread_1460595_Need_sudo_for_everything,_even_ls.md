---
title: "Need sudo for everything, even ls"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by wigout on 2010-04-23
I'm running Ubuntu 9.10.

I must have have done something dumb, but I'm not sure what exactly.

The first odd behavior I noticed was that archive manager kept giving errors on tgz and bz2 files. At first the files were new, so I assumed corruption. Eventually I checked on a known good file and got the same error:

```
An error occurred while loading the archive.
```& Command line output like:
```
/home/wigout/bin/tar: 2: @4H%P4: not found
/home/wigout/bin/tar: 2: ELFEà@ppp@: not found
/home/wigout/bin/tar: 3: Syntax error: ")" unexpected
```Eventually I found that I could open those files if I:
```
sudo file-roller
```Before I found that out, however, whenever I opened a terminal window I get the following line of errors:
```
bash: /home/wigout/bin/uname: cannot execute binary file
bash: /home/wigout/bin/uname: cannot execute binary file
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
bash: /home/wigout/bin/sed: cannot execute binary file
```And that was new and odd. Then this:
```
wigout@xps-1530:~$ ls
bash: /home/wigout/bin/ls: cannot execute binary file
```Google sent me to try this:
```
wigout@xps-1530:~$ export PATH=/usr/bin:/bin
```Which permitted to do common commands like ls and such.

EDIT: On a restart, I had to do repeat the export PATH bit.

What did I do? How can I undo it/fix it?

Here are some of the things I've been doing lately: trying out a couple of video editing programs, hex editor, installed dropbox, installed java plugin...

Any help/suggestions/prodding would be helpful.

Thanks,
wigout

---

### Post by wilee-nilee on 2010-04-23
Are you trying to install these files before you look to see if it is actually available in the repositories? It might help if you identify the downloads to us.

---

### Post by wigout on 2010-04-23
> **wilee-nilee said:**
> Are you trying to install these files before you look to see if it is actually available in the repositories?

Well yes. But if they were not available through synaptic I downloaded the package from the site (like dropbox, I think) which was a deb package and clicking on it opened up the deb installer.

---

### Post by wilee-nilee on 2010-04-23
I am running Lucid but here is a screenshot.[ATTACH]154091[/ATTACH]

The link shown in the information window is the dropbox website. Not sure if this is what you wanted, or installed I haven't used it.

---

### Post by wigout on 2010-04-23
> **wilee-nilee said:**
> I am running Lucid but here is a screenshot.[ATTACH]154091[/ATTACH]

The link shown in the information window is the dropbox website. Not sure if this is what you wanted, or installed I haven't used it.

Well you caught me.

I checked and I did install dropbox through synaptic.

But two of the things I installed over last couple of days involved a deb package... but I can't remember which.

Anyway, I don't know if that would have caused any of the trouble anyhow. I just mentioned it because it was recent change.

---

### Post by Penguin Guy on 2010-04-23
> ```
bash: /home/wigout/bin/ls: cannot execute binary file
```

I believe it's because you have a copy of all your programs in your home directory and they are trying to execute instead of the proper ones. Could you post the output of [FONT="Courier New"]echo $PATH[/FONT] and [FONT="Courier New"]ls ~/bin[/FONT] (you may need to run [FONT="Courier New"]export PATH=/usr/bin:/bin[/FONT] to get [FONT="Courier New"]ls[/FONT] to work).

Also, to find out what porgrams you've installed lately, run: [FONT="Courier New"]cat /var/log/dpkg.log[/FONT]
And remove packages using: [FONT="Courier New"]sudo dpkg --remove <package>[/FONT]

---

### Post by wilee-nilee on 2010-04-23
> **wigout said:**
> Well you caught me.

I checked and I did install dropbox through synaptic.

But two of the things I installed over last couple of days involved a deb package... but I can't remember which.

Anyway, I don't know if that would have caused any of the trouble anyhow. I just mentioned it because it was recent change.

We all have to start somewhere using a new OS, I am assuming it is new to you somewhat. I have never bothered learning the installs of tar or other code related installs. I always look for a deb after confirming whether the program is available in a repository. The apt-get call for packages is quite efficient.

---

### Post by wigout on 2010-04-23
I did have to issue the PATH correction again.

Here's the outputs you requested- well I gave ls -al instead of just an ls

```
wigout@xps-1530:~$ ls -al bin
total 984
drwxr-xr-x  2 wigout wigout   4096 2010-04-21 11:04 .
drwxr-xr-x 67 wigout wigout   4096 2010-04-23 01:04 ..
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 addgroup -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 adduser -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 ash -> busybox
-rwxr-xr-x  1 wigout wigout 993544 2010-04-21 11:04 busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 cat -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 chmod -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 chown -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 cp -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 date -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 dd -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 delgroup -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 deluser -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 df -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 dmesg -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 echo -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 egrep -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 false -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 fgrep -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 getopt -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 grep -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 hostname -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 kill -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 ln -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 login -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 ls -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 mkdir -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 mknod -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 mktemp -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 more -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 mount -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 mv -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 netstat -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 nice -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 pidof -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 ping -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 ps -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 pwd -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 rm -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 rmdir -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 sed -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 sh -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 sleep -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 stty -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 sync -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 tar -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 touch -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 true -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 umount -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 uname -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 usleep -> busybox
lrwxrwxrwx  1 wigout wigout      7 2010-04-21 11:04 vi -> busybox
```



```
wigout@xps-1530:~$ echo $PATH
/usr/bin:/bin
```

---

### Post by Penguin Guy on 2010-04-23
Sorry, could you run [FONT="Courier New"]echo $PATH[/FONT], before you run [FONT="Courier New"]export PATH=/usr/bin:/bin[/FONT] so we can see it unmodified.

---

### Post by wigout on 2010-04-23
pre PATH correction:
```
wigout@xps-1530:~$ echo $PATH 
/home/wigout/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

[FONT=Courier New]cat /var/log/dpkg.log[/FONT]
```
2010-04-08 09:23:03 startup archives unpack
2010-04-08 09:23:15 install libdmraid1.0.0.rc15 <none> 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status half-installed libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 install dmraid <none> 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status half-installed dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status triggers-pending man-db 2.5.6-2
2010-04-08 09:23:15 status half-installed dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:15 install gparted <none> 0.4.5-2ubuntu1
2010-04-08 09:23:15 status half-installed gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-08 09:23:15 status half-installed gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 status half-installed gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-08 09:23:15 status half-installed gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 status unpacked gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 status unpacked gparted 0.4.5-2ubuntu1
2010-04-08 09:23:15 install kpartx <none> 0.4.8-14ubuntu2
2010-04-08 09:23:15 status half-installed kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:15 status half-installed kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:15 status unpacked kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:15 status unpacked kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:15 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-08 09:23:15 status half-configured man-db 2.5.6-2
2010-04-08 09:23:16 status installed man-db 2.5.6-2
2010-04-08 09:23:16 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-08 09:23:16 status half-configured hicolor-icon-theme 0.10-2
2010-04-08 09:23:18 status installed hicolor-icon-theme 0.10-2
2010-04-08 09:23:18 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-08 09:23:18 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-08 09:23:18 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-08 09:23:19 startup packages configure
2010-04-08 09:23:19 configure libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status half-configured libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status installed libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-08 09:23:19 configure dmraid 1.0.0.rc15-11ubuntu3 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status half-configured dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status installed dmraid 1.0.0.rc15-11ubuntu3
2010-04-08 09:23:19 status triggers-pending initramfs-tools 0.92bubuntu53
2010-04-08 09:23:19 configure gparted 0.4.5-2ubuntu1 0.4.5-2ubuntu1
2010-04-08 09:23:19 status unpacked gparted 0.4.5-2ubuntu1
2010-04-08 09:23:19 status half-configured gparted 0.4.5-2ubuntu1
2010-04-08 09:23:19 status installed gparted 0.4.5-2ubuntu1
2010-04-08 09:23:19 configure kpartx 0.4.8-14ubuntu2 0.4.8-14ubuntu2
2010-04-08 09:23:19 status unpacked kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:19 status half-configured kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:19 status installed kpartx 0.4.8-14ubuntu2
2010-04-08 09:23:19 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-08 09:23:19 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-08 09:23:20 status installed libc-bin 2.10.1-0ubuntu16
2010-04-08 09:23:20 trigproc initramfs-tools 0.92bubuntu53 0.92bubuntu53
2010-04-08 09:23:20 status half-configured initramfs-tools 0.92bubuntu53
2010-04-08 09:23:35 status installed initramfs-tools 0.92bubuntu53
2010-04-10 23:41:35 startup archives install
2010-04-10 23:41:47 install google-chrome-beta <none> 5.0.342.9-r43360
2010-04-10 23:41:47 status half-installed google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:49 status triggers-pending man-db 2.5.6-2
2010-04-10 23:41:49 status half-installed google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:49 status unpacked google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:49 status unpacked google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:49 configure google-chrome-beta 5.0.342.9-r43360 5.0.342.9-r43360
2010-04-10 23:41:49 status unpacked google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:49 status half-configured google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:50 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/google-chrome 35
2010-04-10 23:41:50 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/google-chrome 35
2010-04-10 23:41:50 update-alternatives: link group gnome-www-browser updated to point to /usr/bin/google-chrome
2010-04-10 23:41:50 status triggers-awaited google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:50 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-10 23:41:50 status half-configured man-db 2.5.6-2
2010-04-10 23:41:50 status installed google-chrome-beta 5.0.342.9-r43360
2010-04-10 23:41:51 status installed man-db 2.5.6-2
2010-04-11 20:16:24 startup archives unpack
2010-04-11 20:16:24 install freepats <none> 20060219-1
2010-04-11 20:16:24 status half-installed freepats 20060219-1
2010-04-11 20:16:25 status unpacked freepats 20060219-1
2010-04-11 20:16:25 status unpacked freepats 20060219-1
2010-04-11 20:16:25 install gstreamer0.10-ffmpeg <none> 0.10.9-1
2010-04-11 20:16:25 status half-installed gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:25 status unpacked gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:25 status unpacked gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:25 install libenca0 <none> 1.9-7
2010-04-11 20:16:25 status half-installed libenca0 1.9-7
2010-04-11 20:16:25 status unpacked libenca0 1.9-7
2010-04-11 20:16:25 status unpacked libenca0 1.9-7
2010-04-11 20:16:25 install libass3 <none> 0.9.6-1
2010-04-11 20:16:25 status half-installed libass3 0.9.6-1
2010-04-11 20:16:25 status unpacked libass3 0.9.6-1
2010-04-11 20:16:25 status unpacked libass3 0.9.6-1
2010-04-11 20:16:25 install libcdaudio1 <none> 0.99.12p2-7
2010-04-11 20:16:25 status half-installed libcdaudio1 0.99.12p2-7
2010-04-11 20:16:25 status unpacked libcdaudio1 0.99.12p2-7
2010-04-11 20:16:25 status unpacked libcdaudio1 0.99.12p2-7
2010-04-11 20:16:25 install libdc1394-22 <none> 2.1.2-1
2010-04-11 20:16:25 status half-installed libdc1394-22 2.1.2-1
2010-04-11 20:16:25 status unpacked libdc1394-22 2.1.2-1
2010-04-11 20:16:25 status unpacked libdc1394-22 2.1.2-1
2010-04-11 20:16:25 install libdca0 <none> 0.0.5-3
2010-04-11 20:16:25 status half-installed libdca0 0.0.5-3
2010-04-11 20:16:25 status unpacked libdca0 0.0.5-3
2010-04-11 20:16:25 status unpacked libdca0 0.0.5-3
2010-04-11 20:16:25 install libdirac0c2a <none> 1.0.2-0ubuntu1
2010-04-11 20:16:25 status half-installed libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:25 status unpacked libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:25 status unpacked libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:25 install libdvdread4 <none> 4.1.3-5ubuntu2
2010-04-11 20:16:25 status half-installed libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:25 status unpacked libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:25 status unpacked libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:25 install libdvdnav4 <none> 4.1.3-3ubuntu1
2010-04-11 20:16:25 status half-installed libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:25 status unpacked libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:25 status unpacked libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:25 install libfaad0 <none> 2.6.1-3.1
2010-04-11 20:16:25 status half-installed libfaad0 2.6.1-3.1
2010-04-11 20:16:25 status unpacked libfaad0 2.6.1-3.1
2010-04-11 20:16:25 status unpacked libfaad0 2.6.1-3.1
2010-04-11 20:16:26 install libiptcdata0 <none> 1.0.3-1ubuntu1
2010-04-11 20:16:26 status half-installed libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:26 status unpacked libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:26 status unpacked libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:26 install libkate1 <none> 0.3.3-1
2010-04-11 20:16:26 status half-installed libkate1 0.3.3-1
2010-04-11 20:16:26 status unpacked libkate1 0.3.3-1
2010-04-11 20:16:26 status unpacked libkate1 0.3.3-1
2010-04-11 20:16:26 install libmimic0 <none> 1.0.4-2
2010-04-11 20:16:26 status half-installed libmimic0 1.0.4-2
2010-04-11 20:16:26 status unpacked libmimic0 1.0.4-2
2010-04-11 20:16:26 status unpacked libmimic0 1.0.4-2
2010-04-11 20:16:26 install libmms0 <none> 0.4-2
2010-04-11 20:16:26 status half-installed libmms0 0.4-2
2010-04-11 20:16:26 status unpacked libmms0 0.4-2
2010-04-11 20:16:26 status unpacked libmms0 0.4-2
2010-04-11 20:16:26 install libmodplug0c2 <none> 1:0.8.7-1
2010-04-11 20:16:26 status half-installed libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:26 status unpacked libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:26 status unpacked libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:26 install libmpcdec3 <none> 1:1.2.2-2.1
2010-04-11 20:16:26 status half-installed libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:26 status unpacked libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:26 status unpacked libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:26 install libfftw3-3 <none> 3.2.1-2ubuntu2
2010-04-11 20:16:26 status half-installed libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:26 status unpacked libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:26 status unpacked libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:26 install libofa0 <none> 0.9.3-3ubuntu1
2010-04-11 20:16:26 status half-installed libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:26 status unpacked libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:26 status unpacked libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:26 install libopenspc0 <none> 0.3.99a-2
2010-04-11 20:16:26 status half-installed libopenspc0 0.3.99a-2
2010-04-11 20:16:26 status unpacked libopenspc0 0.3.99a-2
2010-04-11 20:16:26 status unpacked libopenspc0 0.3.99a-2
2010-04-11 20:16:26 install libsoundtouch1c2 <none> 1.3.1-2
2010-04-11 20:16:26 status half-installed libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:26 status unpacked libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:26 status unpacked libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:26 install libwildmidi0 <none> 0.2.2-2
2010-04-11 20:16:26 status half-installed libwildmidi0 0.2.2-2
2010-04-11 20:16:26 status unpacked libwildmidi0 0.2.2-2
2010-04-11 20:16:26 status unpacked libwildmidi0 0.2.2-2
2010-04-11 20:16:26 install gstreamer0.10-plugins-bad <none> 0.10.14-4ubuntu1.1
2010-04-11 20:16:26 status half-installed gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:26 status unpacked gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:26 status unpacked gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:27 startup packages configure
2010-04-11 20:16:27 configure freepats 20060219-1 20060219-1
2010-04-11 20:16:27 status unpacked freepats 20060219-1
2010-04-11 20:16:27 status unpacked freepats 20060219-1
2010-04-11 20:16:27 status half-configured freepats 20060219-1
2010-04-11 20:16:27 status installed freepats 20060219-1
2010-04-11 20:16:27 configure gstreamer0.10-ffmpeg 0.10.9-1 0.10.9-1
2010-04-11 20:16:27 status unpacked gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:27 status half-configured gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:27 status installed gstreamer0.10-ffmpeg 0.10.9-1
2010-04-11 20:16:27 configure libenca0 1.9-7 1.9-7
2010-04-11 20:16:27 status unpacked libenca0 1.9-7
2010-04-11 20:16:27 status half-configured libenca0 1.9-7
2010-04-11 20:16:27 status installed libenca0 1.9-7
2010-04-11 20:16:27 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-11 20:16:27 configure libass3 0.9.6-1 0.9.6-1
2010-04-11 20:16:27 status unpacked libass3 0.9.6-1
2010-04-11 20:16:27 status half-configured libass3 0.9.6-1
2010-04-11 20:16:27 status installed libass3 0.9.6-1
2010-04-11 20:16:27 configure libcdaudio1 0.99.12p2-7 0.99.12p2-7
2010-04-11 20:16:27 status unpacked libcdaudio1 0.99.12p2-7
2010-04-11 20:16:27 status half-configured libcdaudio1 0.99.12p2-7
2010-04-11 20:16:27 status installed libcdaudio1 0.99.12p2-7
2010-04-11 20:16:27 configure libdc1394-22 2.1.2-1 2.1.2-1
2010-04-11 20:16:27 status unpacked libdc1394-22 2.1.2-1
2010-04-11 20:16:27 status half-configured libdc1394-22 2.1.2-1
2010-04-11 20:16:27 status installed libdc1394-22 2.1.2-1
2010-04-11 20:16:27 configure libdca0 0.0.5-3 0.0.5-3
2010-04-11 20:16:27 status unpacked libdca0 0.0.5-3
2010-04-11 20:16:27 status half-configured libdca0 0.0.5-3
2010-04-11 20:16:27 status installed libdca0 0.0.5-3
2010-04-11 20:16:27 configure libdirac0c2a 1.0.2-0ubuntu1 1.0.2-0ubuntu1
2010-04-11 20:16:27 status unpacked libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:27 status half-configured libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:27 status installed libdirac0c2a 1.0.2-0ubuntu1
2010-04-11 20:16:27 configure libdvdread4 4.1.3-5ubuntu2 4.1.3-5ubuntu2
2010-04-11 20:16:27 status unpacked libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:27 status half-configured libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:27 status installed libdvdread4 4.1.3-5ubuntu2
2010-04-11 20:16:27 configure libdvdnav4 4.1.3-3ubuntu1 4.1.3-3ubuntu1
2010-04-11 20:16:27 status unpacked libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:27 status half-configured libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:27 status installed libdvdnav4 4.1.3-3ubuntu1
2010-04-11 20:16:27 configure libfaad0 2.6.1-3.1 2.6.1-3.1
2010-04-11 20:16:27 status unpacked libfaad0 2.6.1-3.1
2010-04-11 20:16:27 status half-configured libfaad0 2.6.1-3.1
2010-04-11 20:16:27 status installed libfaad0 2.6.1-3.1
2010-04-11 20:16:27 configure libiptcdata0 1.0.3-1ubuntu1 1.0.3-1ubuntu1
2010-04-11 20:16:27 status unpacked libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:27 status half-configured libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:27 status installed libiptcdata0 1.0.3-1ubuntu1
2010-04-11 20:16:27 configure libkate1 0.3.3-1 0.3.3-1
2010-04-11 20:16:27 status unpacked libkate1 0.3.3-1
2010-04-11 20:16:27 status half-configured libkate1 0.3.3-1
2010-04-11 20:16:27 status installed libkate1 0.3.3-1
2010-04-11 20:16:27 configure libmimic0 1.0.4-2 1.0.4-2
2010-04-11 20:16:27 status unpacked libmimic0 1.0.4-2
2010-04-11 20:16:27 status half-configured libmimic0 1.0.4-2
2010-04-11 20:16:27 status installed libmimic0 1.0.4-2
2010-04-11 20:16:27 configure libmms0 0.4-2 0.4-2
2010-04-11 20:16:27 status unpacked libmms0 0.4-2
2010-04-11 20:16:27 status half-configured libmms0 0.4-2
2010-04-11 20:16:27 status installed libmms0 0.4-2
2010-04-11 20:16:27 configure libmodplug0c2 1:0.8.7-1 1:0.8.7-1
2010-04-11 20:16:27 status unpacked libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:27 status half-configured libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:27 status installed libmodplug0c2 1:0.8.7-1
2010-04-11 20:16:27 configure libmpcdec3 1:1.2.2-2.1 1:1.2.2-2.1
2010-04-11 20:16:27 status unpacked libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:27 status half-configured libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:27 status installed libmpcdec3 1:1.2.2-2.1
2010-04-11 20:16:27 configure libfftw3-3 3.2.1-2ubuntu2 3.2.1-2ubuntu2
2010-04-11 20:16:27 status unpacked libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:27 status half-configured libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:27 status installed libfftw3-3 3.2.1-2ubuntu2
2010-04-11 20:16:27 configure libofa0 0.9.3-3ubuntu1 0.9.3-3ubuntu1
2010-04-11 20:16:27 status unpacked libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:27 status half-configured libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:27 status installed libofa0 0.9.3-3ubuntu1
2010-04-11 20:16:27 configure libopenspc0 0.3.99a-2 0.3.99a-2
2010-04-11 20:16:27 status unpacked libopenspc0 0.3.99a-2
2010-04-11 20:16:27 status half-configured libopenspc0 0.3.99a-2
2010-04-11 20:16:28 status installed libopenspc0 0.3.99a-2
2010-04-11 20:16:28 configure libsoundtouch1c2 1.3.1-2 1.3.1-2
2010-04-11 20:16:28 status unpacked libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:28 status half-configured libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:28 status installed libsoundtouch1c2 1.3.1-2
2010-04-11 20:16:28 configure libwildmidi0 0.2.2-2 0.2.2-2
2010-04-11 20:16:28 status unpacked libwildmidi0 0.2.2-2
2010-04-11 20:16:28 status unpacked libwildmidi0 0.2.2-2
2010-04-11 20:16:28 status half-configured libwildmidi0 0.2.2-2
2010-04-11 20:16:28 status installed libwildmidi0 0.2.2-2
2010-04-11 20:16:28 configure gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1 0.10.14-4ubuntu1.1
2010-04-11 20:16:28 status unpacked gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:28 status half-configured gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:28 status installed gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
2010-04-11 20:16:28 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-11 20:16:28 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-11 20:16:28 status installed libc-bin 2.10.1-0ubuntu16
2010-04-13 22:27:17 startup archives unpack
2010-04-13 22:27:30 install libzlcore-data <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:30 status half-installed libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 install libzlcore0.10 <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status half-installed libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 install liblinebreak1 <none> 1.2-1
2010-04-13 22:27:31 status half-installed liblinebreak1 1.2-1
2010-04-13 22:27:31 status unpacked liblinebreak1 1.2-1
2010-04-13 22:27:31 status unpacked liblinebreak1 1.2-1
2010-04-13 22:27:31 install libzltext-data <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status half-installed libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 install libzltext0.10 <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status half-installed libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 install libzlui-gtk <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status half-installed libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status unpacked libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 install fbreader <none> 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:31 status half-installed fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:32 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-13 22:27:32 status half-installed fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:32 status triggers-pending man-db 2.5.6-2
2010-04-13 22:27:32 status half-installed fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:32 status unpacked fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:32 status unpacked fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:32 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-13 22:27:32 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-13 22:27:32 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-13 22:27:32 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-13 22:27:32 status half-configured man-db 2.5.6-2
2010-04-13 22:27:33 status installed man-db 2.5.6-2
2010-04-13 22:27:34 startup packages configure
2010-04-13 22:27:34 configure libzlcore-data 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed libzlcore-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 configure libzlcore0.10 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed libzlcore0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-13 22:27:34 configure liblinebreak1 1.2-1 1.2-1
2010-04-13 22:27:34 status unpacked liblinebreak1 1.2-1
2010-04-13 22:27:34 status half-configured liblinebreak1 1.2-1
2010-04-13 22:27:34 status installed liblinebreak1 1.2-1
2010-04-13 22:27:34 configure libzltext-data 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed libzltext-data 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 configure libzltext0.10 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed libzltext0.10 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 configure libzlui-gtk 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed libzlui-gtk 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 configure fbreader 0.10.7dfsg-2ubuntu2 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status unpacked fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status half-configured fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 status installed fbreader 0.10.7dfsg-2ubuntu2
2010-04-13 22:27:34 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-13 22:27:34 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-13 22:27:34 status installed libc-bin 2.10.1-0ubuntu16
2010-04-14 14:46:18 startup archives unpack
2010-04-14 14:46:30 install libffmpegthumbnailer3 <none> 1.5.4-1build1
2010-04-14 14:46:30 status half-installed libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:30 status unpacked libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:30 status unpacked libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:30 install libmozjs0d <none> 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:30 status half-installed libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:30 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:30 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:30 install mediatomb-common <none> 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 status half-installed mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 status triggers-pending man-db 2.5.6-2
2010-04-14 14:46:30 status half-installed mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 status unpacked mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 status unpacked mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 install mediatomb-daemon <none> 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:30 status half-installed mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status triggers-pending ureadahead 0.90.3-2
2010-04-14 14:46:31 status half-installed mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 install mediatomb <none> 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status half-installed mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:46:31 status half-installed mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status unpacked mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 status unpacked mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:31 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-14 14:46:31 status half-configured man-db 2.5.6-2
2010-04-14 14:46:31 status installed man-db 2.5.6-2
2010-04-14 14:46:31 trigproc ureadahead 0.90.3-2 0.90.3-2
2010-04-14 14:46:31 status half-configured ureadahead 0.90.3-2
2010-04-14 14:46:32 status installed ureadahead 0.90.3-2
2010-04-14 14:46:32 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-14 14:46:32 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:46:32 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:46:32 startup packages configure
2010-04-14 14:46:32 configure libffmpegthumbnailer3 1.5.4-1build1 1.5.4-1build1
2010-04-14 14:46:32 status unpacked libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:32 status half-configured libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:32 status installed libffmpegthumbnailer3 1.5.4-1build1
2010-04-14 14:46:32 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-14 14:46:32 configure libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:32 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:32 status half-configured libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:32 status installed libmozjs0d 1.8.1.16+nobinonly-0ubuntu1
2010-04-14 14:46:32 configure mediatomb-common 0.12.0~svn2018-4ubuntu1 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status half-configured mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status installed mediatomb-common 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 configure mediatomb-daemon 0.12.0~svn2018-4ubuntu1 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status unpacked mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:32 status half-configured mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 status installed mediatomb-daemon 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 configure mediatomb 0.12.0~svn2018-4ubuntu1 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 status unpacked mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 status half-configured mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 status installed mediatomb 0.12.0~svn2018-4ubuntu1
2010-04-14 14:46:33 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-14 14:46:33 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-14 14:46:34 status installed libc-bin 2.10.1-0ubuntu16
2010-04-14 14:47:14 startup archives unpack
2010-04-14 14:47:14 install liba52-0.7.4 <none> 0.7.4-11ubuntu1
2010-04-14 14:47:14 status half-installed liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:14 status unpacked liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:14 status unpacked liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:14 install libcddb2 <none> 1.2.1-1
2010-04-14 14:47:14 status half-installed libcddb2 1.2.1-1
2010-04-14 14:47:14 status unpacked libcddb2 1.2.1-1
2010-04-14 14:47:14 status unpacked libcddb2 1.2.1-1
2010-04-14 14:47:14 install libdvbpsi5 <none> 0.1.6-1
2010-04-14 14:47:14 status half-installed libdvbpsi5 0.1.6-1
2010-04-14 14:47:14 status unpacked libdvbpsi5 0.1.6-1
2010-04-14 14:47:14 status unpacked libdvbpsi5 0.1.6-1
2010-04-14 14:47:14 install libebml0 <none> 0.7.7-3.1
2010-04-14 14:47:14 status half-installed libebml0 0.7.7-3.1
2010-04-14 14:47:14 status unpacked libebml0 0.7.7-3.1
2010-04-14 14:47:14 status unpacked libebml0 0.7.7-3.1
2010-04-14 14:47:14 install libiso9660-5 <none> 0.78.2+dfsg1-3
2010-04-14 14:47:14 status half-installed libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:14 status unpacked libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:14 status unpacked libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:14 install libmad0 <none> 0.15.1b-4
2010-04-14 14:47:14 status half-installed libmad0 0.15.1b-4
2010-04-14 14:47:14 status unpacked libmad0 0.15.1b-4
2010-04-14 14:47:14 status unpacked libmad0 0.15.1b-4
2010-04-14 14:47:14 install libmatroska0 <none> 0.8.1-1.1
2010-04-14 14:47:14 status half-installed libmatroska0 0.8.1-1.1
2010-04-14 14:47:14 status unpacked libmatroska0 0.8.1-1.1
2010-04-14 14:47:14 status unpacked libmatroska0 0.8.1-1.1
2010-04-14 14:47:14 install libmpeg2-4 <none> 0.4.1-3
2010-04-14 14:47:14 status half-installed libmpeg2-4 0.4.1-3
2010-04-14 14:47:14 status unpacked libmpeg2-4 0.4.1-3
2010-04-14 14:47:14 status unpacked libmpeg2-4 0.4.1-3
2010-04-14 14:47:14 install libsdl-image1.2 <none> 1.2.7-1
2010-04-14 14:47:14 status half-installed libsdl-image1.2 1.2.7-1
2010-04-14 14:47:14 status unpacked libsdl-image1.2 1.2.7-1
2010-04-14 14:47:14 status unpacked libsdl-image1.2 1.2.7-1
2010-04-14 14:47:14 install libtar <none> 1.2.11-6
2010-04-14 14:47:14 status half-installed libtar 1.2.11-6
2010-04-14 14:47:14 status unpacked libtar 1.2.11-6
2010-04-14 14:47:14 status unpacked libtar 1.2.11-6
2010-04-14 14:47:14 install libtwolame0 <none> 0.3.12-1
2010-04-14 14:47:14 status half-installed libtwolame0 0.3.12-1
2010-04-14 14:47:14 status unpacked libtwolame0 0.3.12-1
2010-04-14 14:47:14 status unpacked libtwolame0 0.3.12-1
2010-04-14 14:47:15 install libvcdinfo0 <none> 0.7.23-4ubuntu1
2010-04-14 14:47:15 status half-installed libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:15 status unpacked libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:15 status unpacked libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:15 install vlc-data <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status half-installed vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 install libvlccore2 <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status half-installed libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 install libvlc2 <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status half-installed libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status unpacked libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 install libupnp3 <none> 1:1.6.6-3
2010-04-14 14:47:15 status half-installed libupnp3 1:1.6.6-3
2010-04-14 14:47:15 status unpacked libupnp3 1:1.6.6-3
2010-04-14 14:47:15 status unpacked libupnp3 1:1.6.6-3
2010-04-14 14:47:15 install vlc-nox <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:15 status half-installed vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status triggers-pending man-db 2.5.6-2
2010-04-14 14:47:16 status half-installed vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 install libxcb-keysyms1 <none> 0.3.6-1
2010-04-14 14:47:16 status half-installed libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:16 status unpacked libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:16 status unpacked libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:16 install vlc <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status half-installed vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:47:16 status half-installed vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status half-installed vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 install vlc-plugin-pulse <none> 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status half-installed vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 status unpacked vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:16 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-14 14:47:16 status half-configured man-db 2.5.6-2
2010-04-14 14:47:16 status installed man-db 2.5.6-2
2010-04-14 14:47:16 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-14 14:47:16 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:47:16 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-14 14:47:17 startup packages configure
2010-04-14 14:47:17 configure liba52-0.7.4 0.7.4-11ubuntu1 0.7.4-11ubuntu1
2010-04-14 14:47:17 status unpacked liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:17 status half-configured liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:17 status installed liba52-0.7.4 0.7.4-11ubuntu1
2010-04-14 14:47:17 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-14 14:47:17 configure libcddb2 1.2.1-1 1.2.1-1
2010-04-14 14:47:17 status unpacked libcddb2 1.2.1-1
2010-04-14 14:47:17 status half-configured libcddb2 1.2.1-1
2010-04-14 14:47:17 status installed libcddb2 1.2.1-1
2010-04-14 14:47:17 configure libdvbpsi5 0.1.6-1 0.1.6-1
2010-04-14 14:47:17 status unpacked libdvbpsi5 0.1.6-1
2010-04-14 14:47:17 status half-configured libdvbpsi5 0.1.6-1
2010-04-14 14:47:17 status installed libdvbpsi5 0.1.6-1
2010-04-14 14:47:17 configure libebml0 0.7.7-3.1 0.7.7-3.1
2010-04-14 14:47:17 status unpacked libebml0 0.7.7-3.1
2010-04-14 14:47:17 status half-configured libebml0 0.7.7-3.1
2010-04-14 14:47:17 status installed libebml0 0.7.7-3.1
2010-04-14 14:47:17 configure libiso9660-5 0.78.2+dfsg1-3 0.78.2+dfsg1-3
2010-04-14 14:47:17 status unpacked libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:17 status half-configured libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:17 status installed libiso9660-5 0.78.2+dfsg1-3
2010-04-14 14:47:17 configure libmad0 0.15.1b-4 0.15.1b-4
2010-04-14 14:47:17 status unpacked libmad0 0.15.1b-4
2010-04-14 14:47:17 status half-configured libmad0 0.15.1b-4
2010-04-14 14:47:17 status installed libmad0 0.15.1b-4
2010-04-14 14:47:17 configure libmatroska0 0.8.1-1.1 0.8.1-1.1
2010-04-14 14:47:17 status unpacked libmatroska0 0.8.1-1.1
2010-04-14 14:47:17 status half-configured libmatroska0 0.8.1-1.1
2010-04-14 14:47:17 status installed libmatroska0 0.8.1-1.1
2010-04-14 14:47:17 configure libmpeg2-4 0.4.1-3 0.4.1-3
2010-04-14 14:47:17 status unpacked libmpeg2-4 0.4.1-3
2010-04-14 14:47:17 status half-configured libmpeg2-4 0.4.1-3
2010-04-14 14:47:17 status installed libmpeg2-4 0.4.1-3
2010-04-14 14:47:17 configure libsdl-image1.2 1.2.7-1 1.2.7-1
2010-04-14 14:47:17 status unpacked libsdl-image1.2 1.2.7-1
2010-04-14 14:47:17 status half-configured libsdl-image1.2 1.2.7-1
2010-04-14 14:47:17 status installed libsdl-image1.2 1.2.7-1
2010-04-14 14:47:17 configure libtar 1.2.11-6 1.2.11-6
2010-04-14 14:47:17 status unpacked libtar 1.2.11-6
2010-04-14 14:47:17 status half-configured libtar 1.2.11-6
2010-04-14 14:47:17 status installed libtar 1.2.11-6
2010-04-14 14:47:17 configure libtwolame0 0.3.12-1 0.3.12-1
2010-04-14 14:47:17 status unpacked libtwolame0 0.3.12-1
2010-04-14 14:47:17 status half-configured libtwolame0 0.3.12-1
2010-04-14 14:47:17 status installed libtwolame0 0.3.12-1
2010-04-14 14:47:17 configure libvcdinfo0 0.7.23-4ubuntu1 0.7.23-4ubuntu1
2010-04-14 14:47:17 status unpacked libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:17 status half-configured libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:17 status installed libvcdinfo0 0.7.23-4ubuntu1
2010-04-14 14:47:17 configure vlc-data 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed vlc-data 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 configure libvlccore2 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed libvlccore2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 configure libvlc2 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed libvlc2 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 configure libupnp3 1:1.6.6-3 1:1.6.6-3
2010-04-14 14:47:17 status unpacked libupnp3 1:1.6.6-3
2010-04-14 14:47:17 status half-configured libupnp3 1:1.6.6-3
2010-04-14 14:47:17 status installed libupnp3 1:1.6.6-3
2010-04-14 14:47:17 configure vlc-nox 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed vlc-nox 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 configure libxcb-keysyms1 0.3.6-1 0.3.6-1
2010-04-14 14:47:17 status unpacked libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:17 status half-configured libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:17 status installed libxcb-keysyms1 0.3.6-1
2010-04-14 14:47:17 configure vlc 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed vlc 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 configure vlc-plugin-pulse 1.0.2-1ubuntu2.1 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status unpacked vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status half-configured vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 status installed vlc-plugin-pulse 1.0.2-1ubuntu2.1
2010-04-14 14:47:17 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-14 14:47:17 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-14 14:47:17 status installed libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:39 startup packages remove
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:39 status installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:52 remove libavutil49 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:52 status half-configured libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:52 status half-installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:53 status config-files libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status config-files libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 remove libavcodec52 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status half-configured libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status half-installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status config-files libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 status config-files libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:53 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-15 11:01:53 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:53 status installed libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:54 startup archives unpack
2010-04-15 11:01:54 install libavutil-extra-49 <none> 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status half-installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 install libopenjpeg2 <none> 1.3+dfsg-4
2010-04-15 11:01:54 status half-installed libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:54 status unpacked libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:54 status unpacked libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:54 install libavcodec-extra-52 <none> 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status half-installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status unpacked libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 status unpacked libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:54 install libavdevice52 <none> 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status half-installed libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 install libavfilter0 <none> 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status half-installed libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 install ffmpeg <none> 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:54 status half-installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status triggers-pending man-db 2.5.6-2
2010-04-15 11:01:55 status half-installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-15 11:01:55 status half-configured man-db 2.5.6-2
2010-04-15 11:01:55 status installed man-db 2.5.6-2
2010-04-15 11:01:55 startup packages configure
2010-04-15 11:01:55 configure libavutil-extra-49 4:0.5+svn20090706-2ubuntu3 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status half-configured libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:55 configure libopenjpeg2 1.3+dfsg-4 1.3+dfsg-4
2010-04-15 11:01:55 status unpacked libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:55 status half-configured libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:55 status installed libopenjpeg2 1.3+dfsg-4
2010-04-15 11:01:55 configure libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status unpacked libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status half-configured libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-15 11:01:55 configure libavdevice52 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status half-configured libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status installed libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 configure libavfilter0 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status half-configured libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status installed libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 configure ffmpeg 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status half-configured ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 status installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-15 11:01:55 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-15 11:01:55 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-15 11:01:56 status installed libc-bin 2.10.1-0ubuntu16
2010-04-19 11:58:12 startup archives install
2010-04-19 11:58:27 install handbrake-gtk <none> 0.9.4
2010-04-19 11:58:27 status half-installed handbrake-gtk 0.9.4
2010-04-19 11:58:27 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-19 11:58:27 status half-installed handbrake-gtk 0.9.4
2010-04-19 11:58:27 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-19 11:58:27 status half-installed handbrake-gtk 0.9.4
2010-04-19 11:58:28 status unpacked handbrake-gtk 0.9.4
2010-04-19 11:58:28 status unpacked handbrake-gtk 0.9.4
2010-04-19 11:58:28 configure handbrake-gtk 0.9.4 0.9.4
2010-04-19 11:58:28 status unpacked handbrake-gtk 0.9.4
2010-04-19 11:58:28 status half-configured handbrake-gtk 0.9.4
2010-04-19 11:58:28 status triggers-awaited handbrake-gtk 0.9.4
2010-04-19 11:58:28 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-19 11:58:28 status half-configured hicolor-icon-theme 0.10-2
2010-04-19 11:58:31 status installed hicolor-icon-theme 0.10-2
2010-04-19 11:58:31 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-19 11:58:31 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-19 11:58:31 status installed handbrake-gtk 0.9.4
2010-04-19 11:58:32 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-19 12:50:24 startup archives unpack
2010-04-19 12:50:36 install libzen0 <none> 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:36 status half-installed libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:36 status unpacked libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:36 status unpacked libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:36 install libmediainfo0 <none> 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:36 status half-installed libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:36 status unpacked libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:36 status unpacked libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:36 install libwxbase2.6-0 <none> 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:36 status half-installed libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:36 status unpacked libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 status unpacked libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 install libwxgtk2.6-0 <none> 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 status half-installed libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 status unpacked libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 status unpacked libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:37 install mediainfo <none> 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status half-installed mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status unpacked mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status unpacked mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 install mediainfo-gui <none> 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status half-installed mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-19 12:50:37 status half-installed mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-19 12:50:37 status half-installed mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status unpacked mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 status unpacked mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:37 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-19 12:50:37 status half-configured hicolor-icon-theme 0.10-2
2010-04-19 12:50:41 status installed hicolor-icon-theme 0.10-2
2010-04-19 12:50:41 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-19 12:50:41 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-19 12:50:42 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-19 12:50:43 startup packages configure
2010-04-19 12:50:43 configure libzen0 0.4.12-1~ppa1~karmic1 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:43 status unpacked libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:43 status half-configured libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:43 status installed libzen0 0.4.12-1~ppa1~karmic1
2010-04-19 12:50:43 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-19 12:50:43 configure libmediainfo0 0.7.30-1~ppa1~karmic1 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status unpacked libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status half-configured libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status installed libmediainfo0 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 configure libwxbase2.6-0 2.6.3.2.2-3ubuntu5 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status unpacked libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status half-configured libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status installed libwxbase2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 configure libwxgtk2.6-0 2.6.3.2.2-3ubuntu5 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status unpacked libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status half-configured libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 status installed libwxgtk2.6-0 2.6.3.2.2-3ubuntu5
2010-04-19 12:50:43 configure mediainfo 0.7.30-1~ppa1~karmic1 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status unpacked mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status half-configured mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status installed mediainfo 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 configure mediainfo-gui 0.7.30-1~ppa1~karmic1 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status unpacked mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status half-configured mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 status installed mediainfo-gui 0.7.30-1~ppa1~karmic1
2010-04-19 12:50:43 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-19 12:50:43 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-19 12:50:44 status installed libc-bin 2.10.1-0ubuntu16
2010-04-19 13:02:01 startup archives unpack
2010-04-19 13:02:01 install mencoder <none> 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:01 status half-installed mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:01 status triggers-pending man-db 2.5.6-2
2010-04-19 13:02:01 status half-installed mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:02 status unpacked mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:02 status unpacked mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:02 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-19 13:02:02 status half-configured man-db 2.5.6-2
2010-04-19 13:02:02 status installed man-db 2.5.6-2
2010-04-19 13:02:03 startup packages configure
2010-04-19 13:02:03 configure mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:03 status unpacked mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:03 status half-configured mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:02:03 status installed mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
2010-04-19 13:16:52 startup archives unpack
2010-04-19 13:16:52 install libid3tag0 <none> 0.15.1b-10build1
2010-04-19 13:16:52 status half-installed libid3tag0 0.15.1b-10build1
2010-04-19 13:16:52 status unpacked libid3tag0 0.15.1b-10build1
2010-04-19 13:16:52 status unpacked libid3tag0 0.15.1b-10build1
2010-04-19 13:16:52 install libsidplay1 <none> 1.36.59-5
2010-04-19 13:16:52 status half-installed libsidplay1 1.36.59-5
2010-04-19 13:16:52 status unpacked libsidplay1 1.36.59-5
2010-04-19 13:16:52 status unpacked libsidplay1 1.36.59-5
2010-04-19 13:16:52 install gstreamer0.10-plugins-ugly <none> 0.10.12-1
2010-04-19 13:16:52 status half-installed gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:52 status unpacked gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:52 status unpacked gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:53 startup packages configure
2010-04-19 13:16:53 configure libid3tag0 0.15.1b-10build1 0.15.1b-10build1
2010-04-19 13:16:53 status unpacked libid3tag0 0.15.1b-10build1
2010-04-19 13:16:53 status half-configured libid3tag0 0.15.1b-10build1
2010-04-19 13:16:53 status installed libid3tag0 0.15.1b-10build1
2010-04-19 13:16:53 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-19 13:16:53 configure libsidplay1 1.36.59-5 1.36.59-5
2010-04-19 13:16:53 status unpacked libsidplay1 1.36.59-5
2010-04-19 13:16:53 status half-configured libsidplay1 1.36.59-5
2010-04-19 13:16:53 status installed libsidplay1 1.36.59-5
2010-04-19 13:16:53 configure gstreamer0.10-plugins-ugly 0.10.12-1 0.10.12-1
2010-04-19 13:16:53 status unpacked gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:53 status half-configured gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:53 status installed gstreamer0.10-plugins-ugly 0.10.12-1
2010-04-19 13:16:53 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-19 13:16:53 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-19 13:16:53 status installed libc-bin 2.10.1-0ubuntu16
2010-04-20 07:41:39 startup archives unpack
2010-04-20 07:41:39 install liblzma0 <none> 4.999.8beta-0ubuntu2
2010-04-20 07:41:39 status half-installed liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:41:39 status unpacked liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:41:39 status unpacked liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:41:39 install libqt4-qt3support <none> 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:39 status half-installed libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:39 status unpacked libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:39 status unpacked libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:39 install libclucene0ldbl <none> 0.9.20-3
2010-04-20 07:41:39 status half-installed libclucene0ldbl 0.9.20-3
2010-04-20 07:41:39 status unpacked libclucene0ldbl 0.9.20-3
2010-04-20 07:41:39 status unpacked libclucene0ldbl 0.9.20-3
2010-04-20 07:41:39 install soprano-daemon <none> 2.3.1+dfsg.1-1
2010-04-20 07:41:39 status half-installed soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:41:40 status unpacked soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:41:40 status unpacked soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:41:40 install libsoprano4 <none> 2.3.1+dfsg.1-1
2010-04-20 07:41:40 status half-installed libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:41:40 status unpacked libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:41:40 status unpacked libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:41:40 install libexiv2-5 <none> 0.18.2-1
2010-04-20 07:41:40 status half-installed libexiv2-5 0.18.2-1
2010-04-20 07:41:40 status unpacked libexiv2-5 0.18.2-1
2010-04-20 07:41:40 status unpacked libexiv2-5 0.18.2-1
2010-04-20 07:41:40 install libstreams0 <none> 0.7.0-1
2010-04-20 07:41:40 status half-installed libstreams0 0.7.0-1
2010-04-20 07:41:40 status unpacked libstreams0 0.7.0-1
2010-04-20 07:41:40 status unpacked libstreams0 0.7.0-1
2010-04-20 07:41:40 install libstreamanalyzer0 <none> 0.7.0-1
2010-04-20 07:41:40 status half-installed libstreamanalyzer0 0.7.0-1
2010-04-20 07:41:40 status unpacked libstreamanalyzer0 0.7.0-1
2010-04-20 07:41:40 status unpacked libstreamanalyzer0 0.7.0-1
2010-04-20 07:41:40 install kdelibs5-data <none> 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:40 status half-installed kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:40 status triggers-pending man-db 2.5.6-2
2010-04-20 07:41:40 status half-installed kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-20 07:41:41 status half-installed kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status triggers-pending shared-mime-info 0.70-0ubuntu1
2010-04-20 07:41:41 status half-installed kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status unpacked kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status unpacked kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 install kdelibs-bin <none> 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status half-installed kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status unpacked kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status unpacked kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 install kdelibs5 <none> 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:41 status half-installed kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:43 status unpacked kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:43 status unpacked kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:43 install dvdauthor <none> 0.6.14-3ubuntu4
2010-04-20 07:41:43 status half-installed dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:41:43 status half-installed dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:41:43 status unpacked dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:41:43 status unpacked dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:41:43 install exiv2 <none> 0.18.2-1
2010-04-20 07:41:43 status half-installed exiv2 0.18.2-1
2010-04-20 07:41:43 status half-installed exiv2 0.18.2-1
2010-04-20 07:41:43 status unpacked exiv2 0.18.2-1
2010-04-20 07:41:43 status unpacked exiv2 0.18.2-1
2010-04-20 07:41:43 install libcv1 <none> 1.0.0-6.2ubuntu1
2010-04-20 07:41:43 status half-installed libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 install libcvaux1 <none> 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status half-installed libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 install libgavl1 <none> 1.1.0-2
2010-04-20 07:41:44 status half-installed libgavl1 1.1.0-2
2010-04-20 07:41:44 status unpacked libgavl1 1.1.0-2
2010-04-20 07:41:44 status unpacked libgavl1 1.1.0-2
2010-04-20 07:41:44 install libhighgui1 <none> 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status half-installed libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 status unpacked libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:41:44 install frei0r-plugins <none> 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:41:44 status half-installed frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:41:44 status unpacked frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:41:44 status unpacked frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:41:44 install kde-icons-oxygen <none> 4:4.3.2-0ubuntu1
2010-04-20 07:41:44 status half-installed kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 status unpacked kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 status unpacked kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 install libknotificationitem1 <none> 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 status half-installed libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 status unpacked libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 status unpacked libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:41:47 install libqt4-opengl <none> 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:47 status half-installed libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:47 status unpacked libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:47 status unpacked libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:41:47 install libplasma3 <none> 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:47 status half-installed libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:47 status unpacked libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:47 status unpacked libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:41:47 install libxine1-bin <none> 1.1.16.3-0ubuntu4
2010-04-20 07:41:47 status half-installed libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status half-installed libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 install libxine1-misc-plugins <none> 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status half-installed libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 install libxcb-shape0 <none> 1.4-1
2010-04-20 07:41:48 status half-installed libxcb-shape0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-shape0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-shape0 1.4-1
2010-04-20 07:41:48 install libxcb-shm0 <none> 1.4-1
2010-04-20 07:41:48 status half-installed libxcb-shm0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-shm0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-shm0 1.4-1
2010-04-20 07:41:48 install libxcb-xv0 <none> 1.4-1
2010-04-20 07:41:48 status half-installed libxcb-xv0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-xv0 1.4-1
2010-04-20 07:41:48 status unpacked libxcb-xv0 1.4-1
2010-04-20 07:41:48 install libxine1-x <none> 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status half-installed libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 install libxine1-console <none> 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status half-installed libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 install libxine1 <none> 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status half-installed libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 status unpacked libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:41:48 install kdebase-runtime-bin-kde4 <none> 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status half-installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status unpacked kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status unpacked kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 install kdebase-runtime-data-common <none> 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status half-installed kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status half-installed kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status half-installed kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status unpacked kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status unpacked kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 install kdebase-runtime-data <none> 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:48 status half-installed kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:49 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-20 07:41:49 status half-installed kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:49 status half-installed kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:49 status unpacked kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:49 status unpacked kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:49 install phonon-backend-xine <none> 4:4.3.1-4ubuntu1
2010-04-20 07:41:49 status half-installed phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:41:50 status unpacked phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:41:50 status unpacked phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:41:50 install kdebase-runtime <none> 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:50 status half-installed kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:50 status half-installed kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:50 status unpacked kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:50 status unpacked kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:50 install libquicktime1 <none> 2:1.1.1+debian-1build1
2010-04-20 07:41:50 status half-installed libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:41:50 status unpacked libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:41:50 status unpacked libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:41:50 install libsox1a <none> 14.3.0-1build1
2010-04-20 07:41:50 status half-installed libsox1a 14.3.0-1build1
2010-04-20 07:41:50 status unpacked libsox1a 14.3.0-1build1
2010-04-20 07:41:50 status unpacked libsox1a 14.3.0-1build1
2010-04-20 07:41:50 install libmlt1 <none> 0.4.4-2build1
2010-04-20 07:41:50 status half-installed libmlt1 0.4.4-2build1
2010-04-20 07:41:50 status unpacked libmlt1 0.4.4-2build1
2010-04-20 07:41:50 status unpacked libmlt1 0.4.4-2build1
2010-04-20 07:41:50 install libmlt++2 <none> 0.4.4-2build1
2010-04-20 07:41:50 status half-installed libmlt++2 0.4.4-2build1
2010-04-20 07:41:50 status unpacked libmlt++2 0.4.4-2build1
2010-04-20 07:41:50 status unpacked libmlt++2 0.4.4-2build1
2010-04-20 07:41:50 install kdenlive-data <none> 0.7.5-1ubuntu1
2010-04-20 07:41:50 status half-installed kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:41:50 status half-installed kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:41:52 status half-installed kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:41:52 status unpacked kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:41:52 status unpacked kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:41:53 install libmlt-data <none> 0.4.4-2build1
2010-04-20 07:41:53 status half-installed libmlt-data 0.4.4-2build1
2010-04-20 07:41:53 status unpacked libmlt-data 0.4.4-2build1
2010-04-20 07:41:54 status unpacked libmlt-data 0.4.4-2build1
2010-04-20 07:41:54 install melt <none> 0.4.4-2build1
2010-04-20 07:41:54 status half-installed melt 0.4.4-2build1
2010-04-20 07:41:54 status half-installed melt 0.4.4-2build1
2010-04-20 07:41:55 status unpacked melt 0.4.4-2build1
2010-04-20 07:41:55 status unpacked melt 0.4.4-2build1
2010-04-20 07:41:56 install kdenlive <none> 0.7.5-1ubuntu1
2010-04-20 07:41:56 status half-installed kdenlive 0.7.5-1ubuntu1
2010-04-20 07:41:56 status half-installed kdenlive 0.7.5-1ubuntu1
2010-04-20 07:41:56 status half-installed kdenlive 0.7.5-1ubuntu1
2010-04-20 07:41:56 status unpacked kdenlive 0.7.5-1ubuntu1
2010-04-20 07:41:56 status unpacked kdenlive 0.7.5-1ubuntu1
2010-04-20 07:41:56 install khelpcenter4 <none> 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:56 status half-installed khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:56 status half-installed khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:56 status unpacked khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:56 status unpacked khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:41:56 install libsox-fmt-alsa <none> 14.3.0-1build1
2010-04-20 07:41:56 status half-installed libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:41:56 status unpacked libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:41:56 status unpacked libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:41:56 install libsox-fmt-base <none> 14.3.0-1build1
2010-04-20 07:41:56 status half-installed libsox-fmt-base 14.3.0-1build1
2010-04-20 07:41:56 status unpacked libsox-fmt-base 14.3.0-1build1
2010-04-20 07:41:56 status unpacked libsox-fmt-base 14.3.0-1build1
2010-04-20 07:41:56 install recordmydesktop <none> 0.3.8.1-0ubuntu2
2010-04-20 07:41:56 status half-installed recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:41:56 status half-installed recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:41:56 status unpacked recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:41:56 status unpacked recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:41:56 install swh-plugins <none> 0.4.15-2
2010-04-20 07:41:56 status half-installed swh-plugins 0.4.15-2
2010-04-20 07:41:56 status triggers-pending doc-base 0.9.3
2010-04-20 07:41:56 status half-installed swh-plugins 0.4.15-2
2010-04-20 07:41:56 status unpacked swh-plugins 0.4.15-2
2010-04-20 07:41:56 status unpacked swh-plugins 0.4.15-2
2010-04-20 07:41:56 install ttf-dejavu-extra <none> 2.29-2
2010-04-20 07:41:56 status half-installed ttf-dejavu-extra 2.29-2
2010-04-20 07:41:57 status unpacked ttf-dejavu-extra 2.29-2
2010-04-20 07:41:57 status unpacked ttf-dejavu-extra 2.29-2
2010-04-20 07:41:57 install ttf-dejavu <none> 2.29-2
2010-04-20 07:41:57 status half-installed ttf-dejavu 2.29-2
2010-04-20 07:41:57 status unpacked ttf-dejavu 2.29-2
2010-04-20 07:41:57 status unpacked ttf-dejavu 2.29-2
2010-04-20 07:41:57 install dvgrab <none> 3.4-1build1
2010-04-20 07:41:57 status half-installed dvgrab 3.4-1build1
2010-04-20 07:41:57 status half-installed dvgrab 3.4-1build1
2010-04-20 07:41:57 status unpacked dvgrab 3.4-1build1
2010-04-20 07:41:57 status unpacked dvgrab 3.4-1build1
2010-04-20 07:41:57 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-20 07:41:57 status half-configured man-db 2.5.6-2
2010-04-20 07:41:57 status installed man-db 2.5.6-2
2010-04-20 07:41:57 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-20 07:41:57 status half-configured hicolor-icon-theme 0.10-2
2010-04-20 07:42:02 status installed hicolor-icon-theme 0.10-2
2010-04-20 07:42:03 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2010-04-20 07:42:03 status half-configured shared-mime-info 0.70-0ubuntu1
2010-04-20 07:42:04 status installed shared-mime-info 0.70-0ubuntu1
2010-04-20 07:42:04 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-20 07:42:04 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-20 07:42:04 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-20 07:42:04 trigproc doc-base 0.9.3 0.9.3
2010-04-20 07:42:04 status half-configured doc-base 0.9.3
2010-04-20 07:42:05 status installed doc-base 0.9.3
2010-04-20 07:42:05 startup packages configure
2010-04-20 07:42:05 configure liblzma0 4.999.8beta-0ubuntu2 4.999.8beta-0ubuntu2
2010-04-20 07:42:05 status unpacked liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:42:05 status half-configured liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:42:05 status installed liblzma0 4.999.8beta-0ubuntu2
2010-04-20 07:42:05 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-20 07:42:05 configure libqt4-qt3support 4.5.3really4.5.2-0ubuntu1 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:05 status unpacked libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:05 status half-configured libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:05 status installed libqt4-qt3support 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:05 configure libclucene0ldbl 0.9.20-3 0.9.20-3
2010-04-20 07:42:05 status unpacked libclucene0ldbl 0.9.20-3
2010-04-20 07:42:05 status half-configured libclucene0ldbl 0.9.20-3
2010-04-20 07:42:05 status installed libclucene0ldbl 0.9.20-3
2010-04-20 07:42:05 configure libexiv2-5 0.18.2-1 0.18.2-1
2010-04-20 07:42:05 status unpacked libexiv2-5 0.18.2-1
2010-04-20 07:42:05 status half-configured libexiv2-5 0.18.2-1
2010-04-20 07:42:05 status installed libexiv2-5 0.18.2-1
2010-04-20 07:42:05 configure libstreams0 0.7.0-1 0.7.0-1
2010-04-20 07:42:05 status unpacked libstreams0 0.7.0-1
2010-04-20 07:42:05 status half-configured libstreams0 0.7.0-1
2010-04-20 07:42:06 status installed libstreams0 0.7.0-1
2010-04-20 07:42:06 configure libstreamanalyzer0 0.7.0-1 0.7.0-1
2010-04-20 07:42:06 status unpacked libstreamanalyzer0 0.7.0-1
2010-04-20 07:42:06 status half-configured libstreamanalyzer0 0.7.0-1
2010-04-20 07:42:06 status installed libstreamanalyzer0 0.7.0-1
2010-04-20 07:42:06 configure kdelibs5-data 4:4.3.2-0ubuntu7.2 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:06 status unpacked kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:06 status unpacked kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:06 status half-configured kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:06 status installed kdelibs5-data 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:06 configure dvdauthor 0.6.14-3ubuntu4 0.6.14-3ubuntu4
2010-04-20 07:42:06 status unpacked dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:42:06 status half-configured dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:42:06 status installed dvdauthor 0.6.14-3ubuntu4
2010-04-20 07:42:06 configure exiv2 0.18.2-1 0.18.2-1
2010-04-20 07:42:06 status unpacked exiv2 0.18.2-1
2010-04-20 07:42:06 status half-configured exiv2 0.18.2-1
2010-04-20 07:42:06 status installed exiv2 0.18.2-1
2010-04-20 07:42:06 configure libcv1 1.0.0-6.2ubuntu1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status unpacked libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status half-configured libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status installed libcv1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 configure libcvaux1 1.0.0-6.2ubuntu1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status unpacked libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status half-configured libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status installed libcvaux1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 configure libgavl1 1.1.0-2 1.1.0-2
2010-04-20 07:42:06 status unpacked libgavl1 1.1.0-2
2010-04-20 07:42:06 status half-configured libgavl1 1.1.0-2
2010-04-20 07:42:06 status installed libgavl1 1.1.0-2
2010-04-20 07:42:06 configure libhighgui1 1.0.0-6.2ubuntu1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status unpacked libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status half-configured libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 status installed libhighgui1 1.0.0-6.2ubuntu1
2010-04-20 07:42:06 configure frei0r-plugins 1.1.22git20090409+repack-0ubuntu1 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:42:06 status unpacked frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:42:06 status half-configured frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:42:06 status installed frei0r-plugins 1.1.22git20090409+repack-0ubuntu1
2010-04-20 07:42:06 configure kde-icons-oxygen 4:4.3.2-0ubuntu1 4:4.3.2-0ubuntu1
2010-04-20 07:42:06 status unpacked kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:42:06 status half-configured kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:42:06 status installed kde-icons-oxygen 4:4.3.2-0ubuntu1
2010-04-20 07:42:06 configure libqt4-opengl 4.5.3really4.5.2-0ubuntu1 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:06 status unpacked libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:06 status half-configured libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:06 status installed libqt4-opengl 4.5.3really4.5.2-0ubuntu1
2010-04-20 07:42:06 configure libxine1-bin 1.1.16.3-0ubuntu4 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status unpacked libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status half-configured libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status installed libxine1-bin 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 configure libxine1-misc-plugins 1.1.16.3-0ubuntu4 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status unpacked libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status half-configured libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 configure libxcb-shape0 1.4-1 1.4-1
2010-04-20 07:42:06 status unpacked libxcb-shape0 1.4-1
2010-04-20 07:42:06 status half-configured libxcb-shape0 1.4-1
2010-04-20 07:42:06 status installed libxcb-shape0 1.4-1
2010-04-20 07:42:06 configure libxcb-shm0 1.4-1 1.4-1
2010-04-20 07:42:06 status unpacked libxcb-shm0 1.4-1
2010-04-20 07:42:06 status half-configured libxcb-shm0 1.4-1
2010-04-20 07:42:06 status installed libxcb-shm0 1.4-1
2010-04-20 07:42:06 configure libxcb-xv0 1.4-1 1.4-1
2010-04-20 07:42:06 status unpacked libxcb-xv0 1.4-1
2010-04-20 07:42:06 status half-configured libxcb-xv0 1.4-1
2010-04-20 07:42:06 status installed libxcb-xv0 1.4-1
2010-04-20 07:42:06 configure libxine1-x 1.1.16.3-0ubuntu4 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status unpacked libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status half-configured libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status installed libxine1-x 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 configure libxine1-console 1.1.16.3-0ubuntu4 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status unpacked libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status half-configured libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status installed libxine1-console 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 configure libxine1 1.1.16.3-0ubuntu4 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status unpacked libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status half-configured libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 status installed libxine1 1.1.16.3-0ubuntu4
2010-04-20 07:42:06 configure kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status unpacked kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status half-configured kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status installed kdebase-runtime-data-common 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 configure kdebase-runtime-data 4:4.3.2-0ubuntu4.1 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status unpacked kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status unpacked kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status half-configured kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 status installed kdebase-runtime-data 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:06 configure phonon-backend-xine 4:4.3.1-4ubuntu1 4:4.3.1-4ubuntu1
2010-04-20 07:42:06 status unpacked phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:42:06 status half-configured phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:42:06 status installed phonon-backend-xine 4:4.3.1-4ubuntu1
2010-04-20 07:42:06 configure libquicktime1 2:1.1.1+debian-1build1 2:1.1.1+debian-1build1
2010-04-20 07:42:06 status unpacked libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:42:06 status half-configured libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:42:06 status installed libquicktime1 2:1.1.1+debian-1build1
2010-04-20 07:42:06 configure libsox1a 14.3.0-1build1 14.3.0-1build1
2010-04-20 07:42:06 status unpacked libsox1a 14.3.0-1build1
2010-04-20 07:42:06 status half-configured libsox1a 14.3.0-1build1
2010-04-20 07:42:06 status installed libsox1a 14.3.0-1build1
2010-04-20 07:42:06 configure libmlt1 0.4.4-2build1 0.4.4-2build1
2010-04-20 07:42:06 status unpacked libmlt1 0.4.4-2build1
2010-04-20 07:42:06 status half-configured libmlt1 0.4.4-2build1
2010-04-20 07:42:06 status installed libmlt1 0.4.4-2build1
2010-04-20 07:42:06 configure libmlt++2 0.4.4-2build1 0.4.4-2build1
2010-04-20 07:42:06 status unpacked libmlt++2 0.4.4-2build1
2010-04-20 07:42:06 status half-configured libmlt++2 0.4.4-2build1
2010-04-20 07:42:06 status installed libmlt++2 0.4.4-2build1
2010-04-20 07:42:06 configure kdenlive-data 0.7.5-1ubuntu1 0.7.5-1ubuntu1
2010-04-20 07:42:06 status unpacked kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:42:06 status half-configured kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:42:06 status installed kdenlive-data 0.7.5-1ubuntu1
2010-04-20 07:42:06 configure libmlt-data 0.4.4-2build1 0.4.4-2build1
2010-04-20 07:42:06 status unpacked libmlt-data 0.4.4-2build1
2010-04-20 07:42:06 status half-configured libmlt-data 0.4.4-2build1
2010-04-20 07:42:06 status installed libmlt-data 0.4.4-2build1
2010-04-20 07:42:06 configure melt 0.4.4-2build1 0.4.4-2build1
2010-04-20 07:42:06 status unpacked melt 0.4.4-2build1
2010-04-20 07:42:06 status half-configured melt 0.4.4-2build1
2010-04-20 07:42:06 status installed melt 0.4.4-2build1
2010-04-20 07:42:06 configure libsox-fmt-alsa 14.3.0-1build1 14.3.0-1build1
2010-04-20 07:42:06 status unpacked libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:42:06 status half-configured libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:42:06 status installed libsox-fmt-alsa 14.3.0-1build1
2010-04-20 07:42:06 configure libsox-fmt-base 14.3.0-1build1 14.3.0-1build1
2010-04-20 07:42:06 status unpacked libsox-fmt-base 14.3.0-1build1
2010-04-20 07:42:06 status half-configured libsox-fmt-base 14.3.0-1build1
2010-04-20 07:42:06 status installed libsox-fmt-base 14.3.0-1build1
2010-04-20 07:42:06 configure recordmydesktop 0.3.8.1-0ubuntu2 0.3.8.1-0ubuntu2
2010-04-20 07:42:06 status unpacked recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:42:06 status half-configured recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:42:06 status installed recordmydesktop 0.3.8.1-0ubuntu2
2010-04-20 07:42:06 configure swh-plugins 0.4.15-2 0.4.15-2
2010-04-20 07:42:06 status unpacked swh-plugins 0.4.15-2
2010-04-20 07:42:06 status half-configured swh-plugins 0.4.15-2
2010-04-20 07:42:06 status installed swh-plugins 0.4.15-2
2010-04-20 07:42:06 configure ttf-dejavu-extra 2.29-2 2.29-2
2010-04-20 07:42:06 status unpacked ttf-dejavu-extra 2.29-2
2010-04-20 07:42:06 status unpacked ttf-dejavu-extra 2.29-2
2010-04-20 07:42:06 status half-configured ttf-dejavu-extra 2.29-2
2010-04-20 07:42:19 status installed ttf-dejavu-extra 2.29-2
2010-04-20 07:42:19 configure ttf-dejavu 2.29-2 2.29-2
2010-04-20 07:42:19 status unpacked ttf-dejavu 2.29-2
2010-04-20 07:42:19 status half-configured ttf-dejavu 2.29-2
2010-04-20 07:42:19 status installed ttf-dejavu 2.29-2
2010-04-20 07:42:19 configure dvgrab 3.4-1build1 3.4-1build1
2010-04-20 07:42:19 status unpacked dvgrab 3.4-1build1
2010-04-20 07:42:19 status half-configured dvgrab 3.4-1build1
2010-04-20 07:42:19 status installed dvgrab 3.4-1build1
2010-04-20 07:42:19 configure soprano-daemon 2.3.1+dfsg.1-1 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status unpacked soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status half-configured soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status installed soprano-daemon 2.3.1+dfsg.1-1
2010-04-20 07:42:19 configure libsoprano4 2.3.1+dfsg.1-1 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status unpacked libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status half-configured libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:42:19 status installed libsoprano4 2.3.1+dfsg.1-1
2010-04-20 07:42:19 configure kdelibs-bin 4:4.3.2-0ubuntu7.2 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status unpacked kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status half-configured kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status installed kdelibs-bin 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 configure kdelibs5 4:4.3.2-0ubuntu7.2 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status unpacked kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status half-configured kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status installed kdelibs5 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 configure libknotificationitem1 4:4.3.2-0ubuntu1 4:4.3.2-0ubuntu1
2010-04-20 07:42:19 status unpacked libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:42:19 status half-configured libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:42:19 status installed libknotificationitem1 4:4.3.2-0ubuntu1
2010-04-20 07:42:19 configure libplasma3 4:4.3.2-0ubuntu7.2 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status unpacked libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status half-configured libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 status installed libplasma3 4:4.3.2-0ubuntu7.2
2010-04-20 07:42:19 configure kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 status unpacked kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 status half-configured kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 configure kdebase-runtime 4:4.3.2-0ubuntu4.1 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 status unpacked kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:19 status half-configured kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 update-alternatives: run with --install /usr/lib/kde4/libexec/kdesu kdesu /usr/lib/kde4/libexec/kdesu-distrib/kdesu 50
2010-04-20 07:42:20 update-alternatives: link group kdesu updated to point to /usr/lib/kde4/libexec/kdesu-distrib/kdesu
2010-04-20 07:42:20 status installed kdebase-runtime 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 configure kdenlive 0.7.5-1ubuntu1 0.7.5-1ubuntu1
2010-04-20 07:42:20 status unpacked kdenlive 0.7.5-1ubuntu1
2010-04-20 07:42:20 status half-configured kdenlive 0.7.5-1ubuntu1
2010-04-20 07:42:20 status installed kdenlive 0.7.5-1ubuntu1
2010-04-20 07:42:20 configure khelpcenter4 4:4.3.2-0ubuntu4.1 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 status unpacked khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 status half-configured khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 status installed khelpcenter4 4:4.3.2-0ubuntu4.1
2010-04-20 07:42:20 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-20 07:42:20 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-20 07:42:20 status installed libc-bin 2.10.1-0ubuntu16
2010-04-20 07:49:29 startup archives install
2010-04-20 07:49:29 install debian-multimedia-keyring <none> 2008.10.16
2010-04-20 07:49:29 status half-installed debian-multimedia-keyring 2008.10.16
2010-04-20 07:49:29 status unpacked debian-multimedia-keyring 2008.10.16
2010-04-20 07:49:29 status unpacked debian-multimedia-keyring 2008.10.16
2010-04-20 07:49:29 configure debian-multimedia-keyring 2008.10.16 2008.10.16
2010-04-20 07:49:29 status unpacked debian-multimedia-keyring 2008.10.16
2010-04-20 07:49:29 status half-configured debian-multimedia-keyring 2008.10.16
2010-04-20 07:49:29 status installed debian-multimedia-keyring 2008.10.16
2010-04-21 13:44:31 startup archives unpack
2010-04-21 13:44:47 install gawk <none> 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 status half-installed gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 status triggers-pending install-info 4.13a.dfsg.1-4ubuntu1
2010-04-21 13:44:47 status half-installed gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 status triggers-pending man-db 2.5.6-2
2010-04-21 13:44:47 status half-installed gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 status unpacked gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 status unpacked gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:47 install curl <none> 7.19.5-1ubuntu2
2010-04-21 13:44:47 status half-installed curl 7.19.5-1ubuntu2
2010-04-21 13:44:47 status half-installed curl 7.19.5-1ubuntu2
2010-04-21 13:44:47 status unpacked curl 7.19.5-1ubuntu2
2010-04-21 13:44:47 status unpacked curl 7.19.5-1ubuntu2
2010-04-21 13:44:47 install ffmpeg2theora <none> 0.24-2build1
2010-04-21 13:44:47 status half-installed ffmpeg2theora 0.24-2build1
2010-04-21 13:44:47 status half-installed ffmpeg2theora 0.24-2build1
2010-04-21 13:44:47 status unpacked ffmpeg2theora 0.24-2build1
2010-04-21 13:44:47 status unpacked ffmpeg2theora 0.24-2build1
2010-04-21 13:44:47 install ftplib3 <none> 3.1-1-6
2010-04-21 13:44:47 status half-installed ftplib3 3.1-1-6
2010-04-21 13:44:47 status unpacked ftplib3 3.1-1-6
2010-04-21 13:44:47 status unpacked ftplib3 3.1-1-6
2010-04-21 13:44:47 install libimlib2 <none> 1.4.2-5
2010-04-21 13:44:47 status half-installed libimlib2 1.4.2-5
2010-04-21 13:44:47 status unpacked libimlib2 1.4.2-5
2010-04-21 13:44:47 status unpacked libimlib2 1.4.2-5
2010-04-21 13:44:47 install liblash2 <none> 0.5.4-0ubuntu3
2010-04-21 13:44:47 status half-installed liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:47 status unpacked liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:47 status unpacked liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:47 install libmjpegtools-1.9 <none> 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status half-installed libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 install mjpegtools <none> 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status half-installed mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status half-installed mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status half-installed mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status unpacked mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:47 status unpacked mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:48 install sox <none> 14.3.0-1build1
2010-04-21 13:44:48 status half-installed sox 14.3.0-1build1
2010-04-21 13:44:48 status half-installed sox 14.3.0-1build1
2010-04-21 13:44:48 status unpacked sox 14.3.0-1build1
2010-04-21 13:44:48 status unpacked sox 14.3.0-1build1
2010-04-21 13:44:48 install stopmotion <none> 0.6.2-1
2010-04-21 13:44:48 status half-installed stopmotion 0.6.2-1
2010-04-21 13:44:48 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:44:48 status half-installed stopmotion 0.6.2-1
2010-04-21 13:44:48 status half-installed stopmotion 0.6.2-1
2010-04-21 13:44:48 status unpacked stopmotion 0.6.2-1
2010-04-21 13:44:48 status unpacked stopmotion 0.6.2-1
2010-04-21 13:44:48 install twolame <none> 0.3.12-1
2010-04-21 13:44:48 status half-installed twolame 0.3.12-1
2010-04-21 13:44:48 status half-installed twolame 0.3.12-1
2010-04-21 13:44:48 status unpacked twolame 0.3.12-1
2010-04-21 13:44:48 status unpacked twolame 0.3.12-1
2010-04-21 13:44:48 install kino <none> 1.3.3-1ubuntu2
2010-04-21 13:44:48 status half-installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status half-installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status triggers-pending shared-mime-info 0.70-0ubuntu1
2010-04-21 13:44:48 status half-installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status half-installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status triggers-pending doc-base 0.9.3
2010-04-21 13:44:48 status half-installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status unpacked kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 status unpacked kino 1.3.3-1ubuntu2
2010-04-21 13:44:48 install xjadeo <none> 0.4.7-0ubuntu1
2010-04-21 13:44:48 status half-installed xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:48 status half-installed xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:48 status half-installed xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:49 status unpacked xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:49 status unpacked xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:49 install ubuntustudio-video <none> 0.64
2010-04-21 13:44:49 status half-installed ubuntustudio-video 0.64
2010-04-21 13:44:49 status unpacked ubuntustudio-video 0.64
2010-04-21 13:44:49 status unpacked ubuntustudio-video 0.64
2010-04-21 13:44:49 install vgrabbj <none> 0.9.6-3.1
2010-04-21 13:44:49 status half-installed vgrabbj 0.9.6-3.1
2010-04-21 13:44:49 status half-installed vgrabbj 0.9.6-3.1
2010-04-21 13:44:49 status unpacked vgrabbj 0.9.6-3.1
2010-04-21 13:44:49 status unpacked vgrabbj 0.9.6-3.1
2010-04-21 13:44:49 install transcode <none> 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status half-installed transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status half-installed transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status unpacked transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status unpacked transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 install transcode-doc <none> 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status half-installed transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status half-installed transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status unpacked transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 status unpacked transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:49 trigproc install-info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2010-04-21 13:44:49 status half-configured install-info 4.13a.dfsg.1-4ubuntu1
2010-04-21 13:44:50 status installed install-info 4.13a.dfsg.1-4ubuntu1
2010-04-21 13:44:50 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-21 13:44:50 status half-configured man-db 2.5.6-2
2010-04-21 13:44:51 status installed man-db 2.5.6-2
2010-04-21 13:44:51 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-21 13:44:51 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:44:51 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:44:51 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2010-04-21 13:44:51 status half-configured shared-mime-info 0.70-0ubuntu1
2010-04-21 13:44:52 status installed shared-mime-info 0.70-0ubuntu1
2010-04-21 13:44:52 trigproc doc-base 0.9.3 0.9.3
2010-04-21 13:44:52 status half-configured doc-base 0.9.3
2010-04-21 13:44:53 status installed doc-base 0.9.3
2010-04-21 13:44:53 startup packages configure
2010-04-21 13:44:53 configure gawk 1:3.1.6.dfsg-0ubuntu2 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:53 status unpacked gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:53 status half-configured gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:54 update-alternatives: run with --quiet --install /usr/bin/awk awk /usr/bin/gawk 10 --slave /usr/share/man/man1/awk.1.gz awk.1.gz /usr/share/man/man1/gawk.1.gz --slave /usr/bin/nawk nawk /usr/bin/gawk --slave /usr/share/man/man1/nawk.1.gz nawk.1.gz /usr/share/man/man1/gawk.1.gz
2010-04-21 13:44:54 update-alternatives: link group awk updated to point to /usr/bin/gawk
2010-04-21 13:44:54 status installed gawk 1:3.1.6.dfsg-0ubuntu2
2010-04-21 13:44:54 configure curl 7.19.5-1ubuntu2 7.19.5-1ubuntu2
2010-04-21 13:44:54 status unpacked curl 7.19.5-1ubuntu2
2010-04-21 13:44:54 status half-configured curl 7.19.5-1ubuntu2
2010-04-21 13:44:54 status installed curl 7.19.5-1ubuntu2
2010-04-21 13:44:54 configure ffmpeg2theora 0.24-2build1 0.24-2build1
2010-04-21 13:44:54 status unpacked ffmpeg2theora 0.24-2build1
2010-04-21 13:44:54 status half-configured ffmpeg2theora 0.24-2build1
2010-04-21 13:44:54 status installed ffmpeg2theora 0.24-2build1
2010-04-21 13:44:54 configure ftplib3 3.1-1-6 3.1-1-6
2010-04-21 13:44:54 status unpacked ftplib3 3.1-1-6
2010-04-21 13:44:54 status half-configured ftplib3 3.1-1-6
2010-04-21 13:44:54 status installed ftplib3 3.1-1-6
2010-04-21 13:44:54 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-21 13:44:54 configure libimlib2 1.4.2-5 1.4.2-5
2010-04-21 13:44:54 status unpacked libimlib2 1.4.2-5
2010-04-21 13:44:54 status half-configured libimlib2 1.4.2-5
2010-04-21 13:44:54 status installed libimlib2 1.4.2-5
2010-04-21 13:44:54 configure liblash2 0.5.4-0ubuntu3 0.5.4-0ubuntu3
2010-04-21 13:44:54 status unpacked liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:54 status half-configured liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:54 status installed liblash2 0.5.4-0ubuntu3
2010-04-21 13:44:54 configure libmjpegtools-1.9 1:1.9.0-0.5ubuntu1 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status half-configured libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status installed libmjpegtools-1.9 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 configure mjpegtools 1:1.9.0-0.5ubuntu1 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status unpacked mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status half-configured mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 status installed mjpegtools 1:1.9.0-0.5ubuntu1
2010-04-21 13:44:54 configure sox 14.3.0-1build1 14.3.0-1build1
2010-04-21 13:44:54 status unpacked sox 14.3.0-1build1
2010-04-21 13:44:54 status half-configured sox 14.3.0-1build1
2010-04-21 13:44:55 status installed sox 14.3.0-1build1
2010-04-21 13:44:55 configure stopmotion 0.6.2-1 0.6.2-1
2010-04-21 13:44:55 status unpacked stopmotion 0.6.2-1
2010-04-21 13:44:55 status half-configured stopmotion 0.6.2-1
2010-04-21 13:44:55 status installed stopmotion 0.6.2-1
2010-04-21 13:44:55 configure twolame 0.3.12-1 0.3.12-1
2010-04-21 13:44:55 status unpacked twolame 0.3.12-1
2010-04-21 13:44:55 status half-configured twolame 0.3.12-1
2010-04-21 13:44:55 status installed twolame 0.3.12-1
2010-04-21 13:44:55 configure kino 1.3.3-1ubuntu2 1.3.3-1ubuntu2
2010-04-21 13:44:55 status unpacked kino 1.3.3-1ubuntu2
2010-04-21 13:44:55 status half-configured kino 1.3.3-1ubuntu2
2010-04-21 13:44:55 status installed kino 1.3.3-1ubuntu2
2010-04-21 13:44:55 configure xjadeo 0.4.7-0ubuntu1 0.4.7-0ubuntu1
2010-04-21 13:44:55 status unpacked xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:55 status half-configured xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:55 status installed xjadeo 0.4.7-0ubuntu1
2010-04-21 13:44:55 configure ubuntustudio-video 0.64 0.64
2010-04-21 13:44:55 status unpacked ubuntustudio-video 0.64
2010-04-21 13:44:55 status half-configured ubuntustudio-video 0.64
2010-04-21 13:44:55 status installed ubuntustudio-video 0.64
2010-04-21 13:44:55 configure vgrabbj 0.9.6-3.1 0.9.6-3.1
2010-04-21 13:44:55 status unpacked vgrabbj 0.9.6-3.1
2010-04-21 13:44:55 status unpacked vgrabbj 0.9.6-3.1
2010-04-21 13:44:55 status half-configured vgrabbj 0.9.6-3.1
2010-04-21 13:44:55 status installed vgrabbj 0.9.6-3.1
2010-04-21 13:44:55 configure transcode 3:1.1.4-0.0ubuntu4 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status unpacked transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status half-configured transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status installed transcode 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 configure transcode-doc 3:1.1.4-0.0ubuntu4 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status unpacked transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status half-configured transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 status installed transcode-doc 3:1.1.4-0.0ubuntu4
2010-04-21 13:44:55 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-21 13:44:55 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-21 13:44:55 status installed libc-bin 2.10.1-0ubuntu16
2010-04-21 13:56:53 startup archives install
2010-04-21 13:56:54 install nautilus-dropbox <none> 0.6.2
2010-04-21 13:56:54 status half-installed nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:56:54 status half-installed nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-21 13:56:54 status half-installed nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status triggers-pending man-db 2.5.6-2
2010-04-21 13:56:54 status half-installed nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status unpacked nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status unpacked nautilus-dropbox 0.6.2
2010-04-21 13:56:54 configure nautilus-dropbox 0.6.2 0.6.2
2010-04-21 13:56:54 status unpacked nautilus-dropbox 0.6.2
2010-04-21 13:56:54 status half-configured nautilus-dropbox 0.6.2
2010-04-21 13:56:57 status triggers-awaited nautilus-dropbox 0.6.2
2010-04-21 13:56:57 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-21 13:56:57 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-21 13:56:57 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:56:57 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-21 13:56:57 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-21 13:56:57 status half-configured hicolor-icon-theme 0.10-2
2010-04-21 13:56:57 status installed hicolor-icon-theme 0.10-2
2010-04-21 13:56:57 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-21 13:56:57 status half-configured man-db 2.5.6-2
2010-04-21 13:56:57 status installed nautilus-dropbox 0.6.2
2010-04-21 13:56:57 status installed man-db 2.5.6-2
2010-04-21 13:56:57 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-21 13:56:57 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-21 13:56:57 status installed libc-bin 2.10.1-0ubuntu16
2010-04-21 14:10:38 startup packages remove
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 remove libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status half-configured libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status half-installed libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-21 14:10:38 status config-files libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 status config-files libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3
2010-04-21 14:10:38 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-21 14:10:38 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-21 14:10:38 status installed libc-bin 2.10.1-0ubuntu16
2010-04-21 14:10:39 startup archives unpack
2010-04-21 14:10:39 install cabextract <none> 1.2-3
2010-04-21 14:10:39 status half-installed cabextract 1.2-3
2010-04-21 14:10:39 status triggers-pending man-db 2.5.6-2
2010-04-21 14:10:39 status half-installed cabextract 1.2-3
2010-04-21 14:10:39 status unpacked cabextract 1.2-3
2010-04-21 14:10:39 status unpacked cabextract 1.2-3
2010-04-21 14:10:39 install gstreamer0.10-pitfdll <none> 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:39 status half-installed gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:39 status unpacked gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:39 status unpacked gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:39 install gstreamer0.10-plugins-bad-multiverse <none> 0.10.13-0ubuntu1
2010-04-21 14:10:39 status half-installed gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:39 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:40 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:40 install gstreamer0.10-plugins-ugly-multiverse <none> 0.10.12-0ubuntu1
2010-04-21 14:10:40 status half-installed gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:40 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:40 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:40 install libavcodec52 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:40 status half-installed libavcodec52 4:0.5+svn20090706-2ubuntu2
2010-04-21 14:10:40 status unpacked libavcodec52 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:40 status unpacked libavcodec52 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:40 install libmp4v2-0 <none> 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:40 status half-installed libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:40 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:40 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:40 install ttf-mscorefonts-installer <none> 3.0
2010-04-21 14:10:40 status half-installed ttf-mscorefonts-installer 3.0
2010-04-21 14:10:40 status unpacked ttf-mscorefonts-installer 3.0
2010-04-21 14:10:40 status unpacked ttf-mscorefonts-installer 3.0
2010-04-21 14:10:40 install ubuntu-restricted-extras <none> 36
2010-04-21 14:10:40 status half-installed ubuntu-restricted-extras 36
2010-04-21 14:10:40 status unpacked ubuntu-restricted-extras 36
2010-04-21 14:10:40 status unpacked ubuntu-restricted-extras 36
2010-04-21 14:10:40 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-21 14:10:40 status half-configured man-db 2.5.6-2
2010-04-21 14:10:40 status installed man-db 2.5.6-2
2010-04-21 14:10:41 startup packages configure
2010-04-21 14:10:41 configure cabextract 1.2-3 1.2-3
2010-04-21 14:10:41 status unpacked cabextract 1.2-3
2010-04-21 14:10:41 status half-configured cabextract 1.2-3
2010-04-21 14:10:41 status installed cabextract 1.2-3
2010-04-21 14:10:41 configure gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:41 status unpacked gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:41 status half-configured gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:41 status installed gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2010-04-21 14:10:41 configure gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1 0.10.13-0ubuntu1
2010-04-21 14:10:41 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:41 status half-configured gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:41 status installed gstreamer0.10-plugins-bad-multiverse 0.10.13-0ubuntu1
2010-04-21 14:10:41 configure gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1 0.10.12-0ubuntu1
2010-04-21 14:10:41 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:41 status half-configured gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:41 status installed gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
2010-04-21 14:10:41 configure libavcodec52 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:41 status unpacked libavcodec52 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:41 status half-configured libavcodec52 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:41 status installed libavcodec52 4:0.5+svn20090706-2ubuntu2.1
2010-04-21 14:10:41 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-21 14:10:41 configure libmp4v2-0 1:1.6dfsg-0.2ubuntu5 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:41 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:41 status half-configured libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:41 status installed libmp4v2-0 1:1.6dfsg-0.2ubuntu5
2010-04-21 14:10:41 configure ttf-mscorefonts-installer 3.0 3.0
2010-04-21 14:10:41 status unpacked ttf-mscorefonts-installer 3.0
2010-04-21 14:10:41 status unpacked ttf-mscorefonts-installer 3.0
2010-04-21 14:10:41 status half-configured ttf-mscorefonts-installer 3.0
2010-04-21 14:11:18 status installed ttf-mscorefonts-installer 3.0
2010-04-21 14:11:18 configure ubuntu-restricted-extras 36 36
2010-04-21 14:11:18 status unpacked ubuntu-restricted-extras 36
2010-04-21 14:11:18 status half-configured ubuntu-restricted-extras 36
2010-04-21 14:11:18 status installed ubuntu-restricted-extras 36
2010-04-21 14:11:18 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-21 14:11:18 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-21 14:11:18 status installed libc-bin 2.10.1-0ubuntu16
2010-04-21 14:22:21 startup archives unpack
2010-04-21 14:22:21 install java-common <none> 0.30ubuntu5
2010-04-21 14:22:21 status half-installed java-common 0.30ubuntu5
2010-04-21 14:22:21 status triggers-pending doc-base 0.9.3
2010-04-21 14:22:21 status half-installed java-common 0.30ubuntu5
2010-04-21 14:22:21 status triggers-pending man-db 2.5.6-2
2010-04-21 14:22:21 status half-installed java-common 0.30ubuntu5
2010-04-21 14:22:21 status unpacked java-common 0.30ubuntu5
2010-04-21 14:22:21 status unpacked java-common 0.30ubuntu5
2010-04-21 14:22:21 install sun-java6-jre <none> 6-15-1
2010-04-21 14:22:21 status half-installed sun-java6-jre 6-15-1
2010-04-21 14:22:30 status triggers-pending shared-mime-info 0.70-0ubuntu1
2010-04-21 14:22:30 status half-installed sun-java6-jre 6-15-1
2010-04-21 14:22:30 status unpacked sun-java6-jre 6-15-1
2010-04-21 14:22:30 status unpacked sun-java6-jre 6-15-1
2010-04-21 14:22:30 install sun-java6-bin <none> 6-15-1
2010-04-21 14:22:30 status half-installed sun-java6-bin 6-15-1
2010-04-21 14:22:30 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-21 14:22:30 status half-installed sun-java6-bin 6-15-1
2010-04-21 14:22:33 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:33 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:33 install gsfonts-x11 <none> 0.21
2010-04-21 14:22:33 status half-installed gsfonts-x11 0.21
2010-04-21 14:22:33 status unpacked gsfonts-x11 0.21
2010-04-21 14:22:33 status unpacked gsfonts-x11 0.21
2010-04-21 14:22:33 install sun-java6-plugin <none> 6-15-1
2010-04-21 14:22:33 status half-installed sun-java6-plugin 6-15-1
2010-04-21 14:22:33 status unpacked sun-java6-plugin 6-15-1
2010-04-21 14:22:33 status unpacked sun-java6-plugin 6-15-1
2010-04-21 14:22:33 trigproc doc-base 0.9.3 0.9.3
2010-04-21 14:22:33 status half-configured doc-base 0.9.3
2010-04-21 14:22:34 status installed doc-base 0.9.3
2010-04-21 14:22:34 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-21 14:22:34 status half-configured man-db 2.5.6-2
2010-04-21 14:22:34 status installed man-db 2.5.6-2
2010-04-21 14:22:34 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2010-04-21 14:22:34 status half-configured shared-mime-info 0.70-0ubuntu1
2010-04-21 14:22:35 status installed shared-mime-info 0.70-0ubuntu1
2010-04-21 14:22:35 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-21 14:22:35 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-21 14:22:35 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-21 14:22:35 startup packages configure
2010-04-21 14:22:35 configure java-common 0.30ubuntu5 0.30ubuntu5
2010-04-21 14:22:35 status unpacked java-common 0.30ubuntu5
2010-04-21 14:22:35 status half-configured java-common 0.30ubuntu5
2010-04-21 14:22:35 status installed java-common 0.30ubuntu5
2010-04-21 14:22:35 configure gsfonts-x11 0.21 0.21
2010-04-21 14:22:35 status unpacked gsfonts-x11 0.21
2010-04-21 14:22:35 status unpacked gsfonts-x11 0.21
2010-04-21 14:22:35 status unpacked gsfonts-x11 0.21
2010-04-21 14:22:35 status half-configured gsfonts-x11 0.21
2010-04-21 14:22:36 status installed gsfonts-x11 0.21
2010-04-21 14:22:36 configure sun-java6-jre 6-15-1 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-jre 6-15-1
2010-04-21 14:22:36 status half-configured sun-java6-jre 6-15-1
2010-04-21 14:22:36 status installed sun-java6-jre 6-15-1
2010-04-21 14:22:36 configure sun-java6-bin 6-15-1 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status unpacked sun-java6-bin 6-15-1
2010-04-21 14:22:36 status half-configured sun-java6-bin 6-15-1
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/ControlPanel ControlPanel /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel 63
2010-04-21 14:22:37 update-alternatives: link group ControlPanel updated to point to /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/java java /usr/lib/jvm/java-6-sun/jre/bin/java 63 --slave /usr/share/man/man1/java.1.gz java.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
2010-04-21 14:22:37 update-alternatives: link group java updated to point to /usr/lib/jvm/java-6-sun/jre/bin/java
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/java_vm java_vm /usr/lib/jvm/java-6-sun/jre/bin/java_vm 63
2010-04-21 14:22:37 update-alternatives: link group java_vm updated to point to /usr/lib/jvm/java-6-sun/jre/bin/java_vm
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/javaws javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws 63 --slave /usr/share/man/man1/javaws.1.gz javaws.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/javaws.1.gz
2010-04-21 14:22:37 update-alternatives: link group javaws updated to point to /usr/lib/jvm/java-6-sun/jre/bin/javaws
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/jcontrol jcontrol /usr/lib/jvm/java-6-sun/jre/bin/jcontrol 63
2010-04-21 14:22:37 update-alternatives: link group jcontrol updated to point to /usr/lib/jvm/java-6-sun/jre/bin/jcontrol
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/keytool keytool /usr/lib/jvm/java-6-sun/jre/bin/keytool 63 --slave /usr/share/man/man1/keytool.1.gz keytool.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/keytool.1.gz
2010-04-21 14:22:37 update-alternatives: link group keytool updated to point to /usr/lib/jvm/java-6-sun/jre/bin/keytool
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/pack200 pack200 /usr/lib/jvm/java-6-sun/jre/bin/pack200 63 --slave /usr/share/man/man1/pack200.1.gz pack200.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/pack200.1.gz
2010-04-21 14:22:37 update-alternatives: link group pack200 updated to point to /usr/lib/jvm/java-6-sun/jre/bin/pack200
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/policytool policytool /usr/lib/jvm/java-6-sun/jre/bin/policytool 63 --slave /usr/share/man/man1/policytool.1.gz policytool.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/policytool.1.gz
2010-04-21 14:22:37 update-alternatives: link group policytool updated to point to /usr/lib/jvm/java-6-sun/jre/bin/policytool
2010-04-21 14:22:37 update-alternatives: run with --install /usr/bin/rmid rmid /usr/lib/jvm/java-6-sun/jre/bin/rmid 63 --slave /usr/share/man/man1/rmid.1.gz rmid.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/rmid.1.gz
2010-04-21 14:22:37 update-alternatives: link group rmid updated to point to /usr/lib/jvm/java-6-sun/jre/bin/rmid
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/rmiregistry rmiregistry /usr/lib/jvm/java-6-sun/jre/bin/rmiregistry 63 --slave /usr/share/man/man1/rmiregistry.1.gz rmiregistry.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/rmiregistry.1.gz
2010-04-21 14:22:38 update-alternatives: link group rmiregistry updated to point to /usr/lib/jvm/java-6-sun/jre/bin/rmiregistry
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/unpack200 unpack200 /usr/lib/jvm/java-6-sun/jre/bin/unpack200 63 --slave /usr/share/man/man1/unpack200.1.gz unpack200.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/unpack200.1.gz
2010-04-21 14:22:38 update-alternatives: link group unpack200 updated to point to /usr/lib/jvm/java-6-sun/jre/bin/unpack200
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/orbd orbd /usr/lib/jvm/java-6-sun/jre/bin/orbd 63 --slave /usr/share/man/man1/orbd.1.gz orbd.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/orbd.1.gz
2010-04-21 14:22:38 update-alternatives: link group orbd updated to point to /usr/lib/jvm/java-6-sun/jre/bin/orbd
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/servertool servertool /usr/lib/jvm/java-6-sun/jre/bin/servertool 63 --slave /usr/share/man/man1/servertool.1.gz servertool.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/servertool.1.gz
2010-04-21 14:22:38 update-alternatives: link group servertool updated to point to /usr/lib/jvm/java-6-sun/jre/bin/servertool
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/tnameserv tnameserv /usr/lib/jvm/java-6-sun/jre/bin/tnameserv 63 --slave /usr/share/man/man1/tnameserv.1.gz tnameserv.1.gz /usr/lib/jvm/java-6-sun/jre/man/man1/tnameserv.1.gz
2010-04-21 14:22:38 update-alternatives: link group tnameserv updated to point to /usr/lib/jvm/java-6-sun/jre/bin/tnameserv
2010-04-21 14:22:38 update-alternatives: run with --install /usr/bin/jexec jexec /usr/lib/jvm/java-6-sun/jre/lib/jexec 63 --slave /usr/share/binfmts/jar jexec-binfmt /usr/lib/jvm/java-6-sun/jre/lib/jar.binfmt
2010-04-21 14:22:38 update-alternatives: link group jexec updated to point to /usr/lib/jvm/java-6-sun/jre/lib/jexec
2010-04-21 14:22:39 status installed sun-java6-bin 6-15-1
2010-04-21 14:22:39 configure sun-java6-plugin 6-15-1 6-15-1
2010-04-21 14:22:39 status unpacked sun-java6-plugin 6-15-1
2010-04-21 14:22:39 status half-configured sun-java6-plugin 6-15-1
2010-04-21 14:22:39 update-alternatives: run with --quiet --install /usr/lib/xulrunner-addons/plugins/libjavaplugin.so xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 63
2010-04-21 14:22:39 update-alternatives: link group xulrunner-1.9-javaplugin.so updated to point to /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
2010-04-21 14:22:39 status installed sun-java6-plugin 6-15-1
2010-04-22 08:00:53 startup archives unpack
2010-04-22 08:01:29 upgrade tzdata 2010e-0ubuntu0.9.10 2010h-0ubuntu0.9.10
2010-04-22 08:01:29 status half-configured tzdata 2010e-0ubuntu0.9.10
2010-04-22 08:01:29 status unpacked tzdata 2010e-0ubuntu0.9.10
2010-04-22 08:01:29 status half-installed tzdata 2010e-0ubuntu0.9.10
2010-04-22 08:01:33 status half-installed tzdata 2010e-0ubuntu0.9.10
2010-04-22 08:01:33 status unpacked tzdata 2010h-0ubuntu0.9.10
2010-04-22 08:01:33 status unpacked tzdata 2010h-0ubuntu0.9.10
2010-04-22 08:01:34 startup packages configure
2010-04-22 08:01:34 configure tzdata 2010h-0ubuntu0.9.10 2010h-0ubuntu0.9.10
2010-04-22 08:01:34 status unpacked tzdata 2010h-0ubuntu0.9.10
2010-04-22 08:01:34 status half-configured tzdata 2010h-0ubuntu0.9.10
2010-04-22 08:01:35 status installed tzdata 2010h-0ubuntu0.9.10
2010-04-22 08:01:36 startup archives unpack
2010-04-22 08:01:36 upgrade ifupdown 0.6.8ubuntu21 0.6.8ubuntu21.2
2010-04-22 08:01:36 status half-configured ifupdown 0.6.8ubuntu21
2010-04-22 08:01:36 status unpacked ifupdown 0.6.8ubuntu21
2010-04-22 08:01:36 status half-installed ifupdown 0.6.8ubuntu21
2010-04-22 08:01:37 status triggers-pending man-db 2.5.6-2
2010-04-22 08:01:37 status half-installed ifupdown 0.6.8ubuntu21
2010-04-22 08:01:37 status triggers-pending ureadahead 0.90.3-2
2010-04-22 08:01:37 status half-installed ifupdown 0.6.8ubuntu21
2010-04-22 08:01:37 status triggers-pending ureadahead 0.90.3-2
2010-04-22 08:01:37 status half-installed ifupdown 0.6.8ubuntu21
2010-04-22 08:01:37 status unpacked ifupdown 0.6.8ubuntu21.2
2010-04-22 08:01:37 status unpacked ifupdown 0.6.8ubuntu21.2
2010-04-22 08:01:37 install apport-hooks-medibuntu <none> 1medibuntu1
2010-04-22 08:01:37 status half-installed apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:01:37 status unpacked apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:01:37 status unpacked apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:01:37 upgrade devicekit-disks 007-2ubuntu5 007-2ubuntu6
2010-04-22 08:01:37 status half-configured devicekit-disks 007-2ubuntu5
2010-04-22 08:01:37 status unpacked devicekit-disks 007-2ubuntu5
2010-04-22 08:01:37 status half-installed devicekit-disks 007-2ubuntu5
2010-04-22 08:01:37 status half-installed devicekit-disks 007-2ubuntu5
2010-04-22 08:01:38 status half-installed devicekit-disks 007-2ubuntu5
2010-04-22 08:01:39 status unpacked devicekit-disks 007-2ubuntu6
2010-04-22 08:01:39 status unpacked devicekit-disks 007-2ubuntu6
2010-04-22 08:01:39 upgrade erlang-xmerl 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:39 status half-configured erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:39 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:39 status half-installed erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 upgrade erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status half-configured erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 upgrade erlang-inets 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status half-configured erlang-inets 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-inets 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-inets 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 upgrade erlang-mnesia 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status half-configured erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status half-installed erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:40 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 upgrade erlang-ssl 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:40 status half-configured erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 upgrade erlang-public-key 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status half-configured erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 upgrade erlang-crypto 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status half-configured erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 upgrade erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status half-configured erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status half-installed erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:41 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 upgrade erlang-base 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:41 status half-configured erlang-base 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:42 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:42 status half-installed erlang-base 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:42 status half-installed erlang-base 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:43 status half-installed erlang-base 1:13.b.1-dfsg-2ubuntu1
2010-04-22 08:01:43 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:43 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:01:43 upgrade libavutil-extra-49 4:0.5+svn20090706-2ubuntu3 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:01:43 status half-configured libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-22 08:01:43 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-22 08:01:43 status half-installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-22 08:01:43 status half-installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3
2010-04-22 08:01:43 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:01:43 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:01:43 upgrade libavformat52 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:43 status half-configured libavformat52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status unpacked libavformat52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status half-installed libavformat52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status half-installed libavformat52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status unpacked libavformat52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:43 status unpacked libavformat52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:43 upgrade libavdevice52 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:43 status half-configured libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:43 status half-installed libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libavdevice52 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 upgrade libavfilter0 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status half-configured libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libavfilter0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 upgrade libpostproc51 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status half-configured libpostproc51 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libpostproc51 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libpostproc51 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libpostproc51 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libpostproc51 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status unpacked libpostproc51 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 upgrade libswscale0 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status half-configured libswscale0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libswscale0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libswscale0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed libswscale0 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked libswscale0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status unpacked libswscale0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 upgrade ffmpeg 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:44 status half-configured ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:44 status half-installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:45 status half-installed ffmpeg 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:01:45 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:45 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:01:45 upgrade firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status half-configured firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status unpacked firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status half-installed firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:01:45 status half-installed firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status half-installed firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:45 status unpacked firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:46 status unpacked firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:46 upgrade libnss3-1d 3.12.3.1-0ubuntu2 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:01:46 status half-configured libnss3-1d 3.12.3.1-0ubuntu2
2010-04-22 08:01:46 status unpacked libnss3-1d 3.12.3.1-0ubuntu2
2010-04-22 08:01:46 status half-installed libnss3-1d 3.12.3.1-0ubuntu2
2010-04-22 08:01:46 status half-installed libnss3-1d 3.12.3.1-0ubuntu2
2010-04-22 08:01:46 status unpacked libnss3-1d 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:01:46 status unpacked libnss3-1d 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:01:47 upgrade xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:47 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:47 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:47 status half-installed xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:48 status half-installed xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:48 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:48 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:48 upgrade xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:48 status half-configured xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:51 update-alternatives: run with --remove xulrunner /usr/bin/xulrunner-1.9.1
2010-04-22 08:01:51 update-alternatives: link group xulrunner fully removed
2010-04-22 08:01:51 status unpacked xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:51 status half-installed xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status half-installed xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status unpacked xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status unpacked xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 upgrade firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status half-configured firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status unpacked firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status half-installed firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status half-installed firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status unpacked firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:52 status unpacked firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 upgrade firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-configured firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-installed firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-installed firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 upgrade firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-configured firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-installed firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status half-installed firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:53 status unpacked firefox 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 upgrade firefox-3.0 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-configured firefox-3.0 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 upgrade firefox-3.0-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-configured firefox-3.0-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 upgrade firefox-3.0-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-configured firefox-3.0-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status half-installed firefox-3.0-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:54 status unpacked firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 upgrade firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status half-configured firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status unpacked firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status half-installed firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status half-installed firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status unpacked firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 status unpacked firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:01:55 upgrade libfaac0 1.26-0.1ubuntu2 1.26-0.2
2010-04-22 08:01:55 status half-configured libfaac0 1.26-0.1ubuntu2
2010-04-22 08:01:55 status unpacked libfaac0 1.26-0.1ubuntu2
2010-04-22 08:01:55 status half-installed libfaac0 1.26-0.1ubuntu2
2010-04-22 08:01:55 status half-installed libfaac0 1.26-0.1ubuntu2
2010-04-22 08:01:55 status unpacked libfaac0 1.26-0.2
2010-04-22 08:01:55 status unpacked libfaac0 1.26-0.2
2010-04-22 08:01:55 upgrade libmlt-data 0.4.4-2build1 1:0.3.0-0.1
2010-04-22 08:01:55 status half-configured libmlt-data 0.4.4-2build1
2010-04-22 08:01:55 status unpacked libmlt-data 0.4.4-2build1
2010-04-22 08:01:55 status half-installed libmlt-data 0.4.4-2build1
2010-04-22 08:01:55 status half-installed libmlt-data 0.4.4-2build1
2010-04-22 08:01:55 status unpacked libmlt-data 1:0.3.0-0.1
2010-04-22 08:01:56 status unpacked libmlt-data 1:0.3.0-0.1
2010-04-22 08:01:56 upgrade libpq5 8.4.2-0ubuntu9.10 8.4.3-0ubuntu9.10
2010-04-22 08:01:56 status half-configured libpq5 8.4.2-0ubuntu9.10
2010-04-22 08:01:56 status unpacked libpq5 8.4.2-0ubuntu9.10
2010-04-22 08:01:56 status half-installed libpq5 8.4.2-0ubuntu9.10
2010-04-22 08:01:56 status half-installed libpq5 8.4.2-0ubuntu9.10
2010-04-22 08:01:56 status unpacked libpq5 8.4.3-0ubuntu9.10
2010-04-22 08:01:56 status unpacked libpq5 8.4.3-0ubuntu9.10
2010-04-22 08:01:56 upgrade libxvidcore4 2:1.1.2-0.1ubuntu4 2:1.1.3-0.6
2010-04-22 08:01:56 status half-configured libxvidcore4 2:1.1.2-0.1ubuntu4
2010-04-22 08:01:56 status unpacked libxvidcore4 2:1.1.2-0.1ubuntu4
2010-04-22 08:01:56 status half-installed libxvidcore4 2:1.1.2-0.1ubuntu4
2010-04-22 08:01:56 status half-installed libxvidcore4 2:1.1.2-0.1ubuntu4
2010-04-22 08:01:56 status unpacked libxvidcore4 2:1.1.3-0.6
2010-04-22 08:01:56 status unpacked libxvidcore4 2:1.1.3-0.6
2010-04-22 08:01:56 upgrade obexd-client 0.14-0ubuntu1 0.14-0ubuntu1.1
2010-04-22 08:01:56 status half-configured obexd-client 0.14-0ubuntu1
2010-04-22 08:01:56 status unpacked obexd-client 0.14-0ubuntu1
2010-04-22 08:01:56 status half-installed obexd-client 0.14-0ubuntu1
2010-04-22 08:01:57 status half-installed obexd-client 0.14-0ubuntu1
2010-04-22 08:01:57 status unpacked obexd-client 0.14-0ubuntu1.1
2010-04-22 08:01:57 status unpacked obexd-client 0.14-0ubuntu1.1
2010-04-22 08:01:57 upgrade sudo 1.7.0-1ubuntu2.1 1.7.0-1ubuntu2.2
2010-04-22 08:01:57 status half-configured sudo 1.7.0-1ubuntu2.1
2010-04-22 08:01:57 status unpacked sudo 1.7.0-1ubuntu2.1
2010-04-22 08:01:57 status half-installed sudo 1.7.0-1ubuntu2.1
2010-04-22 08:01:57 status half-installed sudo 1.7.0-1ubuntu2.1
2010-04-22 08:01:58 status half-installed sudo 1.7.0-1ubuntu2.1
2010-04-22 08:01:58 status unpacked sudo 1.7.0-1ubuntu2.2
2010-04-22 08:01:58 status unpacked sudo 1.7.0-1ubuntu2.2
2010-04-22 08:01:58 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 08:01:58 status half-configured man-db 2.5.6-2
2010-04-22 08:01:59 status installed man-db 2.5.6-2
2010-04-22 08:01:59 trigproc ureadahead 0.90.3-2 0.90.3-2
2010-04-22 08:01:59 status half-configured ureadahead 0.90.3-2
2010-04-22 08:01:59 status installed ureadahead 0.90.3-2
2010-04-22 08:01:59 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 08:01:59 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:02:02 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:02:03 startup packages configure
2010-04-22 08:02:03 configure ifupdown 0.6.8ubuntu21.2 0.6.8ubuntu21.2
2010-04-22 08:02:03 status unpacked ifupdown 0.6.8ubuntu21.2
2010-04-22 08:02:03 status half-configured ifupdown 0.6.8ubuntu21.2
2010-04-22 08:02:03 status installed ifupdown 0.6.8ubuntu21.2
2010-04-22 08:02:03 configure apport-hooks-medibuntu 1medibuntu1 1medibuntu1
2010-04-22 08:02:03 status unpacked apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:02:03 status unpacked apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:02:03 status half-configured apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:02:03 status installed apport-hooks-medibuntu 1medibuntu1
2010-04-22 08:02:03 configure devicekit-disks 007-2ubuntu6 007-2ubuntu6
2010-04-22 08:02:03 status unpacked devicekit-disks 007-2ubuntu6
2010-04-22 08:02:03 status unpacked devicekit-disks 007-2ubuntu6
2010-04-22 08:02:03 status half-configured devicekit-disks 007-2ubuntu6
2010-04-22 08:02:03 status installed devicekit-disks 007-2ubuntu6
2010-04-22 08:02:03 configure erlang-base 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:03 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:03 status half-configured erlang-base 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-base 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-xmerl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-mnesia 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-crypto 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-public-key 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-ssl 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure erlang-inets 1:13.b.1-dfsg-2ubuntu1.1 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status half-configured erlang-inets 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 status installed erlang-inets 1:13.b.1-dfsg-2ubuntu1.1
2010-04-22 08:02:04 configure libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:02:04 status unpacked libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:02:04 status half-configured libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:02:04 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:02:04 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 08:02:04 configure libavformat52 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked libavformat52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured libavformat52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed libavformat52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure libavdevice52 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked libavdevice52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured libavdevice52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed libavdevice52 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure libavfilter0 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked libavfilter0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured libavfilter0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed libavfilter0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure libpostproc51 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked libpostproc51 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured libpostproc51 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed libpostproc51 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure libswscale0 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked libswscale0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured libswscale0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed libswscale0 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure ffmpeg 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status unpacked ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status half-configured ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 status installed ffmpeg 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:02:04 configure libnss3-1d 3.12.6-0ubuntu0.9.10.2 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:02:04 status unpacked libnss3-1d 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:02:04 status half-configured libnss3-1d 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:02:04 status installed libnss3-1d 3.12.6-0ubuntu0.9.10.2
2010-04-22 08:02:04 configure xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:04 status unpacked xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:04 status unpacked xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:04 status unpacked xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:04 status half-configured xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 update-alternatives: run with --install /usr/bin/xulrunner xulrunner /usr/bin/xulrunner-1.9.1 50
2010-04-22 08:02:05 update-alternatives: link group xulrunner updated to point to /usr/bin/xulrunner-1.9.1
2010-04-22 08:02:05 status installed xulrunner-1.9.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 configure xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 status installed xulrunner-1.9.1-gnome-support 1.9.1.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:05 configure libfaac0 1.26-0.2 1.26-0.2
2010-04-22 08:02:05 status unpacked libfaac0 1.26-0.2
2010-04-22 08:02:05 status half-configured libfaac0 1.26-0.2
2010-04-22 08:02:05 status installed libfaac0 1.26-0.2
2010-04-22 08:02:05 configure libmlt-data 1:0.3.0-0.1 1:0.3.0-0.1
2010-04-22 08:02:05 status unpacked libmlt-data 1:0.3.0-0.1
2010-04-22 08:02:05 status half-configured libmlt-data 1:0.3.0-0.1
2010-04-22 08:02:05 status installed libmlt-data 1:0.3.0-0.1
2010-04-22 08:02:05 configure libpq5 8.4.3-0ubuntu9.10 8.4.3-0ubuntu9.10
2010-04-22 08:02:05 status unpacked libpq5 8.4.3-0ubuntu9.10
2010-04-22 08:02:05 status half-configured libpq5 8.4.3-0ubuntu9.10
2010-04-22 08:02:05 status installed libpq5 8.4.3-0ubuntu9.10
2010-04-22 08:02:05 configure libxvidcore4 2:1.1.3-0.6 2:1.1.3-0.6
2010-04-22 08:02:05 status unpacked libxvidcore4 2:1.1.3-0.6
2010-04-22 08:02:05 status half-configured libxvidcore4 2:1.1.3-0.6
2010-04-22 08:02:05 status installed libxvidcore4 2:1.1.3-0.6
2010-04-22 08:02:05 configure obexd-client 0.14-0ubuntu1.1 0.14-0ubuntu1.1
2010-04-22 08:02:05 status unpacked obexd-client 0.14-0ubuntu1.1
2010-04-22 08:02:05 status half-configured obexd-client 0.14-0ubuntu1.1
2010-04-22 08:02:05 status installed obexd-client 0.14-0ubuntu1.1
2010-04-22 08:02:05 configure sudo 1.7.0-1ubuntu2.2 1.7.0-1ubuntu2.2
2010-04-22 08:02:05 status unpacked sudo 1.7.0-1ubuntu2.2
2010-04-22 08:02:05 status unpacked sudo 1.7.0-1ubuntu2.2
2010-04-22 08:02:05 status half-configured sudo 1.7.0-1ubuntu2.2
2010-04-22 08:02:05 status installed sudo 1.7.0-1ubuntu2.2
2010-04-22 08:02:06 configure firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-3.5-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-3.0-branding 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox-3.5 40
2010-04-22 08:02:06 status installed firefox-3.5 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-3.5-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-3.0 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-3.0-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 configure firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status unpacked firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status half-configured firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 status installed firefox-gnome-support 3.5.9+nobinonly-0ubuntu0.9.10.1
2010-04-22 08:02:06 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 08:02:06 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 08:02:07 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 08:53:49 startup packages remove
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:53:49 status installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:03 remove libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:03 status half-configured libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:03 status half-installed libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:04 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:04 status config-files libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:04 status config-files libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1
2010-04-22 08:54:04 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 08:54:04 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:04 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:05 startup archives unpack
2010-04-22 08:54:05 install kdelibs-data <none> 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:05 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:05 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:54:05 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:06 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:06 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:06 install libqt3-mt <none> 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:06 status half-installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:07 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:07 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:07 install libavahi-qt3-1 <none> 0.6.25-1ubuntu5.1
2010-04-22 08:54:07 status half-installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:07 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:07 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:07 install liblua50 <none> 5.0.3-3build1
2010-04-22 08:54:07 status half-installed liblua50 5.0.3-3build1
2010-04-22 08:54:07 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:54:07 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:54:07 install liblualib50 <none> 5.0.3-3build1
2010-04-22 08:54:07 status half-installed liblualib50 5.0.3-3build1
2010-04-22 08:54:07 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:54:07 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:54:07 install kdelibs4c2a <none> 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:07 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:07 status triggers-pending man-db 2.5.6-2
2010-04-22 08:54:07 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:08 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:08 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:08 install libavutil49 4:0.5+svn20090706-2ubuntu2 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:08 status half-installed libavutil49 4:0.5+svn20090706-2ubuntu2
2010-04-22 08:54:08 status unpacked libavutil49 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:08 status unpacked libavutil49 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:08 install libx264-60 <none> 1:0.svn20080712-0.1
2010-04-22 08:54:08 status half-installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:08 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:08 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:08 install libx264-65 <none> 1:0.svn20090115-0.0
2010-04-22 08:54:08 status half-installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:08 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:08 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:08 install libamrnb3 <none> 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:08 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:08 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:08 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:08 install libamrwb3 <none> 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:08 status half-installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:09 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:09 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:09 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 08:54:09 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:54:09 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:54:09 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 08:54:09 status half-configured man-db 2.5.6-2
2010-04-22 08:54:10 status installed man-db 2.5.6-2
2010-04-22 08:54:11 startup packages configure
2010-04-22 08:54:11 configure kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:11 status half-configured kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 status installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 configure libqt3-mt 3:3.3.8-b-5ubuntu3 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status half-configured libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:12 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:12 configure libavahi-qt3-1 0.6.25-1ubuntu5.1 0.6.25-1ubuntu5.1
2010-04-22 08:54:12 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:12 status half-configured libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:12 status installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:12 configure liblua50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:54:12 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:54:12 status half-configured liblua50 5.0.3-3build1
2010-04-22 08:54:12 status installed liblua50 5.0.3-3build1
2010-04-22 08:54:12 configure liblualib50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:54:12 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:54:12 status half-configured liblualib50 5.0.3-3build1
2010-04-22 08:54:12 status installed liblualib50 5.0.3-3build1
2010-04-22 08:54:12 configure kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 status half-configured kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 status installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:12 configure libavutil49 4:0.5+svn20090706-2ubuntu2.1 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:12 status unpacked libavutil49 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:12 status half-configured libavutil49 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:12 status installed libavutil49 4:0.5+svn20090706-2ubuntu2.1
2010-04-22 08:54:12 configure libx264-60 1:0.svn20080712-0.1 1:0.svn20080712-0.1
2010-04-22 08:54:12 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:12 status half-configured libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:12 status installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:12 configure libx264-65 1:0.svn20090115-0.0 1:0.svn20090115-0.0
2010-04-22 08:54:12 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:12 status half-configured libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:12 status installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:12 configure libamrnb3 7.0.0.2-0.1medibuntu1 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:12 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:12 status half-configured libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:12 status installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:12 configure libamrwb3 7.0.0.3-0.0medibuntu1 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:12 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:12 status half-configured libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:12 status installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:12 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 08:54:12 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:12 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:54 startup packages remove
2010-04-22 08:54:54 status installed binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 remove binutils-static 2.20-0ubuntu2 2.20-0ubuntu2
2010-04-22 08:54:54 status half-configured binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 status half-installed binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 status config-files binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 status config-files binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 status config-files binutils-static 2.20-0ubuntu2
2010-04-22 08:54:54 status not-installed binutils-static <none>
2010-04-22 08:54:54 status installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 remove kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status half-configured kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status triggers-pending man-db 2.5.6-2
2010-04-22 08:54:54 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 08:54:54 status config-files kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status config-files kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 remove kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status half-configured kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:54:54 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status config-files kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status config-files kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:54:54 status installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 remove libamrnb3 7.0.0.2-0.1medibuntu1 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 status half-configured libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 status config-files libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 status config-files libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:54:54 status installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 remove libamrwb3 7.0.0.3-0.0medibuntu1 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 status half-configured libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 status half-installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 status config-files libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 status config-files libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:54:54 status installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 remove libavahi-qt3-1 0.6.25-1ubuntu5.1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 status half-configured libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 status half-installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 status config-files libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 status config-files libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:54:54 status installed liblualib50 5.0.3-3build1
2010-04-22 08:54:54 remove liblualib50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:54:54 status half-configured liblualib50 5.0.3-3build1
2010-04-22 08:54:54 status half-installed liblualib50 5.0.3-3build1
2010-04-22 08:54:54 status config-files liblualib50 5.0.3-3build1
2010-04-22 08:54:54 status config-files liblualib50 5.0.3-3build1
2010-04-22 08:54:54 status installed liblua50 5.0.3-3build1
2010-04-22 08:54:54 remove liblua50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:54:54 status half-configured liblua50 5.0.3-3build1
2010-04-22 08:54:54 status half-installed liblua50 5.0.3-3build1
2010-04-22 08:54:54 status config-files liblua50 5.0.3-3build1
2010-04-22 08:54:54 status config-files liblua50 5.0.3-3build1
2010-04-22 08:54:54 status installed libopenjpeg2 1.3+dfsg-4
2010-04-22 08:54:55 remove libopenjpeg2 1.3+dfsg-4 1.3+dfsg-4
2010-04-22 08:54:55 status half-configured libopenjpeg2 1.3+dfsg-4
2010-04-22 08:54:55 status half-installed libopenjpeg2 1.3+dfsg-4
2010-04-22 08:54:55 status config-files libopenjpeg2 1.3+dfsg-4
2010-04-22 08:54:55 status config-files libopenjpeg2 1.3+dfsg-4
2010-04-22 08:54:55 status installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 remove libqt3-mt 3:3.3.8-b-5ubuntu3 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 status half-configured libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 status half-installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 status config-files libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 status config-files libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:54:55 status installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:55 remove libx264-60 1:0.svn20080712-0.1 1:0.svn20080712-0.1
2010-04-22 08:54:55 status half-configured libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:55 status half-installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:55 status config-files libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:55 status config-files libx264-60 1:0.svn20080712-0.1
2010-04-22 08:54:55 status installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:55 remove libx264-65 1:0.svn20090115-0.0 1:0.svn20090115-0.0
2010-04-22 08:54:55 status half-configured libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:55 status half-installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:55 status config-files libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:55 status config-files libx264-65 1:0.svn20090115-0.0
2010-04-22 08:54:55 status installed linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:55 remove linux-headers-2.6.31-19-generic 2.6.31-19.56 2.6.31-19.56
2010-04-22 08:54:55 status half-configured linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:55 status half-installed linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:58 status config-files linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:58 status config-files linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:58 status config-files linux-headers-2.6.31-19-generic 2.6.31-19.56
2010-04-22 08:54:58 status not-installed linux-headers-2.6.31-19-generic <none>
2010-04-22 08:54:58 status installed linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:54:58 remove linux-headers-2.6.31-19 2.6.31-19.56 2.6.31-19.56
2010-04-22 08:54:58 status half-configured linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:54:58 status half-installed linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:55:02 status config-files linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:55:02 status config-files linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:55:02 status config-files linux-headers-2.6.31-19 2.6.31-19.56
2010-04-22 08:55:02 status not-installed linux-headers-2.6.31-19 <none>
2010-04-22 08:55:02 status installed linux-image-2.6.28-18-generic 2.6.28-18.59
2010-04-22 08:55:02 remove linux-image-2.6.28-18-generic 2.6.28-18.59 2.6.28-18.59
2010-04-22 08:55:02 status half-configured linux-image-2.6.28-18-generic 2.6.28-18.59
2010-04-22 08:55:02 status half-installed linux-image-2.6.28-18-generic 2.6.28-18.59
2010-04-22 08:55:08 status config-files linux-image-2.6.28-18-generic 2.6.28-18.59
2010-04-22 08:55:08 status config-files linux-image-2.6.28-18-generic 2.6.28-18.59
2010-04-22 08:55:08 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 08:55:08 status half-configured man-db 2.5.6-2
2010-04-22 08:55:08 status installed man-db 2.5.6-2
2010-04-22 08:55:08 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 08:55:08 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 08:55:08 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 08:55:08 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 08:55:08 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:55:08 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:56:59 startup archives unpack
2010-04-22 08:57:12 install kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:12 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:12 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:57:12 status half-installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:13 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:13 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:13 install libqt3-mt 3:3.3.8-b-5ubuntu3 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:13 status half-installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:14 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:14 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:14 install libavahi-qt3-1 0.6.25-1ubuntu5.1 0.6.25-1ubuntu5.1
2010-04-22 08:57:14 status half-installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:14 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:14 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:14 install liblua50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:57:14 status half-installed liblua50 5.0.3-3build1
2010-04-22 08:57:14 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:57:14 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:57:14 install liblualib50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:57:14 status half-installed liblualib50 5.0.3-3build1
2010-04-22 08:57:14 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:57:14 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:57:14 install kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:14 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:14 status triggers-pending man-db 2.5.6-2
2010-04-22 08:57:14 status half-installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:15 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:15 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:15 install libx264-60 1:0.svn20080712-0.1 1:0.svn20080712-0.1
2010-04-22 08:57:15 status half-installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:15 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:15 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:15 install libx264-65 1:0.svn20090115-0.0 1:0.svn20090115-0.0
2010-04-22 08:57:15 status half-installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:15 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:15 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:15 install libamrnb3 7.0.0.2-0.1medibuntu1 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:15 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:15 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:15 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:15 install libamrwb3 7.0.0.3-0.0medibuntu1 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:15 status half-installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:15 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:15 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:15 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 08:57:15 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:57:15 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 08:57:15 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 08:57:15 status half-configured man-db 2.5.6-2
2010-04-22 08:57:17 status installed man-db 2.5.6-2
2010-04-22 08:57:18 startup packages configure
2010-04-22 08:57:18 configure kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status unpacked kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status half-configured kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 status installed kdelibs-data 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:18 configure libqt3-mt 3:3.3.8-b-5ubuntu3 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:18 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:19 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:19 status unpacked libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:19 status half-configured libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:19 status installed libqt3-mt 3:3.3.8-b-5ubuntu3
2010-04-22 08:57:19 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 08:57:19 configure libavahi-qt3-1 0.6.25-1ubuntu5.1 0.6.25-1ubuntu5.1
2010-04-22 08:57:19 status unpacked libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:19 status half-configured libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:19 status installed libavahi-qt3-1 0.6.25-1ubuntu5.1
2010-04-22 08:57:19 configure liblua50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:57:19 status unpacked liblua50 5.0.3-3build1
2010-04-22 08:57:19 status half-configured liblua50 5.0.3-3build1
2010-04-22 08:57:19 status installed liblua50 5.0.3-3build1
2010-04-22 08:57:19 configure liblualib50 5.0.3-3build1 5.0.3-3build1
2010-04-22 08:57:19 status unpacked liblualib50 5.0.3-3build1
2010-04-22 08:57:19 status half-configured liblualib50 5.0.3-3build1
2010-04-22 08:57:19 status installed liblualib50 5.0.3-3build1
2010-04-22 08:57:19 configure kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:19 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:20 status unpacked kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:20 status half-configured kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:20 status installed kdelibs4c2a 4:3.5.10.dfsg.1-2ubuntu7.2
2010-04-22 08:57:20 configure libx264-60 1:0.svn20080712-0.1 1:0.svn20080712-0.1
2010-04-22 08:57:20 status unpacked libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:20 status half-configured libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:20 status installed libx264-60 1:0.svn20080712-0.1
2010-04-22 08:57:20 configure libx264-65 1:0.svn20090115-0.0 1:0.svn20090115-0.0
2010-04-22 08:57:20 status unpacked libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:20 status half-configured libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:20 status installed libx264-65 1:0.svn20090115-0.0
2010-04-22 08:57:20 configure libamrnb3 7.0.0.2-0.1medibuntu1 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:20 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:20 status half-configured libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:20 status installed libamrnb3 7.0.0.2-0.1medibuntu1
2010-04-22 08:57:20 configure libamrwb3 7.0.0.3-0.0medibuntu1 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:20 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:20 status half-configured libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:20 status installed libamrwb3 7.0.0.3-0.0medibuntu1
2010-04-22 08:57:20 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 08:57:20 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 08:57:20 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 15:59:09 startup archives unpack
2010-04-22 15:59:24 install libgtkhex0 <none> 2.24.0-1
2010-04-22 15:59:24 status half-installed libgtkhex0 2.24.0-1
2010-04-22 15:59:24 status unpacked libgtkhex0 2.24.0-1
2010-04-22 15:59:24 status unpacked libgtkhex0 2.24.0-1
2010-04-22 15:59:25 install ghex <none> 2.24.0-1
2010-04-22 15:59:25 status half-installed ghex 2.24.0-1
2010-04-22 15:59:25 status triggers-pending man-db 2.5.6-2
2010-04-22 15:59:25 status half-installed ghex 2.24.0-1
2010-04-22 15:59:25 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 15:59:25 status half-installed ghex 2.24.0-1
2010-04-22 15:59:25 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-22 15:59:25 status half-installed ghex 2.24.0-1
2010-04-22 15:59:25 status unpacked ghex 2.24.0-1
2010-04-22 15:59:25 status unpacked ghex 2.24.0-1
2010-04-22 15:59:25 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 15:59:25 status half-configured man-db 2.5.6-2
2010-04-22 15:59:26 status installed man-db 2.5.6-2
2010-04-22 15:59:26 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 15:59:26 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 15:59:27 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 15:59:27 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-22 15:59:27 status half-configured hicolor-icon-theme 0.10-2
2010-04-22 15:59:30 status installed hicolor-icon-theme 0.10-2
2010-04-22 15:59:31 startup packages configure
2010-04-22 15:59:31 configure libgtkhex0 2.24.0-1 2.24.0-1
2010-04-22 15:59:31 status unpacked libgtkhex0 2.24.0-1
2010-04-22 15:59:31 status half-configured libgtkhex0 2.24.0-1
2010-04-22 15:59:31 status installed libgtkhex0 2.24.0-1
2010-04-22 15:59:31 status triggers-pending libc-bin 2.10.1-0ubuntu16
2010-04-22 15:59:31 configure ghex 2.24.0-1 2.24.0-1
2010-04-22 15:59:31 status unpacked ghex 2.24.0-1
2010-04-22 15:59:31 status half-configured ghex 2.24.0-1
2010-04-22 15:59:31 status installed ghex 2.24.0-1
2010-04-22 15:59:31 trigproc libc-bin 2.10.1-0ubuntu16 2.10.1-0ubuntu16
2010-04-22 15:59:31 status half-configured libc-bin 2.10.1-0ubuntu16
2010-04-22 15:59:31 status installed libc-bin 2.10.1-0ubuntu16
2010-04-22 22:33:29 startup archives unpack
2010-04-22 22:33:42 upgrade bzip2 1.0.5-3 1.0.5-3
2010-04-22 22:33:42 status half-configured bzip2 1.0.5-3
2010-04-22 22:33:42 status unpacked bzip2 1.0.5-3
2010-04-22 22:33:42 status half-installed bzip2 1.0.5-3
2010-04-22 22:33:42 status triggers-pending man-db 2.5.6-2
2010-04-22 22:33:42 status half-installed bzip2 1.0.5-3
2010-04-22 22:33:42 status half-installed bzip2 1.0.5-3
2010-04-22 22:33:42 status unpacked bzip2 1.0.5-3
2010-04-22 22:33:42 status unpacked bzip2 1.0.5-3
2010-04-22 22:33:42 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:33:42 status half-configured man-db 2.5.6-2
2010-04-22 22:33:43 status installed man-db 2.5.6-2
2010-04-22 22:33:43 startup packages configure
2010-04-22 22:33:43 configure bzip2 1.0.5-3 1.0.5-3
2010-04-22 22:33:43 status unpacked bzip2 1.0.5-3
2010-04-22 22:33:43 status half-configured bzip2 1.0.5-3
2010-04-22 22:33:43 status installed bzip2 1.0.5-3
2010-04-22 22:34:49 startup archives unpack
2010-04-22 22:34:49 upgrade file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2010-04-22 22:34:49 status half-configured file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:51 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:51 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:51 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-22 22:34:51 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:51 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:34:51 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:52 status triggers-pending man-db 2.5.6-2
2010-04-22 22:34:52 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:52 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:52 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:53 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:53 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-22 22:34:53 status half-configured hicolor-icon-theme 0.10-2
2010-04-22 22:34:55 status installed hicolor-icon-theme 0.10-2
2010-04-22 22:34:55 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 22:34:55 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:34:55 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:34:55 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:34:55 status half-configured man-db 2.5.6-2
2010-04-22 22:34:55 status installed man-db 2.5.6-2
2010-04-22 22:34:56 startup packages configure
2010-04-22 22:34:56 configure file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2010-04-22 22:34:56 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:56 status half-configured file-roller 2.28.1-0ubuntu1
2010-04-22 22:34:56 status installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:20 startup packages remove
2010-04-22 22:39:20 status installed ubuntu-desktop 1.175
2010-04-22 22:39:20 remove ubuntu-desktop 1.175 1.175
2010-04-22 22:39:20 status half-configured ubuntu-desktop 1.175
2010-04-22 22:39:20 status half-installed ubuntu-desktop 1.175
2010-04-22 22:39:20 status config-files ubuntu-desktop 1.175
2010-04-22 22:39:20 status config-files ubuntu-desktop 1.175
2010-04-22 22:39:20 status config-files ubuntu-desktop 1.175
2010-04-22 22:39:20 status not-installed ubuntu-desktop <none>
2010-04-22 22:39:21 startup packages purge
2010-04-22 22:39:21 status installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:21 remove file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2010-04-22 22:39:21 status half-configured file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status triggers-pending man-db 2.5.6-2
2010-04-22 22:39:22 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:22 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-22 22:39:22 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 purge file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status config-files file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:22 status not-installed file-roller <none>
2010-04-22 22:39:22 status installed zip 3.0-1ubuntu1
2010-04-22 22:39:22 remove zip 3.0-1ubuntu1 3.0-1ubuntu1
2010-04-22 22:39:22 status half-configured zip 3.0-1ubuntu1
2010-04-22 22:39:22 status half-installed zip 3.0-1ubuntu1
2010-04-22 22:39:22 status half-installed zip 3.0-1ubuntu1
2010-04-22 22:39:22 status config-files zip 3.0-1ubuntu1
2010-04-22 22:39:22 status config-files zip 3.0-1ubuntu1
2010-04-22 22:39:22 status config-files zip 3.0-1ubuntu1
2010-04-22 22:39:22 status config-files zip 3.0-1ubuntu1
2010-04-22 22:39:22 status not-installed zip <none>
2010-04-22 22:39:22 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:39:22 status half-configured man-db 2.5.6-2
2010-04-22 22:39:22 status installed man-db 2.5.6-2
2010-04-22 22:39:22 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 22:39:22 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:22 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:22 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-22 22:39:22 status half-configured hicolor-icon-theme 0.10-2
2010-04-22 22:39:23 status installed hicolor-icon-theme 0.10-2
2010-04-22 22:39:55 startup archives unpack
2010-04-22 22:39:55 install zip <none> 3.0-1ubuntu1
2010-04-22 22:39:55 status half-installed zip 3.0-1ubuntu1
2010-04-22 22:39:55 status triggers-pending man-db 2.5.6-2
2010-04-22 22:39:55 status half-installed zip 3.0-1ubuntu1
2010-04-22 22:39:55 status unpacked zip 3.0-1ubuntu1
2010-04-22 22:39:55 status unpacked zip 3.0-1ubuntu1
2010-04-22 22:39:55 install file-roller <none> 2.28.1-0ubuntu1
2010-04-22 22:39:55 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:55 status triggers-pending hicolor-icon-theme 0.10-2
2010-04-22 22:39:55 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:55 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:55 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:55 status half-installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:56 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:56 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:56 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:39:56 status half-configured man-db 2.5.6-2
2010-04-22 22:39:56 status installed man-db 2.5.6-2
2010-04-22 22:39:56 trigproc hicolor-icon-theme 0.10-2 0.10-2
2010-04-22 22:39:56 status half-configured hicolor-icon-theme 0.10-2
2010-04-22 22:39:56 status installed hicolor-icon-theme 0.10-2
2010-04-22 22:39:56 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2010-04-22 22:39:56 status half-configured desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:56 status installed desktop-file-utils 0.15-2ubuntu1
2010-04-22 22:39:57 startup packages configure
2010-04-22 22:39:57 configure zip 3.0-1ubuntu1 3.0-1ubuntu1
2010-04-22 22:39:57 status unpacked zip 3.0-1ubuntu1
2010-04-22 22:39:57 status half-configured zip 3.0-1ubuntu1
2010-04-22 22:39:57 status installed zip 3.0-1ubuntu1
2010-04-22 22:39:57 configure file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2010-04-22 22:39:57 status unpacked file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:57 status half-configured file-roller 2.28.1-0ubuntu1
2010-04-22 22:39:57 status installed file-roller 2.28.1-0ubuntu1
2010-04-22 22:43:48 startup packages purge
2010-04-22 22:43:48 status installed p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 remove p7zip 9.04~dfsg.1-1 9.04~dfsg.1-1
2010-04-22 22:43:48 status half-configured p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status half-installed p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status triggers-pending man-db 2.5.6-2
2010-04-22 22:43:48 status half-installed p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status config-files p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status config-files p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status config-files p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status config-files p7zip 9.04~dfsg.1-1
2010-04-22 22:43:48 status not-installed p7zip <none>
2010-04-22 22:43:48 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:43:48 status half-configured man-db 2.5.6-2
2010-04-22 22:43:48 status installed man-db 2.5.6-2
2010-04-22 22:43:49 startup packages remove
2010-04-22 22:43:49 status installed p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 remove p7zip-rar 9.04~ds.1-1 9.04~ds.1-1
2010-04-22 22:43:49 status half-configured p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 status half-installed p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 status config-files p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 status config-files p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 status config-files p7zip-rar 9.04~ds.1-1
2010-04-22 22:43:49 status not-installed p7zip-rar <none>
2010-04-22 22:43:50 startup packages purge
2010-04-22 22:43:50 status installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 remove p7zip-full 9.04~dfsg.1-1 9.04~dfsg.1-1
2010-04-22 22:43:50 status half-configured p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status half-installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status triggers-pending man-db 2.5.6-2
2010-04-22 22:43:50 status half-installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status config-files p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status config-files p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status config-files p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status config-files p7zip-full 9.04~dfsg.1-1
2010-04-22 22:43:50 status not-installed p7zip-full <none>
2010-04-22 22:43:50 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:43:50 status half-configured man-db 2.5.6-2
2010-04-22 22:43:50 status installed man-db 2.5.6-2
2010-04-22 22:44:10 startup archives unpack
2010-04-22 22:44:10 install p7zip <none> 9.04~dfsg.1-1
2010-04-22 22:44:10 status half-installed p7zip 9.04~dfsg.1-1
2010-04-22 22:44:10 status triggers-pending man-db 2.5.6-2
2010-04-22 22:44:10 status half-installed p7zip 9.04~dfsg.1-1
2010-04-22 22:44:10 status unpacked p7zip 9.04~dfsg.1-1
2010-04-22 22:44:10 status unpacked p7zip 9.04~dfsg.1-1
2010-04-22 22:44:10 install p7zip-full <none> 9.04~dfsg.1-1
2010-04-22 22:44:10 status half-installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:10 status half-installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:10 status unpacked p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:10 status unpacked p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:10 install p7zip-rar <none> 9.04~ds.1-1
2010-04-22 22:44:10 status half-installed p7zip-rar 9.04~ds.1-1
2010-04-22 22:44:10 status unpacked p7zip-rar 9.04~ds.1-1
2010-04-22 22:44:10 status unpacked p7zip-rar 9.04~ds.1-1
2010-04-22 22:44:10 trigproc man-db 2.5.6-2 2.5.6-2
2010-04-22 22:44:10 status half-configured man-db 2.5.6-2
2010-04-22 22:44:10 status installed man-db 2.5.6-2
2010-04-22 22:44:11 startup packages configure
2010-04-22 22:44:11 configure p7zip 9.04~dfsg.1-1 9.04~dfsg.1-1
2010-04-22 22:44:11 status unpacked p7zip 9.04~dfsg.1-1
2010-04-22 22:44:11 status half-configured p7zip 9.04~dfsg.1-1
2010-04-22 22:44:11 status installed p7zip 9.04~dfsg.1-1
2010-04-22 22:44:11 configure p7zip-full 9.04~dfsg.1-1 9.04~dfsg.1-1
2010-04-22 22:44:11 status unpacked p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:11 status half-configured p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:11 status installed p7zip-full 9.04~dfsg.1-1
2010-04-22 22:44:11 configure p7zip-rar 9.04~ds.1-1 9.04~ds.1-1
2010-04-22 22:44:11 status unpacked p7zip-rar 9.04~ds.1-1
2010-04-22 22:44:11 status half-configured p7zip-rar 9.04~ds.1-1
2010-04-22 22:44:11 status installed p7zip-rar 9.04~ds.1-1
2010-04-22 23:10:08 startup packages remove
2010-04-22 23:10:08 status installed apport-hooks-medibuntu 1medibuntu1
2010-04-22 23:10:08 remove apport-hooks-medibuntu 1medibuntu1 1medibuntu1
2010-04-22 23:10:08 status half-configured apport-hooks-medibuntu 1medibuntu1
2010-04-22 23:10:08 status half-installed apport-hooks-medibuntu 1medibuntu1
2010-04-22 23:10:08 status config-files apport-hooks-medibuntu 1medibuntu1
2010-04-22 23:10:08 status config-files apport-hooks-medibuntu 1medibuntu1
2010-04-22 23:20:25 startup packages configure
```

You'll see at the end there I tried uninstalling and reinstalling the zip related utilities to no avail. Sorry for the long list- tried out a fair amount of programs lately.

-wigout

---

### Post by Penguin Guy on 2010-04-23
> **wigout said:**
> ```
wigout@xps-1530:~$ echo $PATH 
/home/wigout/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
It appears that your path is fine, however your [FONT="Courier New"]~/bin[/FONT] contains all the system binaries for some reason. If the programs are in [FONT="Courier New"]/bin[/FONT] then you can just delete the ones in [FONT="Courier New"]~/bin[/FONT], otherwise you'll need to copy the programs from [FONT="Courier New"]~/bin[/FONT] to [FONT="Courier New"]/bin[/FONT]:
```
sudo mv -n ~/bin/* /bin/; sudo rm -r ~/bin
```

---

### Post by wigout on 2010-04-23
Here's what's in my /bin:

```
wigout@xps-1530:~$ ls -al /bin
total 5616
drwxr-xr-x  2 root root   4096 2010-04-22 22:33 .
drwxr-xr-x 21 root root   4096 2010-03-28 20:05 ..
-rwxr-xr-x  1 root root 875596 2009-09-14 00:09 bash
-rwxr-xr-x  3 root root  30192 2009-06-29 19:18 bunzip2
-rwxr-xr-x  3 root root  30192 2009-06-29 19:18 bzcat
lrwxrwxrwx  1 root root      6 2010-04-22 22:33 bzcmp -> bzdiff
-rwxr-xr-x  1 root root   2140 2009-06-29 19:18 bzdiff
lrwxrwxrwx  1 root root      6 2010-04-22 22:33 bzegrep -> bzgrep
-rwxr-xr-x  1 root root   4874 2009-06-29 19:18 bzexe
lrwxrwxrwx  1 root root      6 2010-04-22 22:33 bzfgrep -> bzgrep
-rwxr-xr-x  1 root root   3642 2009-06-29 19:18 bzgrep
-rwxr-xr-x  3 root root  30192 2009-06-29 19:18 bzip2
-rwxr-xr-x  1 root root   9572 2009-06-29 19:18 bzip2recover
lrwxrwxrwx  1 root root      6 2010-04-22 22:33 bzless -> bzmore
-rwxr-xr-x  1 root root   1297 2009-06-29 19:18 bzmore
-rwxr-xr-x  1 root root  50876 2009-10-06 06:07 cat
-rwxr-xr-x  1 root root  59052 2009-10-06 06:07 chgrp
-rwxr-xr-x  1 root root  54932 2009-10-06 06:07 chmod
-rwxr-xr-x  1 root root  59060 2009-10-06 06:07 chown
-rwxr-xr-x  1 root root   5524 2009-06-24 11:28 chvt
-rwxr-xr-x  1 root root 104332 2009-10-06 06:07 cp
-rwxr-xr-x  1 root root 126676 2009-06-23 02:03 cpio
-rwxr-xr-x  1 root root  92132 2009-09-20 18:49 dash
-rwxr-xr-x  1 root root  67224 2009-10-06 06:07 date
-rwxr-xr-x  1 root root   9672 2009-10-23 22:28 dbus-cleanup-sockets
-rwxr-xr-x  1 root root 292728 2009-10-23 22:28 dbus-daemon
-rwxr-xr-x  1 root root   5524 2009-10-23 22:28 dbus-uuidgen
-rwxr-xr-x  1 root root  59092 2009-10-06 06:07 dd
-rwxr-xr-x  1 root root  71412 2009-10-06 06:07 df
-rwxr-xr-x  1 root root 112720 2009-10-06 06:07 dir
-rwxr-xr-x  1 root root   5524 2009-10-22 16:54 dmesg
-rwxr-xr-x  1 root root   9756 2009-09-15 08:21 dnsdomainname
-rwxr-xr-x  1 root root  57936 2009-06-24 11:28 dumpkeys
-rwxr-xr-x  1 root root  34364 2009-10-06 06:07 echo
-rwxr-xr-x  1 root root  39700 2009-07-20 13:45 ed
-rwxr-xr-x  1 root root  96184 2009-04-28 06:03 egrep
-rwxr-xr-x  1 root root  30260 2009-10-06 06:07 false
-rwxr-xr-x  1 root root   9624 2009-06-24 11:28 fgconsole
-rwxr-xr-x  1 root root  59252 2009-04-28 06:03 fgrep
-rwxr-xr-x  1 root root  26460 2009-05-11 07:23 fuser
-rwsr-xr-x  1 root root  26228 2010-01-28 12:07 fusermount
-rwxr-xr-x  1 root root 100312 2009-04-28 06:03 grep
-rwxr-xr-x  2 root root     63 2010-01-19 15:45 gunzip
-rwxr-xr-x  1 root root   5874 2010-01-19 15:45 gzexe
-rwxr-xr-x  1 root root  57388 2010-01-19 15:45 gzip
-rwxr-xr-x  1 root root   9752 2009-09-15 08:21 hostname
-rwxr-xr-x  1 root root 211820 2009-04-28 19:34 ip
-rwxr-xr-x  1 root root   9624 2009-06-24 11:28 kbd_mode
-rwxr-xr-x  1 root root  17956 2009-09-15 16:46 kill
-rwxr-xr-x  1 root root 141192 2009-04-28 19:41 less
-rwxr-xr-x  1 root root   5620 2009-04-28 19:41 lessecho
lrwxrwxrwx  1 root root      8 2010-02-12 21:24 lessfile -> lesspipe
-rwxr-xr-x  1 root root  14408 2009-04-28 19:41 lesskey
-rwxr-xr-x  1 root root   6947 2009-04-28 19:41 lesspipe
-rwxr-xr-x  1 root root  50840 2009-10-06 06:07 ln
-rwxr-xr-x  1 root root  86824 2009-06-24 11:28 loadkeys
-rwxr-xr-x  1 root root  43352 2009-07-31 08:55 login
-rwxr-xr-x  1 root root 112720 2009-10-06 06:07 ls
-rwxr-xr-x  1 root root   5472 2009-09-15 16:46 lsmod
-rwxr-xr-x  1 root root  38544 2009-10-06 06:07 mkdir
-rwxr-xr-x  1 root root  38488 2009-10-06 06:07 mknod
-rwxr-xr-x  1 root root  42640 2009-10-06 06:07 mktemp
-rwxr-xr-x  1 root root  30372 2009-10-22 16:54 more
-rwsr-xr-x  1 root root  72188 2009-10-22 16:54 mount
-rwxr-xr-x  1 root root   5452 2009-11-10 03:44 mountpoint
lrwxrwxrwx  1 root root     20 2009-08-26 14:57 mt -> /etc/alternatives/mt
-rwxr-xr-x  1 root root  34700 2009-06-23 02:03 mt-gnu
-rwxr-xr-x  1 root root  96136 2009-10-06 06:07 mv
-rwxr-xr-x  1 root root 153516 2009-03-30 05:23 nano
lrwxrwxrwx  1 root root     20 2009-08-26 14:57 nc -> /etc/alternatives/nc
-rwxr-xr-x  1 root root  22076 2008-06-21 17:40 nc.traditional
lrwxrwxrwx  1 root root     24 2009-08-26 14:57 netcat -> /etc/alternatives/netcat
-rwxr-xr-x  1 root root 114124 2009-05-04 09:20 netstat
-rwxr-xr-x  1 root root  34784 2009-10-09 06:16 ntfs-3g
-rwxr-xr-x  1 root root   5528 2009-10-09 06:16 ntfs-3g.probe
lrwxrwxrwx  1 root root      6 2010-02-12 21:24 open -> openvt
-rwxr-xr-x  1 root root  13820 2009-06-24 11:28 openvt
lrwxrwxrwx  1 root root     14 2010-02-12 21:28 pidof -> /sbin/killall5
-rwsr-xr-x  1 root root  34696 2009-05-11 16:04 ping
-rwsr-xr-x  1 root root  30492 2009-05-11 16:04 ping6
-rwxr-xr-x  1 root root  83792 2009-09-15 16:46 ps
-rwxr-xr-x  1 root root  38528 2009-10-06 06:07 pwd
lrwxrwxrwx  1 root root      4 2010-02-12 21:28 rbash -> bash
-rwxr-xr-x  1 root root  42620 2009-10-06 06:07 readlink
-rwxr-xr-x  1 root root  59080 2009-10-06 06:07 rm
-rwxr-xr-x  1 root root  34392 2009-10-06 06:07 rmdir
lrwxrwxrwx  1 root root      4 2009-08-26 14:57 rnano -> nano
-rwxr-xr-x  1 root root  13940 2009-02-16 15:27 run-parts
-rwxr-xr-x  1 root root  59512 2009-07-24 11:27 sed
-rwxr-xr-x  1 root root  38580 2009-06-24 11:28 setfont
-rwxr-xr-x  1 root root   9478 2009-10-02 08:19 setupcon
lrwxrwxrwx  1 root root      4 2009-08-26 14:57 sh -> dash
lrwxrwxrwx  1 root root      4 2010-02-12 21:28 sh.distrib -> bash
-rwxr-xr-x  1 root root  34376 2009-10-06 06:07 sleep
-rwxr-xr-x  1 root root  54916 2009-10-06 06:07 stty
-rwsr-xr-x  1 root root  31124 2009-07-31 08:55 su
-rwxr-xr-x  1 root root  30268 2009-10-06 06:07 sync
-rwxr-xr-x  1 root root   9680 2009-10-22 16:54 tailf
-rwxr-xr-x  1 root root 277172 2009-04-29 13:25 tar
-rwxr-xr-x  1 root root   9516 2009-02-16 15:27 tempfile
-rwxr-xr-x  1 root root  54940 2009-10-06 06:07 touch
-rwxr-xr-x  1 root root  30260 2009-10-06 06:07 true
-rwxr-xr-x  1 root root   9716 2010-01-28 12:07 ulockmgr_server
-rwsr-xr-x  1 root root  47096 2009-10-22 16:54 umount
-rwxr-xr-x  1 root root  34372 2009-10-06 06:07 uname
-rwxr-xr-x  2 root root     63 2010-01-19 15:45 uncompress
-rwxr-xr-x  1 root root   2762 2009-06-24 11:28 unicode_start
-rwxr-xr-x  1 root root   9155 2010-04-08 09:02 unyaffs
-rwxr-xr-x  1 root root 112724 2009-10-06 06:07 vdir
-rwxr-xr-x  1 root root    946 2009-02-16 15:27 which
-rwxr-xr-x  1 root root     64 2010-01-19 15:45 zcat
-rwxr-xr-x  1 root root     69 2010-01-19 15:45 zcmp
-rwxr-xr-x  1 root root   4424 2010-01-19 15:45 zdiff
-rwxr-xr-x  1 root root     64 2010-01-19 15:45 zegrep
-rwxr-xr-x  1 root root     64 2010-01-19 15:45 zfgrep
-rwxr-xr-x  1 root root   2015 2010-01-19 15:45 zforce
-rwxr-xr-x  1 root root   5597 2010-01-19 15:45 zgrep
-rwxr-xr-x  1 root root   1733 2010-01-19 15:45 zless
-rwxr-xr-x  1 root root   2416 2010-01-19 15:45 zmore
-rwxr-xr-x  1 root root   4952 2010-01-19 15:45 znew

```looking back at my ~/bin:
Are those commands supposed to be in /bin?
Those are all symlinks for a busybox- and the busybox there is version 1.1.3(according to a strings of ~/bin/busybox)- is that what's supposed to be in /bin?
Busybox 1.1.3 is kinda old and suspiciously identical to my other micro-linux system, a media-player. I can't help but think that I somehow insanely crossed/copied one from the other....

-wigout

---

### Post by mikodo on 2010-04-23
> **Penguin Guy said:**
> It appears that your path is fine, however your [FONT=Courier New]~/bin[/FONT] contains all the system binaries for some reason. If the programs are in [FONT=Courier New]/bin[/FONT] then you can just delete the ones in [FONT=Courier New]~/bin[/FONT], otherwise you'll need to copy the programs from [FONT=Courier New]~/bin[/FONT] to [FONT=Courier New]/bin[/FONT]:
```
sudo mv -n ~/bin/* /bin/; rm ~/bin
```
Just a compliment; You show how easy linux is, when you know what you are doing in the command line.

---

### Post by da burger on 2010-04-23
Your path contains ~/bin. I don't see why this would be necessary so you might want to try removing it.```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
``` Alternatively if it is necessary you could move it to the end of your path. ```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wigout/bin
```

It does seem weird that you have symlinks to busybox named after many commands in your /home directory. I wonder what caused that.

---

### Post by wigout on 2010-04-23
Does anyone else have busybox in their ~/bin or /bin directories?

---

### Post by wigout on 2010-04-23
And anyway, any changes I make to PATH don't seem to persist- every time I open a new terminal it gives the same old errors; and echo $PATH gives the same "old" PATH, not the altered one I set....

---

### Post by da burger on 2010-04-23
If you want to keep a changed path you need to add the ```
export PATH=blah:blah:blah
``` line to your .bashrc file which is hidden in your home directory. To change it open nuatilus, press CTRL-H and it should appear near the bottom (along with lots of other folders). Before adding things to your .bashrc file check that they work by running them in the terminal.

---

### Post by wigout on 2010-04-23
> **da burger said:**
> If you want to keep a changed path you need to add the ```
export PATH=blah:blah:blah
``` line to your .bashrc file which is hidden in your home directory.

Alright, but how is my PATH currently being set- if I add the following to ~/.bashrc:
```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wigout/bin
```Aren't I just dodging the problem- something else is setting my PATH incorrectly everytime, and I'd just being scripting in a reverse of that change? What might be the fix for this?

Does anyone else have busybox in their ~/bin or /bin directories?

-wigout

---

### Post by da burger on 2010-04-23
Have you checked that the path isn't being changed in the .bashrc file. Post the output of ```
grep path .bashrc -i
```

---

### Post by kanikilu on 2010-04-23
> **wigout said:**
> Does anyone else have busybox in their ~/bin or /bin directories? Yes, in /bin. Why everything is symlinked to it in your ~/bin, is beyond me :confused:

---

### Post by srs5694 on 2010-04-23
> **da burger said:**
> If you want to keep a changed path you need to add the ```
export PATH=blah:blah:blah
``` line to your .bashrc file which is hidden in your home directory.

IMHO, it's better to find where the incorrect value is being set and change that. It could be in ~/.bashrc, ~/.profile, /etc/bash.bashrc, /etc/profile, or various other locations. Depending on where it is, the problem could recur if you create new users for any reason; those users might end up with the same strange PATH value. Also, if you just override the PATH in this way, any future edits to the PATH in the system configuration files won't apply to your user account.

I also recommend completely deleting ~/bin. Unless I missed something, in the OP's case it just contains busybox, including a bunch of its symbolic links. This program isn't normally needed on a regular Ubuntu installation, and if it were, it would be better installed in /bin, not ~/bin.

(Those posting all seem to realize this, but in case somebody reading this doesn't, "~" in a Linux shell refers to the current user's home directory. Thus, if your home directory is /home/abc, ~/bin means /home/abc/bin.)

---

### Post by srs5694 on 2010-04-23
> **kanikilu said:**
> Yes, in /bin. Why everything is symlinked to it in your ~/bin, is beyond me :confused:

The [busybox](http://www.busybox.net/) program is a one-program stand-in for a large number of standard Unix utilities. It's intended for use on space-constrained installations, such as emergency floppy disks or embedded Linux systems (on cell phones, say). It works differently depending on how it's called, so a busybox installation normally includes the main busybox binary and a bunch of symbolic links to it using the names of the standard Unix utilities. When you call it by using one of the symbolic links, it acts like the utility with the symbolic link's name. Presumably it got copied to ~/bin on the OP's system by accident; it shouldn't normally be there.

Ubuntu does include a busybox package, so it can be installed. I doubt if it's installed by default, but I don't know that for a fact. (It's not installed on my Ubuntu-based system that's currently running.) When it is installed via this package, it'll reside in /bin, and the Ubuntu binary package doesn't install symbolic links by default, according to its description. There's little or no reason to install busybox on a regular Ubuntu desktop or server computer, since (AFAIK) all the utilities that busybox emulates are available directly, and such computers are usually not so short on disk space that busybox's advantages are important.

---

### Post by Penguin Guy on 2010-04-23
You have BusyBox installed at [FONT="Courier New"]~/bin[/FONT] as well as having the equivalent installed in [FONT="Courier New"]/bin[/FONT]. Which is probably what's confused your computer.

There are two possible fixes to your problem:
[LIST=1]
[*]**Remove [FONT="Courier New"]~/bin[/FONT] From [FONT="Courier New"]$PATH[/FONT]:** Look for something like [FONT="Courier New"]export PATH="$HOME/bin:$PATH"[/FONT] in [FONT="Courier New"]~/.profile[/FONT] and delete it (check back here if you're not sure).
[*]**Remove [FONT="Courier New"]~/bin[/FONT]:** The only thing in [FONT="Courier New"]~/bin[/FONT] (from your earlier [FONT="Courier New"]ls[/FONT] command) is BusyBox, so just delete [FONT="Courier New"]~/bin[/FONT]:
```
sudo rm -r ~/bin
```
[*]Or if you want to keep BusyBox, but want your system to work:
```
sudo mv -f ~/bin /bin/
```
[/LIST]
I would advise going with [FONT="Courier New"]#1[/FONT] **and** [FONT="Courier New"]#2[/FONT].

---

### Post by wigout on 2010-04-23
Well I only did #2, as I might someday have some real commands in ~/bin, so I left the .profile line alone.

I really think I somehow insanely copied over the /bin from the linux media player over to my home directory. I don't know how I did that, but all signs (the links, file size and counts, & version) all match.

Anyway, now archive manager is working without a hitch and no bizarre warnings on opening up terminal.

Thanks Super Ubuntu Friends!

-wigout

---

### Post by Penguin Guy on 2010-04-23
> **wigout said:**
> Well I only did #2, as I might someday have some real commands in ~/bin, so I left the .profile line alone.
Great, as long as you know what you're doing.

> **wigout said:**
> Anyway, now archive manager is working without a hitch and no bizarre warnings on opening up terminal.
Glad you've got the info you wanted, but it would be useful to others if you could [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") though. Thanks.

---

