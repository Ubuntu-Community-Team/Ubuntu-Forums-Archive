---
title: "the flash plugin was blocked because it is out of date"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2011-04-07
*title*

Happens in Chromium.  I went to update it, downloaded the latest version, and put it in my plugins folder for both chromium-browser and mozilla and mozilla-firefox to be sure.

Still having the same issue.  Any ideas?

---

### Post by tgm4883 on 2011-04-07
> **x C0MMAND0 x said:**
> *title*

Happens in Chromium.  I went to update it, downloaded the latest version, and put it in my plugins folder for both chromium-browser and mozilla and mozilla-firefox to be sure.

Still having the same issue.  Any ideas?

Did you restart chromium?

---

### Post by x C0MMAND0 x on 2011-04-07
> **tgm4883 said:**
> Did you restart chromium?

Yes I did.  I know there is an extra switch that I can add to allow it run with the "non-updated plugin" (even though it *should* be up date, but that is a work-around and defeats the purpose of the update.

---

### Post by 5149.5 on 2011-04-07
For firefox you could try the flashaid plugin and run it using the preference button in the plugin.

---

### Post by rburkartjo on 2011-04-07
yes the flash aid ext if you install in ff will also help in chromium. you will get the message that flash player is out of date and give you the option to run this one time. i also do it and have no problem with chromium. are you using chromium on a 64 bit system that is the problem. and i still can figure out how to get the new flash player square to work in chromium.

---

### Post by x C0MMAND0 x on 2011-04-10
> **rburkartjo said:**
> yes the flash aid ext if you install in ff will also help in chromium. you will get the message that flash player is out of date and give you the option to run this one time. i also do it and have no problem with chromium. are you using chromium on a 64 bit system that is the problem. and i still can figure out how to get the new flash player square to work in chromium.

Yes I am on a 64 bit system, and I tried the 64-bit alpha plugin provided from Adobe Labs and that did not solve the issue either.

---

### Post by bkline on 2011-12-07
> **x C0MMAND0 x said:**
> Yes I am on a 64 bit system, and I tried the 64-bit alpha plugin provided from Adobe Labs and that did not solve the issue either.

I added "--allow-outdated-plugins" to the command for launching Chrome.  Seems to solve the problem some of the time.  Those times when it doesn't may be only happening when Xubuntu restores a previous session, dropping the custom launch command string (hard to imagine why it would do that).  Haven't done enough experimenting to verify conclusively that this condition is the only one in which I still see the problem.

I certainly hope the day comes soon when the major producers of software realize that most of the machines in use today are 64-bit.  Sigh.

---

