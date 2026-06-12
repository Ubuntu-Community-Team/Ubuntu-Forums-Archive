---
title: "Tried to install Compiz, fubarred my Ubuntu 10.10"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-01-26
Just installed 10.10 after upgrading from 9.10 (yeah I was way overdue) lol but after I finally got past the NVidia driver issue and got booted in Ubuntu I figured let me get Compiz back so I followed this link [http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html ]("http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html")
And ran into a few issues... Now Ubuntu Software Center doesn't work, Compiz says it's version 0.8.2 not 0.9.1 and when I open Synaptic Manager I get an error of some sort... I had a friend with a similar computer as mine send me his sources.list and I pasted it into mine and it still doesn't work.. No matter what I try I keep getting this error, and I can't even uninstall compiz now either... SMH..!!

This is the error I get when opening Synaptic Package Manager..
"E: Malformed line 59 in source list /etc/apt/sources.list (dist)
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/nilarimogard-test3-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

And when I goto my sources file and check out the line errors, it always changes to something else but that nilarimogard-test-3 blablabla is what's giving me the headache.. Any help..?? 

Thanks in advance..

---

### Post by sikander3786 on 2011-01-26
Welcome to the forums :-)

Please post the complete output of this command from Applications > Accessories > Terminal:

```
cat /etc/apt/sources.list
```

---

### Post by snowpine on 2011-01-26
You broke your software sources. Edit the file with:

```
gksu gedit /etc/apt/sources.list
```

Scroll down to line 59 and delete this "malformed line". Save the changes and then you should be able to update. If it doesn't, you can post your /etc/apt/sources.list file here and I'll try to help.

I personally would not follow some random internet tutorial that warns "using this PPA may break stuff or make your computer explode." :)

---

### Post by JDM_SOHC on 2011-01-26
Whoaaaa, you guys are fast..!! Thanks for the quick replies... This is what I get after I do what the first gentlemen suggested..

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://vi.archive.ubuntu.com/ubuntu/](http://vi.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverseurity multiverse
deb-src [http://security.ubuntu.com/ubu](http://security.ubuntu.com/ubu)

---

### Post by JDM_SOHC on 2011-01-26
> **snowpine said:**
> You broke your software sources. Edit the file with:

```
gksu gedit /etc/apt/sources.list
```Scroll down to line 59 and delete this "malformed line". Save the changes and then you should be able to update. If it doesn't, you can post your /etc/apt/sources.list file here and I'll try to help.

I personally would not follow some random internet tutorial that warns "using this PPA may break stuff or make your computer explode." :)

LoL yeah I usually am way smarter than that but it was the first link that popped up in google so usually those are pretty credential I guess this time it was FML =(

---

### Post by JDM_SOHC on 2011-01-26
I deleted line 59 and now it says this...

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/nilarimogard-test3-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by snowpine on 2011-01-26
> **JDM_SOHC said:**
> I deleted line 59 and now it says this...

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/nilarimogard-test3-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Sorry, my bad, missed that the first time around. :)

```
gksu gedit /etc/apt/sourceslist.d/nilarimogard-test3-maverick.list
```

Delete line 3.

ps Why are you trying to install an unstable and unsupported version of Compiz?

---

### Post by JDM_SOHC on 2011-01-26
> **snowpine said:**
> Sorry, my bad, missed that the first time around. :)

```
gksu gedit /etc/apt/sourceslist.d/nilarimogard-test3-maverick.list
```Delete line 3.

ps Why are you trying to install an unstable and unsupported version of Compiz?

When I open that up, there's no text in there..??

And I just figured it was put as that because it was a newer version, and since my PC is pretty new I never really have compatibility issues, again I'll admit this was totally my fault... I figured Compiz had been updated since last year and FML it seems that the older version is still the one to roll with...

---

### Post by snowpine on 2011-01-26
Sorry, I don't know what's up with me today.... try this instead:

```
gksu gedit  /etc/apt/sources.list.d/nilarimogard-test3-maverick.list
```

---

### Post by JDM_SOHC on 2011-01-26
> **snowpine said:**
> Sorry, I don't know what's up with me today.... try this instead:

```
gksu gedit  /etc/apt/sources.list.d/nilarimogard-test3-maverick.list
```


Wooohooo it worked..!! 

Thanks bro I appreciate your time and effort... 

Now that I have that working, and I'm on 0.8.2 Compiz is there a way to check to make sure my Compiz is fully functional..?? For instance, I don't see the mouse animations or any of that like I did on Ubuntu 9.10..??

Thanks again, been @ this for hours and within 10 minutes I have solved the headache lol...

---

### Post by snowpine on 2011-01-26
I am not a Compiz expert, but I think maybe you change its settings by going to the System menu, Preferences, Desktop Effects?

---

### Post by JDM_SOHC on 2011-01-26
Yeah I'm not in any rush to figure it out I was j/w..

I wonder if theres a way to create smoother mapping though... I had the nVidia issue where I kept getting black screen upon boot so I had to modify grub with "nomodeset" and I can tell the window transitions aren't nearly as smooth in 10.10 as they were in 9.10 so i assume it's a video driver issue... Any feedback on that..??

---

### Post by 0N3 on 2011-01-26
You have to install the compiz fusions plugins extra package im sure to get all the effects

---

### Post by 0N3 on 2011-01-26
You have to install the compiz fusions plugins extra package im sure to get all the effects

---

### Post by realzippy on 2011-01-26
[I]...so I assume it's a video driver issue... Any feedback on that..??
[/I]

Which VGA card/driver?

---

### Post by JDM_SOHC on 2011-01-26
> **0N3 said:**
> You have to install the compiz fusions plugins extra package im sure to get all the effects

thanks bro I remember doing something like that before as well...

> **realzippy said:**
> [I]...so I assume it's a video driver issue... Any feedback on that..??
[/I]

Which VGA card/driver?

I'm using an nVidia GEFORCE 6150 LE...

Does this have any correlation with why I can't play videos in full screen mode either..?

---

### Post by cgroza on 2011-01-26
You can set that up by installing compizconfig-settings-manager. It will show up under System>Preferences and there is a ton of options there.

Posting this because I saw no reference to compizconfig on this thread.

---

### Post by JDM_SOHC on 2011-01-26
> **cgroza said:**
> You can set that up by installing compizconfig-settings-manager. It will show up under System>Preferences and there is a ton of options there.

Posting this because I saw no reference to compizconfig on this thread.

I have that installed already but for some reason I don't have nearly half the options I had on 9.10 Ubuntu and I don't remember installing any plugin's I thought it came standard with all the neat lil extras..

---

### Post by realzippy on 2011-01-27
*...I don't have nearly half the options I had on 9.10 Ubuntu... *


You have installed compiz-fusion-plugins-extra ?

```
sudo apt-get install compiz-fusion-plugins-extra
```


....................................................................

Which nvidia driver version? 173?

---

### Post by JDM_SOHC on 2011-01-27
yeah I have that installed but didn't have the Show Mouse option... thanks for your help though.. I reverted back to 10.04 and now I have no video driver issues =) still no mouse animation but at least it's runnin way smoother than 10.10 was..

---

