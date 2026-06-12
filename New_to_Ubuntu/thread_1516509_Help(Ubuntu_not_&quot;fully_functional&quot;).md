---
title: "Help(Ubuntu not &quot;fully functional&quot;)"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Jaycob on 2010-06-23
Hello Im very new to Linux and I have installed UBUNTU 10.4
on a g60-580 hp laptop. First it was working great !! after that
things went downhill.

problems
1.How do I install programs in linux when the software center cant connect or freezes.
2. even if my headphones are plugged in my computers speakers are still on.
3.the wifi button indicates a blue when connected and orange when not, this light turns blue and orange when im downloading something.

SPECS

HP G60 580US
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01921776&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4072654](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01921776&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4072654)

---

### Post by Windows Nerd on 2010-06-23
> **Jaycob said:**
> Hello Im very new to Linux and I have installed UBUNTU 10.4
on a g60-580 hp laptop. First it was working great !! after that
things went downhill.

problems
1.How do I install programs in linux when the software center cant connect or freezes.
2. even if my headphones are plugged in my computers speakers are still on.
3.the wifi button indicates a blue when connected and orange when not, this light turns blue and orange when im downloading something.

SPECS

HP G60 580US
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01921776&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4072654](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01921776&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4072654)

In response to question #1: Mind specifying a bit more detail or give us any error messages that you see when you cannot connect to the software centre?

In response to question #2: Does sound play out of both the speakers and the headphones when the headphones are plugged in? When you say "My speakers are still on" It could mean they still have power and are "on" but correctly behaving when headphones are plugged in, OR still playing music when headphones are still plugged in.

In response to #3: Which Wifi button? Do you mean the Wifi applet on the top panel on the left-hand side or an actual button on your laptop that enables/disables wifi? 

I (and many other forum users) would love to help you faster, but we ask these questions because you never specific enough in your questions, and we are not sure what exactly your problem is, and cannot help you. The more information you want to give us (as long as it is relevant to the topic, of course!), the better and faster we can help you.

Awaiting your reply,

Scott

---

### Post by Jaycob on 2010-06-24
Thanks

1. Actually I dont get error messages, but the software center load to the main page where it tells you the DIFFERENT types applications to download , like science,browsers,social networking apps,that page loads.if I choose a type of app that I want that page freezes or doesn't load.

2. My speakers play fine,just that they dont mute when i use my headphones.My speakers work fine only problem I have is that they dont mute when I use my headphones.

3. The button that turns on/off wifi blinks orange/blue. Blue being the wifi is on,orange being wifi is off. I have internet, i can surf, I notice when a page is loading in my broswer or a simple youtube vid the wifi button lights flash blue/orange.

4. I have no idea how to install apps.

---

### Post by Windows Nerd on 2010-06-24
> **Jaycob said:**
> Thanks

1. Actually I dont get error messages, but the software center load to the main page where it tells you the DIFFERENT types applications to download , like science,browsers,social networking apps,that page loads.if I choose a type of app that I want that page freezes or doesn't load.

2. My speakers play fine,just that they dont mute when i use my headphones.My speakers work fine only problem I have is that they dont mute when I use my headphones.

3. The button that turns on/off wifi blinks orange/blue. Blue being the wifi is on,orange being wifi is off. I have internet, i can surf, I notice when a page is loading in my broswer or a simple youtube vid the wifi button lights flash blue/orange.

4. I have no idea how to install apps.

4: You can do it via CLI, if you are comfortable using it. Just type:
```
sudo apt-get install *foo*
```
*foo* here is the name of the program you wish to install (well, more specifically the package or package group, if you care to know)

1: Very odd, can you load the Software Centre on your LiveCD? I'm thinking a bug here, I have never heard of this problem. Perhaps another user can help you out here, I'm stumped.

2: This is an ALSA/PulseAudio problem, and luckily it is a common problem.

(Funnily enough, Googling around people get this problem on Windows too)

Anyways, it was a kernel bug in Karmic, though I am assuming you are using Lucid. 

From another thread:

> I am willing to bet that this is fixed by going to system, preferences,  Sound.  Then under sound, select the hardware tab and select your  headphones.  Then under the output tab, select your headphones. See if  this fixes your problem.
If this doesn't work let me know.

3: Besides the funny animation, does it cause any problems? Then it may be an animation bug. It probably peeves you to see that animation every time you load a webpage, but if it doesn't cause any problems, it is a probable bug.

Sorry for not being sure about how to solve some problems, but hey, I'm no guru, and still learn something new about Linux almost daily. :)

Scott

---

### Post by Andrew-J on 2010-06-24
1: can you use synaptic instead of software centre?
3: I would say if its not hindering you then i would leave it alone or make it very low priority.
4: I second the CLI, there are usually pretty good instruction from other users around the internet, or synaptic again.

Synaptic is found <system/Admin/synaptic package manager> if you didn't know.

---

