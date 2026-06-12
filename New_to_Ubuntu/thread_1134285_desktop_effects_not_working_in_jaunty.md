---
title: "desktop effects not working in jaunty"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-04-23
Upgraded to jaunty today and I find compiz isnt working anymore.When I looked at visual effects I found it was set to 'none' and when I ticked extra which was on before,it looked for a driver and then said desktop effects could not be enabled.Even 'normal' wont work.Desktop effects worked in intrepid,why wont it work in jaunty?Is there a way to make it work?

---

### Post by kaixi on 2009-04-23
I experienced the same problems after applying some upgrades to Ubuntu 9.04 RC. I'm downloading right now the ISO and will make a fresh install to see what happens.

---

### Post by velislavv on 2009-04-23
> **gertrude58 said:**
> Upgraded to jaunty today and I find compiz isnt working anymore.When I looked at visual effects I found it was set to 'none' and when I ticked extra which was on before,it looked for a driver and then said desktop effects could not be enabled.Even 'normal' wont work.Desktop effects worked in intrepid,why wont it work in jaunty?Is there a way to make it work?
What model/brand is your videocard if its Intel X3100, then you VGA is blacklisted in compiz. More information [here]("http://ubuntuforums.org/showpost.php?p=3614750&postcount=2")

---

### Post by overdrank on 2009-04-23
> **gertrude58 said:**
> Upgraded to jaunty today and I find compiz isnt working anymore.When I looked at visual effects I found it was set to 'none' and when I ticked extra which was on before,it looked for a driver and then said desktop effects could not be enabled.Even 'normal' wont work.Desktop effects worked in intrepid,why wont it work in jaunty?Is there a way to make it work?

What is the model of the graphics card? That would be my first search of the forums :)

---

### Post by connel on 2009-04-23
hi i am having the same issue, (it worked fine in 8.04 for me also) is there a command i can use to find the model of my graphics card? thanks

---

### Post by kaixi on 2009-04-23
> **velislavv said:**
> What model/brand is your videocard if its Intel X3100, then you VGA is blacklisted in compiz. More information [here]("http://ubuntuforums.org/showpost.php?p=3614750&postcount=2")

That explains all. I've got an Intel 965 card. Now my question is: are there any plans from the Ubuntu team to fix this?

---

### Post by JK3mp on 2009-04-23
> **kaixi said:**
> That explains all. I've got an Intel 965 card. Now my question is: are there any plans from the Ubuntu team to fix this?

Umm...they always plan to fix every glitch for the most part. And its all just a matter of getting the correct propreitary hardware drivers and enabling them.

---

### Post by kaixi on 2009-04-23
> **JK3mp said:**
> Umm...they always plan to fix every glitch for the most part. And its all just a matter of getting the correct propreitary hardware drivers and enabling them.

No proprietary graphic card drivers is showing up in the Restricted Drivers Manager, as for now. :(

I don't remember having any problems with Compiz when I was running the RC (which didn't have the driver blacklisted). I wonder what's the problem.

---

### Post by JK3mp on 2009-04-23
Did you try googling for the right graphics driver ? Its usually a pretty easy process after finding the correct one. Whats the model of your gfx card?

---

### Post by rapachooie on 2009-04-23
I have a 3100 card and also had the problem.

Ever since switching to linux I have had lots of video problems, especially in ubuntu.

Tearing in video mostly.

Anyway its incredibly annoying and id like to know if/when theres a fix?

---

### Post by kaixi on 2009-04-23
> **JK3mp said:**
> Did you try googling for the right graphics driver ? Its usually a pretty easy process after finding the correct one. Whats the model of your gfx card?
Intel 965. I know it's blacklisted and I hope you fix this soon. Meanwhile, I'll patiently wait here.

---

### Post by nwadams on 2009-04-23
ya, nothing we can do about it right now. There is a way to force compiz to start but it may crash your system because compiz was blacklisted to increase stability while they fix the bug.

---

### Post by rabbit251 on 2009-04-23
> **velislavv said:**
> What model/brand is your videocard if its Intel X3100, then you VGA is blacklisted in compiz. More information [here]("http://ubuntuforums.org/showpost.php?p=3614750&postcount=2")

I have that card and the same problem. Glad there was the foresight to blacklist rather than leave the glitch.

