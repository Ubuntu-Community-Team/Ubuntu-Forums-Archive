---
title: "Starting over"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Revord on 2010-04-09
Im looking to get a fresh start with Ubuntu. Ive been trying to get the newer distros to work for me, but Im afraid my hardware isnt up to the task because of age. Im not going to be upgrading any time soon, so here is the question of the hour:

My weakest link is my video card. I have an ATI Radeon X1650 pro. It works great with windows, but not so good with the newer versions of Ubuntu. I have a Athlon x2 64 bit processor with 1.5 gig ram. Also, I have a 50 gig hard drive to dedicate to the cause, along side of my xp drive. What distro can I use that will give me the best results. I have tried 9.1 and 10.04, and they wont recognize my card.

Thanks in advance.

---

### Post by mbzn on 2010-04-09
ATI stopped linux driver support on their older cards. I would go buy a cheap nvidia card and just upgrade that if i need it to run compiz or 3d thingy's.

---

### Post by Revord on 2010-04-14
Sorry for the long delay, I was hoping there would be more ideas, however, I think I probably was not clear enough in my op to get the ideas Im looking for.

Upgrading is a no go. I have an agp system, and the card I have is probably the last one ATI made for agp. In order for me to upgrade the card (please correct me if Im wrong) I would have to upgrade my entire system. Not going to happen. 

While I do understand that ATI has stopped supporting their legacy cards, they do have a driver available for download on their website. The problem is that the newer versions of Ubuntu dont play at all with these legacy cards.

Is there an older release of Ubuntu that will allow me to use this legacy card? What really stinks about this is I really want to go full on with linux, but my 'antiquated' system wont allow me to. I dont mind going as far back as 8.04 or even further if it means that I will be able to start using linux on a more consistent basis. XP is a dying os. I would really like to get onto something more stable, and better built, and when I do upgrade my entire system, I want to be ready for the newest releases available.

Thank you in advance for the time to read this post.

---

### Post by WinterRain on 2010-04-14
8.04 would be a good choice since it will support older ati cards. Then you could just upgrade through the update manager.

---

### Post by quadproc on 2010-04-14
> **Revord said:**
> ...
Is there an older release of Ubuntu that will allow me to use this legacy card? What really stinks about this is I really want to go full on with linux, but my 'antiquated' system wont allow me to. I dont mind going as far back as 8.04 or even further if it means that I will be able to start using linux on a more consistent basis. XP is a dying os. I would really like to get onto something more stable, and better built, and when I do upgrade my entire system, I want to be ready for the newest releases available.
Probably your biggest issue is the availability of the appropriate ATI driver.  I think that ATI's version 9.3 is the latest which will work with your card but you should check ATI's information to be sure.

In any event, if you are running older ATI drivers then you cannot run a newer version of X windows than what came in Ubuntu 8.10.  There was a substantial and completely incompatible design change between the versions of X windows in 8.10 and 9.04.

I am not sure where the FOSS effort will take the open source ATI driver.  You might want to do some web searching to see what is going on in that area.  ATI did something which, IMHO, is really nice and useful - they released specifications on how to software interface to their video hardware!  This is allowing the open source people to make a lot of progress.

At this point in time, I would suggest that youget a copy of whatever releases you can find that will work for you, and keep them safely stored.  The older versions will probably become unavailable from their original providers.

quadproc

---

### Post by achase79 on 2010-04-14
there are good inexpensive Nvidia agp graphics cards out there, they are just not as common, because they are older tech.  You may put out a request on freecycle in your area and get a used one for free.

---

### Post by WinterRain on 2010-04-14
[Here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814143102") is an Nvidia 7300GT AGP card for $70. It will run on the latest ubuntu.

---

### Post by Jeanke on 2010-04-14
I also have an Ati Radeon X-series card.
In Ubuntu 10.04 these older cards are supported by open-source drivers.

Because these cards were not supported (or at least not fully) in Ubuntu 9.10 I took the risk and already upgraded to the beta2 version of Ubuntu 10.04.
After some upgrades (Using packages from the xorg-edgers PPA) I was able to turn on the full Visual Effects with good results.

For documentation see:
[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

---

### Post by cascade9 on 2010-04-14
> **WinterRain said:**
> [Here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814143102") is an Nvidia 7300GT AGP card for $70. It will run on the latest ubuntu.

$70 for that? *disgusted look* AGP prices arent getting any better, and that is boderline robbery. 

You could also run a PCI card, and while the prices there arent much better you could get much newer 9400GT for less...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187057](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187057)

Even a 8400GS would work, and are slightly cheaper.    

> **quadproc said:**
> I am not sure where the FOSS effort will take the open source ATI driver.  You might want to do some web searching to see what is going on in that area.  ATI did something which, IMHO, is really nice and useful - they released specifications on how to software interface to their video hardware!  This is allowing the open source people to make a lot of progress.

True, but for ubuntu its going to take a long time for the newer open-source drivers to filter down. Some other distros (mainly rolling release) will get them much faster.

---

### Post by Revord on 2010-04-23
Thank you everyone for you input. I went with installing 8.04. Runs stable, I get full support for my card, everything. Yeah, its a 2 year old os, but its better than running a 10 year old os huh :) Anyhow, sorry I took so long to get back to you guys, I have been busy preparing for a trip, working over time, etc. Those of you who have driven cross country know about how that goes. Hopefully, when I get back there will be more news about steam porting to linux. Now that would be great!

P.S. I paid $45 for my card about a year and a half ago, so yeah, no more agp cards for me, this is it. Next card I get is going to be PCIe for sure, but with a new system built around it.

---

