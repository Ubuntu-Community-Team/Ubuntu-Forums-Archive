---
title: "Installing Firefox"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Virulent on 2007-09-08
My current version of Firefox keeps crashing and I want to install a new one. I have downloaded the file and extracted it, now what do I do?

---

### Post by spacegypsy on 2007-09-08
see; [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

or you can also try[ Swiftweasel]("http://swiftweasel.sourceforge.net/about.php"), it's in the repo's

---

### Post by Virulent on 2007-09-08
When I download the file that

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

tells me too, My archive manager says "Could not open "ubuntuzilla-4.4.0-0ubuntu1-i386.deb" Archive type not supported."

---

### Post by nanotube on 2007-09-08
> **Virulent said:**
> When I download the file that

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

tells me too, My archive manager says "Could not open "ubuntuzilla-4.4.0-0ubuntu1-i386.deb" Archive type not supported."

what's your version of ubuntu?

also, you are not supposed to open it with archive manager, but install it with gdebi. please read the instructions on the ubuntuzilla site carefully and follow them. :)

---

### Post by rainwalker on 2007-09-08
Are you saying the Firefox that's included with Ubuntu keeps crashing? If so, is there something specific that crashes it?

Also, if you plan on using your own install of Firefox instead of the included one, you're going to have to mess around with the plugins; For a long time I used my own install of Firefox because I didn't want to wait for the included one to update to v2, but none of my plugins worked with it. I later found out that the plugins were installing, but for some reason they only worked with the included Firefox.
Anyway, just some of advice. If that's not what you're planning to do, just ignore this.

---

### Post by maestrobwh1 on 2007-12-30
Yes, I would say that installing Swiftweasel seemed to solve my sudden "closing" of firefox.  It was usually during a banking session so I would have to re-enter my password/username several times.  

Automatix will do it for you but I found that if I can find a repo, it can update/updrade with my entire system.

#Swiftweasel
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) gutsy multiverse

If you want firefox, all you have to do is go to its website, download the tar, and unpack it (say in your home directory).  Open it up, and launch the shell script "firefox" by clicking on it.  You could also just create a shortcut icon to it.  I tried it, but the idea of having to use a package that is not maintained by apt seems annoying to me.  I didn't use it long enough to cite that it was more stable, but for the day I used it that way, I don't remember it crashing.  Whether you do this or swiftweasel, know that if you already have a firefox install, it will install all your preferences, extensions, bookmarks from that installed package so you won't have to do that all over again.

---

