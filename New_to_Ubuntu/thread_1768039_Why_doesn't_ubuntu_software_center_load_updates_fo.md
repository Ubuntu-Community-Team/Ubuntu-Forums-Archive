---
title: "Why doesn't ubuntu software center load updates for programs"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by tumbes2000 on 2011-05-26
I noticed that ubuntu software center does not support updating of programs, like banshee, to new versions (eg, 2.0 to 2.1).  I read that Ubuntu has never done this and that the only way to have the updates is to add them as a PPA (which I have done for some some stuff).  It is annoying for people like me that want the latest and greatest from a program rather quickly.

Anyway, just curious to see why ubuntu software center does not also provide updates for installed programs.  

Thanks,

---

### Post by throese on 2011-05-26
Um, it does, not the software center, but if you want to update the repositories, then do the following in the terminal:

sudo apt-get update

then to apply them do:

sudo apt-get upgrade

OR in Update Manager just click "Check" and then "Install"

---

### Post by ivanovnegro on 2011-05-26
It does only with security updates and with specific Ubuntu things/software but normally not with other normal programs, thats the policy.
So the OP is right, you have to add PPAs or to compile yourself to have the newest stuff if you want like Banshee, Rhythmbox, VLC etc.

---

### Post by snowpine on 2011-05-26
Same reason your mechanic doesn't "upgrade" your steering wheel or your headlights when you go in for an oil change: if it ain't broke don't fix it. If you want the latest features, then you do a full upgrade to the 2011 model.

Ubuntu is not a "rolling release" distro and the update manager provides the minimal updates necessary to keep your system reliable and stable. If you want to "hot rod" your system with more substantial upgrades then you are free to do so using a variety of methods. This is the true meaning of "open source"--you are free to administer your own system as you see best. :)

---

### Post by mcduck on 2011-05-26
The main reason is stability. During development all package versions can be tested to work together without any problems. After release it's not possible to fullyy test how each update would affect other packages, while at the same time users expect a reliable system that doesn't break when you install updates.

If you prefer latest-and-greatest package versions over stability, you can either use third-party repositories or try some Linux distribution with rolling releases.

This page has a pretty good explanation about Ubuntu's  update policy: [https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")

---

### Post by Joe of loath on 2011-05-26
If you always want the latest packages, maybe try Arch Linux? It's pretty tricky to install and configure, but damn quick, and pretty stable.

---

### Post by tumbes2000 on 2011-05-26
Thanks for the input.  I suppose what I am missing is that Ubuntu developers take responsibility for ALL programs included in the distro even ones they did not directly create - libreoffice, banshee, etc.  

I just figured those were included so someone could just run the live cd and see that ubuntu can meet all of their needs (such as myself), but not necessarily mean that to be the final versions for a six month period of the prepackaged programs.

I can certainly understand the need for stability and no desire to constantly update essential programs every month, but I do not see how the devs at  libreoffice release a new stable version of libreoffice would affect system stability (would upgrading from office 2003 to 2007 affect windows 7 or Xp stability?).    If the new version of libreoffice was pushed to users and was unstable for some reason does the ubuntu community blame ubuntu thus the reason for no new releases?  

Not trying to be critical here, just wanting to understand the reasoning.  I have not used linux desktop since 2000 and since then it has been nothing be windows, OS X and android.  I use android quite a bit and its nothing but updates for programs.  Obviously the body of the OS is not updated as frequently, but devs are always pushing out updates, either bug fixes or enhancements to their programs (sometimes too much).

---

### Post by snowpine on 2011-05-26
> **tumbes2000 said:**
> I can certainly understand the need for stability and no desire to constantly update essential programs every month, but I do not see how the devs at  libreoffice release a new stable version of libreoffice would affect system stability (would upgrading from office 2003 to 2007 affect windows 7 or Xp stability?).    If the new version of libreoffice was pushed to users and was unstable for some reason does the ubuntu community blame ubuntu thus the reason for no new releases?  

You may use any version of Libreoffice you like, Ubuntu devs are not impinging your choice in any way.

MS Office is actually a good example. If you buy and install Office 2003, it does not automatically upgrade to 2007. Users can choose the right version based on their needs.

---

### Post by Joe of loath on 2011-05-26
I think it's more repo maintenance than anything else, would you want to be updating 30,000 packages, and building + repackaging them every time there was a new release upstream? :p

---

### Post by audiomick on 2011-05-26
Apart from this very valid point

> **Joe of loath said:**
> I think it's more repo maintenance than  anything else, would you want to be updating 30,000 packages, and  building + repackaging them every time there was a new release upstream?  :p

to this:

> **tumbes2000 said:**
> 
.... but I do not see how the devs at  libreoffice release a new stable version of libreoffice would affect system stability....

