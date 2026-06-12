---
title: "Total download failure w/Ubuntu 10.04"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Loren Bliss on 2010-07-10
Per the update manager, I downloaded Ubuntu 10.04, a next-iteration upgrade from Ubunto 9. whatever. But now I have no Windows capability; anything I downsize is closed and anything downsized without first being manually saved is lost beyond recovery. Needless to say this is terrifying because reading through various notes suggests this is hardware failure, which means not only being totally off-line for close to two weeks but a huge expense -- $300-$400 (in other words approximately 3/4ths the cost of a new computer) as well. Any help much appreciated.   

Thank you
Loren Bliss

---

### Post by Elfy on 2010-07-10
Before anyone is going to be able to help they will need to know some specs. 

You might be better of doing a clean install - making sure you backup any data you need, or indeed going back to 9.10 - same thing with backups.

As it stands people will be shooting blind till there is more information.

Boot with a livecd and run this 

```
lspci &&free -m
```


[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)


Edit - might be worth reading this to see if any of it might apply to you - [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by Loren Bliss on 2010-07-10
Thank you; I read the startup notes, which indicated the problem is a bad (obsolete) graphics chip. Is there any way I can go back to Ubunto 9.8? (I looked for instructions to do this but could not find them anywhere.) 

As to your suggestion I run a line of code, that is totally beyond me: I have no idea how to do that. I am a photographer/editor/writer -- an OLD photographer/editor/writer  (career began 1956) -- and have surrendered to computers only because they are the virtual equivalent of the Borg: "resistance is futile." 

That said, again thanks for any additional info/advice you can provide.

LB

---

### Post by Elfy on 2010-07-10
To go back to the previous version you need to reinstall.

You run the code in a terminal - in the Apps > Accessories menu, no need to worry about being anything other than waht you are - I was in the same boat 3 years ago :)

If you can run the livecd you used to install 9.10 in the first place you can access the information there.

If you do decide to revert to the previous version _then make sure you have backups_ as you will lose data.

---

### Post by Loren Bliss on 2010-07-10
No CD; this computer was set up for me by someone who later revealed himself as rather a bit less than well-disposed: apparently yet another manifestation of the well-documented and ofttimes extremely malicious Pacific Northwest hatred for New Yorkers and intellectuals in general. 

Hence what I may be battling is deliberate sabotage. This machine began crashing inexplicably from the first time I turned it on, but the builder repeatedly assured me the problem was my own ineptitude at making the transition from Microsoft to Linux. However within six months the WP system became totally unreliable -- it would crash anytime a document was open for more than about five minutes, taking all changes (including those I had manually saved) with it.  Internet connections became similarly unreliable: I could access the Internet without difficulty but opened links would soon crash the computer. Only e-mail was (mostly) reliable, though that too would sometimes crash without warning. 

The reason I downloaded (or rather attempted to download) 10.4 is that two people far more knowledgeable about computers than I diagnosed the problems as corrupted software. Ergo sum, my (now obviously moronic) assumption a new version of Ubuntu might cure the ills. 

