---
title: "Keep 'Visual Effects' settings?"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by ManfredKlinglmair on 2010-06-11
Hi,
I've discovered a little nuisance with the 'Visual Effects' setting under System>Preferences in the Main Menu. Every time I start the computer, the setting has gone back to 'None', as opposed to 'Standard', which I want.
How do I 'teach' Ubuntu to keep the setting?

Thanks!
Manfred

---

### Post by philinux on 2010-06-11
> **ManfredKlinglmair said:**
> Hi,
I've discovered a little nuisance with the 'Visual Effects' setting under System>Preferences in the Main Menu. Every time I start the computer, the setting has gone back to 'None', as opposed to 'Standard', which I want.
How do I 'teach' Ubuntu to keep the setting?

Thanks!
Manfred

Specs and graphics card? Version of Ubuntu? etc etc.

---

### Post by ManfredKlinglmair on 2010-06-11
Oh. Sorry.
Running 10.4, card is ATI Mobility Radeon 9700 - just got the visual effects running again after a driver conflict, so I'd be unhappy to tinker with the graphics drivers again.

Is there some way, some box to check or whatever, so that I don't have to manually set the effects to 'Standard' again after every startup?

M.

---

### Post by tom.swartz07 on 2010-06-11
Could you please run this script to help us diagnose the problem?

[http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/compiz-check](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/compiz-check)

It needs to be run from the command line, so Ill walk you through the steps just in case.
Download it to your desktop
then open a terminal and type the following
```
cd Desktop
```
```
chmod +x compiz-check
```
```
./compiz-check
```

You could hit the TAB key after you get the first few letters of Desktop and compiz-check to autocomplete the name (it saves time from typing)

Then simply copy and paste the output here. It will tell us the card you have, the kernel version, and will provide other troubleshooting information for us to use.

---

### Post by ManfredKlinglmair on 2010-06-11
Thanks. 

Erm.... how do I run a script? In the terminal?

---

### Post by tom.swartz07 on 2010-06-11
> **ManfredKlinglmair said:**
> Thanks. 

Erm.... how do I run a script? In the terminal?

Yes. Just follow the instructions I provided and you should be all set. Run it, follow the instructions on screen if it asks anything, and copy/paste the output back here for us to analyze.

---

### Post by ManfredKlinglmair on 2010-06-11
OK, that's what I get:


Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Ideas? :) Looks fine to me... and all the effects (including highest setting) work fine. Hm. Compiz is installed.

---

### Post by tom.swartz07 on 2010-06-11
> **ManfredKlinglmair said:**
> OK, that's what I get:


Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Ideas? :) Looks fine to me... and all the effects (including highest setting) work fine. Hm. Compiz is installed.

Thats strange. Everything seems to be working fine.

Do you have CompizConfig Settings Manager installed?
Try using that to manage your compiz preferences, and see if it makes a difference.

---

### Post by ManfredKlinglmair on 2010-06-11
I did/do use Compiz... so that's really rather vexing.

---

### Post by tom.swartz07 on 2010-06-11
> **ManfredKlinglmair said:**
> I did/do use Compiz... so that's really rather vexing.

I mean, do you have CCSM installed? Its a different program than compiz. Compiz is installed by default on Ubuntu, CCSM is extra and is a much more fine-tuned way of controlling effects.

Try using that program

---

### Post by ManfredKlinglmair on 2010-06-11
Yes, it's up and running, and works fine.

I can't believe there's no simple thing I can change so that my desktop looks the same upon startup, each time! Anyone?

---

### Post by gomerhauler on 2010-06-22
I have the same problem using an upgraded 10.04. CCSM installed and working, and here's the output from compiz-check:

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


That 'rendering method: NONE' seems kinda worrisome, but I have no clue what it means. Any ideas, anyone?

---

### Post by lkjoel on 2010-06-22
Try in a Terminal window (Applications->Accessories->Terminal)
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mesa-common mesa-common-dev libgl1-mesa-glx mesa-utils
```
Tell me it it works!

---

### Post by gomerhauler on 2010-06-22
> **lkjoel said:**
> Try in a Terminal window (Applications->Accessories->Terminal)
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mesa-common mesa-common-dev libgl1-mesa-glx mesa-utils
```
Tell me it it works!

No joy. Here's what I got:

sudo apt-get install mesa-common mesa-common-dev libgl1-mesa-glx mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mesa-common

And I have all the repos enabled.

---

### Post by senning on 2010-06-24
> **ManfredKlinglmair said:**
> Yes, it's up and running, and works fine.

I can't believe there's no simple thing I can change so that my desktop looks the same upon startup, each time! Anyone?

I had the same problem with visual effects, and I think I solved it by starting up compiz and getting the system to remember my settings for startup (System->Preferences->Startup Applications, under the Options tab).  I was following the advice in [another thread]("http://ubuntuforums.org/showpost.php?p=9243635&postcount=22"), and it has some similar, more involved, solutions too.

Hope that helps!

---

### Post by lkjoel on 2010-06-28
> **gomerhauler said:**
> No joy. Here's what I got:

sudo apt-get install mesa-common mesa-common-dev libgl1-mesa-glx mesa-utils
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package mesa-common

And I have all the repos enabled.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mesa-common-dev libgl1-mesa-glx mesa-utils
```
If you want it immediately to work, you can try this.
But if you can wait a month, I will have my other computer back, then I can give you the complete list.

---

### Post by poobathy on 2012-02-02
i faced a problem with visual effects that,
default, the visual effects are in "standard", i need "none" mode.
but in each start up it automatically changed to "standard".
how to avoid this prob?

---

