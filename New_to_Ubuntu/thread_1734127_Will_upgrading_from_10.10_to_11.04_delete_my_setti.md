---
title: "Will upgrading from 10.10 to 11.04 delete my settings/programs from 10.10?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Entyrion on 2011-04-19
So I'm sure this is a very noob-ish question, but with the upcoming stable release of 11.04, it has been nagging me quite a bit.

I've finally gotten 10.10 up and running smoothly, worked out all the little bugs, tweaked the settings, installed the programs I want, and overall gotten this Linux machine purring like a kitten.

My question is, when I finally update to the stable version of 11.04 when it is released, will I end up with a "fresh" install of Ubuntu 11.04? That is, the default I would get if I had installed it directly from a disk, not upgraded from 10.10?

For a noob like me, it was quite an adventure (and a bit of work) to do all the little things like install the drivers for my obsolete printer, install Chromium and add the stable PPA in Synaptic, tweak the Chinese Input Method program, set up compiz, Evolution, and Empathy... all these little mini-troubleshooting projects to get my OS to run perfectly.

Will all that be erased with 11.04? Or will I just upgrade and get the new OS with all my old settings, programs, repositories, etc saved?

I hope this made sense. Thanks for any clarification guys!

---

### Post by Paqman on 2011-04-19
> **Entyrion said:**
> Or will I just upgrade and get the new OS with all my old settings, programs, repositories, etc saved?


This. That's the whole point of doing an upgrade instead of reinstalling.

One thing the upgrade process will do is disable all your PPAs and extra repos. This is so that non-standard packages don't disrupt the upgrade process. You'll need to re-enable them once the upgrade is done (just re-check the box in Software Sources). Since a lot of repos won't have a Natty version available yet, you might find you have to keep using Maverick repos for a while. That's fine, the package manager will handle it.

---

### Post by Rasa1111 on 2011-04-19
I believe 11.04 has the option to upgrade from the disc, rather than a fresh install. So if you did an "upgrade", yes, your stuff will be saved.

 But, some friendly advice..
If you just got 10.10  up and running smoothly..
It might be a mistake to change it for 11.04.

Thats like switching a decked out Harley for an experimental moped. lol :P

:)

---

### Post by beew on 2011-04-19
> **Paqman said:**
> This. That's the whole point of doing an upgrade instead of reinstalling.

One thing the upgrade process will do is disable all your PPAs and extra repos. This is so that non-standard packages don't disrupt the upgrade process. You'll need to re-enable them once the upgrade is done (just re-check the box in Software Sources). Since a lot of repos won't have a Natty version available yet, you might find you have to keep using Maverick repos for a while. That's fine, the package manager will handle it.


I don't find any advantage of upgrade over fresh install. You can keep all the data and settings if you have a separate /home partition. Non standard softewares and PPA would need to be reinstalled anyway (but for third party apps are installed in the /home/usr/ there is no need to reinstall). Upgrade even if run smoothly (big if judging from experience of others) would probably take a few hours and a fresh install takes 15-20 minutes. Let's say it takes another hour to reenanble all the ppas and reinstall the software and you still come out much ahead. But most importantly there is a lot less chance of things going wrong and it is much more transparent so it would be easier to trouble shoot if anything goes wrong.

@OP,

If 10.10 is working great for you why risking it with an upgrade(or fresh install) that doesn't have any obvious advantage? Support for 10.10 wouldn't run out for another year and since you use ppas your software will be up to date.

**Edited:** Just saw Rasa111's comment, my thought also.

---

### Post by wobert on 2011-04-19
I can understand that if we have many stuff working pretty well after significant time invested to have it nicely working, which is my case (broadcom wireless took me a while, etc...) the best answer for now it will be to keep working with the 10.10 version  or whichever we have working nice, but to answer why to upgrade to 11 is simple, we want the latest, and we all  know that eventually we will not have the full support of an older version, plus the  curiosity to have our hands over the new version !
Maybe is a high risk to have working our current programs with the new version, maybe is a huge investment of time again, maybe not, I have an FEA software working nice which took me alot of time to have it working and I am not taking any risk until I understand little bit more and test with another computer the new 11 version.

---

### Post by Paqman on 2011-04-20
> **beew said:**
> I don't find any advantage of upgrade over fresh install.

Depends on your setup and preference really. Either is good in my experience.

