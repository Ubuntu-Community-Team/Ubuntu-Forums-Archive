---
title: "Remix or 8.04?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Drjim on 2009-12-09
I'm in the process of buying a netbook and want to set it up with partitions to dual boot windows or ubuntu. 

I know that remix is designed for netbooks. On the other hand, I know that 8.04 has been around for awhile and is considered more stable. As some of you may be aware, I've had some trouble with my system freezing while running 8.04 using a wubi setup within windows. 

Does anyone have info on how stable remix is? Is it totally new/experimental? Will I be tossing the dice using remix or is it fairly stable on a netbook?

Any idea how 8.04 runs on a netbook? Are there a lot of advantages to running remix on a netbook as opposed to a standard vs of ubuntu?

Thanks,

Jim

---

### Post by beastrace91 on 2009-12-09
If you plan to run Ubuntu on a netbook I would **strongly** recommend from personal experience you use at least 9.04 or later - as netbooks use more recent hardware they have much better support for them with the later Ubuntu versions.

That being said both 9.04 and 9.10 are stable, but when I doubt I always suggest using the release just before the latest as it has had more time to mature but still has most current features that Ubuntu has to offer.

Regards,
~Jeff

---

### Post by raymondh on 2009-12-09
> **Drjim said:**
> I'm in the process of buying a netbook and want to set it up with partitions to dual boot windows or ubuntu. 

I know that remix is designed for netbooks. On the other hand, I know that 8.04 has been around for awhile and is considered more stable. As some of you may be aware, I've had some trouble with my system freezing while running 8.04 using a wubi setup within windows. 

Does anyone have info on how stable remix is? Is it totally new/experimental? Will I be tossing the dice using remix or is it fairly stable on a netbook?

Any idea how 8.04 runs on a netbook? Are there a lot of advantages to running remix on a netbook as opposed to a standard vs of ubuntu?

Thanks,

Jim

Jim,

I like the LTS versions, though I have also used the 6-month versions. The new LTS (lucid) is scheduled for April 2010 (4 months away).  An LTS version focuses more on stability.

If you are hesitant on 8.04 (and given that the netbook may be newer than year 2008 ),  why not try 9.04 DESKTOP.  If you want REMIX, you can now add it thru synaptic as UNR is in the repos (unlike before).

My MSIWind now uses 9.04.  I had problems with Karmic and X and decided to go back to Jaunty and just prepare for Lucid.  I tried UNR (with 8.10) and decided that I preferred the regular desktop.

Your previous freezing problem with 8.04, was it because of the version or was it because of WUBI?

Regards,

---

### Post by Drjim on 2009-12-09
[QUOTE=raymondh;8472645]Jim,


Your previous freezing problem with 8.04, was it because of the version or was it because of WUBI?

Hi Raymond,

I still haven't figured out the problem with the freezup. Does anyone know if this is a problem with wubi? When I set up my netbook, I'll have nothing else on it and it should be pretty easy to set up actual partitions with dual boot.

Raymond, do I understand correctly that you have Ubuntu set up on a netbook?

Jim

---

### Post by raymondh on 2009-12-09
> **Drjim said:**
> [QUOTE=raymondh;8472645]Jim,


Your previous freezing problem with 8.04, was it because of the version or was it because of WUBI?

Hi Raymond,

I still haven't figured out the problem with the freezup. Does anyone know if this is a problem with wubi? When I set up my netbook, I'll have nothing else on it and it should be pretty easy to set up actual partitions with dual boot.

Raymond, do I understand correctly that you have Ubuntu set up on a netbook?

Jim

Yes, I have 9.04 on my MSIWind U100 .... along with win7 pro and OSX 10.5 (a triple boot configuration).  Jaunty is 99% working out-of-the-box.  My only challenge is this darn BISON webcam.

On a side note, since alpha 1 (for 10.04 LTS) will be released in a few days, I am now preparing another partition to install and start tweaking it.

I had a short adventure with WUBI installs.... just to see what the hoopla was all about.  I found out that my wubi-installed Ubuntu (and its' dependability) relied heavily on a clean, healthy and defragged windows.  I am not knocking WUBI.  It's a great tool to experience Ubuntu.   I just prefer to have Ubuntu/linux in it's own partition.

Regards,

---

### Post by SpeechABZ on 2009-12-10
Currently running Karmic UNR on a Toshiba NB200 netbook and finding it pretty good!

Previous I was running Jaunty UNR and personally I'm liking the look and feel of Karmic a bit more than I was with Jaunty (however only really used it for about a month - noob to Ubunu here!!).  As for issues, so far the only thing that I can see that doesn't work out of the box is sound through the in-built speakers but this is a pretty specific issue to the Toshiba netbooks, check out the UNR wiki pages for a list of netbooks which will run perfectly out of the box with Ubuntu if you are going out to buy one with running Ubuntu on it in mind.

As for differences and whether to go for standard desktop or the Netbook Remix that's pretty much personal taste as far as I can see.  Basically the UNR has a tweaked UI that makes it easier to use on the small screens that netbooks come with.  Best bet is to download it onto a USB drive and try it out first to see if UNR is for you - also worth noting is that once you have installed UNR you can swap the UNR interface for the traditional desktop interface and back again, so if you decide after a while that the UNR look isn't for you then you can swap over to standard desktop look! ;)

---

### Post by 3rdalbum on 2009-12-10
8.04 will probably be useless on today's netbooks. It was pretty much useless on netbooks released this time last year.

Try 9.10 for the better hardware support. It doesn't matter if your use Netbook Remix or just the ordinary Desktop version. Ubuntu Netbook Remix is just the ordinary desktop version but with a different GUI.

---

### Post by Drjim on 2009-12-10
Thanks especially for the tip about the UNR wiki list of compatable netbooks! It would have been a drag to end up with one of the 3 tier netbooks and I'm planning on buying today.


Jim

---

### Post by fooman on 2009-12-10
unr 9.10 on my hp mini 1035n runs great....everything works out of box!

had problems with both wireless and sound with 9.04....i quickly ditched that in favor of a remix made just for the hp minis:  [hp mini remix]("http://http://psychocats.net/hpminiremix/download/") ...it is based on 9.04 with some fixes for the sound & wireless.  that one also worked 100% out of box.

---

### Post by Drjim on 2009-12-13
> **raymondh said:**
> [QUOTE=Drjim;8472742]


I had a short adventure with WUBI installs.... just to see what the hoopla was all about.  I found out that my wubi-installed Ubuntu (and its' dependability) relied heavily on a clean, healthy and defragged windows.  I am not knocking WUBI.  It's a great tool to experience Ubuntu.   I just prefer to have Ubuntu/linux in it's own partition.

Regards,

Raymond,

Thanks for the tip about windows health. I had thought that Norton 360 was automatically defragging and doing registry fixes. I was wrong! I did them manually as well as running chkdsk. Now Windows is running much faster. I have yet to see if Ubuntu is doing better. I won't really know until I run it for a few days with no freeze-ups. 

Thanks again,

Jim

---

