---
title: "running ubuntu 11.04, can it be effected by any viruses"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by gudurukarthik on 2011-04-30
can ubuntu be effected by viruses if so what is the best anti-virus software? thanzzz

---

### Post by donkyhotay on 2011-04-30
before this gets shuffled over to recurring discussions. Here is my obligatory "antivirus on linux" post. 


There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

Master Foo,he asked why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?

Master Foo smiled, and said â&#8364;&#339;When your house is well constructed, there is no need to add pillars to keep the roof in place.

The novice replied Would it not be better to use these things anyway, just to be certain?

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

What are you doing? the novice asked in surprise.

Master Foo replied simply: Tying your shoes.

Upon hearing this, the novice was enlightened.

---

### Post by dniMretsaM on 2011-04-30
It could /theoretically/ be infected by viruses, but it's highly unlikely. The two main reasons are that (a) almost all programs are installed from central repositories. You're not usually going to browsing some random site and downloading infected software. And (b) programs are run as a normal use and not root. This means that it can't make any changes to anything important without you purposely entering an admin password. The biggest threat of viruses would be getting a virus in your virtual C: drive (WINE). For more info, there is an article about it in the Ubuntu Wiki.

---

### Post by gudurukarthik on 2011-04-30
i have been using ubuntu since 8-12 months and i never had a problem tilll now.. nothing big but the new firefox4 had just checked for virus and found some later it anyways suggested a file to install but that file is in .exe so there im stuck what 2do?

> **dniMretsaM said:**
> It could /theoretically/ be infected by viruses, but it's highly unlikely. The two main reasons are that (a) almost all programs are installed from central repositories. You're not usually going to browsing some random site and downloading infected software. And (b) programs are run as a normal use and not root. This means that it can't make any changes to anything important without you purposely entering an admin password. The biggest threat of viruses would be getting a virus in your virtual C: drive (WINE). For more info, there is an article about it in the Ubuntu Wiki.

---

### Post by THE CARTER on 2011-04-30
Like everyone else said.  I've been a faithful ubuntu user for a year now, and have not had virus/malware issues.  Its not like windows where everything gets infected.

I highly doubt you would need antivirus software.

---

### Post by K_45 on 2011-04-30
Even if you browse those "interesting" sites *cough* *cough* nothing will really happen. However I still use NoScript + AdBlockPlus + Ghostery to limit what those "interesting" sites can do.

---

### Post by gudurukarthik on 2011-04-30
Fyi:i was downloading a psychology image from goggle 
> **K_45 said:**
> Even if you browse those "interesting" sites *cough* *cough* nothing will really happen. However I still use NoScript + AdBlockPlus + Ghostery to limit what those "interesting" sites can do.

---

### Post by eltonw on 2011-04-30
> **gudurukarthik said:**
> can ubuntu be effected by viruses if so what is the best anti-virus software? thanzzz
The best way to reply to this is to point you to the article on Wikipedia: [http://en.wikipedia.org/wiki/Linux_malware]("http://en.wikipedia.org/wiki/Linux_malware")
Compared to Windows, viruses are practically non-existent in the linux world. However, it is _always good sense to take precautions_, e.g. if you decide to install WINE to run Windows apps on your linux machine, you might inadvertently download infected files. 

As such, it would not hurt to install the virus checker (such as Clam) that is available in ubuntu. Other normal precautions would be to install the WOT and AdBlock extensions for your browser.

More info on **[COLOR="DarkRed"]WINE[/COLOR]** can be found here: [http://www.winehq.org/]("http://www.winehq.org/")
The **[COLOR="DarkRed"]WOT[/COLOR]** (Web Of Trust) browser extension is[/U]highly recommended[U]: [http://www.mywot.com/]("http://www.mywot.com/")

HTH....

---

### Post by gudurukarthik on 2011-04-30
that's really helpful thnazzzz
QUOTE=eltonw;10747634]The best way to reply to this is to point you to the article on Wikipedia: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
Compared to Windows, viruses are practically non-existent in the linux world. However, it is _always good sense to take precautions_, e.g. if you decide to install WINE to run Windows apps on your linux machine, you might inadvertently download infected files. 

As such, it would not hurt to install the virus checker (such as Clam) that is available in ubuntu. Other normal precautions would be to install the WOT and AdBlock extensions for your browser.

More info on **[COLOR=DarkRed]WINE[/COLOR]** can be found here: [http://www.winehq.org/](http://www.winehq.org/)
The **[COLOR=DarkRed]WOT[/COLOR]** (Web Of Trust) browser extension is[/U]highly recommended[U]: [http://www.mywot.com/](http://www.mywot.com/)

HTH....[/QUOTE]

---

### Post by jerome1232 on 2011-04-30
> **gudurukarthik said:**
> i have been using ubuntu since 8-12 months and i never had a problem tilll now.. nothing big but the new firefox4 had just checked for virus and found some later it anyways suggested a file to install but that file is in .exe so there im stuck what 2do?

Firefox doesn't check for viruses, more likely you saw an add that pretends to scan your machine, claim your machine is infected and offer to let you download their "anti-virus"

This is a typical social engineering attempt to get you to download a trojan.

Currently there are no known viruses in the wild which can function on a Linux machine.

---

### Post by dniMretsaM on 2011-04-30
You might wanna read [this](https://help.ubuntu.com/community/Antivirus).

---

