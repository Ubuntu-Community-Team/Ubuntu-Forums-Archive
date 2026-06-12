---
title: "Best(and easiest) backup program?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Norm24 on 2010-01-21
So far Grsync is ok.Anything gui based better?

The only reason I ask is that Lucid is an LTS and Karmic works so well with my machine.I want want the best backup before I do a clean install to Lucid as it will most likely be the version that sits on my machine for the next three years.

---

### Post by Psumi on 2010-01-21
Back In Time.

[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by JC Cheloven on 2010-01-21
I use unison regulary (it is in the repos). Never had a single problem with it. 
Note: it seems not being currently maintained, but anyway.

---

### Post by bark50 on 2010-01-21
> **Psumi said:**
> Back In Time.

[http://backintime.le-web.org/](http://backintime.le-web.org/)

Yep.  Back in Time is the one I recommend.

---

### Post by Norm24 on 2010-01-22
I get this message when trying to install backintime:

```
Error: Dependency is not satisfiable: backintime-common (= 0.9.26)
```

Nevermind.Sometimes I'm an idiot.

---

### Post by doublewitt on 2010-01-27
*Don't know about the error message* - but - **Back in Time** is the one I use. I really appreciate this software. It's simple and straightforward... and does a nice job.

---

### Post by HarrisonNapper on 2010-01-27
Looks like this one is case closed, but I wanted to throw something in that might be typical of a CLI person, but for the record, rsync, mkisofs, and cron are all useful to know independently. Not sure if you like man pages, but if you like to know the "back-end" stuff, those would be the ones to use. Cheers.

---

### Post by dimeotane on 2010-01-31
Unison was working pretty good for me from notebook to USB key to sync my work files regularly. 

For a bare metal recovery you'd maybe want to do a dd image of your entire drive. 

When you say backup it depends on what you're talking about.  How have you configured your system? Do you have a separate /home partition? You might just want to back those files only.  Partimage was fast and easy.. (it doesn't waste time copying empty space).

---

### Post by kronictokr on 2010-01-31
i want to make a backup/distro of my system, so i could install exactly what ive done to another computer. which would i use in this case?

---

### Post by Mrandersonjr on 2010-01-31
Use quickstart.
[http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html](http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html)

---

### Post by kronictokr on 2010-01-31
checking it out now, tx!

---

### Post by kronictokr on 2010-01-31
ive searched and searched, and then some, never came across this one. pretty extensive, thank you very much, gona give quickstart a try right now

---

### Post by rustybutt on 2010-02-22
I'm fond of good old UNIX dump/restore.

sudo apt-get install dump

I just went through the exercise of backing up an Ubuntu install on a VMware Workstation VM, and then rebuilding it into a new VM.  A "bare metal recovery" so to speak, and the procedure would be very similar for a physical machine.  Full write up at:

[http://ubuntuforums.org/showthread.php?t=1412232](http://ubuntuforums.org/showthread.php?t=1412232)

There's a LOT more to the procedure than just doing dump and restore.  You've got to fiddle with re-installing grub onto the drive, reset the boot partition UUID, and make the swap partition and set its UUID as well.  All is detailed in the above article.

By the way, restore can be done interactively to get back just a single file.

Russ

---

### Post by theozzlives on 2010-02-22
I just save a tarball on a network drive of /home. That's really all that matters anyhow (except my /var/www I save that to).

---

### Post by jbalazs on 2010-02-22
Anyone use remastersys. I do

---

### Post by kendoori on 2010-02-22
Clonezilla is a very safe program built for imaging your machine (it's in the repositories). Burn a LiveCD and clone to another drive (e.g. USB) or network drive. The UI is bit crude, but one can easily get by using the defaults. I tried various upgrade steps when I went to 9.10 and felt very safe that I had a clone waiting to be restored from (and indeed I needed it). For day to day back up I use a cloud-based service, SpiderOak.

---

