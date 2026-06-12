---
title: "i am having errors everytime i install"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by imlinux on 2009-03-18
i recently updated as updates were applied suddenly electricity went off while installing updates after that i am having errors every time i install something.
```
Setting up gstreamer0.10-plugins-good (0.10.10.4-1ubuntu1.1) ...
/usr/share/gconf/schemas/gstreamer-0.10.schemas:1: parser error : Start tag expected, '<' not found
t
^
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 subprocess post-installation script returned error exit status 1
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gstreamer0.10-plugins-good (0.10.10.4-1ubuntu1.1) ...
/usr/share/gconf/schemas/gstreamer-0.10.schemas:1: parser error : Start tag expected, '<' not found
t
^
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good-dbg:
 gstreamer0.10-plugins-good-dbg depends on gstreamer0.10-plugins-good (= 0.10.10.4-1ubuntu1.1); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.10-plugins-good
 gstreamer0.10-plugins-good-dbg



```
please help to correct it.

---

### Post by cairnzi on 2009-03-18
i would suggest back up all the data you want to keep and re-install,may be the easiest way..... but wait.... and somebody else may have a work around:)

---

### Post by Wyatt208 on 2009-03-18
Do you know what packages you attempted to update? Try removing those in synaptic and re-installing them.

---

### Post by 123456789123456789123456 on 2009-03-18
From what I get from the error you posted.  It would seem that Ubuntu managed only to install part of the updates, but did not finish any of them.  The error is from the first update, that it expected to find a beginning of a file, but was unable to find it.  The earlier suggestion of backing up and restoring a fresh copy would deffinatly work.  However try these.
Uuntu cd should if I am not mistaken has a repair feature.  Try booting from cd, and running the repair feature.  If that does not work.  Next time you try to update, make note of every packet that it is attempting to install.  Go to the package program, name exscapes me at the moment.  Search for each packet, tell the packet program, to remove them.
That should not only remove the update but the old version as well.
after removing, tell the packet program to install them again.
after that attempt update.
The only thing I can suggest is backup your data before you try this.  It is possible it may cause problems with the system.  Expecially if the files attempting to be updated are needed directly for ubuntu to run, like for instance, the update process was interupted while updating from 8.04 to 8.10.  If the files are not system related, you could tell the packet program to completely remove the packet.  simply removing will uninstall it, but keep the packet on the hard disk.  Completely removing will delete the packet from the hard disk, and the packet next install would have to be downloaded and installed.  Doing this would probably end up downloading the newest version of the packet.  and Update would not be needed.

but as was suggested before, wait, someone may have a work around that is different from mine.

---

### Post by 123456789123456789123456 on 2009-03-18
me again
my plan would work
remove the following from synaptic
gstreamer0.10-plugins-good
this packet from what I read of the entire error message you posted is the one that did not install correctly.  the gstreamer0.10-plugins-good-dbg was not effected.  because the gstreamer0.10-plugins-good packet never installed, it could not install the other one.  attempt to remove this packet, and reinstall it.
that should elieviate the problem.

---

### Post by presence1960 on 2009-03-18
restart your machine and try choosing recovery mode when GRUB menu comes up. Then choose repair broken packages. Also in package manager under edit menu is an option to repair broken packages. I would try these before reinstallation.

---

### Post by tarps87 on 2009-03-18
As mention above try to remove the package gstreamer0.10-plugins-good
```
sudo apt-get remove gstreamer0.10-plugins-good
```
Now try to fix any broken packages
```
sudo apt-get install -f
```
Now just to be on the safe side clean the apt cache using
```
sudo apt-get clean
```
and
```
sudo rm -rf /var/cache/apt/archives/*
```
Now you should be able to down load and install the updates again

If after this it still does not work try
```
sudo apt-get purge gstreamer*
```
Note you will need to reinstall all the gstreamer packages that you use afterwards

---

### Post by imlinux on 2009-03-19
i am not able to uninstall it.is there anyway to fix it using live cd?

---

### Post by tarps87 on 2009-03-19
> **imlinux said:**
> i am not able to uninstall it.is there anyway to fix it using live cd?

What do you mean by not being able to uninstall it? Are there any error messages?

---

