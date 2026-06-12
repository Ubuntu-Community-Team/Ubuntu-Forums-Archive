---
title: "Movie Player"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-10-31
What plugins do I need to get Movie player to actually play movies?  I've tried several DVDs and I get nothing but a notice saying Movie Player needs more plugins, no indication of which plugins or anything useful,  just kvetching about needing plugins.

---

### Post by dj-toonz on 2009-10-31
to play everything under the sun & listen to anything under the sun i.e mp3's you name it, goto Applications, accessory , Terminal & type in what I'm about to post

sudo wget [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list) --output-document=/etc/apt/sources.list.d/medibuntu.list                                ** this enables enables the medibuntu repo so you can download the nonfree codecs & DVD stuff


or substitute the karmic for jaunty if your using that 

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


sudo apt-get install ubuntu-restricted-extras sun-java6-jre sun-java6-plugin sun-java6-fonts msttcorefonts non-free-codecs libdvdcss2 w32codecs

---

### Post by phillw on 2009-10-31
> **Gulfvet91 said:**
> What plugins do I need to get Movie player to actually play movies?  I've tried several DVDs and I get nothing but a notice saying Movie Player needs more plugins, no indication of which plugins or anything useful,  just kvetching about needing plugins.

Hi,

It is a problem with proprietary drivers 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

should get you up and running.

Regards,

Phill.

---

### Post by dj-toonz on 2009-10-31
What I've posted will let him play everything in movie player no problem as there everything anybody needs to listen to anything, watch anything i.e DVD's , the full works, flash, java, you name it

---

### Post by Gulfvet91 on 2009-10-31
> **dj-toonz said:**
> What I've posted will let him play everything in movie player no problem as there everything anybody needs to listen to anything, watch anything i.e DVD's , the full works, flash, java, you name it 

 I notice you said something about "non--free" format.   Does this mean I need to pay a fee of some sort?

---

### Post by bandgeek on 2009-10-31
non-free simply means there are commercial copyrights for those programs. Remember free in the open source community means as in speech not beer.

---

### Post by dj-toonz on 2009-10-31
> **Gulfvet91 said:**
> I notice you said something about "non--free" format.   Does this mean I need to pay a fee of some sort?

No you don't need to pay for anything as the poster above put

---

### Post by Gulfvet91 on 2009-10-31
I used second string you sent since I am using Xubuntu 9.04.  I found Xine in my multimedia folder but it still won't play my DVD.  It says I may not have the rights to this DVD and some other junk.  I noticed during the install it said it souldn't locate keyring.  I'm also having fun with disk drive.  When I try to eject it says:  failed to eject "org/freedesktop/Hal/devices/storage_model_CDRW_DVDSBW242C."  What da heck?  When I tried to play the disk it knew it was Rio Bravo!

---

### Post by Gulfvet91 on 2009-11-01
All is well!  Apparently it was a permissions problem but now it works.  Thanks all!

---

