---
title: "KDEnlive Crashes"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-30
Every time I try to open kdenlive in gnome, it crashes. It works just fine when I run it in kde. Do I have to update it, by adding a repository?

---

### Post by Sup3r3g0 on 2009-01-30
[s]Never mind. It doesn't crash anymore. I just had to reinstall it.[/s]

It still crashes.

---

### Post by Sup3r3g0 on 2009-01-31
Bump

---

### Post by Prometheus28 on 2009-02-07
I has same probem with kdenlive....... I tried 2 [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)...




nick@nick-desktop:~$ gpg --check-sigs 428D7C01
pub   1024D/428D7C01 2008-09-02
uid                  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sig!3        428D7C01 2008-09-02  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sub   2048g/A2C2A7A5 2008-09-02
sig!         428D7C01 2008-09-02  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>

1 signature not checked due to a missing key


Halp

---

### Post by binarymutant on 2009-02-07
please start kdenlive from a terminal and post the output here so that others can see any problems and possibly help determine what is going wrong

---

### Post by Prometheus28 on 2009-02-07
nick@nick-desktop:~$ kdenlive
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
nick@nick-desktop:~$ ICE default IO error handler doing an exit(), pid = 6934, errno = 11



nick@nick-desktop:~$ kdenlive -v
Qt: 3.3.8b
KDE: 3.5.10
Kdenlive: 0.6.0-svn



this happens after about 5-10 mins of working with video. I was hoping 2 install the debug build so i could report a backtrace...

---

### Post by binarymutant on 2009-02-09
sorry for the not so quick reply,
here's your bug [https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/232167](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/232167)
To fix this please install kdebase-bin and kdenlive will work

---

### Post by Prometheus28 on 2009-02-09
I did  these instructions instead

[http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)

> Ubuntu Intrepid

After contacting Ubuntu packagers, it seems that Jaunty packages will never enter backports. Therefore it is recommended to install Kdenlive using alternative repositories.
Here is our recommended choice to install Kdenlive 0.7.2:

   1. Go to your system menu > Software sources > Third-Party Software
   2. Click add and paste this line in:
      deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
   3. Close software source and click reload

Then type:
sudo apt-get update && sudo apt-get install kdenlive dvgrab frei0r swh-plugins

Please report the quality of these packages here:
[http://www.kdenlive.org/forum/please-report-quality-ubuntu-810-packages](http://www.kdenlive.org/forum/please-report-quality-ubuntu-810-packages)

Packages by baumd.

---

### Post by igknighted on 2009-02-09
The 0.6 version of kdenlive is ancient... there are packages for the 0.7 series somewhere, which was basically a complete rewrite.  I would look at getting a hold of the new version instead of trying to fix the old one.

EDIT: Use the PPA mentioned above, safer than the jaunty packages.

---

