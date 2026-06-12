---
title: "Weird Synaptic Problem"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by perito on 2009-11-09
I tried and successfully installed MP3splt-gtk. It works perfectly, but after the installation, I got a weird error sign on the task bar. (Image attached).

Now I can't install anything, I got the following:

> 
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mp3splt-gtk: Depends: libmp3splt0 (>= 0.5.6) but it is not going to be installed
               Depends: libmp3splt0 (< 0.5.7~) but it is not going to be installed
               Depends: libmp3splt-mp3 but it is not going to be installed or
                        libmp3splt-plugin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ubuntu@ubuntu-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmp3splt-mp3 libmp3splt-ogg libmp3splt0
Suggested packages:
  mp3splt
The following NEW packages will be installed:
  libmp3splt-mp3 libmp3splt-ogg libmp3splt0
0 upgraded, 3 newly installed, 0 to remove and 36 not upgraded.
1 not fully installed or removed.
Need to get 0B/101kB of archives.
After this operation, 352kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 116020 files and directories currently installed.)
Unpacking libmp3splt0 (from .../libmp3splt0_0.5.6-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmp3splt0_0.5.6-1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmp3splt.so.0.0.5', which is also in package libmp3splt1 0:0.5.6-1~getdeb1
Unpacking libmp3splt-mp3 (from .../libmp3splt-mp3_0.5.6-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmp3splt-mp3_0.5.6-1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmp3splt/libsplt_mp3.so.0.0.0', which is also in package libmp3splt1 0:0.5.6-1~getdeb1
Unpacking libmp3splt-ogg (from .../libmp3splt-ogg_0.5.6-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmp3splt-ogg_0.5.6-1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmp3splt/libsplt_ogg.so.0.0.0', which is also in package libmp3splt1 0:0.5.6-1~getdeb1
Errors were encountered while processing:
 /var/cache/apt/archives/libmp3splt0_0.5.6-1_i386.deb
 /var/cache/apt/archives/libmp3splt-mp3_0.5.6-1_i386.deb
 /var/cache/apt/archives/libmp3splt-ogg_0.5.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu-laptop:~$ 



what can I do to solve this problem?

---

### Post by MelDJ on 2009-11-09
go to synaptic click edit and select fix broken packages and try again

---

### Post by perito on 2009-11-09
Still not working (image attached)

---

### Post by onyxwolf on 2009-11-09
Did you try what it instructed-- sudo apt-get install -f
? This should fix it.

---

### Post by onyxwolf on 2009-11-09
Sorry I see you did after I took a second to actually look at your output. 

My bad ](*,)

---

### Post by onyxwolf on 2009-11-09
Ok try to completely uninstall the packages libmp3splt-mp3, libmp3splt-ogg, libmp3splt0, mp3split-gtk, libmp3splt-plugin, and mp3split thru synaptic (click on the box of the ones that are showing that they are currently installed and select mark for complete removal), click apply. If that uninstalls them try using synaptic to select those packages to install (starting with the primary, which should automatically mark all dependencies, but double-check that it does).

---

