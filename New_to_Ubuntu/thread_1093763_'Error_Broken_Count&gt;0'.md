---
title: "'Error: Broken Count&gt;0'"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by mkapadia13 on 2009-03-11
I am getting an error when I try to install something.  On the top right I have a red arrow with an ! in the middle which states: 

'An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was:  'Error:  BrokenCount>0'  This usually means that your installed packages have unmet dependencies.'

I typed 'apt-get' in the terminal window and then typed 'apt-get install' which came back with:

'E:  Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
 E:  Unable to lock the administration directory (/var/lib/dpkg/), are you root?'

When I go to Package Manager and try to install updates I get an 'Unable to get exclusive lock'

I'm not sure what any of this means, as I am a new Ubuntu user, so I really appreciate your help.

Thanks.

---

### Post by iaculallad on 2009-03-11
Make sure you're not running other dpkg instances. Close all running installation processes then retry your installation.

On your terminal, issue the command below to view your current dpkg process:

```
ps aux | grep dpkg
```

EDIT:

And use the command below to kill the process:

```
sudo kill -9 PID
```

---

### Post by mkapadia13 on 2009-03-11
Thanks for your help.  This is what I got.......can you help me decipher this?

mizzle@mizzle:~$ ps aux | grep dpkg
root      6199  0.0  0.6  25288 22712 pts/2    Ss+  21:15   0:00 /usr/bin/dpkg --status-fd 20 --unpack --auto-deconfigure /var/cache/apt/archives/java-common_0.30ubuntu3_all.deb /var/cache/apt/archives/sun-java6-jre_6-10-0ubuntu2_all.deb /var/cache/apt/archives/odbcinst1debian1_2.2.11-16build2_i386.deb /var/cache/apt/archives/unixodbc_2.2.11-16build2_i386.deb /var/cache/apt/archives/sun-java6-bin_6-10-0ubuntu2_i386.deb /var/cache/apt/archives/xutils-dev_1%3a7.4+3_i386.deb /var/cache/apt/archives/cabextract_1.2-3_i386.deb /var/cache/apt/archives/freepats_20060219-1_all.deb /var/cache/apt/archives/gsfonts-x11_0.20ubuntu1_all.deb /var/cache/apt/archives/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb /var/cache/apt/archives/libcdaudio1_0.99.12p2-5_i386.deb /var/cache/apt/archives/libdc1394-22_2.0.2-1_i386.deb /var/cache/apt/archives/libfaad0_2.6.1-3.1_i386.deb /var/cache/apt/archives/mysql-common_5.0.67-0ubuntu6_all.deb /var/cache/apt/archives/libmysqlclient15off_5.0.67-0ubuntu6_i386.deb /var/cache/apt/archives/libgmyth0_1%3a0.7.1-1_i386.deb /var/cache/apt/archives/libiptcdata0_1.0.2+libtool01-2_i386.deb /var/cache/apt/archives/libfreebob0_1.0.11-0ubuntu1_i386.deb /var/cache/apt/archives/libjack0_0.109.2-3ubuntu1_i386.deb /var/cache/apt/archives/libmms0_0.4-2_i386.deb /var/cache/apt/archives/libmpcdec3_1.2.2-1build1_i386.deb /var/cache/apt/archives/libneon27-gnutls_0.28.2-2build1_i386.deb /var/cache/apt/archives/libfftw3-3_3.1.2-3.1ubuntu1_i386.deb /var/cache/apt/archives/libofa0_0.9.3-3_i386.deb /var/cache/apt/archives/libopenspc0_0.3.99a-2_i386.deb /var/cache/apt/archives/libsoundtouch1c2_1.3.1-2_i386.deb /var/cache/apt/archives/libwildmidi0_0.2.2-2_i386.deb /var/cache/apt/archives/gstreamer0.10-plugins-bad_0.10.8-1_i386.deb /var/cache/apt/archives/libfaac0_1.26-0.1ubuntu2_i386.deb /var/cache/apt/archives/libmp3lame0_3.98-0.0_i386.deb /var/cache/apt/archives/libx264-59_1%3a0.svn20080408-0.0ubuntu1_i386.deb /var/cache/apt/archives/libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb /var/cache/apt/archives/libavcodec-unstripped-51_3%3a0.svn20080206-12ubuntu3+unstripped5_i386.deb /var/cache/apt/archives/libswscale0_3%3a0.svn20080206-12ubuntu3_i386.deb /var/cache/apt/archives/libquicktime1_2%3a1.0.2+debian-2build2_i386.deb /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb /var/cache/apt/archives/gstreamer0.10-plugins-bad-multiverse_0.10.6-1ubuntu1_i386.deb /var/cache/apt/archives/gstreamer0.10-plugins-ugly-multiverse_0.10.7-2_i386.deb /var/cache/apt/archives/msttcorefonts_2.5_all.deb /var/cache/apt/archives/sun-java6-plugin_6-10-0ubuntu2_i386.deb /var/cache/apt/archives/ubuntu-restricted-extras_25_i386.deb /var/cache/apt/archives/unrar_1%3a3.8.2-1_i386.deb
root      6214  0.0  0.2  11368  8500 pts/2    S+   21:15   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst install
root      6221  0.0  0.0   1844   524 pts/2    S+   21:15   0:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst install
mizzle    6885  0.0  0.0   3240   808 pts/1    S+   23:06   0:00 grep dpkg
mizzle@mizzle:~$ sudo kill -9 PID
[sudo] password for mizzle: 
ERROR: garbage process ID "PID".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.

---

### Post by iaculallad on 2009-03-11
Ok, try killing the process with PID number: 6214 & 6221

> PID = Process ID

```
sudo kill -9 6214
sudo kill -9 6221

```

Afterwards, try reinstalling your application.

---

### Post by mkapadia13 on 2009-03-11
Thanks.

I killed the first one and I got a crash report.  I tried the second one and it said no such process.

I still can't install the updates...

---

### Post by pastalavista on 2009-03-11
In terminal try ```
sudo aptitude --full-resolver
``` and then try and install your app again

---

### Post by mkapadia13 on 2009-03-12
I get a big msg in red with the 2 errors I posted in my first thread.

I hit Ok, and it doesn't let me install anything.:(

---

### Post by bapoumba on 2009-03-12
Regarding the first error in the OP: System > Administration > Synaptic
You probably have broken packages. Find them and try to remove them.

---

### Post by mkapadia13 on 2009-03-13
So after restarting my machine the downloads are working??

But now I get this error as something was installing:

E: /var/cache/apt/archives/sun-java6-jre_6-10-0ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1

---

### Post by mkapadia13 on 2009-03-14
I restarted my computer, and it let me get into the Synaptic Manager (which it wasn't letting me see before).  I erased all my broken packages and things seem to be working fine.

Thanks for all the help.

---

