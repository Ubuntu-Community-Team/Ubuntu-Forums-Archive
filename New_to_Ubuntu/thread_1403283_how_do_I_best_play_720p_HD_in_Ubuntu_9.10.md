---
title: "how do I best play 720p HD in Ubuntu 9.10?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-02-10
I have downloaded some 720p movies, but neither VLC nor MPlayer are capeable of reading the files? Have anybody any tips on which player is best suited for this? and if anybody have any tip on a good working mediacenter (XBMC f.ex) I would be very happy....:)

---

### Post by nhasian on 2010-02-10
you forgot to mention one crucial piece of information.  what the heck file type are you trying to play?  VLC plays everything i've ever thrown at it.

---

### Post by Greenwidth on 2010-02-10
Whats the problem with playback?
You might not have the codecs, see Medibuntu howto:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Or do you mean you get choppy playback?

XBMC ppa:
[https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

---

### Post by tweety_r78 on 2010-02-10
Umm, I don't have the files I downloaded on this computer, so I have to get back to you on that. The only thing I know is that they are 720p, and there should be nothing wrong with the files...

But yes, I do get choppy playback... There is sound but the picture is choppy and it keeps stalling...

...and I'm very new to Ubuntu, so I need the information with teaspoons...:)

---

### Post by audiomick on 2010-02-10
Hi.
Just to exclude the possibility of the problem being too few resources, please post the specifications of your computer, i.e. CPU, RAM, Graphics card

---

### Post by Greenwidth on 2010-02-10
Ok so it sounds like you have the codec you need to play the files as you get sound and picture.

Do you have the driver for your graphics card installed? Look in:
System > Admin > Hardware Drivers

---

### Post by tweety_r78 on 2010-02-10
I have an Acer Revoulution 3600:

[LIST]
[*]Spesifications: 1 Liters Ultra Small Form Factor Kabinett
[*]CPU : Intel® Atom™ 230 processor
[*]Chipset : NVIDIA® ION™ chipset
[*]Memory : 2 GB 2 DDR
[*]Harddisc : 160 GB S-ATA 3.0Gb/s
[*]Grafic card : NVIDIA® ION™ graphics solution
[*]Soundcard : High-definition audio support
[/LIST]
did that help?

---

### Post by audiomick on 2010-02-10
Ok, so it looks like the computer should be able to manage ok.
What about Greenwidth's question about the graphics driver? You have an nVidia graphics card; have you got the driver for it enabled?

Also, it looks like your case is a very small one. Is it properly ventilated?

---

### Post by tweety_r78 on 2010-02-10
Yes I've upgraded my Nvidia card, and enabled it. I think I have version 190. something.
And the machine is very well ventilated. Both sound and picture works very well with "regular" movie files. It is only the 720p I have a problem running on the machine...

---

### Post by audiomick on 2010-02-10
Ok, so maybe it really is a codec issue. I think you will have to have another look at exactly what the file format is.

Greenwidth posted a link to the XBMC ppa, from which you could install that (I don't know what that is, I presume a player).

---

### Post by Greenwidth on 2010-02-10
I would give XBMC a try, it runs well on my netbook which has similar specs, and uses VDPAU (190 driver onwards) to offload to the graphics card.

To use the XBMC ppa:
open Synaptic (System > Admin > Synaptic)

Settings > Repositories > Other Software tab > Add button
paste: ppa:team-xbmc/ppa

Reload

Quick search for xbmc, install, enjoy :)

---

### Post by Menthu_Rae on 2010-02-10
You need to have the nvidia restricted drivers and vdpau installed and use a player that supports VDPAU (such as XBMC or mplayer). You will then be able to play 720p with very low CPU usage since decoding will be offloaded to the GPU (codec dependent)

---

### Post by tweety_r78 on 2010-02-10
great!! Thank you all. I'll try downloading XBMC when I get home...:)

---

### Post by 3rdalbum on 2010-02-10
> **Menthu_Rae said:**
> You need to have the nvidia restricted drivers and vdpau installed and use a player that supports VDPAU (such as XBMC or mplayer). You will then be able to play 720p with very low CPU usage since decoding will be offloaded to the GPU (codec dependent)

+1

Another tip that surprisingly works is to turn off Compiz (i.e. hit Alt-F2 and type "metacity --replace"). Compiz adds a fair amount of overhead to video playback, which can often be the difference between smooth video and jerky video. Intel Atom CPUs are not powerful, so you may need to turn off Compiz AND use a VDPAU-capable player.

---

