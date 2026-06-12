---
title: "And today's issue with Ubuntu is...."
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-22
Firefox 4. There's no option to update Firefox in the currently installed version so I went to the Ubuntu documentation pages which recommended a sudo apt-get install firefox-4.0.

Terminal proceeded to download over 390Mb! of data.... and now I cannot find Firefox anywhere on my system. 

Windows? Downloaded and installed in less than 1 minute with 3 clicks.

Ubuntu is getting to be a bit of a joke to be honest.

So once again I must beg for help to accomplish what should be the simplest of tasks. What's going on here? I love Ubuntu when it works but mostly, it doesn't.

---

### Post by 5149.5 on 2011-03-22
Look for a Minefield app. That is the name of the 4.0 browser while it is in pre-release status.

---

### Post by Paqman on 2011-03-22
To get software that's more recent than what's in the repos you can use PPAs (Private Package Archives). A lot of projects, including Mozilla, maintain a PPA for Ubuntu:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

I believe there are some technical discussions going on about whether this is the best way to handle important, regularly update software like browsers.

---

### Post by philinux on 2011-03-22
> **Torp3x said:**
> Firefox 4. There's no option to update Firefox in the currently installed version so I went to the Ubuntu documentation pages which recommended a sudo apt-get install firefox-4.0.

Terminal proceeded to download over 390Mb! of data.... and now I cannot find Firefox anywhere on my system. 

Windows? Downloaded and installed in less than 1 minute with 3 clicks.

Ubuntu is getting to be a bit of a joke to be honest.

So once again I must beg for help to accomplish what should be the simplest of tasks. What's going on here? I love Ubuntu when it works but mostly, it doesn't.

Unless you're running Natty then 4.0 is not in the current ubuntu repo's.

But see this.
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by Foxcow on 2011-03-22
Firefox 4 is available for 10.10.  Just type these commands in the command line:

```

    sudo add-apt-repository ppa:mozillateam/firefox-stable
    sudo apt-get update && sudo apt-get upgrade

```

I upgraded using the PPA

---

### Post by kellemes on 2011-03-22
> **Torp3x said:**
> 
Ubuntu is getting to be a bit of a joke to be honest.

So once again I must beg for help to accomplish what should be the simplest of tasks. What's going on here? I love Ubuntu when it works but mostly, it doesn't.

I wonder, since you're obviously not happy with Ubuntu.. what made you start using it to begin with?

You should know Ubuntu isn't the bleeding-edge distro that brings you the newest Firefox when it's released. Stability is an issue as well and pulling in the newest of packages isn't helping stability in general.
For that you may have to use something like Arch, just a few minutes ago I updated my Arch-box and pulled in Firefox 4.0 (didn't even have to click ones ;-)

---