> Upgrade even if run smoothly (big if judging from experience of others) would probably take a few hours and a fresh install takes 15-20 minutes. 

The speed of your connection is going to make a big difference. A fresh install (including time to download and ready the image) probably takes slightly less time to get installed, but personally for me it would take longer overall due to getting the system how I like it. If you have a lot of tweaks, then an upgrade will save you a lot of time. Stripped back installs will also benefit from upgrading, as you won't be downloading 700MB.

I've done one upgrade and one reinstall for Natty. Both went smoothly, but i'd say the upgrade was probably less work. I find upgrades very reliable these days, I haven't had one prang on me for a long time.

---

### Post by Entyrion on 2011-04-20
I appreciate everyone's input! It sounds like the upgrade route might be the best option. While I certainly understand the "if it ain't broke, don't fix it" side of things, I think I agree with Wobert... I do want the latest (stable) stuff and I'm curious to try out the new version. 

@Paqman:

You mentioned that the upgrade process will disable the Maveric non-standard PPAs and whatnot and I can simply re-enable them after the upgrade is complete. One question along those lines: Once Natty repositories are available, will the packet manager automatically replace the Maverick ones with the newer version, or will I need to do that manually? (Sounds like doing that manually might be slightly annoying...)

Thanks again guys!

---

### Post by beew on 2011-04-20
> **Entyrion said:**
> I appreciate everyone's input! It sounds like the upgrade route might be the best option. While I certainly understand the "if it ain't broke, don't fix it" side of things, I think I agree with Wobert... I do want the latest (stable) stuff and I'm curious to try out the new version. 


I am trying out the latest stuffs (I am typing from Natty right now) by doing a full install on an external hard disk. It is a "real" install (not a live usb with persistence) but I don't risk messing up my working system.  Best of all worlds. :)

---

### Post by beew on 2011-04-20
> **Paqman said:**
> Depends on your setup and preference really. Either is good in my experience.
 

The speed of your connection is going to make a big difference. A fresh install (including time to download and ready the image) probably takes slightly less time to get installed, but personally for me it would take longer overall due to getting the system how I like it. 
.

Actually in my experience a fresh install didn't take slightly less time but a lot less. I did an experiment by upgrading an almost flash install of 10.04 (with no ppa, only a few applications ) to 10.10. The first time it hanged and the second time was successful but took more than 2 hours. Fresh install would take 15-20 minutes.

But may be technology has improved a lot by now so my experiment might need to be updated. :)

> If you have a lot of tweaks, then an upgrade will save you a lot of  time. Stripped back installs will also benefit from upgrading, as you  won't be downloading 700MB.
That is actually opposite to what I learned (again I could be wrong). I think upgrade is more likely to work if you have a very vanilla system. If you have installed proprietary drivers, enabled ppas, used third party tweaks and softwares then upgrade will fail if you haven't restored the system to a relative pristine state before you upgrade. For example, if you have ppas you would have to not only disable them, but to downgrade all the packages to the official Ubuntu versions with ppa-purge (i.e. use ppa-purge on each ppa) before upgrade. If you have proprietary graphic card installed you are also supposed to revert to the open source driver before proceeding (e.g remove Nvidia driver and restore nouveau)

I keep a separate /home partition for my settings and they will be saved with reinstall.

---

### Post by smoosh on 2011-04-20
I just upgraded last night so let me tell you about my experience. The upgrade process actually uninstalled or broke quite a few programs that I had installed, mostly ones that were being kept updated through PPAs or that I installed with .debs. I never actually thought to simply re-enable the PPA in the sources list, so it was probably harder than it needed to be. 

The good part about upgrading is that the config files will still be there, so once you install all the programs again, they will pretty much work like they did before - assuming you can get them all installed. All mine worked fine, but you never know. If you have a separate /home folder, you can save most of your config file with a new install, too.  

