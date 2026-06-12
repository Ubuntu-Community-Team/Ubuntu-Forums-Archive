---
title: "feisty missing from us archive?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by ducksauce on 2008-12-15
Hi, I'm posting this in the beginners section because I think I am doing something wrong.  Starting last week I was no longer able to install anything via apt-get.  I get a 404 when trying to download packages, specifically:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglib1.2 1.2.10-17build1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]

When I hit [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) in a browser, I see that all the other dists have directories with no modifer (/dapper/, /gutsy/, /hardy/, etc), but not feisty.  Is it no longer supported, or should I be modifying my sources.list?

Thanks for the help.

---

### Post by northern lights on 2008-12-15
Feisty's lifetime has expired on October 19th*.

Maybe the repos are history too?
(Can't check as I am on Intrepid)



*Feisty was released on April 19th 2007. Since it's not an LTS release (such as Dapper and Hardy) the desktop version's support ends after 18 months.

---

### Post by ducksauce on 2008-12-15
Ahh okay.  Thank you.

---

### Post by Toshibawarrior on 2008-12-15
Sadly Feisty Fawn 7.04 reached it's "End Of Life" which means there will be no more updates or support bulletins for it from now on. Non-LTS(Long Term Support) versions of Ubuntu last a year and a half, period which is already expired for Feisty.

The official new article can be found [HERE]("http://www.ubuntu.com/news/ubuntu-7.04-end-of-life")

---

### Post by howefield on 2008-12-15
RIP Feisty

Feisty stopped getting updates and support on the 19th of October.

It won't stop working for you, you just won't get any security patches etc etc. Time to upgrade ?

---

### Post by northern lights on 2008-12-15
> **Toshibawarrior said:**
> ...Non-LTS(Long Time Support) versions...As an aside: It's "Long Term".

---

### Post by Toshibawarrior on 2008-12-15
> **northern lights said:**
> As an aside: It's "Long Term".

Sorry...typo over there...I was reading another post right before posting here... :p...

Long Term Support...:)

---

### Post by Duck2006 on 2008-12-15
This may help with getting repo's for feisty.

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

It does take some time. (A lot of time)

---

### Post by ducksauce on 2008-12-15
Thanks for the link, Duck2006, but I just changed all feisty references to gutsy in my sources.list for now.  That allowed me to install the software I needed.  It will tide me over until I can figure out how to upgrade.  Following the instructions on the Gutsy upgrade page ([https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)) resulted in more 404s.  The moral here is that I shouldn't have waited so long to upgrade, I think.

---

### Post by Toshibawarrior on 2008-12-15
> **ducksauce said:**
> Thanks for the link, Duck2006, but I just changed all feisty references to gutsy in my sources.list for now.  That allowed me to install the software I needed.  It will tide me over until I can figure out how to upgrade.  Following the instructions on the Gutsy upgrade page ([https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)) resulted in more 404s.  The moral here is that I shouldn't have waited so long to upgrade, I think.

Just a thought...

You might want to backup all your important data and make a fresh install of Intrepid (8.10) by formatting your hard drive and installing Ubuntu from scratch. That way you'll avoid annoying errors and future conflicts between versions and you won't waste much time with Upgrade Manager.

Just a thought though...I always do fresh installs...upgrades tend to end up in disaster in some computers, like mine.

---

### Post by northern lights on 2008-12-15
> **Toshibawarrior said:**
> Just a thought...

You might want to backup all your important data and make a fresh install of Intrepid (8.10) 
[...]
I always do fresh installs...upgrades tend to end up in disaster in some computers, like mine.

I wouldn't agree to upgrades being generally worse than fresh installs, but in this case where you'd have to upgrade from Feisty to Gutsy to Hardy to Intrepid (if you'd indeed want Intrepid, which would make sense) upgrading (apart from possible hassles) would take just as long, if not longer than a fresh install.

Do you have a separate /home partition (would make a fresh install easier and backing up quicker)?

Anyhow, since you're not contemplating a move from Hardy to Intrepid but are still on Feisty, I'd vote for the warriors suggestion.

---

### Post by zvacet on 2008-12-15
@ **ducksauce**

>  Following the instructions on the Gutsy upgrade page ([https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)) resulted in more 404s. 

If you want to upgrade to Gutsy then replace 

```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```
 
with 

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 
```

save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

But better solution is to install last version as others adviced allready.

---

