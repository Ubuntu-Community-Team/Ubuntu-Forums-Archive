---
title: "Dvd Rip - Creating DVDs"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-03-01
Hi all, hope your all well.

I have a quick question (I hope).

Im trying to create a dvd. Using Dvd Rip and K3B.

I have used Dvd::Rip to to rip the origional. (I left the settings at thier defaults).

It seemed to go well, after 20 mins I have a new folder with a bunch
of VOB files. (& they seem to work well as stand alone files. I can
watch them fine in vlc or totem).

However When I try to "Create a new dvd project" in K3b (I put the VOB
files in thier respective "Video_TS folder" on the disc.
But When I go to burn the disc I get the following error messages =

i - The project does not contain all the necessary VideoDVD files

i - The resulting DVD will most likely not be playable on a HIFi DVD
    player

x - Could not determine the size of resulting image file


Does anyone have any ideas where Im going wrong?



Ive included the resulting error de-bug report file as an attachment.


Thanks in advance for any help or advice.

---

### Post by mc4man on 2009-03-01
Never used dvd::rip so not sure what it's doing, but you need a VIDEO_TS.VOB and one .ifo, .bup for that .VOB and for each titleset.
Here's an example listing
> :~/WHATEVER/VIDEO_TS$ find  *
VIDEO_TS.BUP
VIDEO_TS.IFO
VIDEO_TS.VOB
VTS_01_0.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_01_1.VOB
VTS_01_2.VOB
VTS_01_3.VOB
VTS_01_4.VOB
VTS_01_5.VOB
VTS_01_6.VOB
VTS_01_7.VOB
VTS_02_0.BUP
VTS_02_0.IFO
VTS_02_0.VOB
VTS_02_1.VOB
VTS_03_0.BUP
VTS_03_0.IFO
VTS_03_0.VOB
VTS_03_1.VOB

You could read the guide here
[http://www.exit1.org/dvdrip/doc/index.cipp](http://www.exit1.org/dvdrip/doc/index.cipp)

Or maybe try k3b itself or k9copy (or other means

---

### Post by GeordieJedi on 2009-03-01
@ mc4man

Thanks mate. I've allready tried just using K3b, but the burn keeps
failing about 1/2 way through.

I'll take a look at your reccomendations.
Cheers

---

### Post by cjv8888 on 2009-03-01
I think DVDRIP is for making an AVI file from a DVD. To make a copy you may need DVD9to5 or DVDShrink under Wine.

---

### Post by MrWES on 2009-03-01
> **cjv8888 said:**
> I think DVDRIP is for making an AVI file from a DVD. To make a copy you may need DVD9to5 or DVDShrink under Wine.

Or K9Copy -- which will rip DVDs to an iso file (DVD5) and then you can burn the iso with K3B.

Bill

---

### Post by handy on 2009-03-01
I've been using DVDShrink 3.2, since it was created which is probably over 4 years ago, & I used the previous versions too.

It is simple as fast as anything else at ripping a DVD & shrinking it to single layer size DVD media.

I have tried the various native burners & found them unreliable if I am burning a lot of disks one after the other.  

For anyone else who experiences that problem I have to recommend NeroLinux, which costs a little, (not very much), & is perfectly reliable, on my hardware anyway.

---

### Post by handy on 2009-03-02
My apologies, I should have stated in the previous post, that DVDShrink is freely available software built to run on windows.

DVDShrink runs perfectly via Wine, & couldn't be easier to install in Wine.

---

### Post by halitech on 2009-03-02
> **MrWES said:**
> Or K9Copy -- which will rip DVDs to an iso file (DVD5) and then you can burn the iso with K3B.

Bill

+1

I started using it a few months back and haven;t found a dvd yet that it won't copy and burn using k3b

---

### Post by handy on 2009-03-03
> **halitech said:**
> +1

I started using it a few months back and haven;t found a dvd yet that it won't copy and burn using k3b

I had no problem with k3b either until I start getting into burning 10 or 15 or more disks in a row.  Then it became unreliable on my systems.

---

### Post by halitech on 2009-03-03
don't know if I've ever burned 10 or more dvds in a row but I have certainly burned more then 20 dvds before doing a reboot as I usually reboot about once a month and burn on average 2 dvds a day lately. Actually I did burn 14 in a day once but don't recall having a problem then either. Maybe I just have the right combination of hardware and software installed.

---

### Post by handy on 2009-03-03
> **halitech said:**
> don't know if I've ever burned 10 or more dvds in a row but I have certainly burned more then 20 dvds before doing a reboot as I usually reboot about once a month and burn on average 2 dvds a day lately. Actually I did burn 14 in a day once but don't recall having a problem then either. Maybe I just have the right combination of hardware and software installed.

Yes, I think the responsibility for this problem would be found in the big bucket of mysterious combinations also... ;)

---

### Post by GeordieJedi on 2009-03-05
Cheers Lads!

Your help is very much appreciated. :D

I've downloaded K9copy and I'll give it a whirl.

---

### Post by GeordieJedi on 2009-03-12
Wow. K9Copy is awesome!

That really solved my issue. thanks very much indeed to you all =

MrWES
Handy
halitech
cjv8888
mc4man

Its much appreciated! :D


Ive tried to Thank you each individually however I cant find the
"Thanks" icon any more. (I am running "No-script" though, but I set
it to allow the Ubuntu forums??...Very strange)

---

### Post by halitech on 2009-03-13
Glad to hear you got everything working :)

I think the admins disabled the thanks button awhile ago, I haven't seen it and I remember someone else saying it had been disabled for some reason.

---

