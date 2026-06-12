---
title: "Isolating DVD Burner Issue"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by steve108 on 2011-04-06
Does anyone have advice on how I can determine if my problems with burning DVDs and CDs are hardware or software issues?

I'm running 10.04 and I can only burn CDs from the command line, no GUI software works - probably a software issue. 

But... I just tried burning a DVD using the same brand and model DVD that I used to use and the same command (growisofs), but about 1/3 of the way through it failed, giving an input/output error. - This leads me to believe that maybe my drive is failing.

Without wasting a ton of DVDs, does anyone have some suggestions for isolating the issue.

This is the first time since updating from 8.xx that I have tried burning a DVD.

Thanks

---

### Post by alphacrucis2 on 2011-04-06
> **steve108 said:**
> Does anyone have advice on how I can determine if my problems with burning DVDs and CDs are hardware or software issues?

I'm running 10.04 and I can only burn CDs from the command line, no GUI software works - probably a software issue. 

But... I just tried burning a DVD using the same brand and model DVD that I used to use and the same command (growisofs), but about 1/3 of the way through it failed, giving an input/output error. - This leads me to believe that maybe my drive is failing.

Without wasting a ton of DVDs, does anyone have some suggestions for isolating the issue.

This is the first time since updating from 8.xx that I have tried burning a DVD.

Thanks

I find K3B gives me the best results of the GUI tools. Anyway, given you are having trouble with the command line tools, it could be more fundamental. Some people say that they have better results using the original cdrtools versus the debian cdrkit (fork of cdrtools) stuff that ubuntu provide. It appears that cdrtools is better maintained than cdrkit although the cdrtools dev seems to have rubbed up the debian devs and others the wrong way. (Seems to be a little bit eccentric). Anyway it is possible to replace cdrkit with cdrtools using this PPA:

[URL="https://launchpad.net/~brandonsnider/+archive/cdrtools"]https://launchpad.net/~brandonsnider/+archive/cdrtools
[/URL]

Could be worth a try.

---

### Post by steve108 on 2011-04-07
That seemed to do the trick. Thanks a bunch!

---

