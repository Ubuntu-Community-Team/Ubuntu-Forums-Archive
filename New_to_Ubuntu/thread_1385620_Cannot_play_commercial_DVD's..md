---
title: "Cannot play commercial DVD's."
date: 2010-01-19
forum: New to Ubuntu
---

### Post by asuastrophysics on 2010-01-19
Hey all, 

I can't get any media player to play a DVD. I've got Realplayer, Totem, and VLC installed and none work.

I have ubuntu-restricted-xtras installed, as well as libdvdcss2. 

Neither of these have corrected the problem. 

Any ideas?

---

### Post by KinKiac on 2010-01-19
Have you tried using VLC media player?  It should have the required DVD decryption built into it if Im not mistaken.  I know it does with windows.  Other than that i dont know where you have gone wrong.  Installing the libdvdcss2 should have done it for you.  Ive played DVD's under karmic for a while now and never had a problem as long as the required package was installed, regardless of the player.

---

### Post by tom.swartz07 on 2010-01-19
> **asuastrophysics said:**
> Hey all, 

I can't get any media player to play a DVD. I've got Realplayer, Totem, and VLC installed and none work.

I have ubuntu-restricted-xtras installed, as well as libdvdcss2. 

Neither of these have corrected the problem. 

Any ideas?

Click the Media Support link in my Signature.

The guide will get everything set up!

---

### Post by asuastrophysics on 2010-01-19
> **KinKiac said:**
> Have you tried using VLC media player?  It should have the required DVD decryption built into it if Im not mistaken.  I know it does with windows.  Other than that i dont know where you have gone wrong.  Installing the libdvdcss2 should have done it for you.  Ive played DVD's under karmic for a while now and never had a problem as long as the required package was installed, regardless of the player.

I followed all of the instructions here: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
 
Installed everything I needed. No dice. 
This is the output VLC spews out:
```
jake@jake-laptop:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x1c2d888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (<unknown>:29881): WARNING **: Invalid borders specified for theme pixmap:
        /home/jake/.themes/Leopardish1/gtk-2.0/slider.png,
borders don't fit within the image
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/jake/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000166
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000248
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000303
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0006b5cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0006b76e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00088385
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00088440
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0008a287
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000a7d33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002e4551
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002e462c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002e4653
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002e470e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002f7789
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002f7844
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x002f7918
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002f79d3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003500e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0035019c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00350fe1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00351157
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00353482
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0035353d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0035360a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003536c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003537ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003538a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00353a98
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00353b53
libdvdread: Elapsed time 0
libdvdread: Found 14 VTS's
libdvdread: Elapsed time 0
[0x232f0d8] main input error: ES_OUT_RESET_PCR called
[0x232f0d8] main input error: ES_OUT_RESET_PCR called

```
I honestly have no idea. I know DVD playback **used** to work, many updates ago. I'm willing to bet that a supported update broke this.

---

### Post by fooman on 2010-01-19
you will need libdvdcss2 from the medibuntu repos. first add the repo by copying/pasting the following command into a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```that will add the repo and the GPG key,  as well as update your repository list.  all that should be needed is to upgrade with the following command:

```
sudo apt-get upgrade
```

that should show that there is an upgrade available for libdvdcss2...say yes to the upgrade and when it completes...try a dvd.

hope that helps.

---

### Post by asuastrophysics on 2010-01-19
> **fooman said:**
> you will need libdvdcss2 from the medibuntu repos. first add the repo by copying/pasting the following command into a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```that will add the repo and the GPG key,  as well as update your repository list.  all that should be needed is to upgrade with the following command:

```
sudo apt-get upgrade
```

that should show that there is an upgrade available for libdvdcss2...say yes to the upgrade and when it completes...try a dvd.

hope that helps.

After running the previous "wget" command listed, I ran the "apt-get upgrade":
```
jake@jake-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jake@jake-laptop:~$ 

```

The first thing I tried was making sure libdvdcss2 was installed.
```
jake@jake-laptop:~$ sudo apt-get install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libdvdcss2 instead of libdvdcss
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jake@jake-laptop:~$ 

``` 
Thanks for your help though! :D
Do you have any idea why else it might not be playing?

---

### Post by Old_Grey_Wolf on 2010-01-19
If you are using Ubuntu 9.04, as your profile suggests, entering these commands should help. If you are using 9.10 then there are some changes to the commands. Just copy and paste into the terminal.

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools
```

```
sudo apt-get install realplayer w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc
```

```
sudo apt-get install easytag faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1 mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool toolame vorbis-tools gecko-mediaplayer
```

---

### Post by asuastrophysics on 2010-01-19
@ Old_Gray_Wolf: thank you thank you thank you thank you!!!!

:popcorn:

awesome. I'm going to suggest that those commands be added to the "complete multimedia guide" :D

thanks again!

---

### Post by Old_Grey_Wolf on 2010-01-19
> **asuastrophysics said:**
> @ Old_Gray_Wolf: thank you thank you thank you thank you!!!!

:popcorn:

awesome. I'm going to suggest that those commands be added to the "complete multimedia guide" :D

thanks again!

Don't thank me. :D

I just added some info that TrakerJon had in his "Ubuntu Desktop Computing Made Easy (Ubuntu 9.04)" thread to a file I keep for stetting up 9.04. Just Google "Ubuntu Desktop Computing Made Easy (Ubuntu 9.04)" for all the other useful stuff in his tutorial.

He also posted a similar tutorial for 9.10.

---