### Post by imlinux on 2009-03-19
> user@user-desktop:~$ sudo apt-get remove gstreamer0.10-plugins-good
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-musicbrainz2 libgda3-common python-gnome2-extras libdiscid0
  python-pymad python-pyogg python-pyvorbis python-ogg python-mutagen
  python-ctypes libtunepimp5 python-tunepimp libgda3-bin libgda3-3 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gstreamer0.10-plugins-good
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 3465kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231420 files and directories currently installed.)
Removing gstreamer0.10-plugins-good ...
/usr/share/gconf/schemas/gstreamer-0.10.schemas:1: parser error : Start tag expected, '<' not found
t
^
dpkg: error processing gstreamer0.10-plugins-good (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gstreamer0.10-plugins-good
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-desktop:~$ 



> user@user-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-musicbrainz2 libgda3-common python-gnome2-extras libdiscid0
  python-pymad python-pyogg python-pyvorbis python-ogg python-mutagen
  python-ctypes libtunepimp5 python-tunepimp libgda3-bin libgda3-3 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gstreamer0.10-plugins-good (0.10.10.4-1ubuntu1.1) ...
/usr/share/gconf/schemas/gstreamer-0.10.schemas:1: parser error : Start tag expected, '<' not found
t
^
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gstreamer0.10-plugins-good
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-desktop:~$ 


 this is the error i get.

---

### Post by yeats on 2009-03-19
There is a dpkg.log (and archived logs dpkg.log.0, etc.) in /var/log.  Why don't you open the one called dpkg.log and post what is says here.  That may reveal what went wrong.

My other question would be, have you edited any configuration files of any kind recently?

---

### Post by sie.iris on 2009-03-19
I am a Linux newbie (4 days old) with two problems. Since yesterday I continue to get this message whenever trying to uninstall or install any program:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the download directory


This occurs whether I use the terminal or the Synaptic Package Manager. I managed to install Hardy Heron with no problems. Installed a number of windows programs using Wine; am now trying to dispose of 1Gb worth of mistaken installes, They will not delete from the trash.

And, now I cannot install any updates, and uninstall any program at all.

---

### Post by yeats on 2009-03-19
@sie.iris

This will happen if you try to use apt when another program is using it (i.e., the graphical Synaptic and Add/Remove programs).  Make sure the graphical apps are closed, then run from the terminal.  apt creates a lock file to prevent you from screwing up your system.

Oh - and if you need more - why not open a new thread?  It can get confusing to have more than one issue per thread :-).

---

