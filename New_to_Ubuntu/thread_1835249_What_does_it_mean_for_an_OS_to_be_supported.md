---
title: "What does it mean for an OS to be supported?"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-08-29
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

I plan to install Ubuntu 11.04 on my new computer I'm getting next week. What does it mean that the OS will not longer be supported after October 2012?

After October 2012, if I want to upgrade to a newer version of Ubuntu, does that mean I will be unable to do so?

Why is Lucid Lynx being supported longer despite it being older?

---

### Post by mcduck on 2011-08-29
When the support period for Ubuntu release ends the developers will stop providing bug fixes and security updates for it, and also it's software repositories will be closed.

(Actually the repositories aren't closed, but rather moved to old-releases.ubuntu.com, but the maintenance stops and really the lack of security updates is definitely a good enough reason to not use unsupported releases.)

Lucid has longer support time since it's a LTS release. To provide users who need longer support times and less frequent need for updating, common thing for business use for example, Ubuntu every now and then releases a version with focus more on stability than on new features, called "Long Term Support". Lucid is one of those versions.

---

### Post by brawnypandora0 on 2011-08-29
> **mcduck said:**
> When the support period for Ubuntu release ends the developers will stop providing bug fixes and security updates for it, and also it's software repositories will be closed.

(Actually the repositories aren't closed, but rather moved to old-releases.ubuntu.com, but the maintenance stops and really the lack of security updates is definitely a good enough reason to not use unsupported releases.)

Lucid has longer support time since it's a LTS release. To provide users who need longer support times and less frequent need for updating, common thing for business use for example, Ubuntu every now and then releases a version with focus more on stability than on new features, called "Long Term Support". Lucid is one of those versions.

Why are security updates important? Have you ever heard of a Ubuntu user using an unsupported release getting infected?

---

### Post by mcduck on 2011-08-29
> **brawnypandora0 said:**
> Why are security updates important? Have you ever heard of a Ubuntu user using an unsupported release getting infected?

Fixing any security holes in programs is pretty much the most important aspect of Linux security.(together with strict user permissions of course). The few Linux viruses that have ever ran wild have all relied on systems running outdated software versions, and security updates are also important to protect you from all the other attack types as well.

Anyway, there really aren't many good reasons why you'd even want to use outdated and unsupported operating system. Not even if you ignore the security aspect. You'd be stuck with old versions of all your programs, bugs and problems that nobody is ever going to fix, and quite likely not being able to get new software working even if you try to manually install them as new versions often require more up-to-date versions of different libraries etc...

---

### Post by jockyburns on 2011-08-29
I'm very new to Ubuntu (having had  a HDD pack up and no OS  to install on the new one) When a newer version of Ubuntu/Linux becomes available, does installing it on the HDD, automatically delete the older version? (trust me, I know very little about computers)

---

### Post by mkornig on 2011-08-29
> **brawnypandora0 said:**
> [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases")

After October 2012, if I want to upgrade to a newer version of Ubuntu, does that mean I will be unable to do so?

No. Upgrading is always possible no matter wheter your old OS has Long Time Support (LTS) or not.

> **brawnypandora0 said:**
> [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

Why is Lucid Lynx being supported longer despite it being older?

Because someone (the technical director of Canonical? I don't actually know who) has decided from the very beginning that Lucid Lynx shall have a longer lifetime. Personally, I've tested both Lucid Lynx and an newer Ubuntu version. I found the former to be more stable and more reliable.

For beginners I would not recommend a very recent version which has been around for only a few weeks or so because these versions tend to have still a few bugs (and beginners sometimes get confused because they can't tell the difference between a bug and normal behavior combined with impropper use). Slightly older (and still supported) versions tend to be "cleaned out" and tested more thorowly, i.e. be more stable.

---

### Post by mcduck on 2011-08-29
> **jockyburns said:**
> I'm very new to Ubuntu (having had  a HDD pack up and no OS  to install on the new one) When a newer version of Ubuntu/Linux becomes available, does installing it on the HDD, automatically delete the older version? (trust me, I know very little about computers)

It depends. You can either just update the installed version, keeping all your files and programs. Or you can download the install disc for the new version and install it alongside the old version, or overwrite the old one. It's really up to you what you want to do.

---

### Post by BlacqWolf on 2011-08-29
> **jockyburns said:**
> I'm very new to Ubuntu (having had  a HDD pack up and no OS  to install on the new one) When a newer version of Ubuntu/Linux becomes available, does installing it on the HDD, automatically delete the older version? (trust me, I know very little about computers)

It depends on what you tell it to do. These are the options you will get if you boot a device with the Ubuntu installation files:

If you have Windows installed, you can use your own configuration, install alongside Windows (the area used for Windows may be shrunk, meaning that you can store less on the Windows side of the disk), or have it format the entire drive and use the entire drive for Ubuntu. If you have it install alongside Windows, you can also have it transfer your desktop background and certain documents from Windows.

If you have Ubuntu installed, you have the option to use your own configuration, or set it to format the entire drive and use a fresh install of Ubuntu, or update a previously installed edition of Ubuntu with the version contained on the installation media (eg. CD drive, USB drive)

If you have a completely empty drive, you can either use your own configuration or have it automatically format the entire drive and use it for Ubuntu.

If you already have a working Ubuntu installation, and you want to upgrade to the latest stable release, just start Ubuntu, log in, go to Update Manager, and there should be a notification saying a new edition of Ubuntu has been release, as well as an option to upgrade through Update Manager.

If you don't see this option, make sure a version of Ubuntu newer than what you run is released and try checking for updates again.

If this needs any more explaining, or if this doesn't answer your question, please let me know and I will attempt to help you further.

---

### Post by alphacrucis2 on 2011-08-29
Just one bit of clarification. If you are running an LTS version, then the update manager will not offer to do a release upgrade until the next LTS version is released. You can manually upgrade to interim releases of course but remember that you will have to sequentially upgrade one release at a time. LTS to LTS is the only normal way to upgrade that skips interim releases. Sometimes it is less trouble to just install the release that you want from scratch.

---

### Post by Wim Sturkenboom on 2011-08-29
> **brawnypandora0 said:**
> Have you ever heard of a Ubuntu user using an unsupported release getting infected?
That does not matter, does it. One day somebody will pick your machine, find out that it has a non-patched kernel with a vulnerability and e.g. happily steal your banking details or spam the world from your ip address. Want to take the risk?

---

### Post by grahammechanical on 2011-08-29
It is not quite six months since I upgraded from 10.10 to 11.04. Yet, I could not direct anyone using 10.10 step by step to alter their settings. I no longer remember these things. I do not want to remember. I am learning new stuff. For example, in 10.04 and 10.10 is Additional Drivers under System>Preferences or System>Administration? I used to know that stuff.

So, anyone using these forums to get help for a problem with an older Ubunutu might find that the advice does not fit what they are seeing on their screen.

I think that this issue will matter a lot more over the coming year. Things will still work the same in a terminal but the desktop way of working will be completely different.

Regards.

---

### Post by jockyburns on 2011-08-29
Blacqwolf, My version (11.04(Latest) is on my newly installed HDD (after the other one packed up) Nephew had promised to install Win7, (but sadly didn't turn up or answer the phone calls), so I just had to get back on the interwebthingymajig and decided to try Ubuntu. So it's now running my computer from a brand new Sata2 HDD completely empty (apart form whatever I've put on since last Friday.

---

