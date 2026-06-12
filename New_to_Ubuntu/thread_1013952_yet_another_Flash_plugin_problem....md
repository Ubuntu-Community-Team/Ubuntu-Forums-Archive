---
title: "yet another Flash plugin problem..."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Jdmisra81 on 2008-12-17
So I did a reinstall of Xubuntu 8.04

I updated Firefox to 3.0

Now I am having zero luck trying to install flash plugin.

I went through synaptic....which tells me it is installed. 

If I go to any site to view videos..it tells me I need to get flash player.

And when I do the about:plugins command in the address bar,....flash player isn't listed

In the past I had the problem where it was listed but didn't work...now I'm 0/2

Why must this be so complicated :/

---

### Post by philinux on 2008-12-17
Lets see where it is.

```

sudo updatedb

locate libflashplayer.so
```

---

### Post by Hospadar on 2008-12-17
I've always had issues installing it through synaptic.

I always just pointed by browser to some page that has a flash animation (Important: it needs to be a page that doesn't check whether or not you have flash, i.e. not youtube) so that firefox asks me if I want to install flash.  Whenever I go this route, it works great, when I go through synaptic, no workey.

Maybe try just removing it in synaptic and going through firefox.

---

### Post by wolfen69 on 2008-12-17
go back to synaptic and completely remove flash. then ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb for ubuntu. click to install. restart firefox if open.

---

### Post by Jdmisra81 on 2008-12-17
> **philinux said:**
> Lets see where it is.

```

sudo updatedb

locate libflashplayer.so
```
Hmm

sudo updatedb 

asks me for my password and then seems to hang up, doesn't do anything...

locate libflashplayer.so

doesn't do anything

So I just removed it with synaptic..And installed it  using the .Deb file and Gdebi package manager.

It said it was successful...But it is still not showing up in Firefox! 

About:plugins

still not there...

Could it be that something else is missing, that flash is dependant on?

---

### Post by Jdmisra81 on 2008-12-17
> **Hospadar said:**
> I've always had issues installing it through synaptic.

I always just pointed by browser to some page that has a flash animation (Important: it needs to be a page that doesn't check whether or not you have flash, i.e. not youtube) so that firefox asks me if I want to install flash.  Whenever I go this route, it works great, when I go through synaptic, no workey.

Maybe try just removing it in synaptic and going through firefox.

I just tried doing that at video.google.com

it installed....but still isn't showing up  afterwards...Ugh.

---

### Post by philinux on 2008-12-17
> **Jdmisra81 said:**
> Hmm

sudo updatedb 

asks me for my password and then seems to hang up, doesn't do anything...

locate libflashplayer.so

doesn't do anything. So presumably it's not installed properly..I'll try removing it..

updatedb updates the indexing system. Leave it to run. Thats why it couldn't find anything.

This site uses flash
[http://news.sky.com/skynews/home](http://news.sky.com/skynews/home)

---

### Post by Jdmisra81 on 2008-12-17
I let it run....it didn't give me any kind of message after...same for locate libflashplayer.so

- nothing. Is it possible I'm just missing that file? And can I add it manually?

---

### Post by philinux on 2008-12-17
> **Jdmisra81 said:**
> I let it run....it didn't give me any kind of message after...same for locate libflashplayer.so

- nothing. Is it possible I'm just missing that file? And can I add it manually?

Ok updatedb does not give messages it just does it's thing. Sounds like flash is not installed.

Assuming you're using 32bit os. then

Either use synaptic or,

sudo apt-get install flashplugin-nonfree
or
sudo apt-get install ubuntu-restricted-extras

---

### Post by Jdmisra81 on 2008-12-17
Ok, so I tried sudo apt-get install ubuntu-restricted-extras

and I think there are all sorts of errors happening
What's going on here?

jdmisra81@jdmisra81:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jdmisra81: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  liba52-0.7.4 libavformat1d libcdaudio1 libdc1394-13 libexempi3 libfaad0
  libgmyth0 libid3tag0 libiptcdata0 libmjpegtools0c2a libmms0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient15off libneon27 libopenspc0 libquicktime1
  libsidplay1 libsndfile1 libsoundtouch1c2 libsoup2.4-1 libwildmidi0
  mysql-common
Suggested packages:
  libflashsupport ttf-xfree86-nonfree xfs sidplay-base xsidplay
Recommended packages:
  w32codecs freepats
The following NEW packages will be installed:
  flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  liba52-0.7.4 libavformat1d libcdaudio1 libdc1394-13 libexempi3 libfaad0
  libgmyth0 libid3tag0 libiptcdata0 libmjpegtools0c2a libmms0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient15off libneon27 libopenspc0 libquicktime1
  libsidplay1 libsndfile1 libsoundtouch1c2 libsoup2.4-1 libwildmidi0
  mysql-common ubuntu-restricted-extras
0 upgraded, 31 newly installed, 0 to remove and 102 not upgraded.
Need to get 5719kB/5738kB of archives.
After this operation, 15.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libavformat1d 3:0.cvs20070307-5ubuntu7.1 [287kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe libfaad0 2.6.1-2ubuntu0.1 [167kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main mysql-common 5.0.51a-3ubuntu5.4 [60.3kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libmysqlclient15off 5.0.51a-3ubuntu5.4 [1837kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libdc1394-13 1.1.0-5ubuntu1        
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe gstreamer0.10-ffmpeg 0.10.3-6
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libcdaudio1 0.99.12p2-3
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libexempi3 1.99.9-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libgmyth0 0.7.debian1-1~hardy1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libiptcdata0 1.0.2-2
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libmms0 0.3-6
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libmusicbrainz4c2a 2.1.5-1ubuntu2
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libneon27 0.27.2-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libopenspc0 0.3.99a-2
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libsndfile1 1.0.17-4
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe libsoundtouch1c2 1.3.0-2.2ubuntu0.1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main libsoup2.4-1 2.4.1-1ubuntu1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libwildmidi0 0.2.2-2
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libquicktime1 2:1.0.0+debian-5
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu5
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.6-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe liba52-0.7.4 0.7.4-11ubuntu1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libid3tag0 0.15.1b-10
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libmpeg2-4 0.4.1-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe libsidplay1 1.36.59-4
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe gstreamer0.10-plugins-ugly 0.10.7-3ubuntu1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.7-1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse ubuntu-restricted-extras 15.2
  Unable to connect to ca.archive.ubuntu.com http:
Fetched 2351kB in 2min0s (19.6kB/s)                      
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/e/exempi/libexempi3_1.99.9-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/e/exempi/libexempi3_1.99.9-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4c2a_2.1.5-1ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4c2a_2.1.5-1ubuntu2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27_0.27.2-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27_0.27.2-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.17-4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.17-4_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.4.1-1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.4.1-1ubuntu1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11ubuntu1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by mrbiggbrain on 2008-12-17
ok to me it seems like the site that its attempting to fetch / get the packages from isnt responding, maybe removing that entree from the list of sources and adding another source would result in better results.

---

### Post by philinux on 2008-12-17
System>Admin>software sources. Look at bottom for download from. Change the server to main. Then try again.

---

