---
title: "So whats going on with my gnome?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by tophatandy on 2009-10-04
So i just got done installing all my codecs to get media working properly, restart ubuntu, and my desktop manager went to the default theme (using ubuntu 9.04 btw), my volume app won't load and when i try to pull up appearances it gives me this in an error box ```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

any ideas to get everything back to normal?

---

### Post by tophatandy on 2009-10-04
anyone?

---

### Post by Junkieman on 2009-10-04
Wow I've never seen that one before. [Here's an older thread]("http://ubuntuforums.org/showthread.php?t=579167") detailing the same issue.

Try selecting Gnome as your login session on the login screen, and make it your default.

Edit: This error seems to have happened in earlier releases ([this thread]("http://ubuntuforums.org/showthread.php?t=955679")), you could try those solutions however I'm not sure how relevant they still are.

---

### Post by ankspo71 on 2009-10-04
Hi I am no way considered an expert in linux, but it looks as if gnome-settings-daemon crashed on startup. Try logging out and back in, or run 
```
gnome-settings-daemon
``` from the terminal and see if your theme is restored. You might need to run ```
sudo killall gnome-settings-daemon
``` first if it is already running, but not functioning properly.

I just killed gnome-settings-daemon in ubuntu Karmic beta (9.10) on purpose and then restarted it to see if it would restore my default human theme... and it did.

Once I restarted gnome-settings-daemon I got the following error:
> (gnome-settings-daemon:2159): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed I think it's because this is a beta version of Ubuntu though, but it still restored my theme.
James.

PS. I am assuming you have no kde packages, or other desktop environments installed.

---

### Post by tophatandy on 2009-10-04
> **ankspo71 said:**
> Hi I am no way considered an expert in linux, but it looks as if gnome-settings-daemon crashed on startup. Try logging out and back in, or run 
```
gnome-settings-daemon
``` from the terminal and see if your theme is restored. You might need to run ```
sudo killall gnome-settings-daemon
``` first if it is already running, but not functioning properly.

I just killed gnome-settings-daemon in ubuntu Karmic beta (9.10) on purpose and then restarted it to see if it would restore my default human theme... and it did.

Once I restarted gnome-settings-daemon I got the following error:
 I think it's because this is a beta version of Ubuntu though, but it still restored my theme.
James.

PS. I am assuming you have no kde packages, or other desktop environments installed.

I ran ```
sudo killall gnome-settings-daemon
``` and it returned
```
 gnome-settings-daemon: no process killed
```

so then i ran ```
 gnome-settings-daemon 
```
and it returned 
```
 (gnome-settings-daemon:3498): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3498): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

```
and this lead to no change in anything graphically.

and i never purposefully tried to install any other desktop environments, but only scanned through the code i was typing in to update the codecs, it was code i got from the forums. how would i check to make sure i don't have kde or something installed?

ps: Thank you for the replies. the help is much appreciated. =]

---

### Post by ankspo71 on 2009-10-04
Hi,

Was the code this?
```
sudo apt-get install ubuntu-restricted-extras
```

If it was, then it didn't install anything that would have interfered with the gnome desktop. 

To check your apt-get history try this code:
```
grep install /var/log/dpkg.log
```
(you can do the same with 'remove' and 'purge' in place of 'install' to see what was removed too)

Or look in the 'log file viewer' under the catagory dpkg.log 

If you installed through Synaptic Package Manager there is a history function located in the menu to see what was installed through synaptic.

Have you tried to create a new user and log into that account? If you can log into another account and the themes are working in that account, then possibly a configuration file in your home/username/ directory might have been damaged or deleted.
James

---

### Post by tophatandy on 2009-10-04
> **ankspo71 said:**
> Hi,

Was the code this?
```
sudo apt-get install ubuntu-restricted-extras
```



nope, i was following a guide on the multimedia forum. I plugged in the code to look through the log file, I saw nothing that was kde related, but the list is pretty big. I see lots of "half installs".

