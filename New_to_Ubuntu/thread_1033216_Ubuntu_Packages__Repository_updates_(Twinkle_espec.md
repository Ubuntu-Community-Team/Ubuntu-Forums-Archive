---
title: "Ubuntu Packages / Repository updates (Twinkle especially)"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Mr. Moustache on 2009-01-07
This is my first post here as I'm new to Ubuntu,
so Hi to everybody! :)

I would like to install Twinkle from the Ubuntu repository but it shows an old version. I could install the newest version manually, but that's not the way it's meant to be (as it already is in Ubuntus repository).

So this is more of a general question:
What can I do if the needed Ubuntu-Package has not been updated, even if the new version of a program has been released quite a while ago?

One more package I had the same 'problem' with was Thunderbird. The 2.0.0.19 was out for days, but Ubuntu still had the 2.0.0.18 in it's repository.

In my opinion it is essential that especially security updates to programs are put into Ubuntus repository as quick as possible.

What has to be done to get software-updates into Ubuntus package-system immediately after a new version of the software has been released? Do I have to be a packet-maintainer to get updates into the repository as quick as I would like to have them?

By the way: this is a problem I heard from a lot of friends using other Linux-distributions, too. You count on the software-repository of your Linux-system, but it's often just "out of date" for just too long. :(

---

### Post by hyper_ch on 2009-01-07
(1) Versions in an Ubuntu release normally won't get updated to the laste bleeding edge release

(2) some people do take time and "backport" such things. Enable the backport updates and and will get updates packages - however it might well be that they break your system

(3) there are also inofficial repositories that have more up-to-date packages. You could find one for that package you look for. In my sig I have "compiled" a little list of some of them.

---

### Post by wizard10000 on 2009-01-07
I've been an IT professional for a whole lotta years - there are a couple of things you've gotta understand here.

First, Linux developers maintain *thousands* of packages.

Second, back in August the Twinkle folks did three releases in less than a week and none of them were security updates.

Did you read Thunderbird's release notes?  What function does the new release provide that you absolutely have to have today?  BTW - I got 2.0.0.19 this morning from Intrepid repos - considering the Mozilla folks only released it nine days ago that ain't too bad.

Professionals don't upgrade software packages just because the new release has a higher number than the old release did - they upgrade software because there's a reason to do so - either security fixes, bugfixes or other reasons - not just because the new version has a higher number than the old one.

---

### Post by Mr. Moustache on 2009-01-07
> **wizard10000 said:**
> Professionals don't upgrade software packages just because the new release has a higher number than the old release did - they upgrade software because there's a reason to do so - either security fixes, bugfixes or other reasons - not just because the new version has a higher number than the old one.
Of course I don't update software just because the version number increased and of course I update software, because I need (want) the features of that new version.

That the developers have to maintain *thousands* of packages might be the problem, but it should not be an excuse for not updating packages "fast" (however one defines that). The problem then is, that there are far to few package maintainers to update packages "in time".

In my opinion you should always have the chance to install, say, the last three versions of a software right from the repository, including the newest version. So installing what hyper_ch calls "bleeding edge" versions (even if the developer of the program declared them as "stable") should always be an option. It should be the users free decision to use the newest version, as he would always have the chance to downgrade to an older version from the repository. In other words: a user should not be dependent on decisions of package-maintainers who say "yeah, that update seems to be important" or "well, that update can wait"!

So, an excuse for not having the newest version of a program in the repository could be that too few maintainers just don't have enought time to maintain too many packages. I have no problem with that. (I would even consider maintaining some package myself to help!) But an excuse should not be "the maintainers decide for you, which updates are important and which not".

---

### Post by hyper_ch on 2009-01-07
> **Mr. Moustache said:**
> but it should not be an excuse for not updating packages "fast" (however one defines that).

It is not. Ubuntu is not a rolling release distro and Ubuntu releases two new versions each year. All the packages have to get compiled, put together and ensure they work together. During a release cycle of an Ubuntu release you will not get any version updates except if they are either security updates or major bug fixes. That's how it works and there's no need for an "excuse" for not updateing packages fast, as you think it would be.

---

### Post by MaximoMilkman on 2009-01-07
Very true post alothough updates may not be EXTREMELY important those little bugfixes may still really help..it does stink that the repos are not always up to date but hey.. it is a free and quite possible the best OS of all when you really get the hang of linux it seems like linux is a blast theres so many programs out there for it.. and a great community!!

---

### Post by wizard10000 on 2009-01-07
All respect but perhaps you should run something a little more bleeding edge, like Fedora  ;)

The user has the freedom to use the newest version of anything they like - all you have to do is go install it.  Maintaining multiple versions of software packages causes problems for several reasons, like

 - supporting multiple versions of the same package
 - file dependencies and up/downgrading breaking other packages.  Do you think you should have the option of installing three versions of gcc?  :D

Anyway, if you want it, install it.  I've been waiting for an upgrade to photoprint (which is broken in Intrepid) since before Intrepid was released.  I finally fixed the version that's broken but I imagine photoprint's pretty low on the list.  launchpad is your friend for finding out what's broken, what you can do to fix it and where the next release might be.

I ran bleeding edge for years - ran Fedora through FC6 and then got tired of the bleeding edge breaking stuff - moved from that to CentOS which was dead stable but the software was a little older than I liked.  I think Ubuntu provides a pretty good balance between stability and cutting-edge software - and if I want something newer I just go install it  ;)

---

### Post by Mr. Moustache on 2009-01-07
Ok, thanks for your answers.

One last question (which I believe I read something about in the Ubuntu docs before)... As Ubuntu releases two major versions each year:
Is it possible to update the whole Ubuntu distribution to a new version, for example 8.04 to 8.10 so that after the update I really have a complete Ubuntu 8.10 which I can update to the following version later? (Without losing my personal data and/or configurations?)

---

### Post by wizard10000 on 2009-01-07
> **Mr. Moustache said:**
> Is it possible to update the whole Ubuntu distribution to a new version, for example 8.04 to 8.10 so that after the update I really have a complete Ubuntu 8.10 which I can update to the following version later? (Without losing my personal data and/or configurations?)

It sure is  :)

The easiest way to do it is like this:

```
sudo apt-get update
```

and then 

```
sudo apt-get upgrade
```

then just hit Alt-F2 and run

update-manager -d

You'll see a checkbox to upgrade the entire distribution.

If you have /home on a separate partition I'd strongly recommend blowing away everything but /home and installing from scratch, though.  That'll preserve all your stuff  :)

good luck -

---

