---
title: "Rhythmbox and wma plugin"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-08-14
I installed the Medibuntu package and followed the instructions from here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

when trying to add the GPG Key in the terminal this happens:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: You may want to run apt-get update to correct these problems


Any ideas anyone?

---

### Post by zvacet on 2009-08-15
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys EF4186FE247510BE
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
```

---

### Post by colau on 2009-08-15
@MattDobson
Ready to go for the above command!

---

### Post by Dobbie03 on 2009-08-15
Awesome thank you.  The keyring etc worked but I still cant find any codec that works.

Any ideas?

---

### Post by zvacet on 2009-08-15
You will find in synaptic w32 ( or w64 if you use 64 bit version)codecs.Install them.For other codecs **applications>add/remove>all available programs>other>ubuntu-restricted-extras**.Or you can go applications>accessories>terminal and type

```
sudo apt-get instal ubuntu-restricted-extras
```

---

### Post by Dobbie03 on 2009-08-15
> **zvacet said:**
> You will find in synaptic w32 ( or w64 if you use 64 bit version)codecs.Install them.For other codecs **applications>add/remove>all available programs>other>ubuntu-restricted-extras**.Or you can go applications>accessories>terminal and type

```
sudo apt-get instal ubuntu-restricted-extras
```

Thank you so much, that did the trick.

---

### Post by Dobbie03 on 2009-08-15
I am about ready to give up, once again Rhythmbox didn't recognise my wma plugin.  I am starting to get bloody frustrated.

---

### Post by jaqrah on 2009-08-15
I don't have an Ubuntu answer for you.

But, I do have a solution.  Rid yourself of a Windows proprietary file format.](*,)  Convert your WMAs to MP3s.  It will save you further headaches in the future.:biggrin:

Sorry...I couldn't resist.:-\"

---

### Post by colau on 2009-08-15
> **MattDobson said:**
> I am about ready to give up, once again Rhythmbox didn't recognise my wma plugin.  I am starting to get bloody frustrated.
Did you do this?
```

sudo aptitude install w32codecs

```

---

### Post by mc4man on 2009-08-15
rhythmbox will play some wma's
It will play wma2 and should play wma3(pro)
It will not play wma lossless (unless you purchase windows media pack from fluendo

Make sure you have the gstreamer plugin 'pitfdll' installed (( search gstreamer in synaptic, you'll see it there

or this (( I'd search and ck. other plugins - this one allows use of w32codecs for gstreamer apps
```

sudo apt-get install gstreamer0.10-pitfdll
```

---

### Post by Dobbie03 on 2009-08-15
> **jaqrah said:**
> I don't have an Ubuntu answer for you.

But, I do have a solution.  Rid yourself of a Windows proprietary file format.](*,)  Convert your WMAs to MP3s.  It will save you further headaches in the future.:biggrin:

Sorry...I couldn't resist.:-\"

Ha you speak the truth, maybe I should just do that.


@ mc4man and colau:  thanks guys, still didnt work

---

### Post by mc4man on 2009-08-15
> still didnt work
Do you have any means or know what type of wma you have? Or want the means to do so?

edit
try r. clicking -> properties -> audio and see if it identifies type

---

### Post by Dobbie03 on 2009-08-15
this is what I found under properties:

Windows Media audio (audio/x-ms-wma)

does that help?

---

### Post by ad_267 on 2009-08-15
Do you get a message about the files being encrypted if you try to open them with Totem?

It's impossible for Ubuntu to play WMA files that have been encrypted with DRM.

---

### Post by Dobbie03 on 2009-08-15
> **ad_267 said:**
> Do you get a message about the files being encrypted if you try to open them with Totem?

It's impossible for Ubuntu to play WMA files that have been encrypted with DRM.

Hello fellow Kiwi.  No I dont.  Basically what happens is that RB asks to search for the codec, it searches and says it can't find any codecs that match.  None of my WMA files are encrypted.

---

### Post by mc4man on 2009-08-15
click on the audio tag in properties
I usually use mediainfo or ffmpeg to check media but it's showing up here fine in properties. (at least some of the info

edit 
got to go but while I don't use rhythmbox as said it can handle all but lossless. Even does a decent job with 6 ch. wma3(pro) audio streams

screen shows 1st. track is wma2, 2nd wma3, third lossless with is rejected

All wma (including lossless) can easily be converted to whatever you wish
Soundkonveter can do wma2 and wma3 and retain tags. Lossless will need other means

---

### Post by Dobbie03 on 2009-08-15
Sorry I should have made it clear I am using Crunchbang, all that comes up is what I posted as far as properties info goes.

---

### Post by mc4man on 2009-08-15
Didn't see your reply will editing, so quickly
if you install ffmpeg you can get some info by this

ffmpeg -i /path/to/[COLOR="Blue"]whatever[/COLOR].wma

Easiest way would be to copy one to home folder, rename 1.wma and then in terminal go 
```
ffmpeg -i 1.wma
```

0x161 = wma2
0x182 = wma3
0x163 = wmal (lossless

how to install medianfo
[http://ubuntuforums.org/showthread.php?p=7717866#post7717866](http://ubuntuforums.org/showthread.php?p=7717866#post7717866)

Gstreamer may use the ffmpeg plugin for wma2, find with other gstreamer plugins
Also search ffmpeg in synaptic and install the unstripped libavcodec52  if not already.  (( don't uninstall current libavcodec, just mark the unstripped one for install and apply

---

### Post by Dobbie03 on 2009-08-15
****, I cant work it out, I am going to bite the bullet and convert them all.
Cheers mc4man for you help :)

---