What I don't understand is why these effects worked on the same machine in earlier versions of Ubuntu (Hardy, Intrepid). That blacklist post was made a long time ago. Can someone clarify this?

---

### Post by dejanh on 2009-04-23
Same here, just installed Jaunty coming from Ibex and perfectly working Desktop Effects to not being able to enable desktop effects.  I also have no Hardware Drivers listed at all and opening the Hardware Driver manager tells me that "No proprietary drives are in use on this system".  All NVIDIA packages seem installed properly.  I have a since GTX 260 card in my system that worked perfectly fine in the previous release.

Edit: Well, after running manual compiz --replace I got an error saying "No whitelisted driver found" or something like it.  Long story short, after a couple of tries searching the repository with the keyword nvidia I finally got the 180 driver as one of the options.  I installed it, rebooted, then went to Hardware Drivers section where the new driver now showed up, enabled the driver, rebooted, and then enabled Desktop Effects just fine.

Why the driver did not even show up in the list of possible drivers is very strange.  Even a bunch of searches did not return it with the same nvidia keyword.  Maybe the servers are too busy so there are problems with the repository?  Anyway, everything works now.

Maybe this can help somebody too :)

---

### Post by farooqmian on 2009-04-24
Can dejanh or anyone post a step by step for intel 965 card?

---

### Post by rapachooie on 2009-04-25
> **farooqmian said:**
> Can dejanh or anyone post a step by step for intel 965 card?

+1... but doubtful. dejanh was looking for nvidia drivers.

I have tried searching for other intel drivers and it seems to me that the only ones around are the open source ones released by intel (which I would think are very mature and good by now... but apparently not).

Anyway, I wouldnt mind a step by step either if anyone has one... Thanks in advance.

---

### Post by spaznrq on 2009-04-25
I'm just going to  wait patiently for the fix.  It seems that the problem started happening when Mesa upgraded, causing X freeze... anyway, I'm not going to repeat what was reported, but here's where this info came from: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392?comments=all]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392?comments=all")

I've tried enabling Compiz in 8.10 and I did indeed experience complete system freezing, so now that I have 9.04, I'd rather wait for the real fix rather than to use workarounds to enable pretty graphics.  There is a reason why it is still blacklisted.

I do hope we don't have to wait long enough for it that 9.10 will be out already, though...

---

### Post by rapachooie on 2009-04-25
I have an x3100 and problems I had were always related to video running through XVideo output as intel overlay (selecting +1 in VLC under xvideo) which I had to do to avoid tearing...

So I dont accept that last reponse because Ive been using Compiz (without any workarounds... it worked out of the box) for the past few months with no other problems besides tearing.

But I suppose we can keep on waiting, Ill just get a hobby and do something else at the same time.

---

### Post by Ratscallion on 2009-04-25
I probably fit into this category as well. I have was using Hardy until the Intrepid release, and Intrepid until the Jaunty release. I am using an Intel 965 Graphics Card (mobile), which worked very well using both Emerald and Compiz in Intrepid. In this case, very well means being able to run most the high usage plug-ins without hassle/flicker/judder etc... Anyway, I downloaded the Jaunty iso yesterday (Friday), and replaced the Intrepid install (after backing up my home folder) with the Jaunty one. I found out my Wireless card (which wasn't installed by default in Intrepid) is working out of the box in Jaunty... Excellent! However, when I go into the Visual Effects, I can't enable them... However, I went ahead and installed ccsm. After trying to enable some of the plug-ins, it gave an error message about "dbus not being enabled". This never happened in Intrepid...

---

### Post by gertrude58 on 2009-04-25
I've been reading all the responses to my original cry for help and the consensis of opinion seems to be that if your card is an Intel 965[which mine is] it's better to wait for a fix than to force Compiz to work and risk a crash.Am I right?

---

### Post by Ratscallion on 2009-04-25
> **gertrude58 said:**
> I've been reading all the responses to my original cry for help and the consensis of opinion seems to be that if your card is an Intel 965[which mine is] it's better to wait for a fix than to force Compiz to work and risk a crash.Am I right?
I went ahead and installed CCSM prior to realising my card was blacklisted. Because of this, I wanted it working (as it had been in Intrepid) I went onto one of the links in this thread, and used the code supplied to remove my card from the installed blacklist. So far, compiz is working fine, nothing has broken/been looking bad. So, I would say, if you have a good quality system, and are willing to take a risk - go ahead!

---

