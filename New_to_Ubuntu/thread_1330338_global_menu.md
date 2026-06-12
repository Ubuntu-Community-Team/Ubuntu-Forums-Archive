---
title: "global menu"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-18
I am using Karmic Kola

I don't understand a single word in this thread:

[http://ubuntuforums.org/showthread.php?t=1286386](http://ubuntuforums.org/showthread.php?t=1286386)

I have switched from Mac. So I do want the global menu badly. Someone please give me proper steps to install it.

---

### Post by philinux on 2009-11-18
You'll have to do some work at your end I'm afraid it's not straight forward. Also they have no karmic version so you'll need to edit a file to get the jaunty version.

1. You need to add the global-menu teams ppa. This is easy. Open a terminal Apps>access>terminal.
```
sudo add-apt-repository ppa:globalmenu-team

```


2. Now you need to edit a file.

```
gksudo gedit /etc/apt/sources.list.d/globalmenu-team-ppa-karmic-list
```

Replace karmic with jaunty. Save the file.

3. Update the repos.

```
sudo apt-get update
```

4. Install global menu.

This is where I'm not sure what its actually called.

```
sudo apt-get install globalmenu
```

or it could be global-menu

Have fun.

---

### Post by iRounak on 2009-11-20
hi,
thanks for the reply.
> Replace karmic with jaunty. Save the file.
I dont understand this part. The code you gave me just opens a blank text file in etc/apt/sources.......

---

### Post by camaron1 on 2009-11-20
> **iRounak said:**
> hi,
thanks for the reply.

I dont understand this part. The code you gave me just opens a blank text file in etc/apt/sources.......

on a terminal:

**gksudo gedit /etc/apt/sources.list**

When asked give your password. 
Scroll down until you find the source for global menu and where it says **karmic** replace this with **jaunty**

---

### Post by iRounak on 2009-11-20
sorry, i am a total newbie. here are the file contents of
**gksudo gedit /etc/apt/sources.list : (Where exactly do i have to change karmic to jaunty. I know that ##lines are comments. But do i have to change every other line from karmic to jaunty or only those that begin with "src"**)

# 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by camaron1 on 2009-11-21
OK, open **Synaptic** manager, go to **Settings**, and **Other software**. Once there press **add** at the bottom of the window and add this:

[B]ppa:globalmenu-team/ppa

[/B]Once you've done this this should appear in the same window:

**[http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main**

If you don't see it just know refresh Synaptic, close it and open it again. Don't worry about the error message just now.

OK, go back to the same window and highlight the above, that is, **[http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main **and press **edit**. In this new window where you see, **Distribution:Karmic** make it **Distribution:Jaunty**. Close, reload and now you are able to install globalmenu.

---

### Post by wiebeest on 2009-11-21
Concerning Global-menu,I really don't get it.

Thought this was a really booming project with it's own google.code page and many enthusiastic contributers that evolved on a fast pace. The latest version worked very well on my Jaunty install. With the unfortunate exception with popular apps like firefox, open-office and opera browser I was still very content with it's existence and how well it integrated with my osx themed setup.

They even mentioned that they were trying to get global-menu in the main repositories of Ubuntu-gnome. 

So when I switched to Karmic the moment it became available and found out there wasn't a version for it yet, I thought this no doubt would come in a few days (as with most other apps).   

But now even a month after the release of Karmic Koala there still isn't a ppa for it available. What goes?

---

