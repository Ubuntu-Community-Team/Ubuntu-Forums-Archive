---
title: "clooless in connecticut - movies, dvd's and iso's - oh, my!"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by donebythefish on 2010-11-24
Hi all!

I'm a first time user, ubuntu 10.10 - I decided to get my fins wet with Ubuntu before relocating out of state in a few days.  Here's the problem(s) I'm having...

I want the machine that Ubuntu is installed on (it's sole O.S.) to merely and purely function as a way of playing movies.  A few are store-bought DVD discs, more are in *.iso format (which I can change if needed) and several hundred (*cough, cough*) were ripped from rentals in DVD format (with VOB, VideoTS, etc files) and all play wonderfully from my Windows machine whose VGA cable is lovingly plugged into a 55" screen. The files reside on a few 1TB drives using a docking station and USB connection.

When I load a store-bought DVD in to my Ubuntu machine, Open Movie Player tells me it "Could not read from resource" (the disc works fine with windows machine).  So, I'd like to get this issue resolved... and on to the next question...

...I see my files/folder when docking station is plugged in, and if I open them with Movie Player they work OK... except for the iso files - do I need to extract them first, or is there an app like VLC Mediaplayer that can read *everything* like it does with windows?

Forgive me for sounding so clueless, I really am a total noob to the linux/Ubuntu environment - but I did figure out where the screensaver options are!  So....  Please be careful with that axe, Eugene - all help is appreciated :)

---

### Post by yankysunny on 2010-11-24
> **donebythefish said:**
> Hi all!

I'm a first time user, ubuntu 10.10 - I decided to get my fins wet with Ubuntu before relocating out of state in a few days.  Here's the problem(s) I'm having...

I want the machine that Ubuntu is installed on (it's sole O.S.) to merely and purely function as a way of playing movies.  A few are store-bought DVD discs, more are in *.iso format (which I can change if needed) and several hundred (*cough, cough*) were ripped from rentals in DVD format (with VOB, VideoTS, etc files) and all play wonderfully from my Windows machine whose VGA cable is lovingly plugged into a 55" screen. The files reside on a few 1TB drives using a docking station and USB connection.

When I load a store-bought DVD in to my Ubuntu machine, **Open Movie Player tells me it "Could not read from resource" (the disc works fine with windows machine).  So, I'd like to get this issue resolved**... and on to the next question...

...I see my files/folder when docking station is plugged in, and if I open them with Movie Player they work OK... **except for the iso files** - do I need to extract them first, or is there an app like VLC Mediaplayer that can read *everything* like it does with windows?

Forgive me for sounding so clueless, I really am a total noob to the linux/Ubuntu environment - but I did figure out where the screensaver options are!  So....  Please be careful with that axe, Eugene - all help is appreciated :)


1. I just know that by default the media player in ubuntu are not installed with all the codecs that a DVD require. If you do not want to install any codecs manually. try to install vlc player from synaptic manager and I think it may solve the problem

2. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

3. ISO file problem :[http://www.howtogeek.com/howto/ubuntu/how-to-use-an-iso-image-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/how-to-use-an-iso-image-on-ubuntu-linux/)

---

### Post by kroq-gar78 on 2010-11-24
> **donebythefish said:**
> Hi all!

I'm a first time user, ubuntu 10.10 - I decided to get my fins wet with Ubuntu before relocating out of state in a few days.  Here's the problem(s) I'm having...

I want the machine that Ubuntu is installed on (it's sole O.S.) to merely and purely function as a way of playing movies.  A few are store-bought DVD discs, more are in *.iso format (which I can change if needed) and several hundred (*cough, cough*) were ripped from rentals in DVD format (with VOB, VideoTS, etc files) and all play wonderfully from my Windows machine whose VGA cable is lovingly plugged into a 55" screen. The files reside on a few 1TB drives using a docking station and USB connection.

When I load a store-bought DVD in to my Ubuntu machine, Open Movie Player tells me it "Could not read from resource" (the disc works fine with windows machine).  So, I'd like to get this issue resolved... and on to the next question...

...I see my files/folder when docking station is plugged in, and if I open them with Movie Player they work OK... except for the iso files - do I need to extract them first, or is there an app like VLC Mediaplayer that can read *everything* like it does with windows?

Forgive me for sounding so clueless, I really am a total noob to the linux/Ubuntu environment - but I did figure out where the screensaver options are!  So....  Please be careful with that axe, Eugene - all help is appreciated :)
First of all, welcome to the forums!

To find screensavers, go to the System menu (near top left), then Preferences, and the "Screensaver" should be right there.

To be able to play DVDs and use the default player, go here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by cariboo on 2010-11-24
I would suggest you install the ubuntu-restricted-extras meta package from the repositories. then open an Applications->Accessories->Terminal and navigate to /usr/share/doc/libdvdread4:

```
cd /usr/share/doc/libdvdread4
```

once at the directory type:

```
ls -l
```

you should get a listing that looks like this:

```
ls -l
total 20
-rw-r--r-- 1 root root  267 2004-09-12 08:18 AUTHORS
-rw-r--r-- 1 root root 2128 2010-11-04 23:27 copyright
-rwxr-xr-x 1 root root 3987 2010-11-04 23:27 install-css.sh
-rw-r--r-- 1 root root 2669 2008-04-10 11:46 README
-rw-r--r-- 1 root root  622 2010-11-04 23:27 README.Debian
```

To install the dvd codec type:

```
sudo ./install-css.sh
```

Once you followed the above two steps, you should be able to play almost any type of audio/video media you may have.

---

