---
title: "Ubuntu Minimal dependency hell"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by philinux on 2010-05-29
[edit] **Solution was to use the main archive rather than the local one ,gb in my case.**

I've got the minimal install to a point where it boots to the shell. 

Tried to start with just installing xorg.

```
sudo apt-get install xorg --no-install recommends
```

Problem is when I try to install anything else I get this.

The usual install -f and dpkg --configure -a don't fix it.

Any suggestions?

---

### Post by wojox on 2010-05-29
You can't install **zlib1g** or **libgcc1** ?

---

### Post by bildr on 2010-05-29
Lfs - compile your base libraries from scratch

---

### Post by anewguy on 2010-05-29
Compared to you I am very much the novice, so forgive me if I give a dumb suggestion:

sudo apt-get build-dep xorg

Won't that get all the dependencies for you?

I hope this isn't to stupid a recommendation!

Dave ;)

---

### Post by pj_kare on 2010-05-30
I've far less experience than **anewguy**, so my suggestion may be even dumber, though my "searches" have helped a few already.

I realise you are trying to do a minimal install but the thread below may help, specifically **hwertz** suggestion on the last (3rd) page. The fix is odd but it seemed to worked .

Basically it's switching from your LOCAL download server to the MAIN server, reload synaptic and then switch back to your LOCAL server and reload synaptic again. (I think.)

[http://ubuntuforums.org/showthread.php?t=649600](http://ubuntuforums.org/showthread.php?t=649600)

---

### Post by orlox on 2010-05-30
@pj_kare

He is doing a minimal install, so I doubt he has synaptic, or gnome, or even anything gtk installed...

Anyways, the "it is not installable" messages can be better understood by trying to install the conflicting packages as wojox suggested. Perhaps for some strange reason, the installation of those packages requires deletion of others, or who knows what, that gets apt dizzy...

As a last resource, couldnt you just try and get the packages from the internet and manually "dpkg -i" them?

---

### Post by bodhi.zazen on 2010-05-30
> **philinux said:**
> I've got the minimal install to a point where it boots to the shell. 

Tried to start with just installing xorg.

```
sudo apt-get install xorg --no-install recommends
```Problem is when I try to install anything else I get this.

The usual install -f and dpkg --configure -a don't fix it.

Any suggestions?

Try apt-get update, then apt-get install -f

---

### Post by pj_kare on 2010-05-30
Sorry, I'll bite my tongue in future....I know I'm too in-experienced to help.....

---

### Post by orlox on 2010-05-30
> **pj_kare said:**
> Sorry, I'll bite my tongue in future....I know I'm too in-experienced to help.....

Sorry if my comment came in too harsh, wasnt the idea at all.

I also gave misplaced advices when I just had started using linux, and I still do!

---

### Post by philinux on 2010-05-30
> **wojox said:**
> You can't install **zlib1g** or **libgcc1** ?

No, I tried that thanks as well. In fact starting from the base install installing anything results in the same borked situation with held broken packages.

I'm using virtualbox so have a snapshot right at the beginning after the base install is complete. No errors with apt-get update and then upgrade.

---

### Post by philinux on 2010-05-30
> **bodhi.zazen said:**
> Try apt-get update, then apt-get install -f

Tried that too nothing fixes the broken packages.

---

### Post by philinux on 2010-05-30
> **pj_kare said:**
> I've far less experience than **anewguy**, so my suggestion may be even dumber, though my "searches" have helped a few already.

I realise you are trying to do a minimal install but the thread below may help, specifically **hwertz** suggestion on the last (3rd) page. The fix is odd but it seemed to worked .

Basically it's switching from your LOCAL download server to the MAIN server, reload synaptic and then switch back to your LOCAL server and reload synaptic again. (I think.)

[http://ubuntuforums.org/showthread.php?t=649600](http://ubuntuforums.org/showthread.php?t=649600)

Right I'll try a new install from the base iso and select the main server instead of gb.

---

### Post by philinux on 2010-05-30
Well pj_kare was spot on, cheers

There was a choice between main and gb so I naturally went with gb.

Just started afresh and chose main. Installed xorg and now there are no apt errors or broken packages.

Odd though innit. :shock:

Not sure what to bug at launchpad, must be the gb repo's though.

I'm following this if anyone interested [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal). I'm building a livecd for my daughter to use. Just a gui, networking and firefox.

---

### Post by mikewhatever on 2010-05-30
What are you going to use for gui?

---

### Post by philinux on 2010-05-30
> **mikewhatever said:**
> What are you going to use for gui?

Maybe icewm or lxde, any suggestions?

---

### Post by Ozymandias_117 on 2010-05-30
I guess the two questions to ask are, how old is the hardware that you are planning on this being used for, and how much Linux knowledge does the end user have?

I think LXDE looks a bit nicer than IceWM as long as the hardware is new enough that you won't see any performance drop from it.

I also think LXDE is easier for a newer user than IceWM.

I always pick IceWM over Openbox or Fluxbox.

---

### Post by anewguy on 2010-05-30
I apologize also for what was a dumb suggestion.

Glad you got things working!

Dave ;)

---

### Post by mikewhatever on 2010-05-30
I don't have any experience with icewm, but given the only program will be a browser, it doesn't really matter.

---

### Post by MooPi on 2010-05-30
I like it. I use openbox and always suggest it but the combo that was displayed by psychocat looks great. I'm going to try this on a spare machine to experiment with icewm.

---

### Post by philinux on 2010-06-01
Got what I wanted use ubuntu minimal as the base then installing lxde, firefox and gdm. Reason for gdm is that remastersys needs this to make the livecd run as expected, other wise you end up with a login screen and have to use the user custom with no password.

The lxde is just the job.

Livecd boots to usable desktop in 1min 30secs.

Iso is 377mb and the installed version boots to usable desktop in about 15 seconds. 

In contrast I tried peppermint as the base before customising a bit, but this takes 2mins 15 seconds to usable desktop.

---

