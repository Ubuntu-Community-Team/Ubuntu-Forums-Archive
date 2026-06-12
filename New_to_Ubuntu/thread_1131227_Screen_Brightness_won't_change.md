---
title: "Screen Brightness won't change?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-20
I'm trying to solve my battery life/power usage woes with Ubuntu, and a big issue is that my screen brightness won't adjust. It's at 100% all the time - it won't dim, and whatever I set the brightness at doesn't make any difference. 

How can I fix this? The notebook is a Sony Vaio VGN-NR498E/W.

---

### Post by unutbu on 2009-04-20
I know this is for a different Sony VAIO, but have you tried this? 
[http://ubuntuforums.org/showthread.php?t=1004568](http://ubuntuforums.org/showthread.php?t=1004568)

Edit: Hm. If the Sony VAIO VGN-NR498E/W has an integrated Intel graphics chip, then the NVIDIA-based solution on the above page probably won't work for you.

---

### Post by Brucevdk on 2009-04-20
See: [http://ubuntuforums.org/showpost.php?p=7090622&postcount=2](http://ubuntuforums.org/showpost.php?p=7090622&postcount=2)

---

### Post by Noise... on 2009-04-20
> **Brucevdk said:**
> See: [http://ubuntuforums.org/showpost.php?p=7090622&postcount=2](http://ubuntuforums.org/showpost.php?p=7090622&postcount=2)

So that command should work?

---

### Post by steve101101 on 2009-04-20
if you upgrade to jaunty (9.04) it will dim. :) my vaio works in 9.04 but not 8.10

---

### Post by Brucevdk on 2009-04-20
> **Noise... said:**
> So that command should work?

It may or it might not. I'd say just try it out on the terminal and see if it does anything (and even though it did allow me to adjust my brightness it wasn't ideal, I've recently switched to a ThinkPad only solution). If not, then browse through the [bug search](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=BACKLIGHT_CONTROL&orderby=-importance&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) I listed in the earlier linked post to see if there is anything relevant in there. You might also want to take a look at [LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch) (but if you cannot adjust brightness through the applet, then it's definitely not a hotkey issue).

---

### Post by Noise... on 2009-04-20
> **steve101101 said:**
> if you upgrade to jaunty (9.04) it will dim. :) my vaio works in 9.04 but not 8.10

I'll have to order a live disk then. 

Does 9.04 have more power options as well? My main issue with Ubuntu right now is that I can't really set power use really low. When I'm just web browsing, there's no reason for me to be using a 2.0GHz Core 2 Duo at full strength and 100% screen brightness. 

Basically, I'm getting an hour and a half on battery with the default power settings, where in Vista I can get close to 5 hours with a custom power saver config.

---

### Post by steve101101 on 2009-04-20
i believe that it is more efficient that previous distros. you don't need to order a disk. you can download it from a variety of torrents or from ubuntu.com

---

### Post by Noise... on 2009-04-20
> **steve101101 said:**
> i believe that it is more efficient that previous distros. you don't need to order a disk. you can download it from a variety of torrents or from ubuntu.com

I'm on Mobile Broadband with a 5GB monthly limit. Downloading a 1GB iso just wouldn't work out - especially with the insane overage charges Verizon has.

---

### Post by steve101101 on 2009-04-20
limits on Internet usage is so dumb. i use 2GB in a day or 2 of downloading various files and movies from sites like hulu and netflix.

---

### Post by Noise... on 2009-04-20
> **steve101101 said:**
> limits on Internet usage is so dumb. i use 2GB in a day or 2 of downloading various files and movies from sites like hulu and netflix.

I know. Not to mention that it's $60 a month. 

I'm completely off grid, so it's my only option. :(

---

### Post by unutbu on 2009-04-20
> **Noise... said:**
> 
Basically, I'm getting an hour and a half on battery with the default power settings, where in Vista I can get close to 5 hours with a custom power saver config.

You might be able to find other ways to extend battery life in these two tutorials:

[HOWTO: saving power on laptops]("http://ubuntuforums.org/showthread.php?t=847773&highlight=USB+writes") 
[How to reduce disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by steve101101 on 2009-04-20
> **Noise... said:**
> I know. Not to mention that it's $60 a month. 

I'm completely off grid, so it's my only option. :(

that sucks.

---

### Post by steve101101 on 2009-04-20
> **unutbu said:**
> You might be able to find other ways to extend battery life in these two tutorials:

[HOWTO: saving power on laptops]("http://ubuntuforums.org/showthread.php?t=847773&highlight=USB+writes") 
[How to reduce disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

tis true

---

### Post by Brucevdk on 2009-04-21
> **Noise... said:**
> My main issue with Ubuntu right now is that I can't really set power use really low. When I'm just web browsing, there's no reason for me to be using a 2.0GHz Core 2 Duo at full strength and 100% screen brightness.

I believe the ondemand governor should be active by default and lower your frequency automatically, you can show the frequency on your panel by adding the frequency applet. When you're on battery power you can also right click on the battery icon and select Power History to find out your power usage. Also might be handy to take a look at [Powertop](http://www.lesswatts.org/projects/powertop/) (sudo apt-get install powertop).

Hope any of this information helps.

EDIT: didn't notice there was a second page and that some links had already been posted whoops

---

### Post by vernonrj on 2009-04-21
Hey, if you're still having a brightness problem, nvclock 0.8b1 is working for me. You may have to compile, I'm not sure if it's in the repos yet.
you may also find this helpful.
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)

---

### Post by Noise... on 2009-04-21
So, is Powertop a manager, or just a general thing of tweaks and a power monitor?

Will it conflict at all with Kpowersave? (Which isn't that great, to be honest..)

Also, the command posted on Page 1 didn't help. My screen flashed black for a second, and there was no change.

---

### Post by Noise... on 2009-04-21
> **vernonrj said:**
> Hey, if you're still having a brightness problem, nvclock 0.8b1 is working for me. You may have to compile, I'm not sure if it's in the repos yet.
you may also find this helpful.
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)

While that does mention Vaios, my Vaio has an Intel X3100 graphics chip in it, rather than a Nvidia.

---

### Post by steve101101 on 2009-04-21
powertop shows processes that are wasting the most power and how to reduce it

---

### Post by Stunt Double on 2009-04-21
I had the same problem with my Vaio.
  Right click on the top panel, then +add to panel, then select Brightness Applet then adjust via the applet.
It was the only solution that worked for me.

---

### Post by Noise... on 2009-04-21
> **Stunt Double said:**
> I had the same problem with my Vaio.
  Right click on the top panel, then +add to panel, then select Brightness Applet then adjust via the applet.
It was the only solution that worked for me.

I tried. It didn't work. :(

---