Now of course without any Windows capability at all  the machine is reduced to nothing but garbage -- totally useless. (I'd have already bought a new computer save that I am  a Social Security pensioner and life in the economically toxic shade of the ObamaBush has permanently canceled all my previous sources of supplemental income.) 

Ergo my next question: without a CD is there any other way to de-load 10.04 and return to what I had, in which I at least had (mostly) functional e-mail? 

Again thanks,

LB

---

### Post by Elfy on 2010-07-10
Does the machine boot to a sort of usable desktop or not?

If you can go here [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Download the dewsktop cd - if you are not sure if you have 32 or 64 bit - choose the 32bit.

Once downloaded check the download was good - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Once checked burn the cd - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Once burnt install - [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

There are ways to install without a cd - [https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by Loren Bliss on 2010-07-10
The desktop is usable, though the CD player on this machine is sufficiently problematical I stopped using it for  music and went back to FM radio. The CD player would open my commercial CDs only with great and complicated guesswork (and for that reason I never attempted to open any homemade CDs with it). But I'll give it a try; this machine is obviously already little more than a boat anchor anyway.

By the way I've become very fond of Ubuntu, but to have a machine built new from scratch that uses it (including the superb Gimp photo software) would cost nearly as much as an Apple: $800 minimum at Puget Sound area prices. So if I do have to replace this computer -- which is looking more likely all the time -- its back to the albatross of Microsoft, which I utterly despise for a list of reasons long enough to fill the Manhattan telephone book.

Also by the way, I've discovered the hardware with which this garbage machine was cobbled together is Gateway -- which I understand on good authority is the worst, most unreliable hardware ever made: more proof of the sabotage hypothesis.  

In any case tomorrow -- actually later today (it's now 1:15 a.m.) -- I'll attempt that download you recommended and again my gratitude. 

LB

---

### Post by Loren Bliss on 2010-07-10
I got your PM Forestpiskie but without Windows there was no way I could figure to save it so please send again when you're back at the keyboard including the real-time chat instructions. Many thanks. 

LB

---

### Post by Elfy on 2010-07-10
> **Loren Bliss said:**
> Also by the way, I've discovered the hardware with which this garbage machine was cobbled together is Gateway -- which I understand on good authority is the worst, most unreliable hardware ever made: more proof of the sabotage hypothesis.  LB
Not the best - but then the thing I am working on at the moment is cobbled together from all sorts of bits of pieces - including a gateway mobo - so it's not impossible :)

It might be that you'll need to install using a usb if that's possible.

> **Loren Bliss said:**
> I got your PM Forestpiskie but without Windows there was no way I could figure to save it so please send again when you're back at the keyboard including the real-time chat instructions. Many thanks. 

LB

When you login you can access PMs - go to [http://ubuntuforums.org/private.php](http://ubuntuforums.org/private.php) and they should be there for you.

---

### Post by Loren Bliss on 2010-07-10
Forestpiskie...Found your PM in email ("duh," said he, slapping his forehead), and I deeply appreciate the encouragement. I slept self-indulgently late and have vital errands to run this afternoon but will be back at this meridian of misery probably around 5 p.m. PDT. Perhaps then with guidance from you or someone like you, we can  determine whether this machine needs to be dropped off the Tacoma Narrows Bridge into the octopi-haunted depths (200 fathom and the planet's largest cephalopods); or hauled to the one repair shop in all of Tacoma that is equipped (mentally as well as technologically) to service Linux (remember that we here are inside the maximum disruption zone of Microsoft); or whether the problem is not the machine at all but merely my own need for what a long-ago parochial school teacher described as "more diligent effort."  Meanwhile thanks.

LB

Apropos meridians, by the time difference (my 1 a.m. to your 9 a.m.) -- I'm guessing you might truly be in the New Forest.

---

### Post by Loren Bliss on 2010-07-11
Forestpiskie, this machine has reached the point even the toolbar clock has become unreliable. Obviously this is hardware failure -- I'm guessing the motherboard is dying -- so I'm giving up on any software fix until  I am able to afford the hardware fix (if indeed I ever can). More likely -- given the hardware costs -- I'll have the damn rotting  Microsoft albatross hung around my neck again. Meanwhile though I'm deeply appreciative of your support, for which again thank you.   

LB

(At this point I can still send and receive email, but it took me four tries to get into Firefox without  crashing, and if I stay on for more than about five minutes the clock freezes, which I take as a warning of greater and more permanent freezes to come.)

---

### Post by Elfy on 2010-07-11
If you are not able to download and burn the iso go to shipit and order one. 

It is still possible that a reinstall will deal with the issue - sometimes an upgrade, for whatever reasons, does not work well. 

I would certainly go for the reinstall option before I looked at blaming hardware.

Shipit - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

