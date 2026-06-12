---
title: "Many questions from a new linux user..."
date: 2010-05-15
forum: New to Ubuntu
---

### Post by swrap on 2010-05-15
Hello everyone...

I'm new to ubuntu and I have been trying to look around and find answers to many questions that I have... yet the answers I found have been fairly indirect or not answering my questions.... however I apologize if my question is answered somewhere and I overlooked it...

but here are the questions I have...

I have a macbook pro 5 (triple booting with mac, windows 7, and ubuntu) and a couple things i was wondering...

is there a package I can download for my keyboard functions to work (like backlighting) and is there a package I can get for my trackpad so I can scroll with two fingers?

also can someone explain to me the difference between Ubuntu, Kubuntu, and Xubuntu? (I have read the wiki pages but I'm guessing i'm looking for not necessarily what IS the difference but why someone would prefer one over the others. what is the pros? the cons? etc...

and lastly I am involved with music... and Ubuntu Studio has interested me. I want to get it but I was wondering... do I have to overwrite Ubuntu on my partition for Ubuntu Studio? and can I install Ubuntu Studio from Ubuntu? Is there a special process to install it since I am on a mac or would I just install it like I did Ubuntu?

Sorry for all the questions but thanks in advance for helping a new user understand Ubuntu, and the world of Linux a little better.

S-Wrap

---

### Post by marshmallow1304 on 2010-05-15
[This page]("https://help.ubuntu.com/community/MacBookPro") should be of assistance with your Mac-specific issues.  For configuring your trackpad, you might try [gpointing-device-settings]("apt://gpointing-device-settings") which, once installed, is available under System->Preferences->Pointing Devices and is separate from the basic Mouse configuration utility.


Ubuntu, Kubuntu, Xubuntu, and now Lubuntu are all basically Ubuntu but with different [desktop environments]("http://en.wikipedia.org/wiki/Desktop_environment") and default programs.
Ubuntu - [GNOME]("http://en.wikipedia.org/wiki/GNOME")
Kubuntu - [KDE]("http://en.wikipedia.org/wiki/KDE")
Xubuntu - [XFCE]("http://en.wikipedia.org/wiki/XFCE")
Lubuntu - [LXDE]("http://en.wikipedia.org/wiki/LXDE")
The desktop environment you use is a question of preference and perhaps hardware specifications as some DEs are more demanding of resources than others.  Generally, KDE > GNOME > XFCE > LXDE in terms of resources used.  There are other DEs as well, but these are the ones chosen to have official Ubuntu releases.
 

You do not have to overwrite your install to add Ubuntu Studio.  I've never used it, but you should be able to add it by installing [ubuntustudio-desktop]("apt://ubuntustudio-desktop") package.  You may have to select it when logging in.  Perhaps someone who's used it can provide more information.

---

### Post by VeeDubb on 2010-05-15
[B][COLOR="DarkOliveGreen"]Welcome to linux.  A lot of times the answers seem wrong or indirect, but it's usually a matter of noob vs non-noob communication.  See my answers in line below.
[/COLOR][/B]
> **swrap said:**
> Hello everyone...

I'm new to ubuntu and I have been trying to look around and find answers to many questions that I have... yet the answers I found have been fairly indirect or not answering my questions.... however I apologize if my question is answered somewhere and I overlooked it...

but here are the questions I have...

I have a macbook pro 5 (triple booting with mac, windows 7, and ubuntu) and a couple things i was wondering...

is there a package I can download for my keyboard functions to work (like backlighting) and is there a package I can get for my trackpad so I can scroll with two fingers?

[B][COLOR="DarkOliveGreen"]I don't know about the extra keyboard functions, but there's a good chance it's no a matter of installing a package, but some simple boot options that need to be enabled.  That's all I had to do to get my extra function keys on my Asus eeePC working, but my fix won't work for you.  Hopefully somebody else will chime in.

As far as the trackpad, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1479361](http://ubuntuforums.org/showthread.php?t=1479361)[/COLOR][/B]

also can someone explain to me the difference between Ubuntu, Kubuntu, and Xubuntu? (I have read the wiki pages but I'm guessing i'm looking for not necessarily what IS the difference but why someone would prefer one over the others. what is the pros? the cons? etc...

[B][COLOR="DarkOliveGreen"]Each of the 3 uses a different window management system and has a different set of associated apps.  As far as the difference between KDE (kubuntu) and Gnome (ubuntu), it's purely a matter of preference.  I recommend that everybody try both.  Years ago, I was a big KDE guy.  These days I refuse to use it because the way all the KDE apps are named started making me twitch.

XFCE (Xubuntu) is much more "light weight."  It uses far less in terms of system resources, but isn't as pretty.  It's a good choice for older systems that would get bogged down with KDE or Gnome.[/COLOR][/B]

and lastly I am involved with music... and Ubuntu Studio has interested me. I want to get it but I was wondering... do I have to overwrite Ubuntu on my partition for Ubuntu Studio? and can I install Ubuntu Studio from Ubuntu? Is there a special process to install it since I am on a mac or would I just install it like I did Ubuntu?

[B][COLOR="DarkOliveGreen"]There are two ways to get Ubuntu Studio.  You can download an ISO for it and do a fresh install, but if you've already got a running ubuntu system, there's not much point.  Just go into synaptic package manager, and search for ubuntustudio, and install everything that comes up.  

Alternatively, you can enter the following command in a terminal
```
sudo apt-get install ubuntustudio*
```

That star at the end of the command is NOT an accident.  Last time I installed Ubuntu Studio, I only got the basic parts.  Putting that star at the end will install every package that starts with "ubuntustudio" which is exactly what you want.[/COLOR][/B]

Sorry for all the questions but thanks in advance for helping a new user understand Ubuntu, and the world of Linux a little better.

S-Wrap

---

### Post by swrap on 2010-05-17
> **VeeDubb said:**
> [B][COLOR=DarkOliveGreen]
[/COLOR][/B][B][COLOR=DarkOliveGreen]There are two ways to get Ubuntu Studio.   You can download an ISO for it and do a fresh install, but if you've  already got a running ubuntu system, there's not much point.  Just go  into synaptic package manager, and search for ubuntustudio, and install  everything that comes up.  

Alternatively, you can enter the following command in a terminal
 	Code:
 	sudo apt-get install ubuntustudio* 
That star at the end of the command is NOT an accident.  Last time  I installed Ubuntu Studio, I only got the basic parts.  Putting that  star at the end will install every package that starts with  "ubuntustudio" which is exactly what you want.[/COLOR][/B]


When I go into the terminal and try to install that I get an error message and so the packages won't install. I went to Ubuntu > Software Center and downloaded everything under Ubuntu Studio... but how to I get the layout I would if I was to install Ubuntu Studio vs. Ubuntu?

---

### Post by VeeDubb on 2010-05-17
Well, that command should have worked, but in any case, I'd go to synaptic package manager and install everything that comes up when you search for ubuntu studio that way.  That should get you all of it.

Bare in mind, I have not used ubuntu studio in quite some time.

---

