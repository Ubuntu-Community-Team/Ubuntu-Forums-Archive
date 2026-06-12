---
title: "Updates suck"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by psycosmyth on 2008-12-12
yes I said it, if it ain't broke............
Why have the latest updates and upgrade to 8.10 been so damaging?
I just threw the mods some bait but I am upset at Canonical's push for the newest versus what works. Sorry.

---

### Post by tuxxy on 2008-12-12
Care to elaborate on the issue?

---

### Post by JoshuaRL on 2008-12-13
Yeah, seriously.  What exactly are the issues you're having?  Did you track down the offending packages?  Did you make any bug reports on Launchpad?

---

### Post by oldsoundguy on 2008-12-13
Launchpad is a sick joke!  If you have a real problem, they ignore you.  IF it is simple and any clown could figure it out with a little time and by coming into the forums for help .. they jump right in with an answer to look good.

The stone MESS with NVidia legacy drivers (the advanced packages including  RandRotate), 8.10 and Gnome is a prime example of ignoring the problem (and maybe it will go away?)

Or maybe they are planning to wait and address the issues with Jaunty? hmmmmm

---

### Post by nakama85 on 2008-12-13
Maybe I am the only one who has been pleased with 8.10. I run both 8.10 and 8.04 on two different computers and have had more luck with 8.10 thus far. Of course things could change but that is my opinion for now.

---

### Post by JoshuaRL on 2008-12-13
Nope, I agree.  I just installed on my new Compaq laptop and it works great.  Didn't need Envy, the Restricted Drivers GUI autodetected my 8200M and offered two drivers, one of which it recommended.  And it picked out my Broadcom wifi card and gave me a driver for that too.  Couldn't be easier.  

Much better than Hardy has been for my desktop.  I've just had lots of little buggy problems.  Nothing worth tracking down and submitting a bug report for, but still aggrivating.  So far I like Intrepid much better.  Hopefully autodetection will just get even better and Jaunty will be delicious.

Sorry if your experience doesn't match mine, but I think that could be said for everyone about everyone.  I think that a lot more of the negative voices have come forward from Gutsy on.  By this time we all just expect Ubuntu to work, and we tend to not hear back from anyone unless something goes wrong.  After all, this is a support forum.

And be careful putting down the developers.  Many good and honest people have worked and continue to work on Intrepid.  But the farther it goes, the more demanding the standard is and the more involved all the parts are.  For instance, (if I remember correctly) Envy is a helper script written and supported entirely by one Alberto Milone.  So hats off to him even making that at all.  But I think we all understand that the goal was to one day not need Envy or anything like it.  Maybe that day is closer than we all imagined.  Hey, at least we're not stuck with an expensive, bloated, insecure OS!

---

### Post by scorp123 on 2008-12-13
> **oldsoundguy said:**
>  Launchpad is a sick joke!  If you have a real problem, they ignore you.   I have to agree here. I opened a bug report concerning NFS and the different behaviour we get now in those packages. I have commercial (= closed source $$$) apps that expect certain NFS mount options ... Between Ubuntu 7.10 and 8.04 Canonical simply changed some of the options without telling anyone. So if I want to use certain commercial apps I cannot use them on anything that's newer than Ubuntu 7.10 .... And this seriously sucks.

The bug reports have been open for months and guess what: Status is still "new" and "undecided". Nice. Quite the way of having pro users switch to Ubuntu ... tss tss tss :mad:

> **oldsoundguy said:**
>  Or maybe they are planning to wait and address the issues with Jaunty? hmmmmm  What I have come to dislike about Canonical is the fact that they sometimes "fix" stuff that wasn't even broken in the first place. Multimedia keys for example. Mine started to work perfectly in Ubuntu 7.10. Wow. And they worked perfectly in Ubuntu 8.04. Wow. And they have stopped working in Ubuntu 8.10 because someone decided that it is a good idea to break this stuff again after it was working so perfectly for two releases. Wow again ... just in the different sense.

---

### Post by spiderbatdad on 2008-12-13
Your menu.lst can easily be configured to save earlier versions of the kernels (if it doesn't already) during any development cycle. So, if you have a problem after an upgrade, you can select an earlier kernel version and make it default until the problem ( for your machine ) is fixed.

The great thing about launchpad is: you are free to make it better. Jump right in, join a team, get mentoring on how to mark and triage bugs, maybe even move on to fixing bugs, or making packages. If you are entirely unsatisfied, your money will be cheerfully refunded.

---

### Post by billgoldberg on 2008-12-13
> **psycosmyth said:**
> yes I said it, if it ain't broke............
Why have the latest updates and upgrade to 8.10 been so damaging?
I just threw the mods some bait but I am upset at Canonical's push for the newest versus what works. Sorry.

Ubuntu and newest?

Those don't go along.

---

### Post by Paqman on 2008-12-13
> **psycosmyth said:**
> I am upset at Canonical's push for the newest versus what works. Sorry.

Don't be sorry, just use the right version of Ubuntu. If you value stability you should be using 8.04 and only including security updates. That's precisely what LTS releases are for.

---

### Post by scorp123 on 2008-12-13
> **billgoldberg said:**
> Ubuntu and newest?

Those don't go along. But "Ubuntu" and "not 100% properly tested" do ;)

In each release (yes, LTS releases too) there seem to be a bunch of ugly bugs or odd features not working properly. Sometimes I wish they'd postpone their release schedules a bit (as they did with 6.06) in favour of having stuff properly tested and implemented. "It's ready when it's ready" ... I'm fine with that. But "It's ready when the release date is due and we will release it no matter how buggy it still is.... "  well, that sort of sucks.

---

### Post by Kareeser on 2008-12-13
In my opinion, there's a fine line between releasing buggy code that shouldn't be released in the first place, and increasing a userbase for a feature that could potentially improve Ubuntu tenfold.

Lots of legacy features are used for backwards compatability reasons, and if Ubuntu stuck with those, sure, everybody could use Ubuntu, but then it wouldn't be very state-of-the-art.

For example, Ubuntu's move to PulseAudio could have been to increase the userbase (and thereby increase the bug-fixing power) of PulseAudio, to replace ALSA, which may be getting a lil' dated.

Again, with Compiz installed and enabled by default (depending on hardware), we see a good jump in eye candy (which can be turned off if needed), and an increased user base who will scream whenever something goes wrong, and as such, **more people will be inclined to fix them**.

Looking on the bright side :)

---

### Post by psycosmyth on 2008-12-13
I actually wrote this in my SLEEP!!!
I had a dream that I said something like this. Not the first time, my lappy is beside my bed too. I did have some problems with 8.10 relating to restricted modules, Nvidia for one box and Atheros for the lappy.
neither would load. I have returned to 8.04 but the updates from a few days ago dropped more restricted packages such as flash player. I have fixed all other bugs and have set my updates for security only, thank you Paqman. 
Sorry for the rant, must have had some dream!! :p

---