### Post by imlinux on 2009-03-19
it will be very tedious for you to find error in this al tho i have tried to post the record till just before problem started 
```
2009-03-15 16:28:45 status installed man-db 2.5.2-2
2009-03-15 16:28:45 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-15 16:28:45 status half-configured menu 2.1.40ubuntu1
2009-03-15 16:28:47 status installed menu 2.1.40ubuntu1
2009-03-15 16:28:48 startup packages configure
2009-03-15 16:28:48 configure bluefish 1.0.7-5 1.0.7-5
2009-03-15 16:28:48 status unpacked bluefish 1.0.7-5
2009-03-15 16:28:48 status half-configured bluefish 1.0.7-5
2009-03-15 16:28:53 status installed bluefish 1.0.7-5
2009-03-15 16:28:53 status triggers-pending menu 2.1.40ubuntu1
2009-03-15 16:28:53 status triggers-awaited menu 2.1.40ubuntu1
2009-03-15 16:28:53 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-15 16:28:53 status half-configured menu 2.1.40ubuntu1
2009-03-15 16:28:54 status installed menu 2.1.40ubuntu1
2009-03-17 04:39:29 startup archives unpack
2009-03-17 04:39:51 install p7zip <none> 4.58~dfsg.1-1
2009-03-17 04:39:51 status half-installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:51 status triggers-pending man-db 2.5.2-2
2009-03-17 04:39:51 status half-installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 install p7zip-full <none> 4.58~dfsg.1-1
2009-03-17 04:39:52 status half-installed p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status half-installed p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:54 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 04:39:54 status half-configured man-db 2.5.2-2
2009-03-17 04:39:56 status installed man-db 2.5.2-2
2009-03-17 04:39:58 startup packages configure
2009-03-17 04:39:58 configure p7zip 4.58~dfsg.1-1 4.58~dfsg.1-1
2009-03-17 04:39:58 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 status half-configured p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 status installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 configure p7zip-full 4.58~dfsg.1-1 4.58~dfsg.1-1
2009-03-17 04:39:58 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:58 status half-configured p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:58 status installed p7zip-full 4.58~dfsg.1-1
2009-03-17 06:13:01 startup archives unpack
2009-03-17 06:13:21 upgrade libglib2.0-dev 2.18.2-0ubuntu2 2.18.2-0ubuntu2.1
2009-03-17 06:13:21 status half-configured libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:21 status unpacked libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:21 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:22 status triggers-pending man-db 2.5.2-2
2009-03-17 06:13:22 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:23 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:23 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:13:23 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:13:25 upgrade libglib2.0-0 2.18.2-0ubuntu2 2.18.2-0ubuntu2.1
2009-03-17 06:13:25 status half-configured libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:25 status unpacked libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:26 status half-installed libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:26 status half-installed libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:27 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:13:27 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:13:27 upgrade libgstreamer-plugins-base0.10-0 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:27 status half-configured libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:27 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status half-installed libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status half-installed libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 upgrade gstreamer0.10-alsa 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status half-configured gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 upgrade gstreamer0.10-gnomevfs 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status half-configured gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 upgrade gstreamer0.10-plugins-base 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status half-configured gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 upgrade gstreamer0.10-plugins-base-apps 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status half-configured gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:13:30 upgrade gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:30 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:44 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:45 status half-installed gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:46 status half-installed gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 upgrade gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 status half-configured gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:25:13 startup packages configure
2009-03-17 06:25:13 configure gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:13 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 status half-configured gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 status triggers-awaited gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 06:25:13 status half-configured man-db 2.5.2-2
2009-03-17 06:25:13 status installed gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed man-db 2.5.2-2
2009-03-17 06:25:16 configure libglib2.0-0 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2
2009-03-17 06:25:16 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status half-configured libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status installed libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-17 06:25:16 configure libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:16 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status half-configured libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 configure gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:16 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status half-configured gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 06:25:16 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:25:16 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:25:17 configure gstreamer0.10-alsa 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:17 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status half-configured gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status installed gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 configure libglib2.0-dev 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2
2009-03-17 06:25:17 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 status half-configured libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 status installed libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 configure gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:17 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status half-configured gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status installed gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-17 06:25:17 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-17 06:25:18 status installed libc6 2.8~20080505-0ubuntu9
2009-03-17 06:32:05 startup archives unpack
2009-03-17 06:32:26 upgrade gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:27 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:32:28 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:32:28 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:28 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:28 upgrade gnome-user-guide 2.24.0+svn20080922ubuntu1 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:28 status half-configured gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:28 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:28 status half-installed gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:44 status half-installed gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:48 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:50 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:51 upgrade gstreamer0.10-x 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:32:51 status half-configured gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:51 status unpacked gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:51 status half-installed gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:52 status half-installed gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:53 status unpacked gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:32:53 status unpacked gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:32:53 upgrade libavutil49 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:53 status half-configured libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:53 status unpacked libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:53 status half-installed libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status half-installed libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status unpacked libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 status unpacked libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 upgrade libavformat52 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 status half-configured libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status unpacked libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status half-installed libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:55 status half-installed libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:55 status unpacked libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:56 status unpacked libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:56 upgr
```

---

