---
title: "Upgrading from an obsolete release"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by gmg2000 on 2011-01-10
Hello Ubuntu masters. I have couple of questions about upgrading from an old release. I am currently running Feisty fawn(I know, I was lazy and didn't upgrade like I should). I was wondering if there was any way I could upgrade to 8.04 or 10.04 without losing all of my media? Thank you for your time.

---

### Post by psusi on 2011-01-10
I would suggest just doing a clean install of 10.04 or 10.10.  Choose manual partitioning, and do NOT tick the format box and the contents of your /home directory will remain intact.  Then again, you may as well go ahead and format and just restore your media from backup.  You do keep backups right?

---

### Post by dBuster on 2011-01-10
> **gmg2000 said:**
> Hello Ubuntu masters. I have couple of questions about upgrading from an old release. I am currently running Feisty fawn(I know, I was lazy and didn't upgrade like I should). I was wondering if there was any way I could upgrade to 8.04 or 10.04 without losing all of my media? Thank you for your time.

In theory if you have a LTS release and want to upgrade that you can indeed go to the next LTS release without having to upgrade to each step in between.

I can not remember if Feisty was a LTS or not but if it was go for it to 8.04 then I believe you can go to 10.04.

---

### Post by Zilioum on 2011-01-10
I agree with psusi. I think it's your only option anyway, since Feisty wasn't a long term release (LTS). With the normal releases you can only update from one version to the next.

---

### Post by cgroza on 2011-01-10
You need to do a fresh install. Anyway, I always upgrade to the latest one, just can't resist to try the new stuff!

---

### Post by snowpine on 2011-01-10
A fresh reinstall gets my vote as well. However, you most certainly can upgrade if you choose, [by following these instructions]("https://help.ubuntu.com/community/EOLUpgrades").

---

### Post by CharlesA on 2011-01-10
+1 to clean install as well.

I definitely suggest backing up anything you value before doing anything.

---

### Post by dBuster on 2011-01-10
> **Zilioum said:**
> I agree with psusi. I think it's your only option anyway, since Feisty wasn't a long term release (LTS). With the normal releases you can only update from one version to the next.

There the answer is simple since Feisty was not a LTS then definitely a clean new install.

---

### Post by gmg2000 on 2011-01-10
Thanks for the info.

---

### Post by gmg2000 on 2011-01-11
second question, could I download and burn gutsy gibbon and hardy heron isos and upgrade from there?

---

### Post by snowpine on 2011-01-11
> **gmg2000 said:**
> second question, could I download and burn gutsy gibbon and hardy heron isos and upgrade from there?

The only supported method for upgrading Feisty is described in detail here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you are going to download new isos anyway, why not just download the newest? :) A fresh install will be quicker and have a greater chance of success. You could even set up a "dual boot" between Feisty and Maverick, so that you can use your old install as a fall-back while you're learning your way around the new release.

---

### Post by gmg2000 on 2011-01-12
Well, a fresh install is not an option. I don't have the resources to back up all my files. I tried to dual boot when I first got my laptop. I lost everything I had on my Vista partition. 

I don't have a problem with a Feisty Fawn; it just that some of the programs(firefox, adobe flash) are obsolete and not working properly.

Thanks for your input though.

---

### Post by snowpine on 2011-01-12
> **gmg2000 said:**
> Well, a fresh install is not an option. I don't have the resources to back up all my files. I tried to dual boot when I first got my laptop. I lost everything I had on my Vista partition. 

I don't have a problem with a Feisty Fawn; it just that some of the programs(firefox, adobe flash) are obsolete and not working properly.

Thanks for your input though.

If you can't back up your important files to an external drive (1TB drives are under US$100!), then I cannot recommend any type of upgrade. Keep your system as-is and hope nothing goes wrong. :(

---

### Post by Rex Bouwense on 2011-01-12
You have only three options.  One, do nothing and continue with the OS that you have which hasn't had any updates since its EOL.  Programs will continue to work to the best of their ability until a disaster happens.  Two, upgrade like snowpine suggested using the article that was pointed out.  Three, install a new OS as a dual boot as was suggested by snowpine.  In any event you need to back up the data that you cannot afford to lose.  USB flash drives are so cheap now that you can back up your stuff using nothing but them.  I do that routinely.  Installing a second OS is not difficult and as been pointed out you can use your old one until you are comfortable with the new one.  A piece of advice from one who failed to take it, make a detailed plan and follow it.  Backup what you cannot afford to lose just in case.

---

### Post by walt.smith1960 on 2011-01-12
> **snowpine said:**
> If you can't back up your important files to an external drive (1TB drives are under US$100!), then I cannot recommend any type of upgrade. Keep your system as-is and hope nothing goes wrong. :(

What he said!!! If you have anything of consequence-music movies whatever-you need to back it up. It's not a question of if your hard drive will fail, it's a question of when.  I've seen 500 Gb. external drives for $39.99 in the U.S. If you're impatient you could just copy your entire home directory to backup media. I'm not sure whether configuration files and such found in the home directory would cause problems if copied to a new install or not.

---

### Post by NT4usB on 2011-01-12
fwiw, I'll put a new drive in the box (assuming desktop, and not laptop) and slave the old drive.
Fresh install on the new drive, then cp (drag) all the data over from the slave.

The old software is running on an old HDD. 
Wouldn't want a brandy new install to go tango uniform when the old drive dies.
Drives are cheap. Way cheaper then the time I spend doing something over because I did it half fast the first time.

---

### Post by kansasnoob on 2011-01-12
I've not read all replies but I also agree with psusi. You can possibly also install a new OS (Ubuntu 10.04.1 or 10.10) in parallel with the existing OS, that is you could dual/multi-boot like I do:

[ATTACH]180891[/ATTACH]

I realize that's major "overkill" to most people but I do a lot of testing. The thing is though I can easily "move" parts-n-pieces/files-n-folders from an old distro to a new distro and I don't have to rush. I can keep testing until I know I have things right on the new distro.

There are of course limitations and caveats. We'd first have no know what your current drive and partition arrangement looks like. The best way for us to see that is a screenshot of Gparted for each drive.

Have I confused you yet?

I like this guide for multi-booting:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by 1clue on 2011-01-12
IMO any system which you don't easily back up is considered to be completely expendable by the owner.

There is no such thing as a no-incidents upgrade, and to go from that far back and chain upgrades you will be lucky to keep any settings at all, and I wouldn't count out losing some of your personal data as well.

Any reasonable box that's that old has a relatively tiny drive on it.  IMO if you're bothering to upgrade the box then it's worth buying something that you can use to back it up.  I agree with NT4usB, buy a new drive.  Install the latest OS on it, get it set up and then pull your data off the old drive a bit at a time.

---

### Post by kansasnoob on 2011-01-12
> **walt.smith1960 said:**
> What he said!!! If you have anything of consequence-music movies whatever-you need to back it up. It's not a question of if your hard drive will fail, it's a question of when.  I've seen 500 Gb. external drives for $39.99 in the U.S. If you're impatient you could just copy your entire home directory to backup media. I'm not sure whether configuration files and such found in the home directory would cause problems if copied to a new install or not.

Or a power outage happens during repartitioning and such :o

If you just can't lose it you must have a back up!

---

### Post by NT4usB on 2011-01-13
> **1clue said:**
> ...There is no such thing as a no-incidents upgrade, and to go from that far back and chain upgrades you will be lucky to keep any settings at all, and I wouldn't count out losing some of your personal data as well...

Ubuntu (Linux) has surprised me in this regard. 
I have one box I've been using the same /home since Dapper.
/home is on its own partition so I format /, /boot, and /swap, then install the new release.
Usually a bunch of extra programs need installing to get me back to where I was but all the configurations are still there. 
If I run one that's not installed, terminal points it out that I need to sudo apt-get install *bla* and it's good as new.
Stuff like browsers, email, etc., pick up right where they left off, as if nothing happened.

---

### Post by gmg2000 on 2011-01-13
All of my money is tied up in other projects. I can't spare $40 for an external hard drive. My laptop dual boots Vista and Feisty Fawn, and my desktop has 10.04. Like I said, I don't need to upgrade, but I would like to have some of my programs up-to-date ( firefox, opera, vlc, etc) 

Thanks for the info.

---

### Post by CharlesA on 2011-01-13
Well you could always backup your laptop to the desktop and reinstall. Only thing you'd need is a network cable, and NFS or something.

---