here is the list:
```
2009-10-04 00:21:41 install libcurl3 <none> 7.18.2-8ubuntu4.1
2009-10-04 00:21:41 status half-installed libcurl3 7.18.2-8ubuntu4.1
2009-10-04 00:21:42 install libnspr4-dev <none> 4.7.5-0ubuntu0.9.04.1
2009-10-04 00:21:42 status half-installed libnspr4-dev 4.7.5-0ubuntu0.9.04.1
2009-10-04 00:21:42 install libnss3-dev <none> 3.12.3.1-0ubuntu0.9.04.2
2009-10-04 00:21:42 status half-installed libnss3-dev 3.12.3.1-0ubuntu0.9.04.2
2009-10-04 00:21:43 status installed libcurl3 7.18.2-8ubuntu4.1
2009-10-04 00:21:43 status installed libnspr4-dev 4.7.5-0ubuntu0.9.04.1
2009-10-04 00:21:43 status installed libnss3-dev 3.12.3.1-0ubuntu0.9.04.2
2009-10-04 00:21:44 status installed libc6 2.9-4ubuntu6.1
2009-10-04 00:21:45 startup archives install
2009-10-04 00:21:45 install adobe-flashplugin <none> 10.0.32.18-1
2009-10-04 00:21:45 status half-installed adobe-flashplugin 10.0.32.18-1
2009-10-04 00:21:47 status installed adobe-flashplugin 10.0.32.18-1
2009-10-04 01:43:59 install ttf-wqy-zenhei <none> 0.8.34-cvs20081027-0ubuntu1
2009-10-04 01:43:59 status half-installed ttf-wqy-zenhei 0.8.34-cvs20081027-0ubuntu1
2009-10-04 01:44:02 install libboost-iostreams1.37.0 <none> 1.37.0-3ubuntu3
2009-10-04 01:44:02 status half-installed libboost-iostreams1.37.0 1.37.0-3ubuntu3
2009-10-04 01:44:02 install libboost-regex1.37.0 <none> 1.37.0-3ubuntu3
2009-10-04 01:44:02 status half-installed libboost-regex1.37.0 1.37.0-3ubuntu3
2009-10-04 01:44:02 install libmikmod2 <none> 3.1.11-a-6ubuntu3
2009-10-04 01:44:02 status half-installed libmikmod2 3.1.11-a-6ubuntu3
2009-10-04 01:44:02 install libsdl-image1.2 <none> 1.2.6-3
2009-10-04 01:44:02 status half-installed libsdl-image1.2 1.2.6-3
2009-10-04 01:44:02 install libsmpeg0 <none> 0.4.5+cvs20030824-2.2
2009-10-04 01:44:02 status half-installed libsmpeg0 0.4.5+cvs20030824-2.2
2009-10-04 01:44:03 install libsdl-mixer1.2 <none> 1.2.8-5
2009-10-04 01:44:03 status half-installed libsdl-mixer1.2 1.2.8-5
2009-10-04 01:44:03 install libsdl-net1.2 <none> 1.2.7-2
2009-10-04 01:44:03 status half-installed libsdl-net1.2 1.2.7-2
2009-10-04 01:44:03 install libsdl-ttf2.0-0 <none> 2.0.9-1
2009-10-04 01:44:03 status half-installed libsdl-ttf2.0-0 2.0.9-1
2009-10-04 01:44:03 install ttf-dejavu-extra <none> 2.28-1
2009-10-04 01:44:03 status half-installed ttf-dejavu-extra 2.28-1
2009-10-04 01:44:04 install ttf-dejavu <none> 2.28-1
2009-10-04 01:44:04 status half-installed ttf-dejavu 2.28-1
2009-10-04 01:44:04 install wesnoth-data <none> 1:1.6a-3ubuntu1
2009-10-04 01:44:04 status half-installed wesnoth-data 1:1.6a-3ubuntu1
2009-10-04 01:44:21 status half-installed wesnoth-data 1:1.6a-3ubuntu1
2009-10-04 01:44:21 install wesnoth-core <none> 1:1.6a-3ubuntu1
2009-10-04 01:44:21 status half-installed wesnoth-core 1:1.6a-3ubuntu1
2009-10-04 01:44:23 status half-installed wesnoth-core 1:1.6a-3ubuntu1
2009-10-04 01:44:24 install wesnoth-httt <none> 1:1.6a-3ubuntu1
2009-10-04 01:44:24 status half-installed wesnoth-httt 1:1.6a-3ubuntu1
2009-10-04 01:44:26 install wesnoth-tsg <none> 1:1.6a-3ubuntu1
2009-10-04 01:44:26 status half-installed wesnoth-tsg 1:1.6a-3ubuntu1
2009-10-04 01:44:26 install wesnoth-ttb <none> 1:1.6a-3ubuntu1
2009-10-04 01:44:26 status half-installed wesnoth-ttb 1:1.6a-3ubuntu1
2009-10-04 01:44:28 status installed doc-base 0.8.20
2009-10-04 01:44:29 status installed man-db 2.5.5-1build1
2009-10-04 01:45:03 status installed ttf-wqy-zenhei 0.8.34-cvs20081027-0ubuntu1
2009-10-04 01:45:03 status installed libboost-iostreams1.37.0 1.37.0-3ubuntu3
2009-10-04 01:45:03 status installed libboost-regex1.37.0 1.37.0-3ubuntu3
2009-10-04 01:45:03 status installed libmikmod2 3.1.11-a-6ubuntu3
2009-10-04 01:45:04 status installed libsdl-image1.2 1.2.6-3
2009-10-04 01:45:04 status installed libsmpeg0 0.4.5+cvs20030824-2.2
2009-10-04 01:45:04 status installed libsdl-mixer1.2 1.2.8-5
2009-10-04 01:45:04 status installed libsdl-net1.2 1.2.7-2
2009-10-04 01:45:04 status installed libsdl-ttf2.0-0 2.0.9-1
2009-10-04 01:45:20 status installed ttf-dejavu-extra 2.28-1
2009-10-04 01:45:21 status installed ttf-dejavu 2.28-1
2009-10-04 01:45:21 status installed wesnoth-data 1:1.6a-3ubuntu1
2009-10-04 01:45:21 status installed wesnoth-core 1:1.6a-3ubuntu1
2009-10-04 01:45:21 status installed wesnoth-httt 1:1.6a-3ubuntu1
2009-10-04 01:45:21 status installed wesnoth-tsg 1:1.6a-3ubuntu1
2009-10-04 01:45:21 status installed wesnoth-ttb 1:1.6a-3ubuntu1
2009-10-04 01:45:22 status installed libc6 2.9-4ubuntu6.1
2009-10-04 13:30:53 install medibuntu-keyring <none> 2008.04.20
2009-10-04 13:30:53 status half-installed medibuntu-keyring 2008.04.20
2009-10-04 13:30:54 status installed medibuntu-keyring 2008.04.20
2009-10-04 13:52:19 install java-common <none> 0.30ubuntu4
2009-10-04 13:52:19 status half-installed java-common 0.30ubuntu4
2009-10-04 13:52:19 status half-installed java-common 0.30ubuntu4
2009-10-04 13:52:19 status half-installed java-common 0.30ubuntu4
2009-10-04 13:52:20 install sun-java6-jre <none> 6-16-0ubuntu1.9.04
2009-10-04 13:52:20 status half-installed sun-java6-jre 6-16-0ubuntu1.9.04
2009-10-04 13:53:19 status half-installed sun-java6-jre 6-16-0ubuntu1.9.04
2009-10-04 13:53:19 install odbcinst1debian1 <none> 2.2.11-16build3
2009-10-04 13:53:19 status half-installed odbcinst1debian1 2.2.11-16build3
2009-10-04 13:53:19 status half-installed odbcinst1debian1 2.2.11-16build3
2009-10-04 13:53:19 install unixodbc <none> 2.2.11-16build3
2009-10-04 13:53:19 status half-installed unixodbc 2.2.11-16build3
2009-10-04 13:53:19 status half-installed unixodbc 2.2.11-16build3
2009-10-04 13:53:19 install sun-java6-bin <none> 6-16-0ubuntu1.9.04
2009-10-04 13:53:19 status half-installed sun-java6-bin 6-16-0ubuntu1.9.04
2009-10-04 13:53:27 install alsa-oss <none> 1.0.17-1
2009-10-04 13:53:27 status half-installed alsa-oss 1.0.17-1
2009-10-04 13:53:27 status half-installed alsa-oss 1.0.17-1
2009-10-04 13:53:27 install cabextract <none> 1.2-3
2009-10-04 13:53:27 status half-installed cabextract 1.2-3
2009-10-04 13:53:27 status half-installed cabextract 1.2-3
2009-10-04 13:53:27 install libfaac0 <none> 1.26-0.1ubuntu2
2009-10-04 13:53:27 status half-installed libfaac0 1.26-0.1ubuntu2
2009-10-04 13:53:28 install libmp4v2-0 <none> 1:1.6dfsg-0.2ubuntu4
2009-10-04 13:53:28 status half-installed libmp4v2-0 1:1.6dfsg-0.2ubuntu4
2009-10-04 13:53:28 install faac <none> 1.26-0.1ubuntu2
2009-10-04 13:53:28 status half-installed faac 1.26-0.1ubuntu2
2009-10-04 13:53:28 status half-installed faac 1.26-0.1ubuntu2
2009-10-04 13:53:28 install libfaad0 <none> 2.6.1-3.1
2009-10-04 13:53:28 status half-installed libfaad0 2.6.1-3.1
2009-10-04 13:53:28 install faad <none> 2.6.1-3.1
2009-10-04 13:53:28 status half-installed faad 2.6.1-3.1
2009-10-04 13:53:28 status half-installed faad 2.6.1-3.1
2009-10-04 13:53:28 install flashplugin-installer <none> 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:28 status half-installed flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:28 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:28 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:29 install flashplugin-nonfree <none> 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:29 status half-installed flashplugin-nonfree 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:53:29 install freepats <none> 20060219-1
2009-10-04 13:53:29 status half-installed freepats 20060219-1
2009-10-04 13:53:32 install gsfonts-x11 <none> 0.21
2009-10-04 13:53:32 status half-installed gsfonts-x11 0.21
2009-10-04 13:53:32 install libavutil-unstripped-49 <none> 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:53:32 status half-installed libavutil-unstripped-49 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:53:32 install libmp3lame0 <none> 3.98-0.0
2009-10-04 13:53:32 status half-installed libmp3lame0 3.98-0.0
2009-10-04 13:53:32 install libx264-65 <none> 1:0.svn20081230-0.0ubuntu1
2009-10-04 13:53:32 status half-installed libx264-65 1:0.svn20081230-0.0ubuntu1
2009-10-04 13:53:32 install libxvidcore4 <none> 2:1.1.2-0.1ubuntu3
2009-10-04 13:53:32 status half-installed libxvidcore4 2:1.1.2-0.1ubuntu3
2009-10-04 13:53:33 install libavcodec-unstripped-52 <none> 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:53:33 status half-installed libavcodec-unstripped-52 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:53:33 install libavformat52 <none> 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:33 status half-installed libavformat52 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:34 install libpostproc51 <none> 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:34 status half-installed libpostproc51 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:34 install libswscale0 <none> 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:34 status half-installed libswscale0 3:0.svn20090303-1ubuntu6
2009-10-04 13:53:34 install gstreamer0.10-ffmpeg <none> 0.10.6.2-1ubuntu2
2009-10-04 13:53:34 status half-installed gstreamer0.10-ffmpeg 0.10.6.2-1ubuntu2
2009-10-04 13:53:34 install gstreamer0.10-pitfdll <none> 0.9.1.1+cvs20080215-1ubuntu1
2009-10-04 13:53:34 status half-installed gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2009-10-04 13:53:34 install libenca0 <none> 1.9-6
2009-10-04 13:53:34 status half-installed libenca0 1.9-6
2009-10-04 13:53:35 install libass1 <none> 0.9.5-2
2009-10-04 13:53:35 status half-installed libass1 0.9.5-2
2009-10-04 13:53:35 install libcdaudio1 <none> 0.99.12p2-7
2009-10-04 13:53:35 status half-installed libcdaudio1 0.99.12p2-7
2009-10-04 13:53:35 install libcelt0 <none> 0.5.1-0ubuntu1
2009-10-04 13:53:35 status half-installed libcelt0 0.5.1-0ubuntu1
2009-10-04 13:53:35 install libdc1394-22 <none> 2.0.2-1
2009-10-04 13:53:35 status half-installed libdc1394-22 2.0.2-1
2009-10-04 13:53:35 install libdca0 <none> 0.0.5-0.1
2009-10-04 13:53:35 status half-installed libdca0 0.0.5-0.1
2009-10-04 13:53:36 status half-installed libdca0 0.0.5-0.1
2009-10-04 13:53:36 install libdvdread4 <none> 4.1.3-4ubuntu2
2009-10-04 13:53:36 status half-installed libdvdread4 4.1.3-4ubuntu2
2009-10-04 13:53:36 install libdvdnav4 <none> 4.1.3-3
2009-10-04 13:53:36 status half-installed libdvdnav4 4.1.3-3
2009-10-04 13:53:37 install mysql-common <none> 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:53:37 status half-installed mysql-common 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:53:38 install libmysqlclient15off <none> 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:53:38 status half-installed libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:53:39 install libgmyth0 <none> 1:0.7.1-1ubuntu1
2009-10-04 13:53:39 status half-installed libgmyth0 1:0.7.1-1ubuntu1
2009-10-04 13:53:39 install libiptcdata0 <none> 1.0.2+libtool01-2ubuntu1
2009-10-04 13:53:39 status half-installed libiptcdata0 1.0.2+libtool01-2ubuntu1
2009-10-04 13:53:40 install libxml++2.6-2 <none> 2.24.0-1ubuntu1
2009-10-04 13:53:40 status half-installed libxml++2.6-2 2.24.0-1ubuntu1
2009-10-04 13:53:40 install libffado0 <none> 2.0~rc1-0ubuntu2
2009-10-04 13:53:40 status half-installed libffado0 2.0~rc1-0ubuntu2
2009-10-04 13:53:41 install libfreebob0 <none> 1.0.11-0ubuntu1
2009-10-04 13:53:41 status half-installed libfreebob0 1.0.11-0ubuntu1
2009-10-04 13:53:41 install libjack0 <none> 0.116.1-3ubuntu3
2009-10-04 13:53:41 status half-installed libjack0 0.116.1-3ubuntu3
2009-10-04 13:53:42 install libraptor1 <none> 1.4.18-2
2009-10-04 13:53:42 status half-installed libraptor1 1.4.18-2
2009-10-04 13:53:42 install liblrdf0 <none> 0.4.0-1.1
2009-10-04 13:53:42 status half-installed liblrdf0 0.4.0-1.1
2009-10-04 13:53:42 install libmms0 <none> 0.4-2
2009-10-04 13:53:42 status half-installed libmms0 0.4-2
2009-10-04 13:53:42 install libmodplug0c2 <none> 1:0.8.4-3ubuntu1.1
2009-10-04 13:53:42 status half-installed libmodplug0c2 1:0.8.4-3ubuntu1.1
2009-10-04 13:53:42 install libmpcdec3 <none> 1.2.2-1build1
2009-10-04 13:53:42 status half-installed libmpcdec3 1.2.2-1build1
2009-10-04 13:53:43 install libneon27-gnutls <none> 0.28.2-6.1ubuntu0.1
2009-10-04 13:53:43 status half-installed libneon27-gnutls 0.28.2-6.1ubuntu0.1
2009-10-04 13:53:43 install libfftw3-3 <none> 3.1.2-3.1ubuntu1
2009-10-04 13:53:43 status half-installed libfftw3-3 3.1.2-3.1ubuntu1
2009-10-04 13:53:43 install libofa0 <none> 0.9.3-3
2009-10-04 13:53:43 status half-installed libofa0 0.9.3-3
2009-10-04 13:53:43 install libopenspc0 <none> 0.3.99a-2
2009-10-04 13:53:43 status half-installed libopenspc0 0.3.99a-2
2009-10-04 13:53:43 install libsoundtouch1c2 <none> 1.3.1-2
2009-10-04 13:53:43 status half-installed libsoundtouch1c2 1.3.1-2
2009-10-04 13:53:43 install libwildmidi0 <none> 0.2.2-2
2009-10-04 13:53:43 status half-installed libwildmidi0 0.2.2-2
2009-10-04 13:53:44 install gstreamer0.10-plugins-bad <none> 0.10.11-2ubuntu1
2009-10-04 13:53:44 status half-installed gstreamer0.10-plugins-bad 0.10.11-2ubuntu1
2009-10-04 13:53:44 install libquicktime1 <none> 2:1.1.0+debian-1build1
2009-10-04 13:53:44 status half-installed libquicktime1 2:1.1.0+debian-1build1
2009-10-04 13:53:44 install libmjpegtools-1.9 <none> 1:1.9.0-0.0ubuntu3
2009-10-04 13:53:44 status half-installed libmjpegtools-1.9 1:1.9.0-0.0ubuntu3
2009-10-04 13:53:45 install gstreamer0.10-plugins-bad-multiverse <none> 0.10.11-0ubuntu1
2009-10-04 13:53:45 status half-installed gstreamer0.10-plugins-bad-multiverse 0.10.11-0ubuntu1
2009-10-04 13:53:45 install liba52-0.7.4 <none> 0.7.4-11ubuntu1
2009-10-04 13:53:45 status half-installed liba52-0.7.4 0.7.4-11ubuntu1
2009-10-04 13:53:45 install libid3tag0 <none> 0.15.1b-10
2009-10-04 13:53:45 status half-installed libid3tag0 0.15.1b-10
2009-10-04 13:53:45 install libmad0 <none> 0.15.1b-4
2009-10-04 13:53:45 status half-installed libmad0 0.15.1b-4
2009-10-04 13:53:45 install libmpeg2-4 <none> 0.4.1-3
2009-10-04 13:53:45 status half-installed libmpeg2-4 0.4.1-3
2009-10-04 13:53:45 install libsidplay1 <none> 1.36.59-5
2009-10-04 13:53:45 status half-installed libsidplay1 1.36.59-5
2009-10-04 13:53:45 install libtwolame0 <none> 0.3.12-1
2009-10-04 13:53:45 status half-installed libtwolame0 0.3.12-1
2009-10-04 13:53:46 install gstreamer0.10-plugins-ugly <none> 0.10.10.2-1build1
2009-10-04 13:53:46 status half-installed gstreamer0.10-plugins-ugly 0.10.10.2-1build1
2009-10-04 13:53:46 install gstreamer0.10-plugins-ugly-multiverse <none> 0.10.7-2
2009-10-04 13:53:46 status half-installed gstreamer0.10-plugins-ugly-multiverse 0.10.7-2
2009-10-04 13:53:46 install libstdc++5 <none> 1:3.3.6-17ubuntu1
2009-10-04 13:53:46 status half-installed libstdc++5 1:3.3.6-17ubuntu1
2009-10-04 13:53:46 install libamrnb3 <none> 7.0.0.2-0.1medibuntu1
2009-10-04 13:53:46 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1
2009-10-04 13:53:46 install libamrwb3 <none> 7.0.0.3-0.0medibuntu1
2009-10-04 13:53:46 status half-installed libamrwb3 7.0.0.3-0.0medibuntu1
2009-10-04 13:53:47 install ubuntu-restricted-extras <none> 31
2009-10-04 13:53:47 status half-installed ubuntu-restricted-extras 31
2009-10-04 13:53:47 install w32codecs <none> 20071007-0medibuntu4
2009-10-04 13:53:47 status half-installed w32codecs 20071007-0medibuntu4
2009-10-04 13:53:52 install non-free-codecs <none> 4medibuntu1
2009-10-04 13:53:52 status half-installed non-free-codecs 4medibuntu1
2009-10-04 13:53:52 install raptor-utils <none> 1.4.18-2
2009-10-04 13:53:52 status half-installed raptor-utils 1.4.18-2
2009-10-04 13:53:52 status half-installed raptor-utils 1.4.18-2
2009-10-04 13:53:52 install sun-java6-fonts <none> 6-16-0ubuntu1.9.04
2009-10-04 13:53:52 status half-installed sun-java6-fonts 6-16-0ubuntu1.9.04
2009-10-04 13:53:52 install sun-java6-plugin <none> 6-16-0ubuntu1.9.04
2009-10-04 13:53:52 status half-installed sun-java6-plugin 6-16-0ubuntu1.9.04
2009-10-04 13:53:52 install ttf-liberation <none> 1.04.93-1
2009-10-04 13:53:52 status half-installed ttf-liberation 1.04.93-1
2009-10-04 13:53:53 install ttf-mscorefonts-installer <none> 2.6
2009-10-04 13:53:53 status half-installed ttf-mscorefonts-installer 2.6
2009-10-04 13:53:53 status unpacked ttf-mscorefonts-installer 2.6
2009-10-04 13:53:53 status unpacked ttf-mscorefonts-installer 2.6
2009-10-04 13:53:53 install unrar <none> 1:3.8.5-1
2009-10-04 13:53:53 status half-installed unrar 1:3.8.5-1
2009-10-04 13:53:53 status half-installed unrar 1:3.8.5-1
2009-10-04 13:53:54 status installed doc-base 0.8.20
2009-10-04 13:53:55 status installed man-db 2.5.5-1build1
2009-10-04 13:53:58 status installed shared-mime-info 0.60-1
2009-10-04 13:53:59 status installed java-common 0.30ubuntu4
2009-10-04 13:53:59 status installed odbcinst1debian1 2.2.11-16build3
2009-10-04 13:53:59 status installed unixodbc 2.2.11-16build3
2009-10-04 13:53:59 status installed alsa-oss 1.0.17-1
2009-10-04 13:54:00 status installed cabextract 1.2-3
2009-10-04 13:54:00 status installed libfaac0 1.26-0.1ubuntu2
2009-10-04 13:54:00 status installed libmp4v2-0 1:1.6dfsg-0.2ubuntu4
2009-10-04 13:54:00 status installed faac 1.26-0.1ubuntu2
2009-10-04 13:54:00 status installed libfaad0 2.6.1-3.1
2009-10-04 13:54:00 status installed faad 2.6.1-3.1
2009-10-04 13:54:00 configure flashplugin-installer 10.0.32.18ubuntu0.9.04.1 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:54:00 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:54:00 status half-configured flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:54:08 status installed flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:54:08 status installed flashplugin-nonfree 10.0.32.18ubuntu0.9.04.1
2009-10-04 13:54:08 status installed freepats 20060219-1
2009-10-04 13:54:09 status installed gsfonts-x11 0.21
2009-10-04 13:54:09 status installed libavutil-unstripped-49 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:54:09 status installed libmp3lame0 3.98-0.0
2009-10-04 13:54:09 status installed libx264-65 1:0.svn20081230-0.0ubuntu1
2009-10-04 13:54:09 status installed libxvidcore4 2:1.1.2-0.1ubuntu3
2009-10-04 13:54:09 status installed libavcodec-unstripped-52 3:0.svn20090303-1ubuntu2+unstripped1
2009-10-04 13:54:09 status installed libavformat52 3:0.svn20090303-1ubuntu6
2009-10-04 13:54:09 status installed libpostproc51 3:0.svn20090303-1ubuntu6
2009-10-04 13:54:09 status installed libswscale0 3:0.svn20090303-1ubuntu6
2009-10-04 13:54:09 status installed gstreamer0.10-ffmpeg 0.10.6.2-1ubuntu2
2009-10-04 13:54:09 status installed gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1
2009-10-04 13:54:09 status installed libenca0 1.9-6
2009-10-04 13:54:09 status installed libass1 0.9.5-2
2009-10-04 13:54:09 status installed libcdaudio1 0.99.12p2-7
2009-10-04 13:54:10 status installed libcelt0 0.5.1-0ubuntu1
2009-10-04 13:54:10 status installed libdc1394-22 2.0.2-1
2009-10-04 13:54:10 status installed libdca0 0.0.5-0.1
2009-10-04 13:54:10 status installed libdvdread4 4.1.3-4ubuntu2
2009-10-04 13:54:10 status installed libdvdnav4 4.1.3-3
2009-10-04 13:54:10 status installed mysql-common 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:54:10 status installed libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.2
2009-10-04 13:54:10 status installed libgmyth0 1:0.7.1-1ubuntu1
2009-10-04 13:54:10 status installed libiptcdata0 1.0.2+libtool01-2ubuntu1
2009-10-04 13:54:10 status installed libxml++2.6-2 2.24.0-1ubuntu1
2009-10-04 13:54:10 status installed libffado0 2.0~rc1-0ubuntu2
2009-10-04 13:54:10 status installed libfreebob0 1.0.11-0ubuntu1
2009-10-04 13:54:10 status installed libjack0 0.116.1-3ubuntu3
2009-10-04 13:54:10 status installed libraptor1 1.4.18-2
2009-10-04 13:54:10 status installed liblrdf0 0.4.0-1.1
2009-10-04 13:54:10 status installed libmms0 0.4-2
2009-10-04 13:54:10 status installed libmodplug0c2 1:0.8.4-3ubuntu1.1
2009-10-04 13:54:10 status installed libmpcdec3 1.2.2-1build1
2009-10-04 13:54:10 status installed libneon27-gnutls 0.28.2-6.1ubuntu0.1
2009-10-04 13:54:11 status installed libfftw3-3 3.1.2-3.1ubuntu1
2009-10-04 13:54:11 status installed libofa0 0.9.3-3
2009-10-04 13:54:11 status installed libopenspc0 0.3.99a-2
2009-10-04 13:54:11 status installed libsoundtouch1c2 1.3.1-2
2009-10-04 13:54:11 status installed libwildmidi0 0.2.2-2
2009-10-04 13:54:11 status installed gstreamer0.10-plugins-bad 0.10.11-2ubuntu1
2009-10-04 13:54:11 status installed libquicktime1 2:1.1.0+debian-1build1
2009-10-04 13:54:11 status installed libmjpegtools-1.9 1:1.9.0-0.0ubuntu3
2009-10-04 13:54:11 status installed gstreamer0.10-plugins-bad-multiverse 0.10.11-0ubuntu1
2009-10-04 13:54:11 status installed liba52-0.7.4 0.7.4-11ubuntu1
2009-10-04 13:54:11 status installed libid3tag0 0.15.1b-10
2009-10-04 13:54:11 status installed libmad0 0.15.1b-4
2009-10-04 13:54:11 status installed libmpeg2-4 0.4.1-3
2009-10-04 13:54:11 status installed libsidplay1 1.36.59-5
2009-10-04 13:54:11 status installed libtwolame0 0.3.12-1
2009-10-04 13:54:11 status installed gstreamer0.10-plugins-ugly 0.10.10.2-1build1
2009-10-04 13:54:11 status installed gstreamer0.10-plugins-ugly-multiverse 0.10.7-2
2009-10-04 13:54:11 status installed libstdc++5 1:3.3.6-17ubuntu1
2009-10-04 13:54:11 status installed libamrnb3 7.0.0.2-0.1medibuntu1
2009-10-04 13:54:12 status installed libamrwb3 7.0.0.3-0.0medibuntu1
2009-10-04 13:54:12 status installed ubuntu-restricted-extras 31
2009-10-04 13:54:12 status installed w32codecs 20071007-0medibuntu4
2009-10-04 13:54:12 status installed non-free-codecs 4medibuntu1
2009-10-04 13:54:12 status installed raptor-utils 1.4.18-2
2009-10-04 13:54:29 status installed ttf-liberation 1.04.93-1
2009-10-04 13:54:30 configure ttf-mscorefonts-installer 2.6 2.6
2009-10-04 13:54:30 status unpacked ttf-mscorefonts-installer 2.6
2009-10-04 13:54:30 status unpacked ttf-mscorefonts-installer 2.6
2009-10-04 13:54:30 status half-configured ttf-mscorefonts-installer 2.6
2009-10-04 13:55:22 status installed ttf-mscorefonts-installer 2.6
2009-10-04 13:55:22 status installed unrar 1:3.8.5-1
2009-10-04 13:55:22 status installed sun-java6-jre 6-16-0ubuntu1.9.04
2009-10-04 13:55:39 status installed sun-java6-fonts 6-16-0ubuntu1.9.04
2009-10-04 13:55:45 status installed sun-java6-bin 6-16-0ubuntu1.9.04
2009-10-04 13:55:46 status installed sun-java6-plugin 6-16-0ubuntu1.9.04
2009-10-04 13:55:47 status installed libc6 2.9-4ubuntu6.1
2009-10-04 13:56:35 status installed totem-mozilla 2.26.1-0ubuntu5
2009-10-04 13:56:37 status half-installed totem-mozilla 2.26.1-0ubuntu5
2009-10-04 13:56:37 status not-installed totem-mozilla <none>
2009-10-04 13:57:27 install libdiscid0 <none> 0.1.0-1
2009-10-04 13:57:27 status half-installed libdiscid0 0.1.0-1
2009-10-04 13:57:27 install libmusicbrainz3-6 <none> 3.0.2-1
2009-10-04 13:57:27 status half-installed libmusicbrainz3-6 3.0.2-1
2009-10-04 13:57:27 install libaudio2 <none> 1.9.1-5
2009-10-04 13:57:27 status half-installed libaudio2 1.9.1-5
2009-10-04 13:57:27 install libgii1 <none> 1:1.0.2-4
2009-10-04 13:57:27 status half-installed libgii1 1:1.0.2-4
2009-10-04 13:57:27 status half-installed libgii1 1:1.0.2-4
2009-10-04 13:57:27 install libsvga1 <none> 1:1.4.3-27
2009-10-04 13:57:27 status half-installed libsvga1 1:1.4.3-27
2009-10-04 13:57:27 status half-installed libsvga1 1:1.4.3-27
2009-10-04 13:57:28 install libggi2 <none> 1:2.2.2-3ubuntu1
2009-10-04 13:57:28 status half-installed libggi2 1:2.2.2-3ubuntu1
2009-10-04 13:57:28 status half-installed libggi2 1:2.2.2-3ubuntu1
2009-10-04 13:57:28 install liblzo2-2 <none> 2.03-1
2009-10-04 13:57:28 status half-installed liblzo2-2 2.03-1
2009-10-04 13:57:28 install libopenal1 <none> 1:1.4.272-2
2009-10-04 13:57:28 status half-installed libopenal1 1:1.4.272-2
2009-10-04 13:57:28 install mplayer-skins <none> 2-7
2009-10-04 13:57:28 status half-installed mplayer-skins 2-7
2009-10-04 13:57:28 install mplayer <none> 2:1.0~rc2-0ubuntu19+medibuntu1
2009-10-04 13:57:28 status half-installed mplayer 2:1.0~rc2-0ubuntu19+medibuntu1
2009-10-04 13:57:29 status half-installed mplayer 2:1.0~rc2-0ubuntu19+medibuntu1
2009-10-04 13:57:29 install gnome-mplayer <none> 0.9.4-1
2009-10-04 13:57:29 status half-installed gnome-mplayer 0.9.4-1
2009-10-04 13:57:29 status half-installed gnome-mplayer 0.9.4-1
2009-10-04 13:57:30 install gecko-mediaplayer <none> 0.9.4-1ubuntu1
2009-10-04 13:57:30 status half-installed gecko-mediaplayer 0.9.4-1ubuntu1
2009-10-04 13:57:30 install libgii1-target-x <none> 1:1.0.2-4
2009-10-04 13:57:30 status half-installed libgii1-target-x 1:1.0.2-4
2009-10-04 13:57:30 install libggi-target-x <none> 1:2.2.2-3ubuntu1
2009-10-04 13:57:30 status half-installed libggi-target-x 1:2.2.2-3ubuntu1
2009-10-04 13:57:30 status half-installed libggi-target-x 1:2.2.2-3ubuntu1
2009-10-04 13:57:31 status installed man-db 2.5.5-1build1
2009-10-04 13:57:32 status installed libdiscid0 0.1.0-1
2009-10-04 13:57:32 status installed libmusicbrainz3-6 3.0.2-1
2009-10-04 13:57:32 status installed libaudio2 1.9.1-5
2009-10-04 13:57:33 status installed libgii1 1:1.0.2-4
2009-10-04 13:57:33 status installed libsvga1 1:1.4.3-27
2009-10-04 13:57:33 status installed libggi2 1:2.2.2-3ubuntu1
2009-10-04 13:57:33 status installed liblzo2-2 2.03-1
2009-10-04 13:57:33 status installed libopenal1 1:1.4.272-2
2009-10-04 13:57:33 status installed mplayer-skins 2-7
2009-10-04 13:57:33 status installed mplayer 2:1.0~rc2-0ubuntu19+medibuntu1
2009-10-04 13:57:34 status installed gnome-mplayer 0.9.4-1
2009-10-04 13:57:35 status installed gecko-mediaplayer 0.9.4-1ubuntu1
2009-10-04 13:57:35 status installed libgii1-target-x 1:1.0.2-4
2009-10-04 13:57:35 status installed libggi-target-x 1:2.2.2-3ubuntu1
2009-10-04 13:57:35 status installed libc6 2.9-4ubuntu6.1
2009-10-04 14:01:04 install audacity-data <none> 1.3.7-2ubuntu1
2009-10-04 14:01:04 status half-installed audacity-data 1.3.7-2ubuntu1
2009-10-04 14:01:05 status half-installed audacity-data 1.3.7-2ubuntu1
2009-10-04 14:01:05 install libflac++6 <none> 1.2.1-1.2
2009-10-04 14:01:05 status half-installed libflac++6 1.2.1-1.2
2009-10-04 14:01:05 install libwxbase2.8-0 <none> 2.8.9.1-0ubuntu6
2009-10-04 14:01:05 status half-installed libwxbase2.8-0 2.8.9.1-0ubuntu6
2009-10-04 14:01:05 install libwxgtk2.8-0 <none> 2.8.9.1-0ubuntu6
2009-10-04 14:01:05 status half-installed libwxgtk2.8-0 2.8.9.1-0ubuntu6
2009-10-04 14:01:06 install audacity <none> 1.3.7-2ubuntu1
2009-10-04 14:01:06 status half-installed audacity 1.3.7-2ubuntu1
2009-10-04 14:01:06 status half-installed audacity 1.3.7-2ubuntu1
2009-10-04 14:01:07 install soundconverter <none> 1.4.1-0ubuntu1
2009-10-04 14:01:07 status half-installed soundconverter 1.4.1-0ubuntu1
2009-10-04 14:01:07 status half-installed soundconverter 1.4.1-0ubuntu1
2009-10-04 14:01:07 install oggconvert <none> 0.3.2-2ubuntu1
2009-10-04 14:01:07 status half-installed oggconvert 0.3.2-2ubuntu1
2009-10-04 14:01:08 status half-installed oggconvert 0.3.2-2ubuntu1
2009-10-04 14:01:09 status installed shared-mime-info 0.60-1
2009-10-04 14:01:09 status installed man-db 2.5.5-1build1
2009-10-04 14:01:10 status installed audacity-data 1.3.7-2ubuntu1
2009-10-04 14:01:10 status installed libflac++6 1.2.1-1.2
2009-10-04 14:01:10 status installed libwxbase2.8-0 2.8.9.1-0ubuntu6
2009-10-04 14:01:10 status installed libwxgtk2.8-0 2.8.9.1-0ubuntu6
2009-10-04 14:01:11 status installed audacity 1.3.7-2ubuntu1
2009-10-04 14:01:11 status installed soundconverter 1.4.1-0ubuntu1
2009-10-04 14:01:11 status installed oggconvert 0.3.2-2ubuntu1
2009-10-04 14:01:12 status installed libc6 2.9-4ubuntu6.1
2009-10-04 14:03:59 install avidemux-common <none> 1:2.4.4-0.0ubuntu1
2009-10-04 14:03:59 status half-installed avidemux-common 1:2.4.4-0.0ubuntu1
2009-10-04 14:03:59 status half-installed avidemux-common 1:2.4.4-0.0ubuntu1
2009-10-04 14:03:59 install avidemux <none> 1:2.4.4-0.0ubuntu1
2009-10-04 14:03:59 status half-installed avidemux 1:2.4.4-0.0ubuntu1
2009-10-04 14:04:00 status half-installed avidemux 1:2.4.4-0.0ubuntu1
2009-10-04 14:04:00 install libavdevice52 <none> 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 status half-installed libavdevice52 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 install libavfilter0 <none> 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 status half-installed libavfilter0 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 install ffmpeg <none> 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 status half-installed ffmpeg 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 status half-installed ffmpeg 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:00 install lame <none> 3.98-0.0
2009-10-04 14:04:00 status half-installed lame 3.98-0.0
2009-10-04 14:04:01 status half-installed lame 3.98-0.0
2009-10-04 14:04:01 status half-installed lame 3.98-0.0
2009-10-04 14:04:01 install mjpegtools <none> 1:1.9.0-0.0ubuntu3
2009-10-04 14:04:01 status half-installed mjpegtools 1:1.9.0-0.0ubuntu3
2009-10-04 14:04:01 status half-installed mjpegtools 1:1.9.0-0.0ubuntu3
2009-10-04 14:04:01 install toolame <none> 02l-6
2009-10-04 14:04:01 status half-installed toolame 02l-6
2009-10-04 14:04:01 status half-installed toolame 02l-6
2009-10-04 14:04:01 install winff <none> 0.45.1-1ubuntu1
2009-10-04 14:04:01 status half-installed winff 0.45.1-1ubuntu1
2009-10-04 14:04:01 status half-installed winff 0.45.1-1ubuntu1
2009-10-04 14:04:01 status half-installed winff 0.45.1-1ubuntu1
2009-10-04 14:04:02 status installed man-db 2.5.5-1build1
2009-10-04 14:04:03 status installed doc-base 0.8.20
2009-10-04 14:04:03 status installed libavdevice52 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:04 status installed libavfilter0 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:04 status installed ffmpeg 3:0.svn20090303-1ubuntu6
2009-10-04 14:04:04 status installed lame 3.98-0.0
2009-10-04 14:04:04 status installed mjpegtools 1:1.9.0-0.0ubuntu3
2009-10-04 14:04:04 status installed toolame 02l-6
2009-10-04 14:04:04 status installed winff 0.45.1-1ubuntu1
2009-10-04 14:04:04 status installed avidemux-common 1:2.4.4-0.0ubuntu1
2009-10-04 14:04:04 status installed avidemux 1:2.4.4-0.0ubuntu1
2009-10-04 14:04:04 status installed libc6 2.9-4ubuntu6.1
2009-10-04 14:33:59 status half-installed adobe-flashplugin 10.0.32.18-1
2009-10-04 14:33:59 status half-installed adobe-flashplugin 10.0.32.18-1
2009-10-04 14:34:01 status installed adobe-flashplugin 10.0.32.18-1jaunty1

```

