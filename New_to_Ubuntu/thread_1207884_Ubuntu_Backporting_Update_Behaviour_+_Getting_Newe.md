---
title: "Ubuntu Backporting Update Behaviour + Getting Newest versions of programs"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-08
[Part 1: Ubuntu Backporting Update Behaviour]

Hi,

I have already read the relevant help files [[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) and [https://help.ubuntu.com/community/UbuntuBackportson]](https://help.ubuntu.com/community/UbuntuBackportson]) and also the desktop help file. However, I am still confused about it a bit so I have a few questions

1.What do backports do exactly?  Are they for newer versions of programs (the version of which would be the base default on the latest Ubuntu release) on older than current Ubuntu OS releases 

OR 

Are backports also for newer feature versions on current releases? I mean Ubuntu only provides bugfix and security patches right? 

2.How does Ubuntu decide what is a major version release and what is a minor bugfix and security release? For example Ubuntu updated FFv3.0 all the way to 3.0.11 as incremental updates but did not update Pidgin (a default program) which went from 2.5.5 to 2.5.8 now without too many new features, mostly just fixes and fine tuning. Why the difference? Similarly VLC (a non default program) does not get auto updated despite installing from repos.
I would have thought I have the behaviour nailed if it wasn't for this apparent inconsistency.

---

### Post by Andy06 on 2009-07-08
[Part 2: Getting newest versions of programs]

On installing new version of some programs directly from packages, I realised the massive difference in versions and features that the Ubuntu update system sometimes causes (such as with Cairo dock which is unrecognisably good in its newest form as compared to the repos version). For MY use case and the use cases of dozens of fellow students I helped with Ubuntu, this is a total deal breaker. We absolutely need the latest stable feature versions of the commonly used programs. This is easy in windows as we only have to manually check for updates which is not a problem. I am trying to now implement something similar in Ubuntu and would appreciate some help.:D

So the next few questions have to do with getting the latest versions of programs.

I need especially the latest stable feature version of:

Firefox
Pidgin
Empathy
Opera
Chrome
Compiz
Cairo dock
AWN dock
Screenlets
Deluge
Sunbird
Songbird
VLC
Ubuntu Tweak

I understand that I will have to set up custom third party repos for all of these. Could you please provide me the correct ones? I googled and searched the forums but I find a lot of non-official PPAs and inactive repositories. These won't do since I am going to be enabling this on dozens of computers that are not my own. Official PPAs (is there such a thing?) are fine. Also I could not figure out how to get keys for all of the repos I did find. At least the big name software apps would all have keys for their repos right?

Finally, I would greatly appreciate it if the instructions were geared towards using the GUI [what to add in system>admin>software sources>third party software rather than asking me to sudo apt get or add deb xxxyyyzzz in sources.list], the reason for this is I am going to instruct a lot of people in turn on how to do it once and having them use the GUI helps them internalise the process and put it into graphical memory, they don't need help from then on and learn how to do it. With the CLI/Terminal, they put in the (admittedly easy) commands but never remember/internalise/understand what is going on and will then keep coming back for those "easy commands" again and again the next time they need to tweak or add something. :D

Thank you very much.

P.S Would I be better off looking elsewhere apart from Ubuntu? The only other distro with enough polish that I would feel comofrtable trying would be Mint but that is again based on Ubuntu. Thing is I liked everything else about Ubuntu and don't mind putting in work to make this work and then tweak out the hiccups, its just the system of using 6 month old feature versions of programs that I cannot handle. :)

---

### Post by philinux on 2009-07-08
This is the best explanation I've read.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Andy06 on 2009-07-08
Already read that :D
I posted it in the first post.

The problem is not so much the vague differences in the help file content themselves but in understanding the update behaviour based on actual observations. See Firefox, Pidgin and VLC updates as a case in point (The first 2 being default apps and the last not, yet only 1 is regularly updated and kept in sync with the actual available version).

Once I have solved that, I need to enable a method to bypass Ubuntu's update mechanism and update all manually and promptly as soon as a new major stable version is released.

Thanks :D

---

### Post by Mornedhel on 2009-07-08
You won't get more recent versions than what's available on the PPAs (and no, there are no unofficial PPAs, all PPAs are official), except possibly if the upstream developers maintain their own repository for your distribution, or if a kind soul does. You still need to wait for someone to actually package the thing. Not everyone codes with Ubuntu in mind. Your only two options for cutting-edge packages are 1. package the thing yourself 2. hope that a package maintainer somewhere is as interested as you in getting the cutting-edge version in the repositories.

Backports are for all supported versions except the one being actively worked on (right now, Karmic Koala). Basically, people request backports from $their_ubuntu_release+1 to $their_ubuntu_release, and someone takes the time to package it for $their_ubuntu_release, or doesn't. Backport updates generally bring new functionality. Security updates, bugfix updates and updates that restore broken functionality come through other channels.

For your friends, the easiest way is *still* to tell them to cat yourspecialppas.list >> /etc/apt/sources.list, otherwise they'll need to click and click and click again in Synaptic.

---

### Post by Andy06 on 2009-07-08
Mornedhel,

Thanks a ton. Official PPAs are fine with me, don't need more cutting edge than that. Problem is that a lot of PPAs I've seen mentioned thrown around are maintained by some good soul and are not in fact the official ones. For example, they will have someone's name in them and he might be the maintainer or team lead but its still not official. 

Also not all third party repos are PPAs right? Like Opera's for example, thats a third party repo but not a PPA?

Can someone please give me the official repos/PPAs for the software I listed below and some way to add keys if they exist (I had far more trouble googling for keys).


> For your friends, the easiest way is *still* to tell them to cat yourspecialppas.list >> /etc/apt/sources.list, otherwise they'll need to click and click and click again in Synaptic.

Won't happen. Have tried to tell and have tried it myself too :D
Its just one of those things that Linux users will always do one way and those migrating from windows will do it another. I see merit in both approaches. Their click-click-click does not require them to re-learn anything, no adapting, no barrier-to-entry so to speak. Its easy to memorise and they will subsequently not bother me with the small issues, leaving me free to troubleshoot the big muck ups. I've had people come upto me and ask "what was that thing, sodoit getit package?" :D but once I show them the GUI way, they become self sufficient. 

I can add packages and sources through CLI/terminal (though I usually don't) but I have no idea how to add keys through there. (Is that what wget is for? wget, dpkg, apt-get....noooo). I started with Hardy and never added a key thus far, would you believe that? I'm such a noob :D

Anyway, do let me know if I can find official repos/PPA/keys of that software anywhere. 

Thanks a lot

---

### Post by Mornedhel on 2009-07-08
> **Andy06 said:**
> Thanks a ton. Official PPAs are fine with me, don't need more cutting edge than that. Problem is that a lot of PPAs I've seen mentioned thrown around are maintained by some good soul and are not in fact the official ones. For example, they will have someone's name in them and he might be the maintainer or team lead but its still not official. 

Also not all third party repos are PPAs right? Like Opera's for example, thats a third party repo but not a PPA?

PPAs are exactly like third party repositories, except they're hosted on Launchpad. You could divide PPAs between "official" PPAs, for instance the Pidgin official PPA : [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa) and "unofficial" PPAs, maintained by good souls as you say, but still hosted on Launchpad. Only applications included in Ubuntu have "official" PPAs.

> **Andy06 said:**
> Can someone please give me the official repos/PPAs for the software I listed below and some way to add keys if they exist (I had far more trouble googling for keys).

You could go to the Launchpad home page and search for "ppa <application>", here : [https://launchpad.net/](https://launchpad.net/) . Once you've found the PPA page, there should be a mention of the key's fingerprint. Write the last eight (after the slash) characters. Then do

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <fingerprint>
```

Or, if you need to do it with a GUI, follow the link to the actual key contents, copy and paste everything starting with -----BEGIN PGP PUBLIC KEY BLOCK----- in a file called something.gpg, start Synaptic and import the key from the file, which you can delete afterwards. I like the command-line version better, but this way has the advantage that you can gather all the keys you need and give them to your friends (whose trust in the packages will have to be at most how much they trust *you*, but that's another lesson in cryptography).

> **Andy06 said:**
> Won't happen. Have tried to tell and have tried it myself too :D
Its just one of those things that Linux users will always do one way and those migrating from windows will do it another. I see merit in both approaches. Their click-click-click does not require them to re-learn anything, no adapting, no barrier-to-entry so to speak. Its easy to memorise and they will subsequently not bother me with the small issues, leaving me free to troubleshoot the big muck ups. I've had people come upto me and ask "what was that thing, sodoit getit package?" :D but once I show them the GUI way, they become self sufficient.

True.

Darn end-users :)

> **Andy06 said:**
> I can add packages and sources through CLI/terminal (though I usually don't) but I have no idea how to add keys through there. (Is that what wget is for? wget, dpkg, apt-get....noooo). I started with Hardy and never added a key thus far, would you believe that? I'm such a noob :D

wget simply retrieves a file from the Internet. You probably have come across those one-liners that have wget download a key, write it somewhere.gpg, and then apt-key adds it to the keyring.

The entire point of having keys to sign packages is that you can check the fingerprints yourself, not that you just download any file and hope it wasn't from someone else impersonating the maintainers. So far I don't know of any such case, though.

---

### Post by Andy06 on 2009-07-08
Is there a list somewhere of a lot of official PPAs and other third party non-PPA repos (like the Opera one)?

Everyone who is reading :),
If there is please post it here, else check back after about 12 hours if you too are interested, I will try my best to compile a comprehensive one here.

Thanks a ton.

---

### Post by fabounet on 2009-07-09
I thought the same when trying some games, they are all outdated in the repository, always have to search and add third party repos :-/
anyway, for Cairo-Dock : [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

### Post by Andy06 on 2009-07-12
Ok here is what I have,

Pls note that where ever PPAs are involved, I have linked to the PPA homepage rather than the PPA itself so that you can get the key and watch for changes as well. 


Firefox:

This one can be approached in a million ways (almost)
See lovinglinux's thread for possible options (including PPAs):
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
Usually any modifications here are not necessary since Firefox is the one app that the repos keep in step with the official developers updates.


Pidgin:
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
and
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)


Empathy:
Could not find, this is for telepathy on which it is based:
[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)


Opera:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [release] partner
(you can enable this by simply ticking the relevant entry present by default in the "third party" tab in Software sources")
or
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) [RELEASE] non-free

gpg --keyserver subkeys.pgp.net --recv-key 6A423791
gpg --fingerprint 6A423791
gpg --armor --export  6A423791| apt-key add -


Chrome:
To be updated
upon release
Currently only available for Chromium[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)


Compiz:
No official ones found, please post if you know
Unofficial:
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) [Release] main
What is this? Official?
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)


Cairo Dock:
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock
wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O- | sudo apt-key add -


Awn Dock:
[https://launchpad.net/~awn-core/+archive/ppa](https://launchpad.net/~awn-core/+archive/ppa)
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)


Screenlets:
Project abandoned :(
There is a Universal appelets fork but seems to be going nowhere.


Gnome Do:
[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)


Deluge:
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)


Sunbird:
Could not find, probably does not exist, no one cares :)


Songbird:
[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa) (Unstable)
Please post an official one if you know.


Swiftfox:
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free


Ubuntu Tweak
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
Sounds unofficial, but he is the developer.


VLC:
No official, found this
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)
Who is he? Official? Developer?
This PPA is listed on official site


THE BEST LINKS IN THIS THREAD (until now):
[https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas) [Launchpad's own PPA search]
[http://ppa-search.appspot.com/](http://ppa-search.appspot.com/) [searches for PPAs]


Others that I din't initially mention but people might find useful:
Medibuntu
Wine
Openoffice
Google Chrome
Banshee
all @ [http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html](http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html)



So basically these are still needed:

Official (Mozilla?) Firefox one
Chrome (upon release)
Compiz
Screenlets
Sunbird
Songbird
VLC

And where ever possible, please post official repos to replace PPAs (such as the ones that exist for Opera, Cairo dock and Swiftfox.


Also you can visit these threads:
[http://ubuntuforums.org/showthread.php?t=1157181](http://ubuntuforums.org/showthread.php?t=1157181) [people sharing their sources.list]

[http://ubuntuforums.org/showthread.php?t=1133304](http://ubuntuforums.org/showthread.php?t=1133304) [discussion of PPAs people enable]

---

### Post by Andy06 on 2009-07-12
Ok now I have some questions:

1.Firefox: What is the difference between
[https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
and
[https://edge.launchpad.net/~mozillateam/+archive/ppa](https://edge.launchpad.net/~mozillateam/+archive/ppa)

One is official Mozilla and other is "official" Ubuntu team for Mozilla?


2.Pidgin: There's some difference in the repos of
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
and
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Why is there a difference, or is it just slightly different syntax?

3.The PPA for telepathy has packages for both empathy and telepathy, is telepathy like the backend or protocol for empathy? Will empathy properly update using the telepathy PPA? Is there a separate Empathy PPA anywhere?

4.Opera can be updated manually by going to Help>Check for updates. So are PPAs necessary then? Isn't this a much better method to check manually. I have Opera 10 beta installed.
There is an official repo and also a PPA, which is better? 

5.Does it matter if I install an app from a .deb file using Gdebi and THEN afterwards add a repository? Will it still update?
What about manual installs using scripts? These do not register with synaptic so will they update? I'm guessing not.

6.Awn core and Awn testing PPAs above are for stable and experimental right?

Thanks a lot

---

### Post by Mornedhel on 2009-07-12
> **Andy06 said:**
> Ok now I have some questions:

1.Firefox: What is the difference between
[https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
and
[https://edge.launchpad.net/~mozillateam/+archive/ppa](https://edge.launchpad.net/~mozillateam/+archive/ppa)

One is official Mozilla and other is "official" Ubuntu team for Mozilla?

ubuntu-mozilla-daily looks like the PPA end-users would add. The other one looks more like the Ubuntu/Mozilla development PPA, that is, their own repository for their own purposes.


> **Andy06 said:**
> 3.The PPA for telepathy has packages for both empathy and telepathy, is telepathy like the backend or protocol for empathy? Will empathy properly update using the telepathy PPA? Is there a separate Empathy PPA anywhere?

Yes, libtelepathy is the Empathy backend. If there are packages for Empathy in the Telepathy PPA, I would assume they are bleeding-edge as well. They will be updated normally.

> **Andy06 said:**
> 4.Opera can be updated manually by going to Help>Check for updates. So are PPAs necessary then? Isn't this a much better method to check manually. I have Opera 10 beta installed.
There is an official repo and also a PPA, which is better?

Updating Opera through the software itself should not be possible, unless you start it with administration rights. It's better to always use packages when you can and maintain the healthiest repository possible.

> **Andy06 said:**
> What about manual installs using scripts? These do not register with synaptic so will they update? I'm guessing not.

They won't update. They aren't tracked by your package manager.

---

### Post by Andy06 on 2009-07-12
Thanks a ton Mornedhel,

Just few more questions:

With pidgin, lanchpad says this is the repo:
[http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main 

But the pidgin official site [[http://www.pidgin.im/download/ubuntu/]](http://www.pidgin.im/download/ubuntu/]) says:
echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

which looks like a real messy format that I have never seen before. Why is it different? It seems to be pointing at the same source. Oh and it actually works, even without substituting the release name.


Also,

Opera allows you to "Check for updates" without running in admin mode. I don't know how, but it does. So do all apps "installed" by merely unzipping tar.gz packages.

---

### Post by Mornedhel on 2009-07-12
> **Andy06 said:**
> Thanks a ton Mornedhel,

Just few more questions:

With pidgin, lanchpad says this is the repo:
[http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main 

But the pidgin official site [[http://www.pidgin.im/download/ubuntu/]](http://www.pidgin.im/download/ubuntu/]) says:
echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Yes, it's a smart (?) way of writing a line with your current Ubuntu release codename into a file. The backticks (`this`) are shorthand for "execute the contents and append its stdout to the string" ; tee is a basic command that outputs its stdin to both stdout (so you can read the result) and to a file, here /etc/apt/sources.list.d/pidgin-ppa.list. The end result is identical, provided you run Karmic.

Also,

> **Andy06 said:**
> Opera allows you to "Check for updates" without running in admin mode. I don't know how, but it does. So do all apps "installed" by merely unzipping tar.gz packages.

Applications which are run from a directory you own will have no problem writing to it and you will not need to be root to update them.

---

### Post by Andy06 on 2009-07-12
With pidgin, I was actually on Jaunty, it still worked (it was not my computer actually, but it was jaunty, I installed it myself).

The tarballed apps (including Opera) work with manual updates but so does the .deb installed opera! That's integrated with synaptic right? How does it manage to upgrade?

I tried tracing the path in Synaptic and it is installed to usr/share which is a root directory and all other apps in there cannot manually update but Opera can. Do you have Opera on your system? Can it manually update?

Thanks a lot.

---

### Post by Mornedhel on 2009-07-15
Never installed Opera, don't know how it can update without administration access, a bit suspicious that it can at all if it is installed system-wide. Nevertheless.

I thought you in particular might be interested in this : [http://ubuntuforums.org/showthread.php?t=1213538](http://ubuntuforums.org/showthread.php?t=1213538)

---

### Post by 3rdalbum on 2009-07-15
If you need the latest software all the time (do you *need* it, or do you just *want* it?) then Ubuntu is not the distribution for you. As the Ubuntu base is designed for a commercial environment, it doesn't get updates mid-life that will add or remove features - that would be difficult for a system administrator or help-desk to support as they'd get calls like "Hey, this function I used to use has disappeared, where did it go?".

You should look for a "rolling release" distribution. If you don't want to fall too far from the Ubuntu tree, then you could try Debian Unstable, which still might be a little slow for your needs and wants, but then it might be just the ticket.

---

### Post by Andy06 on 2009-07-15
I'm sort of coming to that realisation myself. I both need and want the latest programs. Frankly, the lines are a bit blurred. Who "needs" anything, I'm sure we could all get by with something as old as XP just fine :D

You are right in that I have a needs/wants mismatch here. To ME, Ubuntu's way of updating and releases makes no sense. They give you the latest versions of X.org, GNOME etc but give you old apps. To me, and indeed the dozens of people I have converted, as end users, they want the latest APPS but don't care about the back end infrastructure (like X).

In fact, I would really appreciate if you could tell me the reasoning behind such a strategy? To me it seems like an enormous strain on Canonical's/Ubuntu's resources to quality test with new back end stuff every six months. Indeed its the back end that cause most of Ubuntu's problems (like the serious regression that the new X caused in 9.04). I can't quite imagine newer versions of programs conflicting and bringing systems down.

This is not a criticism, I'm just asking. Besides I'll keep looking around to make it work for my needs. Basically, I am perfectly ok with manually updating programs like In Windows, that is a pretty good system for staying up to date. 

I tried some other distros, but for my needs and the end users I am dealing with regularly, I don't see how anything apart from Ubuntu or Linux Mint (which is also based on Ubuntu)can be made to work. As it is, we've had lots of problems, I dare not step outside of Ubuntu/Mint. Tried Arch, Gentoo (shouldn't have tried those, they are OBVIOUSLY not aimed at casual end users looking for a system that just *works*) and then Fedora, which felt like a completely unpolished and half done Ubuntu. Tried some others, but did not find anything. Any suggestions? (will give Debian Unstable a shot). I only need a different updating mechanism, something like Windows would be great or any system that makes it easy to stay up to date.

Thanks a lot.

---

### Post by Andy06 on 2009-07-25
Stumbled upon this while looking at some tech blogs.
Looks very useful, not sure if it is up to date though.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Andy06 on 2009-07-29
> You should look for a "rolling release" distribution. If you don't want to fall too far from the Ubuntu tree, then you could try Debian Unstable, which still might be a little slow for your needs and wants, but then it might be just the ticket.

I looked at Debian Unstable, but haven't used it properly for a while though. Why do you think it might be a little slow?

I am basically looking for Ubuntu like, Ubuntuesque type of polish and completeness (at least, better is awesome) with just the important application updated to the latest stable versions. I don't need experimental, beta or alpha software, just the latest stable feature versions.

The windows updating paradigm is not a problem for me, I like it and if there is a distro that does provide that, that's fine too.

Thinking of taking a look at Sidux as well. What do you recommend?

---