### Post by netwarriorwy on 2010-06-24
Hi! I've been using Ubuntu for two years but I'm not an expert, but I also second the CLI solution on how to install apps.

Besides the ```
sudo apt-get install *foo*
``` approach you may not have a clue about the names of the apps, so if you wanna search some names that contain a word you know you can run this command on run CLI
```
sudo apt-cache search *keyword*
```. For example if you replace the keyword with "firefox" you'll get a list of packages related to the Mozilla Firefox Explorer.

If you're not having trouble with your connection it may be a bug the flashing light,to be sure try this on the CLI
```
ping google.com
``` and after 10 seconds press > Ctrl+C if you see that you haven't lost any packets then u're connection is fine, and the light thing is a bug.

I hope I helped a lil bit :wink:

---

### Post by Windows Nerd on 2010-06-24
> **netwarriorwy said:**
> Hi! I've been using Ubuntu for two years but I'm not an expert, but I also second the CLI solution on how to install apps.

Besides the ```
sudo apt-get install *foo*
``` approach you may not have a clue about the names of the apps, so if you wanna search some names that contain a word you know you can run this command on run CLI
```
sudo apt-cache search *keyword*
```. For example if you replace the keyword with "firefox" you'll get a list of packages related to the Mozilla Firefox Explorer. 
I forgot about that function. This guy has it covered, couldn't have said it better myself.

> **netwarriorwy said:**
> If you're not having trouble with your connection it may be a bug the flashing light,to be sure try this on the CLI
```
ping google.com
``` and after 10 seconds press  if you see that you haven't lost any packets then u're connection is fine, and the light thing is a bug.

I hope I helped a lil bit :wink:
I he is just loading a webpage, unless he has dial-up (which is becoming more and more uncommon these days) the button should only be flashing like that for a second (or maybe two).

May I add a correction: when you say the internet "button", for terminalogy's sake it is *Network Manager's Panel Icon*. Much more specifc, and won't cause confusion.

Scott

---

### Post by netwarriorwy on 2010-06-24
Please tell us how you're doing and if there's something else we can do for you. Best Regards! ):P

---

### Post by Jaycob on 2010-06-24
> **Andrew-J said:**
> 1: can you use synaptic instead of software centre?
3: I would say if its not hindering you then i would leave it alone or make it very low priority.
4: I second the CLI, there are usually pretty good instruction from other users around the internet, or synaptic again.

Synaptic is found <system/Admin/synaptic package manager> if you didn't know.

this is the error I get when I tried to access the synaptic  package manager

E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Windows Nerd on 2010-06-25
> **Jaycob said:**
> this is the error I get when I tried to access the synaptic  package manager

E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
From this, I take it you are not able to access stuff via CLI

could you post the output of
```
cat /etc/apt/sources.list
```

from the terminal please?

Scott

---

### Post by Jaycob on 2010-06-26
> **Windows Nerd said:**
> From this, I take it you are not able to access stuff via CLI

could you post the output of
```
cat /etc/apt/sources.list
```

from the terminal please?

Scott
here  

 deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntukarmic](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntukarmic) main

---

### Post by philinux on 2010-06-26
Open a terminal.

```
gksu gedit /etc/apt/sources.list
```

Delete or put a # in front of the very last line. i.e. line 48 as the error says.

This line is the error.
deb [http://ppa.launchpad.net/globalmenu-...a/ubuntukarmic](http://ppa.launchpad.net/globalmenu-...a/ubuntukarmic)  main

---

### Post by sukigenseki on 2010-06-26
After following the instructions on the post previous to mine when you are finished with that sources.list file make sure to do

sudo apt-get update;sudo apt-get upgrade

---

### Post by Jaycob on 2010-06-26
> **Windows Nerd said:**
> From this, I take it you are not able to access stuff via CLI

could you post the output of
```
cat /etc/apt/sources.list
```

from the terminal please?

Scott

OK I did and it worked!!!!!!!!!!! THANKS TO ALL YOU

IM still having the speaker problem.....

---

### Post by Windows Nerd on 2010-06-27
> **Jaycob said:**
> OK I did and it worked!!!!!!!!!!! THANKS TO ALL YOU

IM still having the speaker problem.....
So, just to make sure:

Problem #1 is fixed and is working just fine for you.

Problem #2 is still a problem

Problem # 3 is a bug (I am unsure if I should file the bug report or not as it is your system and I do not know your system.

As far as #2 goes, did you try the fix I mentioned on the first page (I *think* it is my 3rd post).

Anyways, I am glad one of the problems was fixed for you.

Scott

---

### Post by Windows Nerd on 2010-06-28
> **sukigenseki said:**
> After following the instructions on the post previous to mine when you are finished with that sources.list file make sure to do

sudo apt-get update;sudo apt-get upgrade
Shouldn't you do:

```
sudo apt-get update && sudo apt-get upgrade
```

putting the semi colon in there only executes the command after the semicolon.

---