thats everything that happened today. I know its alot, but I just finished installing this yesterday, and was trying to get the codec headaches out of the way asap. looks like that was probably a poor decision..

I also tried to make a new user and it had the exact same problem. I have restarted several times, but am still thoroughly confused by whats going on. how would multimedia packages effect my gnome?

Once again, thanks for the help guys. :)

---

### Post by tophatandy on 2009-10-04
thinking about just reinstalling the karmic koala beta. Its not like I would be loosing much data anyway. 

Would like to see if there is any other way to resolve it first though..

---

### Post by ankspo71 on 2009-10-04
Hi,
I don't understand how codecs could do that either.

Resorting to google::P

Try the last solution mentioned here: (not #3, the one below that)
[http://phparch.cn/index.php/linux/75-solutions/239-Unable-to-start-the-settings-manager-gnome-settings-daemon-solution](http://phparch.cn/index.php/linux/75-solutions/239-Unable-to-start-the-settings-manager-gnome-settings-daemon-solution)

Solution #1 and #2 might work too.
James

---

### Post by renkinjutsu on 2009-10-04
also, check your dmrc file

```
cat ~/.dmrc
```

---

### Post by tophatandy on 2009-10-04
> **ankspo71 said:**
> Hi,
I don't understand how codecs could do that either.

Resorting to google::P

Try the last solution mentioned here: (not #3, the one below that)
[http://phparch.cn/index.php/linux/75-solutions/239-Unable-to-start-the-settings-manager-gnome-settings-daemon-solution](http://phparch.cn/index.php/linux/75-solutions/239-Unable-to-start-the-settings-manager-gnome-settings-daemon-solution)

Solution #1 and #2 might work too.
James

no go for any of them. the file from the last solution was just those two lines. so that didn't work. thanks for the suggestions though. I have been googling like mad, and have only come up with solutions for old problems similar to mine, all of the solutions from which leave me right back where i started. 

thanks though.

---

### Post by tophatandy on 2009-10-04
> **renkinjutsu said:**
> also, check your dmrc file

```
cat ~/.dmrc
```

plugged that in, and got back

```
 [Desktop]
Session=default

```

don't know how much help this is. I don't even know what that file is tbh. :/

---

### Post by ankspo71 on 2009-10-05
Hi,
My results for cat ~/.dmrc are:

```
james@Ubuntu:~$ cat ~/.dmrc

[Desktop]
Language=en_US.UTF-8
james@Ubuntu:~$
```

James

---

