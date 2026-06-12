---
title: "Ubuntu 9.10 - can't connect to sourceforge.net"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by JM067 on 2009-11-28
Hi guys, i'm a total newbie to Ubuntu, I installed 9.10 after my computer crashed and I didn't have a windows backup disc. I didn't realise 9.10 was a new release and i've done nothing but spend all my time fixing problem after problem. There's one problem though that seems to have me completely stumped:

Everytime I try to do pretty much anything on Ubuntu - update it, install flash, remove software, it keeps trying to connect to sourceforge.net and then timing out.

I also have to search for a new server about every 5 minutes when downloading any software because it keeps cutting out.

Any help would be much  appreciated.

JM

---

### Post by mkvnmtr on 2009-11-28
I have installed a lot of times. The only time I remember connecting to sorceforge in the process of getting every thing to work was to get microsoft fonts. Maybe you should be more exact on what you are doing and how you are doing it.

---

### Post by JM067 on 2009-11-28
OK, my main problem is that I can't see youtube - ie Flash player is not installed. I've spent hours on this, searched all the forums and tried out all their suggestions. Everytime I keep coming against this problem of trying to connect to some server and not being able to get through. Most of the time the problem is trying to connect to sourceforge.net

---

### Post by JM067 on 2009-12-02
PSA screenshot for what happened when I tried to update using the update manager. If anyone can shed any light on this it would be massively appreciated:

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by mkvnmtr on 2009-12-02
From the look of the screenshot the only problem is that the fonts did not install. Did it complete everything else? If so you should be good to go. Just try again on the fonts a a later time. Sometimes a repo is down for some reason. Even though utube works od on my system I am now using an app called Minitube to view thier movies. It does not use flash to view movies. You can get it by googling Get Deb and enabling their repository. They have some other apps you might be interested in.

---

### Post by coffeecat on 2009-12-02
**JM067**, there's an obscure bug affecting only a minority of users (you must be one of the unlucky ones) that causes timeouts when the package manager tries to download the MS font files from sourceforge. In your screenshot you can see that it stalled when trying to get Andale, the first of about a couple of dozen files that it needs to fetch from sourceforge. Your problem is that this causes a total failure of installation when you've selected a whole load of packages which include the MS fonts installer. Since you mention flash, I guess that you selected the ubuntu-restricted-extras package which includes both flash and ms fonts.

Here's what to do. Go to System > Administration > Synaptic. Select ubuntu-restricted-extras but don't click on apply just yet. Now find the package ttf-mscorefonts-installer and unmark it by right-clicking and selecting 'unmark'. Now you can click on 'Apply' and all your restricted multimedia stuff and flash will be installed.

If you need the mscorefonts and have access to the *.ttf files, there's another way of installing them. Post back if you need details.

There's been quite a few threads about the bug that's tripped you up but I can't give you any links atm. But if you're interested a forum search should throw them up. I don't know whether a fix is imminent or not.

---

### Post by stalkier on 2009-12-02
> **coffeecat said:**
> **JM067**, there's an obscure bug affecting only a minority of users (you must be one of the unlucky ones) that causes timeouts when the package manager tries to download the MS font files from sourceforge. In your screenshot you can see that it stalled when trying to get Andale, the first of about a couple of dozen files that it needs to fetch from sourceforge. Your problem is that this causes a total failure of installation when you've selected a whole load of packages which include the MS fonts installer. Since you mention flash, I guess that you selected the ubuntu-restricted-extras package which includes both flash and ms fonts.

Here's what to do. Go to System > Administration > Synaptic. Select ubuntu-restricted-extras but don't click on apply just yet. Now find the package ttf-mscorefonts-installer and unmark it by right-clicking and selecting 'unmark'. Now you can click on 'Apply' and all your restricted multimedia stuff and flash will be installed.

If you need the mscorefonts and have access to the *.ttf files, there's another way of installing them. Post back if you need details.

There's been quite a few threads about the bug that's tripped you up but I can't give you any links atm. But if you're interested a forum search should throw them up. I don't know whether a fix is imminent or not.

Kinda funny. Out of all the years I have been using Ubuntu with almost no problems I run into this obscure bug. :D More of an annoyance for me. I guess it is one more reason for me to not like MS. Darn you Gates!!! Darn you!! :D

---

### Post by JM067 on 2009-12-06
Thanks for letting me know about this. Is there any way I can stop it from messing up every software install/ uninstall as it happens virtually every time?

JM

---

### Post by durand on 2009-12-06
Just remove msttcorefonts for now and install it in maybe a week.
Go to the package manager: System > Admin > Synaptic
Search for msttcorefonts
Right click on the box at the front of the row and change it to remove. Then press apply at the top of the window.

---

### Post by coffeecat on 2009-12-06
> **JM067 said:**
> Thanks for letting me know about this. Is there any way I can stop it from messing up every software install/ uninstall as it happens virtually every time?

It only happens if you specifically mark it for installation, or if you mark ubuntu-restricted-extras for installation. I've described how to deal with the latter.

---