for example, I used to have my Symbian 60 phone synchronising with Evolution. The stuff to do that was mostly in the Repos, but not all. At any rate, at some point there was an update of something, not any of the packages to do with the synching, or Evolution either, I think, and it just stopped working. There are quite extensive thread here that deal with the problem, but no-one seems to have been able to really solve it.

The point? There is a chance that updating a package might take out something apparently completely unrelated. Therefore, nothing is changed or added without it having been well tested. This is annoying. I have had to wait for various things myself, but as has been pointed out, the way is open to add it yourself if you want to.

> 
If the new version of libreoffice was pushed to users and was unstable for some reason does the ubuntu community blame ubuntu thus the reason for no new releases?  


I believe that a rather large number would, people being as they are. For the ones who say "It's not Ubuntu's fault, they didn't make it" there would be at least as many, I reckon about 10 times as many, who would say "why did those idiots include it without checking it".

---

### Post by beew on 2011-05-26
> **throese said:**
> Um, it does, not the software center, but if you want to update the repositories, then do the following in the terminal:

sudo apt-get update

then to apply them do:

sudo apt-get upgrade

OR in Update Manager just click "Check" and then "Install"

No it doesn't. It updates from the same repos whether you use the command line or the software center. If you want feature updates there are 3 ways:

Add ppa to your sources list (recommend)
download and install from a .deb file
Install from source

---

### Post by beew on 2011-05-26
> **snowpine said:**
> Same reason your mechanic doesn't "upgrade" your steering wheel or your headlights when you go in for an oil change: if it ain't broke don't fix it. If you want the latest features, then you do a full upgrade to the 2011 model.


Except in this case it doesn't fix it even if it is broken, unless it is something security related.

---

### Post by spillage2 on 2011-05-26
All valid points..I must say when using something like firefox you should not need to have to include the ppa as this could be a security risk and should be done automatically. Of course something that would not cause a risk should be left to the user.

I love ubuntu and can understand that the makers want us the users to have as much control as possible..but not all users may realise that they are running an old version of say ff and/or may not understand how to go about upgrading and think if it aint broke dont fix it..

Wouldnt be a bad idea if common software such as ff could be updated more without any user input..just to help those who have recently come from a windows environment..

---

### Post by beew on 2011-05-26
> **snowpine said:**
> 
MS Office is actually a good example. If you buy and install Office 2003, it does not automatically upgrade to 2007. Users can choose the right version based on their needs.

MSO is a paid product of course it doesn't automatically update. But since it is a paid product chances are it has done quite a bit of in house testing and is sufficiently polished and feature complete when it is released, so you don't have to and are not expected to update often (who would pay a couple of hundred bucks every few months?) So commercial softwares are relatively static in that way.

But open source has different developmental strategy and has different release cycles. Typically open source programs follow the "release early, release often" strategy because they rely on users for testing and feedback for features, new features and important bug fixes are constantly coming in through updates so it doesn't make sense to compare that with the relative stability of commercial softwares. For opensource  18 months is a very long time, not to mention 3 years for LTS.

---

### Post by tumbes2000 on 2011-05-26
One thing that I really like about Ubuntu is the Software Center.  It has many of the features that make android market successful 1) searchable, 2) user ratings and feedback 3) access to dev website 4) install and uninstall from Software Center.  Its a great feature.  However, it needs to go the extra step of allowing devs to push updates to users through the software center (you can check if you want auto update or not).  Now I do not know what that entails for updates can be verified (no malicious software, etc) and it sounds like it would be too much work from the previous posts.  Maybe just on the more important programs like Firefox or libreoffice updates could be reviewed and then updated by ubuntu devs and the rest work as it is now?  Would make it very appealing to new users.

---

### Post by snowpine on 2011-05-26
> **spillage2 said:**
> All valid points..I must say when using something like firefox you should not need to have to include the ppa as this could be a security risk and should be done automatically. Of course something that would not cause a risk should be left to the user.

I love ubuntu and can understand that the makers want us the users to have as much control as possible..but not all users may realise that they are running an old version of say ff and/or may not understand how to go about upgrading and think if it aint broke dont fix it..

Wouldnt be a bad idea if common software such as ff could be updated more without any user input..just to help those who have recently come from a windows environment..

Firefox is actually one of the few exceptions to the rule, because using a supported browser is so important to security. If the version of Firefox becomes obsolete in any supported Ubuntu release, it will be updated to a supported version through the Update Manager, no PPA necessary.

LibreOffice is at the opposite end of the spectrum, it is not vital to security therefore it is an optional upgrade. As you point out, millions of people are happily using Office 2007 or even 2003 to get their work done; using a 6-month old LibreOffice is fine for most people.