Some very important things (to me) however, were obliterated. I had to completely re-tweak compiz and AWN (which is fine, it just took longer than I expected). The "Ubuntu Classic" session also did not want to work for me (wallpaper and cursor were visible but no compiz or gnome-panel [couldn't open the menu to launch anything]), so I had to disable unity through CCSM in the regular "ubuntu" session, since I don't want to use unity.

I had to re-enable all the restricted extras and rerun the script to read DVD menus so commercial DVDs play correctly, which was a fun thing to have to do while my two year old sat there and whined that she wanted to watch Elmo. "One second sweety, daddy has to tweak out on this a little more. What, these tiny words aren't as fun to watch as Elmo??"

The whole process was actually pretty frustrating, but I'm happy with the results. Definitely don't expect any settings you had to be in tact. My experience was almost opposite that. Internet Explorer (that I need almost never use) still ran (once I re-installed Wine), which I got a good chuckle out of, but almost all the programs I depend on were broken or un-installed.

The process also installed a whole bunch of crap that I never use that I had to (once again) remove. 

So, it really wasn't worth it for me to upgrade. It felt much more like a new install to me. Just a heads up, so you don't expect any of your settings and programs to be intact, as mine did not work out that way. My wallpaper made it through the process! Not much else did, though.

If you use Compiz and/or AWN, those were the most difficult to return to functional states. And I still don't know why I can't log in as "ubuntu classic". 

It seems funny (or sad) to me that upgrading resulted in a completely un-recognizable desktop, with things like restricted extras that were installed before completely removed. But like I said, after messing with it all day, I am happy with the results. It definitely was not smooth though. Wish I would have done a fresh install! Or read this thread before I upgraded... But who cares? It all works now!

---

### Post by Rasa1111 on 2011-04-20
smoosh~ LOL, Thanks for the laughs!
haha, had me laughin' a few times. :lol: 

Glad it is good now though. :)
<3

---

### Post by smoosh on 2011-04-20
Hey, anything I can do to help the community!;)

---

### Post by Paqman on 2011-04-21
> **Entyrion said:**
> 
@Paqman:

You mentioned that the upgrade process will disable the Maveric non-standard PPAs and whatnot and I can simply re-enable them after the upgrade is complete. One question along those lines: Once Natty repositories are available, will the packet manager automatically replace the Maverick ones with the newer version

Nope, because it doesn't know why you pointed them at the Maverick versions in the first place.

> 
or will I need to do that manually? (Sounds like doing that manually might be slightly annoying...)


Nope, very, very easy. Just open up the software sources, and edit the entry for the PPAs, changing the "maverick" to "natty". Should take you about a whole 30 seconds ;)

---

### Post by PPPilot on 2011-04-21
I run Lucid for daily work and I had Maverick on another partition just to keep up to date. Both if these were fresh installs. In fact, all I had ever done, going back to 8.04, was do fresh installs because of all the horror stories I heard here about the upgrade route. 

This time I decided to roll the dice and and do an upgrade of Maverick. The whole thing went very smoothly even though I was upgrading to a beta version of Natty. The only thing I had to do, when completed, was to enable the PPAs disabled during the upgrade. I was clearly informed, during the upgrade, why I had to do this and how to do it. The PPAs were even clearly marked as disabled when I went to Software Sources to enable them. All my tweaks and settings stayed in place just fine. I run both Gnome and KDE Desktops and both survived the upgrade intact.

So I am pretty impressed with my first upgrade. Natty is running quite well and it is nice to get on line with Firefox 4.0. So nice in fact, I just upgraded to Firefox 4.0 on Lucid. The only down side is that there are a lot of daily upgrades of Natty but that is to be expected with a beta release.

---

### Post by Entyrion on 2011-04-21
Thanks again to Paqman and everyone else for their informative input! Since my initial (and followup) questions have been answered to my satisfaction, I'll be marking this as thread as "solved." If the **** hits the fan on the 28th with Natty's official stable release, I'll be sure to come back and start pestering you guys for tips!

---

### Post by 3rdalbum on 2011-04-21
> **Entyrion said:**
> 

For a noob like me, it was quite an adventure (and a bit of work) to do all the little things like install the drivers for my obsolete printer, install Chromium and add the stable PPA in Synaptic, tweak the Chinese Input Method program, set up compiz, Evolution, and Empathy... all these little mini-troubleshooting projects to get my OS to run perfectly.

Will all that be erased with 11.04? Or will I just upgrade and get the new OS with all my old settings, programs, repositories, etc saved?

Settings are saved in your home directory - so assuming you don't wipe your disk, your Compiz, Evolution, Empathy and Chromium (and other) settings will be saved. Printer drivers, possibly - depends how they were installed. PPAs, I don't think they stay.

Now you know how to do these things though, it shouldn't take you more than an hour to get your system up and running to your satisfaction.

---

