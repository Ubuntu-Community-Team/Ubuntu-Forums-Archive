---
title: "generic mouse leaves trail after restart"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by Ghazoot on 2011-09-05
I am very new. I have tried to install linux three times. I used an old 9.1 disk to install ubuntu on an old gateway computer. the mouse works until I restart. First I just let the network upgrade and when I restarted the mouse left a broken trail and will work but left so many after images that eventually I couldn't see anything. Last night I reinstalled 9.1 and the went straight to upgrade to the next version(10.04). I used the computer all night with out any mouse problems (after a reboot with successful installation and upgrade) and powered off correctly and when I restarted this morning the mouse problem is back.I plugged in a usb mouse and had the exact same thing happen. keyboard seems to work fine. the mouse is also sluggish. It is set to the cheapest setting in preferences I tried the second one and it wouldn't work. 

the computer is a pentium 3 with 450 processer speed and 192 mb ram
thanks for any help

---

### Post by Old_Grey_Wolf on 2011-09-05
> **Ghazoot said:**
> ......
the computer is a pentium 3 with 450 processer speed and 192 mb ram
thanks for any help

Ubuntu 9.10 and 10.04 have a minimum RAM requirement of 256MB. You should look for other alternatives; such as, Vector Linux. It is going to be a challenge to find a modern OS that will run well on 192 MB of RAM with a 450MHz processor. Other people on the forum will provide other options as well, I'm sure.

---

### Post by Ghazoot on 2011-09-05
> **Old_Gray_Wolf said:**
> Ubuntu 9.10 and 10.04 have a minimum RAM requirement of 256MB. You should look for other alternatives; such as, Vector Linux. It is going to be a challenge to find a modern OS that will run well on 192 MB of RAM with a 450MHz processor. Other people on the forum will provide other options as well, I'm sure.
Thanks, I probably should have spotted the minimum ram requirement. That being said it still worked fine and was fast enough until I reboot. So I don't understand why the low processing speed would affect the mouse. I  am not a tech guy just stubborn enough to persevere until I fix the problem. My intention for this computer is to have it run my stereo and internet music radio and I want to control it through my network. so it doesn't have to do a lot. I did try to install puppy linux but I must not think the same way linux people do. :) It seems like all the instructions had parts missing. Its embarrasing how long it took me to figure out how to post my question in this forum. :)

---

### Post by Old_Grey_Wolf on 2011-09-06
If you don't need a GUI you could try the 10.04 Alternate CD. The RAM requirements are lower.

---

### Post by Old_Grey_Wolf on 2011-09-06
You could also try to set the run level so the GUI doesn't start in your current install.

---

### Post by snip3r8 on 2011-09-06
[http://lubuntu.net/tags/requirements](http://lubuntu.net/tags/requirements)

---

### Post by Ghazoot on 2011-09-06
Thanks for the suggestions, I presume gui means gnome interface and yeah I would be lost without it. I don't mean to be obtuse but I can't understand why it would run fine for a few hours and then the power up and power off would cause the low ram to cause me mouse problems. I would expect the low ram to choke on applications or be slow. I spent sunday afternoon downloading and trying to connect to my network without any problems.including a restart or 2 after downloading upgrades. I made no changes between the last restart and the end of the night. The gateway setup has a setting to select plug and play os's. I tried both settings with no change. It seems to me that some setting is changing or something is not loading correctly. Since it seems so close to usable, I would like to take a shot at getting this going before I start over with a new os.

---

### Post by snip3r8 on 2011-09-06
GUI - Graphical user interface

---

### Post by Ghazoot on 2011-09-07
Does anybody have any other ideas to the problem besides low ram? I really think its something else.

---

### Post by Old_Grey_Wolf on 2011-09-08
Just to add some more information, Ubuntu 9.10 is no longer supported. The 9.10 repositories are no longer kept up to date and the normal ones have been removed.

You might be able to install the 10.04 Alternate CD, get it working, and after it is working install a light weight Desktop Environment (such as, XFCE). Or, as I have already suggested install something like Vector Linux.

Maybe someone will come along that can answer your question better than I can. However, this thread has had 125 views already without any  other suggestions. I wish you luck it getting it working. If you do, post how you did it as I am always willing to learn something new.

---

### Post by Old_Grey_Wolf on 2011-09-08
> **Ghazoot said:**
> ...That being said it still worked fine and was fast enough until I reboot. So I don't understand why the low processing speed would affect the mouse...

It's probably the RAM not meeting the minimum requirement that is causing most of your problem plus the slow processor. When you reboot the computer, several process run that use a lot of RAM and CPU; such as, the Update Manager. With the amount of RAM and CPU speed you have, it may take 30 minutes or more for them to run. You could try not using the computer for 30 minutes to an hour after rebooting it to see if it helps. If that helps, you may find that you will need to leave the machine on all the time rather than wait after you boot it.

---

