---
title: "How can i upgrade my firefox to 3.5 version?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-30
i have just downloaded an archive from off site - "firefox-3.5.rc.tar.gz", but I don't know how to install it
help me please.

---

### Post by Paqman on 2009-06-30
Firefox 3.5 is available in the Jaunty repos. Go to System > Admin > Synaptic Package Manager and search for it.

It's always best to check the repos before downloading tarballs from some site. Tarballs are a pain, and don't update properly (which is *very* important for a browser)

---

### Post by SKYDOS on 2009-06-30
> **Paqman said:**
> Firefox 3.5 is available in the Jaunty repos. Go to System > Admin > Synaptic Package Manager and search for it.

It's always best to check the repos before downloading tarballs from some site. Tarballs are a pain, and don't update properly (which is *very* important for a browser)

i can't find there firefox 3.5 (( what's the name of that package?

---

### Post by Paqman on 2009-06-30
> **SKYDOS said:**
> i can't find there firefox 3.5 (( what's the name of that package?

Make sure you've got the Universe repo enabled (in Synaptic go to Settings > Repos). The package is just called [firefox-3.5]("http://packages.ubuntu.com/jaunty/firefox-3.5").

---

### Post by SunnyRabbiera on 2009-06-30
Also note that sometimes the repos are a little behind, patience is needed sometimes when concerning fresh stuff.

---

### Post by lovinglinux on 2009-06-30
The package is [firefox-3.5](apt:firefox-3.5) [apt-get]. Nevertheless, it's not rc2, but beta 4 pre. Firefox 3.5 final probably won't get into the Jaunty repositories anyway.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by Paqman on 2009-06-30
> **lovinglinux said:**
> The package is [firefox-3.5](apt:firefox-3.5) [apt-get]. Nevertheless, it's not rc2, but beta 4 pre. Firefox 3.5 final probably won't get into the Jaunty repositories anyway.

Bummer. I'm sure somebody will post up a link to a PPA in the next day or two that will contain the final version.

General note for PPAs: as with all repos you add, make sure they're from a source that's trusted in the community.

---

### Post by masux594 on 2009-06-30
Hmm.. The stable linux version is not released yet.. .. or i'm wrong?

Sysc, A

---

### Post by lovinglinux on 2009-06-30
> **Paqman said:**
> Bummer. I'm sure somebody will post up a link to a PPA in the next day or two that will contain the final version.

General note for PPAs: as with all repos you add, make sure they're from a source that's trusted in the community.

I think everyone wants to upgrade.

---

### Post by lovinglinux on 2009-06-30
> **masux594 said:**
> Hmm.. The stable linux version is not released yet.. .. or i'm wrong?

Sysc, A

None of them has been released yet.

---

### Post by masux594 on 2009-06-30
Great, so, just wait a couple of days .. We had wait until now guys! Don't be hasty..

Sysc, A

---

### Post by stenvoon on 2009-06-30
For easy install of latest versions of Firefox try Ubuntuzilla [[http://ubuntuzilla.wiki.sourceforge.net/]](http://ubuntuzilla.wiki.sourceforge.net/])

I just tested it with Ubuntu 9.04 and it successfully upgraded my Firefox 3 to 3.5.

Ubuntuzilla will also install a daily check for new versions (if you ask it to -- the option to do this is part of the Ubuntuzilla installer).

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by EarthMind on 2009-07-01
Here's the latest Firefox:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by SunnyRabbiera on 2009-07-01
But really its not mission critical to use 3.5 right now, its not a security update or anything.

---

### Post by lovinglinux on 2009-07-01
> **SunnyRabbiera said:**
> But really its not mission critical to use 3.5 right now, its not a security update or anything.

Yeah, but Firefox 3.5 is running with 200% better performance than Firefox 3.0.11 .See my benchmark points:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119664&stc=1&d=1246476466[/IMG]

Firefox 3.5 (optimized) performance doubles on both tests comparisons, with and without extensions loaded.

> **[color=#CC0000]Note:[/color]** Firefox 3.5 optimized is the official final version from Mozilla, compiled from source with optimization flags. More info [here](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Fallible on 2009-08-07
Hi, I'm an abject beginner but trying to get a bit of familiarity with Jaunty. Downloaded Firefox 3.5 in Synaptic package manager and it seemed to install okay, but Firefox 3.0.13 still loads and is oblivious to the upgrade. Am I missing some really basic step, or am I just rushing the process? Thanks!

---

### Post by lovinglinux on 2009-08-07
> **Fallible said:**
> Hi, I'm an abject beginner but trying to get a bit of familiarity with Jaunty. Downloaded Firefox 3.5 in Synaptic package manager and it seemed to install okay, but Firefox 3.0.13 still loads and is oblivious to the upgrade. Am I missing some really basic step, or am I just rushing the process? Thanks!

You need to start Firefox 3.5 from "Applications >>> Internet >>> Shiretoko Web Browser". It is installed side-by-side with FF 3.0 and won't replace it until next version of Ubuntu.

Shiretoko is the codename of Firefox 3.5. They are the same thing.

---

### Post by Fallible on 2009-08-08
Thanks, wasn't looking for that one!

---

### Post by JoeNZ on 2009-08-09
Ubuntuzilla is the way to go. It does Firefox, Thunderbird etc. All the latest versions.

---

### Post by grashdur on 2009-12-13
FYI: If you add Firefox 3.5 using Synaptic Pkg Mgr, you'll have *two* Firefox programs: You'll have this "Shiretoko" version of Firefox 3.5 (for which you can create a custom quicklauncher on your toolbar by using "add to panel" -- the file to specify is /usr/lib/firefox-3.5.5/firefox-3.5); and you'll have the basic, standard version of Firefox that Ubuntu Jaunty Jack is designed to operate with, and which it will always call up by default. 

There are probably ways to integrate the new version into Ubuntu--I tried switching the program in Preferences > Preferred Applications, but it didn't work.

I also tried removing the original Firefox 3.0, but then Ubuntu acted like there was no Firefox browser available.

---

### Post by retro_killa on 2010-01-22
> **stenvoon said:**
> For easy install of latest versions of Firefox try Ubuntuzilla [[http://ubuntuzilla.wiki.sourceforge.net/]](http://ubuntuzilla.wiki.sourceforge.net/])

I just tested it with Ubuntu 9.04 and it successfully upgraded my Firefox 3 to 3.5.

Ubuntuzilla will also install a daily check for new versions (if you ask it to -- the option to do this is part of the Ubuntuzilla installer).


I did this @ Firefox is running so much faster & better then before thx ;)

---