### Post by imlinux on 2009-03-19
it will be very tedious for you to find error in this al tho i have tried to post the record till just before problem started 
```
2009-03-15 16:28:45 status installed man-db 2.5.2-2
2009-03-15 16:28:45 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-15 16:28:45 status half-configured menu 2.1.40ubuntu1
2009-03-15 16:28:47 status installed menu 2.1.40ubuntu1
2009-03-15 16:28:48 startup packages configure
2009-03-15 16:28:48 configure bluefish 1.0.7-5 1.0.7-5
2009-03-15 16:28:48 status unpacked bluefish 1.0.7-5
2009-03-15 16:28:48 status half-configured bluefish 1.0.7-5
2009-03-15 16:28:53 status installed bluefish 1.0.7-5
2009-03-15 16:28:53 status triggers-pending menu 2.1.40ubuntu1
2009-03-15 16:28:53 status triggers-awaited menu 2.1.40ubuntu1
2009-03-15 16:28:53 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-15 16:28:53 status half-configured menu 2.1.40ubuntu1
2009-03-15 16:28:54 status installed menu 2.1.40ubuntu1
2009-03-17 04:39:29 startup archives unpack
2009-03-17 04:39:51 install p7zip <none> 4.58~dfsg.1-1
2009-03-17 04:39:51 status half-installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:51 status triggers-pending man-db 2.5.2-2
2009-03-17 04:39:51 status half-installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:52 install p7zip-full <none> 4.58~dfsg.1-1
2009-03-17 04:39:52 status half-installed p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status half-installed p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:53 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:54 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 04:39:54 status half-configured man-db 2.5.2-2
2009-03-17 04:39:56 status installed man-db 2.5.2-2
2009-03-17 04:39:58 startup packages configure
2009-03-17 04:39:58 configure p7zip 4.58~dfsg.1-1 4.58~dfsg.1-1
2009-03-17 04:39:58 status unpacked p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 status half-configured p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 status installed p7zip 4.58~dfsg.1-1
2009-03-17 04:39:58 configure p7zip-full 4.58~dfsg.1-1 4.58~dfsg.1-1
2009-03-17 04:39:58 status unpacked p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:58 status half-configured p7zip-full 4.58~dfsg.1-1
2009-03-17 04:39:58 status installed p7zip-full 4.58~dfsg.1-1
2009-03-17 06:13:01 startup archives unpack
2009-03-17 06:13:21 upgrade libglib2.0-dev 2.18.2-0ubuntu2 2.18.2-0ubuntu2.1
2009-03-17 06:13:21 status half-configured libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:21 status unpacked libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:21 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:22 status triggers-pending man-db 2.5.2-2
2009-03-17 06:13:22 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:23 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2009-03-17 06:13:23 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:13:23 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:13:25 upgrade libglib2.0-0 2.18.2-0ubuntu2 2.18.2-0ubuntu2.1
2009-03-17 06:13:25 status half-configured libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:25 status unpacked libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:26 status half-installed libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:26 status half-installed libglib2.0-0 2.18.2-0ubuntu2
2009-03-17 06:13:27 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:13:27 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:13:27 upgrade libgstreamer-plugins-base0.10-0 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:27 status half-configured libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:27 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status half-installed libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status half-installed libgstreamer-plugins-base0.10-0 0.10.21-3
2009-03-17 06:13:28 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 upgrade gstreamer0.10-alsa 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status half-configured gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-alsa 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 upgrade gstreamer0.10-gnomevfs 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:28 status half-configured gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:28 status unpacked gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:28 status half-installed gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-gnomevfs 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 upgrade gstreamer0.10-plugins-base 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status half-configured gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 upgrade gstreamer0.10-plugins-base-apps 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status half-configured gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status half-installed gstreamer0.10-plugins-base-apps 0.10.21-3
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:13:29 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:13:30 upgrade gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:30 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:44 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:45 status half-installed gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:46 status half-installed gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 upgrade gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:13:47 status half-configured gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:13:47 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:25:13 startup packages configure
2009-03-17 06:25:13 configure gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:13 status unpacked gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 status half-configured gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 status triggers-awaited gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:13 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 06:25:13 status half-configured man-db 2.5.2-2
2009-03-17 06:25:13 status installed gstreamer0.10-plugins-base-apps 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed man-db 2.5.2-2
2009-03-17 06:25:16 configure libglib2.0-0 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2
2009-03-17 06:25:16 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status half-configured libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status installed libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-17 06:25:16 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-17 06:25:16 configure libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:16 status unpacked libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status half-configured libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed libgstreamer-plugins-base0.10-0 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 configure gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:16 status unpacked gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status half-configured gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 status installed gstreamer0.10-plugins-base 0.10.21-3ubuntu0.1
2009-03-17 06:25:16 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 06:25:16 status unpacked gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:25:16 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:25:17 configure gstreamer0.10-alsa 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:17 status unpacked gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status half-configured gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status installed gstreamer0.10-alsa 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 configure libglib2.0-dev 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2
2009-03-17 06:25:17 status unpacked libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 status half-configured libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 status installed libglib2.0-dev 2.18.2-0ubuntu2.1
2009-03-17 06:25:17 configure gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1 0.10.21-3
2009-03-17 06:25:17 status unpacked gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status half-configured gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 status installed gstreamer0.10-gnomevfs 0.10.21-3ubuntu0.1
2009-03-17 06:25:17 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-17 06:25:17 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-17 06:25:18 status installed libc6 2.8~20080505-0ubuntu9
2009-03-17 06:32:05 startup archives unpack
2009-03-17 06:32:26 upgrade gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:27 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:32:28 status half-installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1
2009-03-17 06:32:28 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:28 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:32:28 upgrade gnome-user-guide 2.24.0+svn20080922ubuntu1 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:28 status half-configured gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:28 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:28 status half-installed gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:44 status half-installed gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-03-17 06:32:48 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:50 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:32:51 upgrade gstreamer0.10-x 0.10.21-3 0.10.21-3ubuntu0.1
2009-03-17 06:32:51 status half-configured gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:51 status unpacked gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:51 status half-installed gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:52 status half-installed gstreamer0.10-x 0.10.21-3
2009-03-17 06:32:53 status unpacked gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:32:53 status unpacked gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:32:53 upgrade libavutil49 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:53 status half-configured libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:53 status unpacked libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:53 status half-installed libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status half-installed libavutil49 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status unpacked libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 status unpacked libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 upgrade libavformat52 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:54 status half-configured libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status unpacked libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:54 status half-installed libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:55 status half-installed libavformat52 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:55 status unpacked libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:56 status unpacked libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:56 upgrade libglib2.0-data 2.18.2-0ubuntu2 2.18.2-0ubuntu2.1
2009-03-17 06:32:56 status half-configured libglib2.0-data 2.18.2-0ubuntu2
2009-03-17 06:32:56 status unpacked libglib2.0-data 2.18.2-0ubuntu2
2009-03-17 06:32:56 status half-installed libglib2.0-data 2.18.2-0ubuntu2
2009-03-17 06:32:56 status half-installed libglib2.0-data 2.18.2-0ubuntu2
2009-03-17 06:32:56 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-17 06:32:56 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-17 06:32:56 upgrade libpostproc51 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:56 status half-configured libpostproc51 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:56 status unpacked libpostproc51 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:56 status half-installed libpostproc51 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:56 status half-installed libpostproc51 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:57 status unpacked libpostproc51 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:57 status unpacked libpostproc51 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:57 upgrade libswscale0 3:0.svn20080206-12ubuntu3 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:57 status half-configured libswscale0 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:57 status unpacked libswscale0 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:57 status half-installed libswscale0 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:57 status half-installed libswscale0 3:0.svn20080206-12ubuntu3
2009-03-17 06:32:57 status unpacked libswscale0 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:57 status unpacked libswscale0 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:32:57 upgrade linux-libc-dev 2.6.27-13.29 2.6.27-14.30
2009-03-17 06:32:57 status half-configured linux-libc-dev 2.6.27-13.29
2009-03-17 06:32:57 status unpacked linux-libc-dev 2.6.27-13.29
2009-03-17 06:32:58 status half-installed linux-libc-dev 2.6.27-13.29
2009-03-17 06:32:59 status half-installed linux-libc-dev 2.6.27-13.29
2009-03-17 06:32:59 status unpacked linux-libc-dev 2.6.27-14.30
2009-03-17 06:32:59 status unpacked linux-libc-dev 2.6.27-14.30
2009-03-17 06:33:00 startup packages configure
2009-03-17 06:33:00 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 06:33:00 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 06:33:02 configure gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1.1
2009-03-17 06:33:02 status unpacked gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:33:02 status half-configured gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:33:02 status installed gstreamer0.10-pulseaudio 0.10.10.4-1ubuntu1.1
2009-03-17 06:33:03 configure gnome-user-guide 2.24.0+svn20080922ubuntu2 2.24.0+svn20080922ubuntu2
2009-03-17 06:33:03 status unpacked gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:33:03 status half-configured gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:33:03 status installed gnome-user-guide 2.24.0+svn20080922ubuntu2
2009-03-17 06:33:03 configure gstreamer0.10-x 0.10.21-3ubuntu0.1 0.10.21-3ubuntu0.1
2009-03-17 06:33:03 status unpacked gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:33:03 status half-configured gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:33:03 status installed gstreamer0.10-x 0.10.21-3ubuntu0.1
2009-03-17 06:33:03 configure libavutil49 3:0.svn20080206-12ubuntu3.1 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status unpacked libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status half-configured libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status installed libavutil49 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-17 06:33:03 configure libavformat52 3:0.svn20080206-12ubuntu3.1 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status unpacked libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status half-configured libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status installed libavformat52 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 configure libglib2.0-data 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2.1
2009-03-17 06:33:03 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-17 06:33:03 status half-configured libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-17 06:33:03 status installed libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-17 06:33:03 configure libpostproc51 3:0.svn20080206-12ubuntu3.1 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status unpacked libpostproc51 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:03 status half-configured libpostproc51 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 status installed libpostproc51 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 configure libswscale0 3:0.svn20080206-12ubuntu3.1 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 status unpacked libswscale0 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 status half-configured libswscale0 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 status installed libswscale0 3:0.svn20080206-12ubuntu3.1
2009-03-17 06:33:04 configure linux-libc-dev 2.6.27-14.30 2.6.27-14.30
2009-03-17 06:33:04 status unpacked linux-libc-dev 2.6.27-14.30
2009-03-17 06:33:04 status half-configured linux-libc-dev 2.6.27-14.30
2009-03-17 06:33:04 status installed linux-libc-dev 2.6.27-14.30
2009-03-17 06:33:04 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-17 06:33:04 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-17 06:33:05 status installed libc6 2.8~20080505-0ubuntu9
2009-03-17 06:35:58 startup packages configure
2009-03-17 06:35:58 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 06:35:58 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:35:48 startup archives unpack
2009-03-17 08:36:13 install acroread-debian-files <none> 0.0.24medibuntu1.1
2009-03-17 08:36:13 status half-installed acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:13 status triggers-pending menu 2.1.40ubuntu1
2009-03-17 08:36:13 status half-installed acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:13 status triggers-pending man-db 2.5.2-2
2009-03-17 08:36:13 status half-installed acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:13 status unpacked acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:13 status unpacked acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:13 install acroread <none> 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:13 status half-installed acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:23 status unpacked acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:23 status unpacked acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:23 install acroread-dictionary-de <none> 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:23 status half-installed acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:23 status unpacked acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:23 status unpacked acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:24 install acroread-dictionary-en <none> 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status half-installed acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status unpacked acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status unpacked acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 install acroread-escript <none> 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status half-installed acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status unpacked acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:24 status unpacked acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:25 install acroread-l10n-de <none> 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:25 status half-installed acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:25 status unpacked acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:25 status unpacked acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:25 install acroread-plugins <none> 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:25 status half-installed acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 status unpacked acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 status unpacked acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 install acroread-plugin-speech <none> 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 status half-installed acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 status unpacked acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 status unpacked acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:30 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-17 08:36:30 status half-configured menu 2.1.40ubuntu1
2009-03-17 08:36:33 status installed menu 2.1.40ubuntu1
2009-03-17 08:36:33 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 08:36:33 status half-configured man-db 2.5.2-2
2009-03-17 08:36:36 status installed man-db 2.5.2-2
2009-03-17 08:36:37 startup packages configure
2009-03-17 08:36:37 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:36:37 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:36:39 configure acroread 8.1.3-0medibuntu0.8.10.2 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:39 status unpacked acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:39 status half-configured acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:49 status installed acroread 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 configure acroread-debian-files 0.0.24medibuntu1.1 0.0.24medibuntu1.1
2009-03-17 08:36:50 status unpacked acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:50 status half-configured acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:50 status installed acroread-debian-files 0.0.24medibuntu1.1
2009-03-17 08:36:50 status triggers-pending menu 2.1.40ubuntu1
2009-03-17 08:36:50 status triggers-awaited menu 2.1.40ubuntu1
2009-03-17 08:36:50 configure acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status unpacked acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status half-configured acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status installed acroread-dictionary-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 configure acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status unpacked acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status half-configured acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status installed acroread-dictionary-en 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 configure acroread-escript 8.1.3-0medibuntu0.8.10.2 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status unpacked acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status half-configured acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status installed acroread-escript 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 configure acroread-l10n-de 8.1.3-0medibuntu0.8.10.1 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status unpacked acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status half-configured acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 status installed acroread-l10n-de 8.1.3-0medibuntu0.8.10.1
2009-03-17 08:36:50 configure acroread-plugins 8.1.3-0medibuntu0.8.10.2 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status unpacked acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status half-configured acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status installed acroread-plugins 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 configure acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status unpacked acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status half-configured acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 status installed acroread-plugin-speech 8.1.3-0medibuntu0.8.10.2
2009-03-17 08:36:50 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-17 08:36:50 status half-configured menu 2.1.40ubuntu1
2009-03-17 08:36:51 status installed menu 2.1.40ubuntu1
2009-03-17 08:37:17 startup packages configure
2009-03-17 08:37:17 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:37:17 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:11 startup archives unpack
2009-03-17 08:44:33 install gstreamer0.10-esd <none> 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:33 status half-installed gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:34 status unpacked gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:34 status unpacked gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:34 install gstreamer0.10-plugins-good-dbg <none> 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:34 status half-installed gstreamer0.10-plugins-good-dbg 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:35 status unpacked gstreamer0.10-plugins-good-dbg 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:35 status unpacked gstreamer0.10-plugins-good-dbg 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:36 startup packages configure
2009-03-17 08:44:36 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:44:36 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:36 configure gstreamer0.10-esd 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:36 status unpacked gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:37 status half-configured gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:44:37 status installed gstreamer0.10-esd 0.10.10.4-1ubuntu1.1
2009-03-17 08:45:00 startup packages configure
2009-03-17 08:45:00 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:45:00 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:47:54 startup archives unpack
2009-03-17 08:48:16 install deborphan <none> 1.7.26
2009-03-17 08:48:16 status half-installed deborphan 1.7.26
2009-03-17 08:48:16 status triggers-pending man-db 2.5.2-2
2009-03-17 08:48:16 status half-installed deborphan 1.7.26
2009-03-17 08:48:16 status triggers-pending menu 2.1.40ubuntu1
2009-03-17 08:48:16 status half-installed deborphan 1.7.26
2009-03-17 08:48:17 status unpacked deborphan 1.7.26
2009-03-17 08:48:17 status unpacked deborphan 1.7.26
2009-03-17 08:48:17 install dialog <none> 1.1-20080316-1
2009-03-17 08:48:17 status half-installed dialog 1.1-20080316-1
2009-03-17 08:48:17 status half-installed dialog 1.1-20080316-1
2009-03-17 08:48:18 status unpacked dialog 1.1-20080316-1
2009-03-17 08:48:18 status unpacked dialog 1.1-20080316-1
2009-03-17 08:48:18 install gtkorphan <none> 0.4.4-1
2009-03-17 08:48:18 status half-installed gtkorphan 0.4.4-1
2009-03-17 08:48:18 status half-installed gtkorphan 0.4.4-1
2009-03-17 08:48:18 status unpacked gtkorphan 0.4.4-1
2009-03-17 08:48:18 status unpacked gtkorphan 0.4.4-1
2009-03-17 08:48:18 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-17 08:48:18 status half-configured man-db 2.5.2-2
2009-03-17 08:48:22 status installed man-db 2.5.2-2
2009-03-17 08:48:22 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-17 08:48:22 status half-configured menu 2.1.40ubuntu1
2009-03-17 08:48:24 status installed menu 2.1.40ubuntu1
2009-03-17 08:48:25 startup packages configure
2009-03-17 08:48:25 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:48:25 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:48:25 configure deborphan 1.7.26 1.7.26
2009-03-17 08:48:25 status unpacked deborphan 1.7.26
2009-03-17 08:48:26 status unpacked deborphan 1.7.26
2009-03-17 08:48:26 status half-configured deborphan 1.7.26
2009-03-17 08:48:26 status installed deborphan 1.7.26
2009-03-17 08:48:26 status triggers-pending menu 2.1.40ubuntu1
2009-03-17 08:48:26 status triggers-awaited menu 2.1.40ubuntu1
2009-03-17 08:48:26 configure dialog 1.1-20080316-1 1.1-20080316-1
2009-03-17 08:48:26 status unpacked dialog 1.1-20080316-1
2009-03-17 08:48:26 status half-configured dialog 1.1-20080316-1
2009-03-17 08:48:26 status installed dialog 1.1-20080316-1
2009-03-17 08:48:26 trigproc menu 2.1.40ubuntu1 2.1.40ubuntu1
2009-03-17 08:48:26 status half-configured menu 2.1.40ubuntu1
2009-03-17 08:48:27 status installed menu 2.1.40ubuntu1
2009-03-17 08:48:27 configure gtkorphan 0.4.4-1 0.4.4-1
2009-03-17 08:48:27 status unpacked gtkorphan 0.4.4-1
2009-03-17 08:48:27 status half-configured gtkorphan 0.4.4-1
2009-03-17 08:48:27 status installed gtkorphan 0.4.4-1
2009-03-17 08:48:51 startup packages configure
2009-03-17 08:48:51 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:48:51 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 08:56:07 startup packages configure
2009-03-17 08:56:07 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 08:56:07 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 09:04:18 startup packages configure
2009-03-17 09:04:18 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 09:04:18 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-17 09:05:17 startup packages configure
2009-03-17 09:05:17 configure gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1 0.10.10.4-1ubuntu1
2009-03-17 09:05:17 status half-configured gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1.1
2009-03-18 04:04:30 startup archives unpack
2009-03-18 04:04:52 install chromium-browser <none> 2.0.171.0~svn20090317r11882-0ubuntu1~ucd2~intrepid
2009-03-18 04:04:52 status half-installed chromium-browser 2.0.171.0~svn20090317r11882-0ubuntu1~ucd

```