Anyways, there is a type of Linux distro called "rolling release" that always gives you the latest applications rather than having time-based releases (like Ubuntu 11.04, 11.10, etc). Ubuntu simply is not designed to fall into this category of "rolling release."

---

### Post by beew on 2011-05-26
> **snowpine said:**
> Firefox is actually one of the few exceptions to the rule, because using a supported browser is so important to security. If the version of Firefox becomes obsolete in any supported Ubuntu release, it will be updated to a supported version through the Update Manager, no PPA necessary.


Has FF in Lucid and Maverick been updated to FF4 yet? I think it will be updated to FF4 only when support for FF3.X expires and god knows when that will happen. So I would still use PPA (and am using one) FF4 is a lot faster. It is not a security issue that you want a fast browser but it is nice.

As for rolling releases, I probably don't want my system stuffs to roll, now that is instability that may break everything.

---

### Post by snowpine on 2011-05-26
> **beew said:**
> Has FF in Lucid and Maverick been updated to FF4 yet? I think it will be updated to FF4 only when support for FF3.X expires and god knows when that will happen. 

[http://packages.ubuntu.com/lucid-updates/firefox](http://packages.ubuntu.com/lucid-updates/firefox)
[http://packages.ubuntu.com/maverick-updates/firefox](http://packages.ubuntu.com/maverick-updates/firefox)
[http://support.mozilla.com/questions/811563](http://support.mozilla.com/questions/811563)

---

### Post by Ghost|BTFH on 2011-05-26
Personally, I hate the Software Center and still use either cli (apt-get awesome -now) or Synaptic Package Manager, which allows me to browse dependent upon my own search parameters to find, games, security features and more.

Not to mention I can then read a brief overview on it, and simply check the box or not in order to install.

Add to that the fact I can update right there on the spot when there's optional updates available that aren't security related, and Syn is my buddy.

Cheers,
Ghost|BTFH

---

### Post by wildmanne39 on 2011-05-26
> **beew said:**
> Has FF in Lucid and Maverick been updated to FF4 yet? I think it will be updated to FF4 only when support for FF3.X expires and god knows when that will happen. So I would still use PPA (and am using one) FF4 is a lot faster. It is not a security issue that you want a fast browser but it is nice.

As for rolling releases, I probably don't want my system stuffs to roll, now that is instability that may break everything.Hi, personally I am happy the way things are if I want to upgrade a package that is not in the repos it is very easy to add it or download a .deb file, I have had updates in the past that have broke something  so I like ubuntu not updating everything it is much more stable, I think we sometimes forget how much work developers and testers do.

---

### Post by ExileAmongYou on 2011-05-26
> **tumbes2000 said:**
> One thing that I really like about Ubuntu is the Software Center.  It has many of the features that make android market successful 1) searchable, 2) user ratings and feedback 3) access to dev website 4) install and uninstall from Software Center.  Its a great feature.  However, it needs to go the extra step of allowing devs to push updates to users through the software center (you can check if you want auto update or not).  Now I do not know what that entails for updates can be verified (no malicious software, etc) and it sounds like it would be too much work from the previous posts.  Maybe just on the more important programs like Firefox or libreoffice updates could be reviewed and then updated by ubuntu devs and the rest work as it is now?  Would make it very appealing to new users.

There are a few reasons why they don't push updated versions of the programs. One is stability, because with any new version there are going to be bugs. Another is the shared system libraries- sometimes a newer version of a program will require a newer version of some of the system libraries, so if you upgrade that program, you might break some of the other programs that depend on those same libraries.

If you're really keen to keep up with the latest versions of programs, familiarize yourself with how to add PPAs. Once you've got the hang of it, it becomes very easy to upgrade to the latest version of a program.

---

### Post by snowpine on 2011-05-26
Another option is to get involved with Ubuntu development (currently 11.10 O.O.). Not only will this give you the latest & greatest software, it is also a good way to give back to the community by testing & reporting bugs and sharing your feedback! :)

---

### Post by alphacrucis2 on 2011-05-26
> **snowpine said:**
> Another option is to get involved with Ubuntu development (currently 11.10 O.O.). Not only will this give you the latest & greatest software, it is also a good way to give back to the community by testing & reporting bugs and sharing your feedback! :)

I wouldn't recommend this to newbies right now. The process of changing from gtk+ 2 to gtk+ 3 that is happening in 11.10 is a lot more painful than what occurred in previous alpha releases for a few years. There is lots of breakage.

---

### Post by tumbes2000 on 2011-05-26
Thanks guys for all of the input.  I am still quite satisfied with Ubuntu and unity s growing on me.  I definitely have a lot more to read about Ubuntu.

---

