---
title: "No more updates for 8.04?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by ecmatter on 2009-05-26
After nearly a year of multiple daily updates to 8.04,  I haven't had an available update in a couple of weeks.  I just ran the update Manager from the terminal, and it says that I'm up to date.  Have they stopped updating 8.04?  Have the updates slowed to a crawl?  Or has something gone wrong with my computer?

TYIA

---

### Post by SunnyRabbiera on 2009-05-26
> **ecmatter said:**
> After nearly a year of multiple daily updates to 8.04,  I haven't had an available update in a couple of weeks.  I just ran the update Manager from the terminal, and it says that I'm up to date.  Have they stopped updating 8.04?  Have the updates slowed to a crawl?  Or has something gone wrong with my computer?

TYIA

Hardy gets mainly security updates, so it doesnt always get the latest software unless its a backport or something.
Hardy is still supported in terms of security patches.
If you got updates recently then it will be a while before more patches will come, as patches are only made to hardy when they become necessary.

---

### Post by ecmatter on 2009-05-26
Here's the output from the terminal:

```
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Reading package lists... Done

abc@abc-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by sailthesea on 2009-05-26
They may have finally fixed it! ;)

---

### Post by ecmatter on 2009-05-26
> **SunnyRabbiera said:**
> Hardy gets mainly security updates, so it doesnt always get the latest software unless its a backport or something.
Hardy is still supported in terms of security patches.
If you got updates recently then it will be a while before more patches will come, as patches are only made to hardy when they become necessary.

That's what I'd expect, but it's like the updates disappeared overnight.  Just a few weeks ago, I'd get an update every day or every other day.  Now, nothing.

Thanks for the response.

---

### Post by SunnyRabbiera on 2009-05-26
Sounds right, like I said Hardy does not get all the "latest and greatest" software.
Hardy is intended to be for people who want stability, and not really need the most up to date software.
Hardy is what is called a LTS, or long term support version.
LTS versions are supposed to only include stable software, Hardy mostly comes with stable versions of most software.
This sacrifices always having the latest version of everything though, but most software updates are minor patches or reversion changes.
The software still gets maintained however with a LTS, security patches are available when it becomes needed.

> **ecmatter said:**
> That's what I'd expect, but it's like the updates disappeared overnight.  Just a few weeks ago, I'd get an update every day or every other day.  Now, nothing.

Thanks for the response.

Is this a fresh off the lot install?
If so then what you say is expected, Ubuntu typically has a lot of updates at first depending on the age of the release.
Hardy is a older release, dating to April 2008 so if you installed it then you will see loads of patches initially but after a while there wont be as many.
Thats because in the linux world if something is patched it typically stays patched.
I know it seems odd especially if you are coming from say windows XP where there is a patch needed every 8th of a second but on Ubuntu the security is very tight.

---

### Post by hjacker on 2009-05-26
> **ecmatter said:**
> After nearly a year of multiple daily updates to 8.04,  I haven't had an available update in a couple of weeks.  I just ran the update Manager from the terminal, and it says that I'm up to date.  Have they stopped updating 8.04?  Have the updates slowed to a crawl?  Or has something gone wrong with my computer?

TYIA

the closer you get to perfection - the less patches you need. Tough reality. Get used to it, you patching junkie.^_^

---

### Post by ecmatter on 2009-05-26
> **SunnyRabbiera said:**
> Sounds right, like I said Hardy does not get all the "latest and greatest" software.
Hardy is intended to be for people who want stability, and not really need the most up to date software.
Hardy is what is called a LTS, or long term support version.
LTS versions are supposed to only include stable software, Hardy mostly comes with stable versions of most software.
This sacrifices always having the latest version of everything though, but most software updates are minor patches or reversion changes.
The software still gets maintained however with a LTS, security patches are available when it becomes needed.



Is this a fresh off the lot install?
If so then what you say is expected, Ubuntu typically has a lot of updates at first depending on the age of the release.
Hardy is a older release, dating to April 2008 so if you installed it then you will see loads of patches initially but after a while there wont be as many.
Thats because in the linux world if something is patched it typically stays patched.
I know it seems odd especially if you are coming from say windows XP where there is a patch needed every 8th of a second but on Ubuntu the security is very tight.

Installed nearly a year ago.  And up until a couple of weeks ago, I'd get one or two updates a day.  I had noticed that the updates had leveled off a bit (as expected), but since installing, this is the first I've ever went more than a couple of days without at least one update.

---

### Post by ecmatter on 2009-05-26
> **hjacker said:**
> the closer you get to perfection - the less patches you need. Tough reality. Get used to it, you patching junkie.^_^

I hope that's it.  It just seems strange that they'd stop all at once.

---

### Post by SunnyRabbiera on 2009-05-26
Yeh the older it is the less the updates, like I said only software that needs patching will be patched.
I would not worry about security issues if that is your concern here, patches will come when they become needed.
Like I said I understand the worry, a windows user is used to seeing a patch every 9 seconds due to how bad the security is on windows.
But on Ubuntu security issues are no where near as common.

---

### Post by ecmatter on 2009-05-26
Thanks, everyone.

---

### Post by hjacker on 2009-06-01
The one and the only threat to windows security is windows itself. Stay away from this evil ****.

---

