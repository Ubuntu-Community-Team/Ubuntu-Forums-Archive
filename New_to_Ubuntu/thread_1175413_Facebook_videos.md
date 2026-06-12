---
title: "Facebook videos?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by volkanmet86 on 2009-06-01
hi! i have been using win fir about 15 years and recently started to use ubuntu 904. but i cannot watch uploaded videos on facebook over firefox? hiw can i solve this problem?

---

### Post by nandemonai on 2009-06-01
> **volkanmet86 said:**
> hi! i have been using win fir about 15 years and recently started to use ubuntu 904. but i cannot watch uploaded videos on facebook over firefox? hiw can i solve this problem?

Do you have flash installed?

```
sudo apt-get install adobe-flashplugin
```

---

### Post by Tibuda on 2009-06-01
> **nandemonai said:**
> Do you have flash installed?

```
sudo apt-get install adobe-flashplugin
```

I thought the package name were [flashplugin-nonfree]("apt:flashplugin-nonfree")?

---

### Post by nandemonai on 2009-06-01
> **danielrmt said:**
> I thought the package name were [flashplugin-nonfree]("apt:flashplugin-nonfree")?

There are a few different versions. I hear the adobe one tends to work better though I do use flashplugin-nonfree myself.

Only issue is to make sure you only have 1 plugin installed at any one time.

---

### Post by Tibuda on 2009-06-01
> **nandemonai said:**
> There are a few different versions. I hear the adobe one tends to work better though I do use flashplugin-nonfree myself.

Only issue is to make sure you only have 1 plugin installed at any one time.
But flashplugin-nonfree is from adobe, and I can't find adobe-flashplugin in my Synaptic

---

### Post by nandemonai on 2009-06-01
Good point..

I guess a new repository is added when you install it from the adobe site:

> Installation instructions via APT

       1. Click the download link and follow the instructions to complete installation
       2. To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.
       3. To get the most up-to-date Flash Player in the future, issue the following commands from the Terminal:

              * sudo apt-get update
              * sudo apt-get install adobe-flashplugin



My bad.

---

### Post by volkanmet86 on 2009-06-01
yes i have installed flash but the problem remains. i got this message,

[http://img217.imageshack.us/my.php?image=screenshotxwv.png](http://img217.imageshack.us/my.php?image=screenshotxwv.png)
[IMG]http://img217.imageshack.us/my.php?image=screenshotxwv.png[/IMG]

---

### Post by Tibuda on 2009-06-01
Have you read the message? The video was removed.

---

### Post by volkanmet86 on 2009-06-01
i can open these videos in vista but i get such messeges in ubuntu

---

### Post by nandemonai on 2009-06-01
> **volkanmet86 said:**
> i can open these videos in vista but i get such messeges in ubuntu

Seems like a facebook issue to me then.

---

### Post by Tibuda on 2009-06-01
Why they just don't tell the truth then? Try installing the [user agent switcher plugin]("https://addons.mozilla.org/en/firefox/addon/59") to pretend you are using windows, and see what happens.

---

### Post by chrisod on 2009-06-01
I watch FB videos all the time with the adobe plugin (downloaded direct from Adobe) and Firefox in Ubuntu. I don't think it's a FB program. I'd suggest uninstalling all Flash plugins, then install the Adobe one.

---

### Post by volkanmet86 on 2009-06-01
i have tried all the suggestions but still no solution :(

---

### Post by chebbie on 2009-06-12
i'm having the same problem and i've downloaded the .deb version of flashplugin 10 for ubuntu and while installing i'm having the problem 'error architecture i386'..i'm on ubuntu 9.04 jaunty

---

### Post by pous on 2009-06-12
although i haven't tried fb videos, i do seem to have trouble with all the sites i watch anime on, except for videos posted on megavideo which i usually try to avoid due to the time limit...

---

### Post by anaconda on 2009-06-12
I have the same problem on my work machine.

Facebook videos wont work, BUT eg. youtube videos play without problems.

In facebook I get complains that I need to install a new flashplugin, so I installed the flashplugin 10.. but still no luck.

---

### Post by pous on 2009-06-12
would it help to install windows' firefox and plugins+codecs through wine?
is it possible, if so, is it better or worse compared to the linux version of firefox??

just a thought i just had..

---

### Post by Sinkingships7 on 2009-06-12
> **nandemonai said:**
> There are a few different versions. I hear the adobe one tends to work better though I do use flashplugin-nonfree myself.

Only issue is to make sure you only have 1 plugin installed at any one time.

flashplugin-nonfree is Adobe's flash... *slightly confused*

---

### Post by ahmedsaieed on 2009-06-13
having same problem here and its turning me crazy!

---

### Post by pous on 2009-06-14
> **volkanmet86 said:**
> i have tried all the suggestions but still no solution :(

i found the solution to my video issue hope it might help you... [http://ubuntuforums.org/showthread.php?t=1180896&](http://ubuntuforums.org/showthread.php?t=1180896&)

---

### Post by hegex on 2009-06-23
The problem is, facebook devs say: "Currently, Facebook requires a minimum Flash Player version of either 9.0.159.0 or 10.0.22.87 for all <fb:swf> tags." and Ubuntu uses 10.0.21 version. And i think Volkanmet86 has Ubuntu 64bit and how ever he will install things, he wount get the videos works, simply cos there is no 10.0.22 version for 64bit linux yet.

So if there is a way to cheat and pretend that you have 10.0.22 version, i want to know it too. User Agent Switcher just fakes your browser.

---

### Post by awaisclub on 2009-06-27
Thanks Pous. I have resolved my facebook problem through the thread link you have given.

---