---

### Post by tarps87 on 2009-03-19
Try moving the corrupted file and run the fix command again.
```
sudo mv /usr/share/gconf/schemas/gstreamer-0.10.schemas /usr/share/gconf/schemas/gstreamer-0.10.schemas.bck
```
If this works you can remove the old schema files:
```
sudo rm /usr/share/gconf/schemas/gstreamer-0.10.schemas.bck
```
The fix command should recreate the file.

> **sie.iris said:**
> I am a Linux newbie (4 days old) with two problems. Since yesterday I continue to get this message whenever trying to uninstall or install any program:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the download directory


This occurs whether I use the terminal or the Synaptic Package Manager. I managed to install Hardy Heron with no problems. Installed a number of windows programs using Wine; am now trying to dispose of 1Gb worth of mistaken installes, They will not delete from the trash.

And, now I cannot install any updates, and uninstall any program at all.

If you are sure the are not apt processes running you can delete the lock file.
```
sudo rm /var/cache/apt/archives/lock
```

Please start a new thread with if you have any other questions

---

### Post by yeats on 2009-03-19
Forum Tip:  if you use CODE tags (click the # symbol in the menu while composing a post), it will create a scrollable window for such output :-).

---

### Post by imlinux on 2009-03-19
oh yes i tried removing that gstreamer-0.10.schemas before you,then tried removing gstreamer-0.10 forcefully ,still it didn't worked.anyways i will be removing complete ubuntu  install and replace it with jaunty backing up configurations in home and etc directories,just tell me if this problem is going to presist if i install old configuration in new install.

---

### Post by imlinux on 2009-03-19
oh thank you , i am sorry for selecting quote option.

---

### Post by overdrank on 2009-03-19
My apologies to imlinux as some of the data was lost when I was editing for the code tags

---

### Post by tarps87 on 2009-03-19
> **imlinux said:**
> oh yes i tried removing that gstreamer-0.10.schemas before you,then tried removing gstreamer-0.10 forcefully ,still it didn't worked.anyways i will be removing complete ubuntu  install and replace it with jaunty backing up configurations in home and etc directories,just tell me if this problem is going to presist if i install old configuration in new install.

The problem file is in /usr so reinstalling will solve the problem. Although assuming you are currently using Intrepid (8.10) there is no guaranty that all the configuration file will work in Jaunty, also Jaunty is still in it alpha stage so not recommended if you are looking for a stable release.

---

### Post by imlinux on 2009-03-19
its okay no worries,thanks for editing.

---

### Post by imlinux on 2009-03-19
> **tarps87 said:**
> The problem file is in /usr so reinstalling will solve the problem. Although assuming you are currently using Intrepid (8.10) there is no guaranty that all the configuration file will work in Jaunty, also Jaunty is still in it alpha stage so not recommended if you are looking for a stable release.
 oh thank you i shall take that note,thanks for spending your time with my problem.

---

