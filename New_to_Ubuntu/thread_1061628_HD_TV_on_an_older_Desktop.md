---
title: "HD TV on an older Desktop"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by dave00001 on 2009-02-06
I've been using Ubuntu (almost exclusively) for over 2 years now on an old box I bought for school in 2002, and looking to see what the possibilities are for digital and HD TV viewing over the air.  I've been using an analogue tuner running TVTime for the past year - and it works just fine - but I've just moved and not looking to buy into any of the cable packages that will cost upwards of $30/mo.  Also, with the switch over to digital, this seems like a good opportunity....

More specifically, I'm looking for advice on 

a) a tuner card that will capture lots of channels (HD or not)
b) whether or not I should upgrade my system
c) programs to watch tv on.

I know there are some programs (MythTV?) that are capible of recording - but for me the most important thing is just to be able to watch live TV.  Not sure whether TVtime can do this for me with HDTV, so your opinions are welcome.  

My system specs (without opening the box :) ) are:  Pentium 4 2.0GHz, 1.2 Gb RAM, Nvidia GEforce 6???, hauppage analogue tuner (winTV go plus?).  PCI slots (lots of them).  80Gb HDD.

I would LOVE to be able to get Mythtv or Mythbuntu, but I have no idea whether my system can handle it. It seems like it would be too taxing for my outdated box...  Keep in mind that cost is also an issue...

Let me know what you think!

---

### Post by cariboo on 2009-02-06
The way I understand it, when the switch over is made to DTV the analog channels will no longer be available. So what ever DTV channels you can get over the air is all you are going to get.

I don't know how it is down south, but my cable company keeps calling me up and offering some really smokin' deals if I add cable TV service to my cable internet account. The last time they called they offered an HD DVR for free along with the service.

I've seen the HD cable offerings on an HD TV, and the quality is not much better than analog TV. I have an HD DVR hooked to a satellite system, I get more channels and  the digital channels are better than the cable company's hd offerings, and HD is just incredible. 

Jim

---

### Post by dave00001 on 2009-02-06
Thanks for the reply!

The cable offers here are not that bad, but I've heard of many people getting over the air (OTA) channels with good reception... I've heard people say they get 5 or 6 HD channels as well as a number of digital channels on a basic, well placed antenna (on an HD ready TV, of course).  

As I am a student still, I don't have a TV - just a desktop with a rather large monitor.  Have you ever tried capturing OTA signals with an HD tuner?  I'm really just looking to see if anyone has done this before, and what kind of advice they can give me...

Thanks!

---

### Post by punx45 on 2009-02-06
for an HD tuner i would go with this:

[http://www.pchdtv.com/](http://www.pchdtv.com/)   i dont have one, but if i were to get an HD tuner, that would probably be it.

it captures NTSC/ATSC and QAM, so all your bases are covered for reception.   that will get you any OTA signal, as well as unencrypted digital cable signals both SD and HD if you ever have cable in the future

OTA reception totally depends on your distance from transmission towers, and the topography of your area.   i have heard though, that most broadcasters will be improving signal strength after the transition on the 17th.

also, myth tv is pretty light, its basically a graphical front end for a SQL database and video playback.   but if you only plan on watching live TV its a bit of overkill.   i run it on the mythbox system listed in my sig.  with 512MB ram.

---

### Post by cariboo on 2009-02-06
I live in an area where you can't even receive a regular NTSC signal over the air, even if I could there is only two channels available, neither of which have any intention of changing to DTV let alone HD TV. I live half way between the Washington State and Alaska borders, so we don't have to put up with the change the way you have to down south.

Jim

---

### Post by emarkd on 2009-02-06
Your box is not even close to being too outdated for mythbuntu.  I run it on a 8-year-old 1 GHz P-3 box with 512 MB ram.  You can tell it's an older box while its booting, but once its up it runs great - at SD resolution, at least.  Give it a shot.  I bet you'll be surprised at how lightweight it is.

---

### Post by dave00001 on 2009-02-08
Thanks for the help!  (Note to cariboo907, I just moved from the great white north - which is why I'm stuck with this (soon-to-be) useless analog tuner!

punx45 - Since I've never tried mythTV before, any words of advice?  I'm thinking that if my system can handle it, I may opt for a 1TB hard drive to go with the tuner...  I appreciate any help!

---

### Post by punx45 on 2009-02-08
yeah, if this isnt your main box, (or even if it is and you dont mind a fresh start) i would suggest going with a prebuilt distro like mythbuntu or mythdora, just because alot of the dirty work will be done for you already.  

the extra HDD space definitely cant hurt, especially if you are encoding in HD (about 4GB/30 min) and the one thing i wish i had on my system was a 2 disk setup, one for the OS and one for the recordings.   a single disk can get thrashed pretty hard handling both.   i have occasional hard crashes and i suspect this may be the cause.

---

### Post by dave00001 on 2009-02-08
This is my only box, so it will have to do.  I'm going to do a clean wipe, and try out mythbuntu this coming week after I find the hardware.  It looks like there's room for another hard drive as well, so I'll follow your advice about the OS on the smaller one.

Wish me luck!

---

### Post by dave00001 on 2009-02-17
Ok - so I just bought the pcHDTV tuner today...  should arrive in the mail shortly!  Thanks to all for your help and I will keep you updated on the results.

PS - does the tuner come with a remote?  If not, can anyone comment on the usability of MythTV with a simple wireless mouse and keyboard?

Thanks!

---

### Post by dave00001 on 2009-03-01
So - I have the tuner in the box - and though the mythbuntu installation is quite cumbersome I suspect I have the correct drivers and have set up the backend to the best of my knowledge.  However I am having trouble viewing live HDTV - it seems to be stuttering every seconds or so...  I actually put up another thread without thinking on the forums here: 

[http://ubuntuforums.org/showthread.php?t=1080988](http://ubuntuforums.org/showthread.php?t=1080988)

Anyway I suspect that the problem is in my processor.  I've heard ~3GHz is the norm for viewing or playing HDTV.  I really don't want to have to buy a new system - possibly getting XmVC to work is an option??


EDIT - I figured it out - needs XvMC to work properly.  Even with this I am almost at 100%, but at least I can watch live TV without stuttering.

---

