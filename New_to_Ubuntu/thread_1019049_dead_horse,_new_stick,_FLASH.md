---
title: "dead horse, new stick, FLASH"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by PermNoob on 2008-12-22
ok, so I am trying to get my laptop to run vidoes hosted, well, anywhere.  I have installed flash, but I still can't watch videos on youtube and the like.  it is just a grey screen.  I think my initial mistake was I ended out installing two different programs trying to rectify the problem, and I think I made it worse.  I tried uninstalling flash but that still didn't help.  I can open a terminal and type commands, but that is about where my ubuntu experince ends, willing to learn tho!

Ubuntu 7.10
Gnome 2.20.0

---

### Post by PermNoob on 2008-12-22
oh, and in firefox, forgot to mention that.  I tried installing konqueror to see if I could make it work there, and failed, and I would rather stick w/ FF, as it is what I know.  also, installing a new program just because you can't make the one you have work is a sign of weakness.  at least thats what my lifecoach told me.

---

### Post by ercferret18 on 2008-12-22
you could try reinstalling... that should fix it

---

### Post by taurus on 2008-12-22
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by Chew N Tobacca on 2008-12-22
If you run this in the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

it will download and install a bunch of stuff including Java, Adobe Flash, and various other audio/video codecs that are commonly used but not included in the base install.

Note: if you are using xubuntu or kubuntu, replace "ubuntu-restricted-extras" with "xubuntu-restricted-extras" and so on. Essentially they are the same.

---

### Post by PermNoob on 2008-12-22
I have tried reinstalling a couple times to no availe.
I am running those commands now.  the update is doing a whole heck of a lot, but is hung up at 
99% [Connecting to packages.freecontrib.org (34.52.53.34)]                     

also a stupid question, but I belive i installed gnash swf to try and play flash.  I say believe becasue I can't remember if that is actually what I installed.  If it is not included in my original Ubuntu install, I would like to remove it, I just want to make sure that that is it.

---

### Post by PermNoob on 2008-12-22
it keeps timing out on that step, should I worry about that or just continue?

---

### Post by taurus on 2008-12-22
Can you post your /etc/apt/sources.list?  Looks like you could have some dead repos/sites.

```
cat /etc/apt/sources.list
```

---

### Post by PermNoob on 2008-12-22
still doesn't work.   first time i try to install flashplugin-nonfree (same as I was using before) i get this message :

(Reading database ... 101996 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--19:11:59--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.178.70
Connecting to fpdownload.macromedia.com|96.6.178.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:11:59 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


then if I try to install it again, I get a real quick check that claims its already at the most current version

---

### Post by PermNoob on 2008-12-22
## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe multiverse
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by PermNoob on 2008-12-28
wow this is a lively forum, too bad my thread isn't as well...

bump

---

### Post by PermNoob on 2008-12-29
how often am I allowed to bump before I am just abnoxious?  

any more info, kinda got dropped half way thru my diagnostics.

---

### Post by PermNoob on 2008-12-31
bump again.
also, are there any other forums, this one is swamped!

---

### Post by PermNoob on 2009-01-02
am I getting ignored because this is a common problem and no one wants to help?  I don't mean to be abnoxious, but it has been over a week and I have got nothing, I am tempted to start a new thread w/ a new title.

---

### Post by OldTimeTech on 2009-01-02
May I suggest that your using feisty and most of us have moved on to Intrepid or are still on Hardy Heron....and this problem is not such a problem in the newer distros.

---

### Post by PermNoob on 2009-01-02
ok, but is it possible to make it work now?  I see an update in my future, but I have several other computer projects ahead of me before I can tackle that.  short of videos, fiesty has all the functionality i need right now.

---

