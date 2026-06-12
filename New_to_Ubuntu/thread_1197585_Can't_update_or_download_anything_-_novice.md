---
title: "Can't update or download anything - novice"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by aierlan on 2009-06-26
Hi 
I'm VERY new to ubuntu, A friend of mine gave me a ubuntu 7.04 disk and i loaded it on a spare pc i had 3 days ago to try and figure it out. So far no good! 
I have a direct connection to the internet via network cable. And have very good and fast surfing capabilities.  

I've had a look at a few tutorials and stuff but cant figure out how to fix my problem.  Every time I try to download a package or update something i get the error 

"Could not download all repository indexes"

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I get this message for everything.  Even when i go to the update manager I get the above followed by:

[SIZE=1]http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:) 404 Not Found
[http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:) 404 Not Found
[/SIZE]
I've searched this error message in various posts but I'm afraid I'm a little too much of a novice to understand the lingo.  I can find my way around the desktop and have been checking everything out but not sure how to use the terminal or anything like that yet.  

The thing that bugs me the most is I cant import anything into Rhythmbox music player.  When I try to import a folder all the tracks are greyed out.  I've tried to update the plugins for gstreamer but as i said above I get so far only to receive a similar message to the one above.  

Thank you in advance to anyone who has the patience to talk me through a couple of things step by step.  I'm trying to get to know this os as best I can so as to not have to use microsoft's sh"*tty products anymore, but sofar finding it pretty daunting

aierlan

---

### Post by billgoldberg on 2009-06-26
Well those websites don't exist anymore.

Maybe try a mirror in Synaptic.

---

### Post by VCoolio on 2009-06-26
Feisty (Ubuntu 7.04) is not supported anymore. Go with Hardy Heron (8.04), the latest Long Term Support release (supported until aptil 2011), or Jaunty Jackalope (9.04), the latest release, supporting ext4 filesystem. Download preferably by torrent, you'll have it in no time, burn to cd and install that. 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by michy99 on 2009-06-26
7.04 is no longer supported. The repositories have been moved to
```
 http://old-releases.ubuntu.com/
```You best bet is installing 8.04 or later.

---

### Post by Sef on 2009-06-26
7.04, Fiesty Fawn, is not supported any more.  I would download and install [Jaunty Jackalope]("http://www.ubuntu.com/"), which is the latest release.

---

### Post by Therion on 2009-06-26
You need a little bit more recent version of Ubuntu to test out.  7.04 (Feisty Fawn) is pretty old by Ubuntu standards (new release every six months).

I'd suggest you download a more current version from here:  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it to a CD as instructed here:  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and do a fresh install.

---

### Post by aierlan on 2009-06-26
Thanks so much guys

I guess I've exposed just how much of a novice I am, but on the road to discovery!

---

