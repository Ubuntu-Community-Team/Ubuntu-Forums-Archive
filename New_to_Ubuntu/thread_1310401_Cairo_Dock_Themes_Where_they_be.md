---
title: "Cairo Dock Themes: Where they be?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by hollowtd on 2009-11-01
Howdy

Just got Cairo dock but when I go to manage themes, there is only one--the default theme. How do I get the list of themese in there to choose from? Please help asap. Cheers

---

### Post by hollowtd on 2009-11-01
Hi 

JUst got Cairo dock and there are no themese besides the default theme to choose from. know how to get those so they show up when I go to manage themes? I'm using koala. Thanks

---

### Post by pootan on 2009-11-01
I had the themes missing on mine initially and I got them back by closing the dock completely. When I did this I found I had another dock running under the second one. After I killed this as well then reopened Cairo from the system tools menu the themes reappeared.

---

### Post by hollowtd on 2009-11-01
I do that and still there is only the default theme under the manage themes menu. When I initially start cairo dock, however, it says that it can't open the dustbin and the default theme will be used instead. Is this maybe the problem? Something I need to get from Terminal? Weird. Thanks

---

### Post by hollowtd on 2009-11-01
Man, killed it, re downloaded it and still the themese are not there. Strange.

---

### Post by pootan on 2009-11-01
Ah I think i know your problem. The version in the repositories is and old version. To get the new version with themes you have to go to a Launchpad page and download the latest Cairo core package AND the plugins package. I'll see if I can find the official download page again.

---

### Post by peculiar penguin on 2009-11-01
I think I ran into that problem with Jaunty and the version in its repositories a long time ago... IIRC I had to download the themes separately (from [here]("http://developer.berlios.de/project/showfiles.php?group_id=8724")?) and extract them to /usr/share/cairo-dock/themes or something like that.

Instead I would recommend adding [this PPA]("https://launchpad.net/%7Ecairo-dock-team/+archive/ppa") to your software sources and installing from there. That way you'll get a much more recent version which works better and can download themes from the internet directly.

---

### Post by pootan on 2009-11-01
Yes adding the ppa method is the best way as even the files on the berlios site are old.


this is what you get when you download the latest help file from there. 

We are now on Launchpad, using bzr instead of svn.
[]("http://launchpad.net/cairo-dock")
current version on 13/10/2009 is 2.1.1
see you soon ! ;-)

---

### Post by fabounet on 2009-11-02
are you connected to the Net ? if so, are you behind a firewall ?
if so, try to set up *wget*

---

### Post by fabounet on 2009-11-02
If you don't have themes in the Theme Manager, it may be a connexion problem, or if you're under a firewall you may have to configure *wget*

See the wiki (wiki.cairo-dock.org) to solve the common problems ;-)

---

### Post by cariboo on 2009-11-02
Please don't double post. I have merged your two threads.

---

### Post by user39472 on 2009-12-15
I have the same problem, no themes but the default and I had the error message about no theme for the dustbin (and clock) but that problem went away when I deleted the ~/.config/cairo-dock folder.

> **fabounet said:**
> If you don't have themes in the Theme Manager, it may be a connexion problem, or if you're under a firewall you may have to configure *wget*

See the wiki (wiki.cairo-dock.org) to solve the common problems ;-)

The only common theme problem I found on the wiki was if you are behind a proxy. I'm behind a router with a firewall. Is there anyway to test if it's a connection problem?


EDIT:
It seems to be some kind of connection problem, I found by accident the setting for connection time out for the theme server and increased it (Behaviour > System). So now with a little patience I can download and change themes. But since the theme is changed I have to go back and change the time out setting again.

Thnx

---

### Post by turboopugsleylx on 2010-01-17
This ticks me off...

I went to the link listed above

[https://launchpad.net/%7Ecairo-dock-team/+archive/ppa](https://launchpad.net/%7Ecairo-dock-team/+archive/ppa)

Followed directions on there now my synaptic gives me this error...

E: Type 'main' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How in the sam H#LL do I fix this?

---

### Post by fabounet on 2010-01-17
the line 
> echo "deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list

is **1** line
it is cut on the site because it's larger than the page, but it's a aingle line.
I guess when you did the copy-paste you pasted the carriage return with it.
so you just have to correct that in your */etc/apt/sources.list*

---

