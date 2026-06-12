---
title: "Ubuntu-Tweak Daemon Problem"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-07-30
I like to use Ubuntu-Tweak to do various stuff on my system, but for the past couple of days I've encountered some odd problems.

When I start it, I'm getting the following error alert:
```
The daemon of Ubuntu Tweak doesn't start correctly, that means some advanced features may not work.
If you want to help our developers to debug this problem, try to run "sudo ubuntu-tweak-daemon" under terminal.
```

But when I open Terminal and enter "sudo ubuntu-tweak-daemon" (and of course my sudo password), nothing whatsoever happens.

The next error alert is:
```
Warning

It is highly recommend to enable the stable source of Ubuntu Tweak to get security and normal updates.
If you don't enable the source, you will need to update manually.

Would you like to enable the stable source?
```

Well, even though I know I've got the stable source of Ubuntu-Tweak enabled in my software sources, I click the Yes button.

Then I try to do some stuff, but it seems that anything that needs sudo privileges is completely impossible.

Anyone got any ideas?

I'm using 32-bit karmic, btw.

---

### Post by j7%&lt;RmUg on 2010-07-30
Could be a bug in the karmic version of Ubuntu Tweak, assuming you know how to use PPA's:

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by Roger Allott on 2010-07-30
> **nisshh said:**
> Could be a bug in the karmic version of Ubuntu Tweak, assuming you know how to use PPA's:

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

Well, that's the repository that I already had, isn't it? I added it again and, as one might expect, I got this error message when I ran the apt-get update command:
```
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
```

---

### Post by k3lt01 on 2010-07-30
Remove the source from your list and allow your software sources to refresh and update itself. Reboot your machine and then add the source back to your list, again allow it to refresh and update itself.

You may need to remove UT as well but take it one step at a time and just work on the source first up.

---

### Post by Roger Allott on 2010-07-31
> **k3lt01 said:**
> Remove the source from your list and allow your software sources to refresh and update itself. Reboot your machine and then add the source back to your list, again allow it to refresh and update itself.

You may need to remove UT as well but take it one step at a time and just work on the source first up.

Thanks. I just did exactly that, including a complete removal of Ubuntu-Tweak, removal of the tualatrix ppa from sources, reboot, add tualatrix ppa to sources, install Ubuntu-Tweak.

I then ran Ubuntu-Tweak, and got exactly the same situation that I had at the start of this thread.

---

### Post by k3lt01 on 2010-07-31
When you removed UT did you "Mark for Removal" did you "Mark for Complete Removal"? Mark for Complete Removal removes everything directly associated with it such as config files etc, while Mark for Removal will leave configs in place.

---

### Post by Roger Allott on 2010-07-31
> **k3lt01 said:**
> When you removed UT did you "Mark for Removal" did you "Mark for Complete Removal"? Mark for Complete Removal removes everything directly associated with it such as config files etc, while Mark for Removal will leave configs in place.

I marked for complete removal.

---

### Post by k3lt01 on 2010-07-31
Have you tried removing via terminal? If yes what command did you use?
```
sudo apt-get purge [package name]
```

If everything else in Synaptic and/or apt-aptitude works as it should (i.e. removals and installations) I'd also be popping on over to the UT forum and asking them what the go is.

---

### Post by Roger Allott on 2010-07-31
> **k3lt01 said:**
> Have you tried removing via terminal? If yes what command did you use?
```
sudo apt-get purge [package name]
```

If everything else in Synaptic and/or apt-aptitude works as it should (i.e. removals and installations) I'd also be popping on over to the UT forum and asking them what the go is.

I removed it via Synaptic, not Terminal. It all seemed to work as usual.

There have been some odd things happening to my system recently though, such as some icons changing on my main panel. Also, the number of packages suggested by Update Manager has been unusually low for the past few days. I think the last time there was anything in the list at all was Wednesday, which is a bit weird as there ought to be at least one per day from the Chromium browser repository.

---

### Post by imjafo on 2010-07-31
Roger: I had the same problem with 64 bit 9.10 (Ultimate Edition). I  removed UT 5.4.1 with synaptic (complete removal). I went to the launchpad page for UT and downloaded version 5.2.1, installed it and pinned the version in synaptic.  I then rebooted and it seems to have cured the problem. I also made sure that the testing (unstable) version was not checked as a source in UT. All seems to be working fine now.
I hope this helps.

---

### Post by soldier1st on 2010-08-03
also did you try to upgrade to Lucid lynx 10.04?

---

### Post by sosaudio1 on 2010-08-04
> **imjafo said:**
> Roger: I had the same problem with 64 bit 9.10 (Ultimate Edition). I  removed UT 5.4.1 with synaptic (complete removal). I went to the launchpad page for UT and downloaded version 5.2.1, installed it and pinned the version in synaptic.  I then rebooted and it seems to have cured the problem. I also made sure that the testing (unstable) version was not checked as a source in UT. All seems to be working fine now.
I hope this helps.

I am there with everyone with problems with this daemon...I am using Linux Mint 8 and I am running UT 5.4.1 which is the one right before 5.5. It is running fine on both of my boxes. Something has changed between the two versions....

---

### Post by frogotronic on 2010-08-05
I also have this problem and downgraded to the 0.5.1 version from getadeb.

Seems to working ok.

- CH

---

### Post by Roger Allott on 2010-08-22
> **cement_head said:**
> I also have this problem and downgraded to the 0.5.1 version from getadeb.

Seems to working ok.

- CH

I've just done exactly that, but I've still got exactly the same problem as I had before with 0.5.5.

---

