---
title: "dumping FF for Midori"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by degarb on 2011-02-21
I cannot upgrade from the bloated Firefox to Midori.  Something about dependencies.  [http://www.ubuntugeek.com/midori-a-lightweight-web-browser.html](http://www.ubuntugeek.com/midori-a-lightweight-web-browser.html)   These instructions don't work.

---

### Post by uRock on 2011-02-21
Can you explain the errors you are having? It is hard to help when we don't know what you have or have not done. 

Honestly, I wouldn't try to install something that uses a Gutsy repository. Is Midori that far out of date?

---

### Post by degarb on 2011-02-21
Also failed with here: [http://ubuntuforums.org/archive/index.php/t-1199960.html](http://ubuntuforums.org/archive/index.php/t-1199960.html)
-----------
The following packages have unmet dependencies:
  midori: Depends: libatk1.0-0 (>= 1.29.3) but 1.28.0-0ubuntu1 is to be installed
          Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
          Depends: libglib2.0-0 (>= 2.23.5) but 2.22.3-0ubuntu1 is to be installed
          Depends: libgtk2.0-0 (>= 2.20.0) but 2.18.3-1ubuntu2.2 is to be installed
          Depends: libsqlite3-0 (>= 3.6.22) but 3.6.16-1ubuntu1 is to be installed
E: Broken packages
--------------------

---

### Post by uRock on 2011-02-21
I am running Ubuntu 10.10 and when I ran **sudo apt-get install midori**, the install started to install without any complaints.

What version of Ubuntu are you using?

---

### Post by degarb on 2011-02-21
This is a 600 mhz 6 gig hard drive laptop, with 9.10.  I cannot upgrade to 10.10 with only 600 meg free. But I want to uninstall Firefox which is too heavy for the machine, and put Midori on it.  Opera 11 runs fast enough on it. 

I put Midori on my Mint machine, no problems.   On my virtual crunchbang machine, Midori runs much smoother than Opera and takes a fraction of the memory.  Midori is the default browser in Slitaz.

---

### Post by uRock on 2011-02-21
I just installed Midori in Karmic using **sudo apt-get install midori** 

If you need the newest version, then if can be downloaded here [http://www.twotoasts.de/index.php?/pages/midori_summary.html](http://www.twotoasts.de/index.php?/pages/midori_summary.html)

---

### Post by Old *ix Geek on 2011-02-21
When I installed Midori a while back I did it via Synaptic and had no problems. Did you try Synaptic? I'm using Kubuntu 9.10.

---

### Post by degarb on 2011-02-21
> **Old *ix Geek said:**
> When I installed Midori a while back I did it via Synaptic and had no problems. Did you try Synaptic? I'm using Kubuntu 9.10.

Of course, I tried with Synaptic, but these libfontconfig version complaints.  I even downloaded source and tried to compile but got vela complaints, then with switch error 11234, whatever that meant.

I don't see way to update just the needed components without updating the OS, which is impossible with 200 meg free. (temporarily up to 600 meg free, after manually un-installing kernel headers, and 86 megs with bleach bit.)

---

