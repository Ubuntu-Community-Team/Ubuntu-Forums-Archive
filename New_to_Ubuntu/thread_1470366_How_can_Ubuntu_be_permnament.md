---
title: "How can Ubuntu be permnament?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-05-02
Well here's the story, my mother uses Ubuntu to surf the net since she use to get Windows viruses.  So I installed Ubuntu 8.04 on her computer via Wubi and she used it.  I recently did the same with 10.04 and she isn't liking it since everything needed to be reinstalled.

Wubi makes it easy to add and remove if a new version comes along.  I'd love to do a pernament install of Ubuntu, but there's the threat of the "End of Life" date, which forces to upgrade, making it impossible to keep it pernament.

So how can I have a pernament version of Ubuntu without worrying about the end of life date.  The repos are needed to install software and dependencies with ease and if they go down, no more new software.

---

### Post by sandyd on 2010-05-02
easy. install the LTS versions of ubuntu.
10.04 is a LTS and reaches EOL in 2013. which is 3 years.

Additionally, you can use dpkg -l to list the packages that are currently installed

---

### Post by LinuxFox on 2010-05-02
> **carlee said:**
> easy. install the LTS versions of ubuntu.
10.04 is a LTS and reaches EOL in 2013. which is 3 years.

Additionally, you can use dpkg -l to list the packages that are currently installedYes, I know that, but it eventually ends.  That's my problem.  I already put the new LTS on my mother's computer and it works.  Takes long to login, but works quite well after that.

I want to be able to keep Ubuntu on her computer without worrying about newer versions, since specs change.  For example needs more memory or a faster processor.

---

### Post by tica vun on 2010-05-02
Well, you could just upgrade when the next release comes along. In fact, you can even wait for the next LTS release, 12.04, because Lucid will still be supported then. Ubuntu makes it pretty easy to upgrade to a new release, it's gotten basically as seamless as a kernel update, all you have to do is run the update manager with the --dist-upgrade switch, let it install the new release, and reboot your PC.

---

### Post by scradock on 2010-05-02
> **LinuxFox said:**
> Yes, I know that, but it eventually ends.  That's my problem.  I already put the new LTS on my mother's computer and it works.  Takes long to login, but works quite well after that.

I want to be able to keep Ubuntu on her computer without worrying about newer versions, since specs change.  For example needs more memory or a faster processor.
There is no real need to upgrade, if you don't want to. There are plenty of people running versions of Ubuntu that are years old, way beyond their "end of life" date. All you miss is the comfort of knowing that you'll get security-updates sent to you automatically.

The bottom line is, if the version you have does what you need it to, why change anything about it? Just turn off automatic update checking or limit it to security releases. Remember, this is NOT Windows - YOU own the computer (or your mother does) and YOU decide what to run on it.

HTH

---

### Post by marshmallow1304 on 2010-05-02
I suppose you could use a rolling release distro like Debian Testing so you'll never need to do an "upgrade".  But even so, software (and its requirements) will change over time.  I am not aware of any OS that has pledged to support the same versions of the same software indefinitely.

---

### Post by snowpine on 2010-05-02
Ubuntu does not magically stop working at the end of 3 years. :) You can keep using an Ubuntu release after it reaches end-of-life; you just won't get any security patches, bug fixes, updates, or help from Canonical if something breaks.

If 3 years of support is not enough, look into a distro like Red Hat, which I believe provides up to 10 years of support (but it's not cheap).

---

### Post by Dougie187 on 2010-05-02
It works the same as when windows hits EOL. It's not like you can't install/use it. They just don't release security updates for it anymore. 

The best option, as some have mentioned, is to leapfrog versions by going from one LTS to another. You can try to upgrade instead of clean install, that way you don't have to reinstall everything. However if you would rather, you can just stick with one LTS (as that has the longest time for upgrades) and never reinstall her computer.

You just won't get anymore updates after the end of life.

---

### Post by LinuxFox on 2010-05-02
> **Dougie187 said:**
> It works the same as when windows hits EOL. It's not like you can't install/use it. They just don't release security updates for it anymore. I understand it will keep working, but when Ubuntu reaches End of Life, don't the repos get shutdown, making it impossible to install software?

---

### Post by theozzlives on 2010-05-02
The problem is simple. All your files and settings are in /home. Just put that into it's own [partition]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") and don't format it when you update. If you're serious about Ubuntu, get rid of WUBI.

---

### Post by snowpine on 2010-05-02
> **LinuxFox said:**
> I understand it will keep working, but when Ubuntu reaches End of Life, don't the repos get shutdown, making it impossible to install software?

The repos move to old-releases.ubuntu.com 

You can edit your /etc/apt/sources.list and change all instances of archive.ubuntu.com (or whichever mirror you use) to old-releases.ubuntu.com

This will allow you to install apps from the repos. These apps will of course be old and will not receive updates. :)

---

### Post by LinuxFox on 2010-05-02
> **snowpine said:**
> The repos move to old-releases.ubuntu.com 

You can edit your /etc/apt/sources.list and change all instances of archives.ubuntu.com (or whichever mirror you use) to old-releases.ubuntu.com

This will allow you to install apps from the repos. These apps will of course be old and will not receive updates. :)I just looked at old-releases and I all I saw were the ISOs to the older versions.  This also has repositories as well?  Is there an example I could see?

---

### Post by snowpine on 2010-05-02
> **LinuxFox said:**
> I just looked at old-releases and I all I saw were the ISOs to the older versions.  This also has repositories as well?  Is there an example I could see?

[http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/](http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/)

---

### Post by LinuxFox on 2010-05-02
> **snowpine said:**
> [http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/](http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/)That answers my question.  If she doesn't like 10.04, I guess I could reinstall 8.04 without worry since there are old repositories.

I know it has 1 year left, but it's good to know ahead of time.

Thanks a lot.

---

