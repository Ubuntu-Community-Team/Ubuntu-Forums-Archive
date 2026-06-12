---
title: "New build, new user, no sound."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by chris282 on 2009-12-04
Hi all,

Wondered if I could get some advice.  I've recently installed Ubuntu on a newly built pc, but have no sound.  So far I've done the following:

* Checked the volume in System Preferences.

* Checked the forums for similar problems - there are many, but I'm afraid I can't tell which are related to mine, and I'd rather not go off down a blind alley in unfamiliar territory (did that once in Amsterdam, never again).

* Followed the steps in Ubuntu Documentation > Community Documentation > Sound Troubleshooting: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) as follows:

I have established that my soundcard is an: 
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)[FONT=Verdana]

The module is: [/FONT]snd_hda_intel

[FONT=Verdana]The codec is: [/FONT]Realtek ALC883

[FONT=Verdana]But here I've got stuck.  The next step reads:

[/FONT]"Now take a look at [ALSA-Configuration.txt]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=e0e54a27fc10905a62bd649605ad2dbe8f8bfdbf;hb=ba283e5ded21f6585b1f15254d6b4df94638eac2") again, and you will find a section that looks like this, which matches up with my soundcard's codec: 

   STAC9227/9228/9229/927x    ref           Reference board    3stack        D965 3stack    5stack        D965 5stack + SPDIF    dell-3stack   Dell Dimension E520    dell-bios     Fixes with Dell BIOS setup"

but I can't find a section that looks like this.  Could anyone point me in the right direction?

Any help gratefully appreciated.  Many thanks,

Chris.


Additional information, possibly irrelevant: I've noticed that the Sound Server ESound Daemon isn't running:

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Does this mean anything at all?

---

### Post by M!K3_$ on 2009-12-04
> **chris282 said:**
> * Checked the forums for similar problems - there are many, but I'm afraid I can't tell which are related to mine, and I'd rather not go off down a blind alley in unfamiliar territory (did that once in Amsterdam, never again).

lol.

sorry, i dont know what you can do besides google your sound card.

```
<soundcard> linux help
```

---

### Post by M!K3_$ on 2009-12-04
try this.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=8&PFid=14&Level=3&Conn=2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=8&PFid=14&Level=3&Conn=2")

---

### Post by chris282 on 2009-12-04
Thanks M!K3.

I've now got more information about the ALC883 codec than I can shake a stick at - but I'm still not entirely sure what to do with it.

I'm also confused by the guide, which seems to suggest that I'm trying to find out how many stacks I have.  I have 5.  I counted twice.  I've then followed the instructions to the end, with little hope of success and marginally less actual success.  I'm pretty certain there's something I'm not understanding properly here.  Possibly a number of things.

Hints?

- Chris

---

### Post by M!K3_$ on 2009-12-04
to be completely honest, i've been graced with good luck as far as sound cards go so i'm kinda in unknown territory here also. 

do you have all the ALSA packages installed?

---

### Post by kadeous on 2009-12-04
There is a great how to at [http://ubuntuforums.org/showthread.php?t=1046137&highlight=Alsa](http://ubuntuforums.org/showthread.php?t=1046137&highlight=Alsa)

Give it a try

---

### Post by chris282 on 2009-12-05
Hi both,

Many thanks for your help, it really is appreciated.  However, I'm afraid I'm starting to feel a little out of my depth.  The link instructions look simple enough to follow if I could get as far as starting them, but they suggest that I first make a backup:

"As usual - Make a backup first! - A restore will just take 5 minutes with rsync. That might save you hours of troubleshooting and frustration :wink:  ."

So that sank me up to my ears in technical jargon about how to run a tar file (?), which I've actually managed before, but I couldn't run this thing for love nor money.

Anyway, having decided to give up on that and just press on regardless, I've gone to step one: 

"1. download the script and save it somewhere"

Simple enough, I thought, but I've followed the link and found this:

**Latest Software Source Releases**

    Package  Stable Release (2008-02-06) 
  Development Release  Description    [Driver (alsa-driver)]("ftp://ftp.alsa-project.org/pub/driver/")  [1.0.21]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2")  none  Kernel drivers    [Firmware alsa-firmware)]("ftp://ftp.alsa-project.org/pub/firmware/")  [1.0.20]("ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.20.tar.bz2")  none  Firmware for cards that require it    [Library (alsa-lib)]("ftp://ftp.alsa-project.org/pub/lib/")  [1.0.21a]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21a.tar.bz2")  none  Userspace library    [Plugins (alsa-plugins)]("ftp://ftp.alsa-project.org/pub/plugins/")  [1.0.21]("ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.21.tar.bz2")  none  Additional library plugins Eg.jack, pulse, maemo ...    [Utilities (alsa-utils)]("ftp://ftp.alsa-project.org/pub/utils/")  [1.0.21]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2")  none  Utilities aplay,arecord,amixer etc    [Tools (alsa-tools)]("ftp://ftp.alsa-project.org/pub/tools/")  [1.0.21]("ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.21.tar.bz2")  none  Tools    [PyALSA (pyalsa)]("ftp://ftp.alsa-project.org/pub/pyalsa/")  [1.0.21]("ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.21.tar.bz2")  none  Python bindings for ALSA lib    [OSS compat lib (alsa-oss)]("ftp://ftp.alsa-project.org/pub/oss-lib/")  [1.0.17]("ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.17.tar.bz2")  none  OSS compatibility library 

Am I right in thinking I should be downloading everything here?

Sorry if I'm being a bit hopeless, but I'm starting to feel like I've started a new job that I don't really have the skills for.  :-(

Perhaps I don't really need sound.  I could just turn the radio on.  Or hum.

- Chris

---

### Post by chris282 on 2009-12-05
Oh, for the love of...

That mess of information was in a table format when I pasted it:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

You'll excuse me while I kick my computer into twisted pile of wires and circuitry.

Ta.

- Chris

---

### Post by endBc on 2009-12-05
```
sudo adduser $USER audio

```

Restart your PC and let us know whether you still have this problem or not.

---

### Post by chris282 on 2009-12-05
But... but... that was impossibly simple.  Almost embarrassingly so.

endBc, you are a marvel.  May your camels be fruitful and multiply.

I am filled with joy and good feeling for the world once again, as illustrated: :D

- Chris

---

