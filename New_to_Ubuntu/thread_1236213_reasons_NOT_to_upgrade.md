---
title: "reasons NOT to upgrade?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by vegmunky on 2009-08-10
Is there a general reason to ever NOT to upgrade?  Like, is it generally better to stick with the LTS releases, or should I just upgrade to each new release?

I thought maybe I could tell how stable the releases are by the version numbers (like 1.5 is better than 1.0) but I just realized the version numbers are mere dates.

I keep all my data files backed up so even if I kill my system with an upgrade I'm not going to cry too much, but I'd rather avoid the time wasted.

---

### Post by theozzlives on 2009-08-10
> **vegmunky said:**
> Is there a general reason to ever NOT to upgrade?  Like, is it generally better to stick with the LTS releases, or should I just upgrade to each new release?

I thought maybe I could tell how stable the releases are by the version numbers (like 1.5 is better than 1.0) but I just realized the version numbers are mere dates.

I keep all my data files backed up so even if I kill my system with an upgrade I'm not going to cry too much, but I'd rather avoid the time wasted.

I've found that sometimes things that work are blacklisted or do not work in newer versions, nonetheless I still upgrade, use Alphas, etc. just to see what's new. If you're happy with an LTS, wait til the next LTS.

---

### Post by taavikko on 2009-08-10
I would stick to older versions, unless:

there are fixes in apps that I need.
This can be bypassed using PPA's (most of the times)

My hardware works better with new kernel
Also can be bypassed.

I like things to be new and shiny,
better to upgrade so my install wouldn't become a mess with all the extra PPA's and installs from source code etc.

Basically, if you don't have any need for newer version, stick with the older ones.
Upgrade LTS -> LTS

---

### Post by Sef on 2009-08-10
You are happy with your current os.

---

### Post by abrari on 2009-08-10
I fear the upgrade will ruin my well-customized system. So I prefer to wait some guys' report about the upgrade to see if the upgrade doesn't mess the system up.

Is there any chance to revert all things back after a disastrous upgrade?

---

### Post by vegmunky on 2009-08-10
> **taavikko said:**
> This can be bypassed using PPA's (most of the times)eh...what's a PPA?

---

### Post by Humanum on 2009-08-10
> **vegmunky said:**
> eh...what's a PPA?

PPA means : Personal Package Archive

It's the package each developper is working on ... before being put together with the whole system

---

### Post by Tmatherne on 2009-08-10
> **abrari said:**
> I fear the upgrade will ruin my well-customized system. So I prefer to wait some guys' report about the upgrade to see if the upgrade doesn't mess the system up.
 
Is there any chance to revert all things back after a disastrous upgrade?
 
 
There is, sort of.  Run a live CD for a while until you have an idea as to how it will work.  If you don't like it, remove the CD and reboot. =]
 
Tommie

---

### Post by t0p on 2009-08-10
> **Tmatherne said:**
> There is, sort of.  Run a live CD for a while until you have an idea as to how it will work.  If you don't like it, remove the CD and reboot. =]
 

Pah!  A live cd can give you a rough idea of how an os will work, but is no alternative to installing to your computer.  Like most users, I have a great many apps installed.  It's just not feasible to install all this stuff during a live session.  Yet how am I meant to discover if the new version of an app will work okay with my hardware?

Etc.

---

### Post by credobyte on 2009-08-10
If you don't feel the need to upgrade, don't. Upgrading is important only in case if you have encountered some hardware compatibility issues ( otherwise, while you can access repositories, use what you already have ).

---

### Post by andrew.46 on 2009-08-10
Hi vegmunky,

> **vegmunky said:**
> Is there a general reason to ever NOT to upgrade?  Like, is it generally better to stick with the LTS releases, or should I just upgrade to each new release?

I think there are 2 factors there:

[LIST=1]
[*]If your system is stable and does all you want of it *stay with it*.
[*]If you decide to upgrade don't do it on the exact release date, wait a little while until early teething problems have been addressed.
[/LIST]

Now if I could only follow my own advice :-).

Andrew

---

### Post by slakkie on 2009-08-10
Reasons not to upgrade:

* Stay at same version
* No need to upgrade for a longer period of time since LTS is supported till after intermediate releases become EOL. See [ this page](http://www.ubuntu.com/products/ubuntu/release-cycle) for a graphical picture of it.
* Want stability over new features
* You are afraid that an upgrade will break your system
* You don't feel the need to upgrade
* Wait for bugs to settle (be resolved) on newer packages so you can upgrade later on when everything is stable...

---

### Post by Hallvor on 2009-08-10
If it isn`t broken, don`t fix it!

There are so many other things you can do with your time.

---

### Post by mikechant on 2009-08-10
> Is there any chance to revert all things back after a disastrous upgrade?

You can use the partimage program (or similar partition backup utility) to make an exact copy of your root partition (and seperate /home partition if you've got one). Restoring from these backups should get you back to exactly where you were before the upgrade.

Or you can install the new release on a seperate partition so you can boot old or new releases, test the new release and copy/switch your /home over to the new release when you're happy. This method invovles more work (since you will have to redo any non-/home based customization on the new release)and needs extra disk space, but allows switching between the releases with only a reboot, so it's more convienient if the new release isn't usable for you or you need to check something on the old release etc.

---

### Post by red_spyder on 2009-08-31
So if I were to upgrade from my current OS (8.10) to Jaunty Jackalope going to System>Administration>Update Manager, would my programs like wine, Euler (a math program located in the repositories), ect. be erased? Would I be given back my customized desktop or would I have to start from cratch again?

---

