---
title: "namoroka versus firefox 3.5"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by senorian on 2010-02-27
SOLVED

I keep on applying updates for firefox 3.5 and then restarting firefox ( or the browser) as instructed, but the icon remains blue and the name remains namoroka. But if I go to synaptic and search for "namoroka" there is no response.
Searching for "firefox" in synaptic brings up a whole raft of entries, a few of which are marked as installed.
So, how do I get rid of "namoroka" and which of the many entries do I use to install firefox?
Thank
(confused)

---

### Post by Ozymandias_117 on 2010-02-27
Go to your software sources and remove/disable Firefox-Stable PPA (Or something to that effect) then type "sudo aptitude update" "sudo aptitude reinstall firefox" and you should be back to 3.5

---

### Post by lovinglinux on 2010-02-27
> **Ozymandias_117 said:**
> Go to your software sources and remove/disable Firefox-Stable PPA (Or something to that effect) then type "sudo aptitude update" "sudo aptitude reinstall firefox" and you should be back to 3.5

The firefox stable PPA does not install Namoroka. It install Firefox 3.6 stable with proper branding.

> **senorian said:**
> I keep on applying updates for firefox 3.5 and then restarting firefox ( or the browser) as instructed, but the icon remains blue and the name remains namoroka. But if I go to synaptic and search for "namoroka" there is no response.
Searching for "firefox" in synaptic brings up a whole raft of entries, a few of which are marked as installed.
So, how do I get rid of "namoroka" and which of the many entries do I use to install firefox?
Thank
(confused)


Go to you "System >> Administration >> Software Sources >> Other Software" and disable the *ubuntu-mozilla-daily* ppa. Then go to Synaptic Package manager and mark firefox and firefox-3.5 for reinstallation and click "Apply". This will revert your Firefox to 3.5. If you want to upgrade to Firefox 3.6 stable version, with proper branding (logo and name), then and add the firefox stable ppa with these commands:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade

```

For additional info see the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Ozymandias_117 on 2010-02-27
Yeah, that one =P I couldn't remember what the name of it was =D

---

### Post by senorian on 2010-03-09
Thanks to all
I googled namoroka but still do not understand why there is an app with this name and why (and how ) I managed to get it installed.
What is the relationship between FF and Namoroka
Has the name been dropped from the FF system?
Thanks

---

### Post by lovinglinux on 2010-03-09
> **senorian said:**
> I googled namoroka but still do not understand why there is an app with this name...

Use Google site search feature. For example, if you have searched for [Namoroka site:ubuntuforums.org](http://www.google.com/search?q=Namoroka+site%3Aubuntuforums.org) you would find your answer on the third search result.

> **senorian said:**
> ...and why (and how ) I managed to get it installed

Probably because you have followed a tutorial without understanding it. You have added a Firefox development repository to your Software Sources, which upgrades Firefox with development versions called Namoroka.

Go to "System >> Administration >> Software Sources >> Other Software" and disable the *ubuntu-mozilla-daily* repository. Then run these:

```
sudo apt-get remove firefox && sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox
```

This will remove Namoroka and install the stable version of Firefox 3.6.

For additional info see the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by senorian on 2010-03-18
Many thanks lovinglinux
Sorry for the delay in replying
I followed your instructions (but there were 2 lines with "daily" and , at first try, I only unchecked (and hit "remove") one line so I was still left with Namoroka)
so went back and unchecked the other line.
Now the icon is orange and the title is Mozilla Firefox.
Many , many thanks

---

### Post by lilyatwt on 2010-04-09
Probably because you have followed a tutorial without understanding it. You have added a Firefox development repository to your Software Sources, which upgrades Firefox with development versions called Namoroka.

Go to "System >> Administration >> Software Sources >> Other Software" and disable the *ubuntu-mozilla-daily* repository. Then run these:

```
sudo apt-get remove firefox && sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox
```This will remove Namoroka and install the stable version of Firefox 3.6.

hi .. i'm new to Ubuntu and wanted Firefox 3.6 .. wound up with Namoroka .. your instructions worked beautifully .. thank you so much .. i've found lots of help in this forum .. thanks again!

---

### Post by lilyatwt on 2010-04-09
> **lilyatwt said:**
> Probably because you have followed a tutorial without understanding it. You have added a Firefox development repository to your Software Sources, which upgrades Firefox with development versions called Namoroka.

Go to "System >> Administration >> Software Sources >> Other Software" and disable the *ubuntu-mozilla-daily* repository. Then run these:

```
sudo apt-get remove firefox && sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox
```This will remove Namoroka and install the stable version of Firefox 3.6.

hi .. i'm new to Ubuntu and wanted Firefox 3.6 .. wound up with Namoroka .. your instructions worked beautifully .. thank you so much .. i've found lots of help in this forum .. thanks again!

---

### Post by nareshmeee on 2010-05-01
> **lovinglinux said:**
> Use Google site search feature. For example, if you have searched for [Namoroka site:ubuntuforums.org]("http://www.google.com/search?q=Namoroka+site%3Aubuntuforums.org") you would find your answer on the third search result.



Probably because you have followed a tutorial without understanding it. You have added a Firefox development repository to your Software Sources, which upgrades Firefox with development versions called Namoroka.

Go to "System >> Administration >> Software Sources >> Other Software" and disable the *ubuntu-mozilla-daily* repository. Then run these:

```
sudo apt-get remove firefox && sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox
```This will remove Namoroka and install the stable version of Firefox 3.6.

For additional info see the [COLOR=Sienna]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

thanx a lot i too did the samething and had problems

---

