---
title: "[SOLVED] How do I convert .oga to .mp3?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by jpease on 2009-01-03
total newbie here.  I ripped a cd using rhytmbox 0.11.6.  Been a total ubuntu newbie when I went to move them to my mp3 server to my surprise they where .oga.  I need to convert them to mp3.

Is there a pluging I can install to rhytmbox to go straight to mp3?

---

### Post by RomeReactor on 2009-01-03
Hi. In Rhythmbox, go to "Edit->Preferences" and on the "Music" tab, change the preferred format to "CD Quality, MP3 (.mp3-type)"

To convert existing files, try with soundconverter:
```
sudo aptitude install soundconverter gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg
```

---

### Post by logos34 on 2009-01-03
delete

---

### Post by Steveway on 2009-01-03
> **jpease said:**
> total newbie here.  I ripped a cd using rhytmbox 0.11.6.  Been a total ubuntu newbie when I went to move them to my mp3 server to my surprise they where .oga.  I need to convert them to mp3.

Is there a pluging I can install to rhytmbox to go straight to mp3?

.oga is a far superior file-format compared to .mp3.
But since it is also a lossy format you should not convert it to another lossy format, the resulting soundquality will be miserable.
If you really insist on using the deprecated .mp3 format then re-rip them and choose .mp3 as output format, providing you got all the necesary tools installed.

---

### Post by jpease on 2009-01-03
I went in there and in the "preferred format" drop down there is no mp3 option.   Said that, I click on "edit" and I see the option in there but I can not get that to become my preferred option in the preferred format list.

How do I do that?

---

### Post by jpease on 2009-01-03
> **Steveway said:**
> .oga is a far superior file-format compared to .mp3.
But since it is also a lossy format you should not convert it to another lossy format, the resulting soundquality will be miserable.
If you really insist on using the deprecated .mp3 format then re-rip them and choose .mp3 as output format, providing you got all the necesary tools installed.thanks for the info.  It makes sense.

I had planned to do a clean rip to mp3 all over.

---

### Post by logos34 on 2009-01-03
> **jpease said:**
> I went in there and in the "preferred format" drop down there is no mp3 option.   Said that, I click on "edit" and I see the option in there but I can not get that to become my preferred option in the preferred format list.

How do I do that?

try

sudo apt-get install ubuntu-restricted-extras lame

---

### Post by RomeReactor on 2009-01-03
> **jpease said:**
> I went in there and in the "preferred format" drop down there is no mp3 option.   Said that, I click on "edit" and I see the option in there but I can not get that to become my preferred option in the preferred format list.

How do I do that?

You probably don't have these installed yet (close Rhythmbox first):
```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```
Now open it again and see if the option is available now.

---

### Post by sherriesyo on 2009-01-03
are you a game player?Y/N? come and have a lookmaplestoryer.com provide quick and safely [maple story items](http://www.maplestoryer.com/)  [maple story mesos](http://www.maplestoryer.com/) [maple story power leveling](http://www.maplestoryer.com/) service.come and try!

---

### Post by jpease on 2009-01-04
> **logos34 said:**
> try

sudo apt-get install ubuntu-restricted-extras lame
ok, I did the above command.  I did some work.  Within the terminal window I got a "configuring sun-java6-jre" license.  At the very end it says <OK>

Here is the really embarrassing totally newbie question.  How do I accept the license?  I hit enter and nothing happened.  It seems like it is stuck in "Package Configuration"

Am I done?  Can I close the terminal window?

Lost and confused a poor windows guy trying to crossover to ubuntu.......:confused:

---

### Post by logos34 on 2009-01-04
you have to accept license (use arrow keys to highlight botton), then hit enter.

Try again but add the gstreamer stuff as RomeReactor suggests (what Rhythmbox needs specifically and they're recommended pkgs anyway--i thought they were included as depends.):

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdread3 liblame0




> Package: ubuntu-restricted-extras
Priority: optional
Section: multiverse/metapackages
Installed-Size: 32
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: amd64
Version: 15
flashplugin-nonfree, gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, icedtea-gcjwebplugin, libdvdread3, liblame0, msttcorefont
Filename: pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15_amd64.deb
Size: 3660
MD5sum: 75251f3957481a25551a3693e93c5f8c
SHA1: 0f8b28a4d59d51eda2c1537b5784f3666d56bd32
SHA256: 69ba3cdb238685d16aab5bcf83dac7bf98fb663fe7c52911d48ee0c7fb91e331
Description: Commonly used restricted packages
 This package depends on some commonly used packages in the Ubuntu
 multiverse repository.
 .
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (gstreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio files),
 and DVD playback.
 .
 Please note that packages from multiverse are restricted by copyright
 or legal issues in some countries. See
 [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
 for more information.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by jpease on 2009-01-04
> **logos34 said:**
> you have to accept license (use arrow keys to highlight botton), then hit enter.
Oh jeez, I feel about this big . right about now.

It is doing something.

---

### Post by jpease on 2009-01-04
> **logos34 said:**
> you have to accept license (use arrow keys to highlight botton), then hit enter.
I checked in Rhythmbox and it is there in the drop down.  Very Cool.

> add the gstreamer stuff as RomeReactor suggests (what Rhythmbox needs specifically and they're recommended pkgs anyway--i thought they were included as depends.):
I also did what you suggested.  It is working as we speak.

Thanks everyone for all the help!

---

