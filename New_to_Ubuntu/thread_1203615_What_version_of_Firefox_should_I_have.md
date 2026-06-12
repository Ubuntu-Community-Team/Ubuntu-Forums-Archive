---
title: "What version of Firefox should I have?"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by oxf on 2009-07-03
Hi,

What version of Firefox do I have and what version should I have? About 10 day ago I downloaded and burned a new 9.04 Live CD and installed it.

It was my impression (wrongly perhaps?) that 9.04 came with FF 3.5? Now looking through Synaptic PKG MGR I see I have various FF 3.0 bits installed but anything to do with 3.5 is not installed. 

Finally to install 3.5 do I need to uninstall 3.0 ones first or will they be upgraded automatically if I install 3.5. Any reason why I should not install 3.5 at this point?

Thanks

---

### Post by ubudog on 2009-07-03
You should have 3.0.11 I think.

---

### Post by linux_lover69 on 2009-07-03
> Any reason why I should not install 3.5 at this point?



Well I have found firefox 3.5 is kinda buggy. For example when I try to play stuff on like Hulu and try to play full screen, it crashes. Its up to you if you think you should install it.

---

### Post by ubudog on 2009-07-03
I have 3.0.11 and it runs perfectly.

---

### Post by oxf on 2009-07-03
> **linux_lover69 said:**
> Well I have found firefox 3.5 is kinda buggy. For example when I try to play stuff on like Hulu and try to play full screen, it crashes. Its up to you if you think you should install it.

Thats one of the things I wmdered about! I know theres a way of checking the version but it escapes me right now.

---

### Post by oxf on 2009-07-03
> **ubudog said:**
> I have 3.0.11 and it runs perfectly.

Mine does too so maybe I should leave well alone for now!

Also what do all these packages mean? eg Branding, Dummy packages, etc etc. Is there a tutorial explaining this stuff?

---

### Post by lovinglinux on 2009-07-03
> **oxf said:**
> What version of Firefox do I have and what version should I have? About 10 day ago I downloaded and burned a new 9.04 Live CD and installed it.

It was my impression (wrongly perhaps?) that 9.04 came with FF 3.5? Now looking through Synaptic PKG MGR I see I have various FF 3.0 bits installed but anything to do with 3.5 is not installed. 

If your system is updated, then you have version 3.0.11. Whenever you need to check this open Firefox, click the "Help" menu and then "About Mozilla Firefox". It will show the version info. Most applications display version info the same way.

> **oxf said:**
> Finally to install 3.5 do I need to uninstall 3.0 ones first or will they be upgraded automatically if I install 3.5. Any reason why I should not install 3.5 at this point?

No. You don't need and you shouldn't uninstall firefox-3.0, because firefox-3.5 is installed side-by-side with it and copy your current profiles to another location. So, your Firefox 3.0 packages will not be updated automatically until the official 3.5 updates reaches the repositories. If you install the package firefox-3.5 from synaptic you will get the Beta version, while the final release is already on Mozilla web site or through alternative repositories. There are 3 methods of installing firefox 3.5 in my tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Scroll down to the "Installing Other Versions" section.

> **oxf said:**
> Any reason why I should not install 3.5 at this point?Thanks

Well, if you check my benchmarks you will see that Firefox 3.5 is much faster and responsive than 3.0.11. Since the packages are installed side-by-side, I would test the Beta version if I were you. Just install it through Synapti and open it through "Applications >> Internet >> Shiretoko Web Browser". You will still be able to use Firefox 3.0 and it won't be affected, so give it a go. If you like it, then you can follow the instructions on my tutorial to update to the final version or newer versions. You could also wait for updates on the official repository, then uninstall Shiretoko when Firefox 3.0.11 gets updated (if it will be).


> **linux_lover69 said:**
> Well I have found firefox 3.5 is kinda buggy. For example when I try to play stuff on like Hulu and try to play full screen, it crashes. Its up to you if you think you should install it.

> **oxf said:**
> Mine does too so maybe I should leave well alone for now!

Also what do all these packages mean? eg Branding, Dummy packages, etc etc. Is there a tutorial explaining this stuff?

To fix the fullscreen video issue visit [this post](http://ubuntuforums.org/showthread.php?p=7487421) and [this](http://ubuntuforums.org/showpost.php?p=7550250&postcount=21).

---

### Post by oxf on 2009-07-03
> **lovinglinux said:**
> If your system is updated, then you have version 3.0.11. Whenever you need to check this open Firefox, click the "Help" menu and then "About Mozilla Firefox". It will show the version info. Most applications display version info the same way.



No. You don't need and you shouldn't uninstall firefox-3.0, because firefox-3.5 is installed side-by-side with it and copy your current profiles to another location. So, your Firefox 3.0 packages will not be updated automatically until the official 3.5 updates reaches the repositories. If you install the package firefox-3.5 from synaptic you will get the Beta version, while the final release is already on Mozilla web site or through alternative repositories. There are 3 methods of installing firefox 3.5 in my tutorial [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567"). Scroll down to the "Firefox Alternatives & Newer Versions" section.



Well, if you check my benchmarks you will see that Firefox 3.5 is much faster and responsive than 3.0.11. Since the packages are installed side-by-side, I would test the Beta version if I were you. Just install it through Synapti and open it through "Applications >> Internet >> Shiretoko Web Browser". You will still be able to use Firefox 3.0 and it won't be affected, so give it a go. If you like it, then you can follow the instructions on my tutorial to update to the final version or newer versions. You could also wait for updates on the official repository, then uninstall Shiretoko when Firefox 3.0.11 gets updated (if it will be).






To fix the fullscreen video issue visit [this post]("http://ubuntuforums.org/showthread.php?p=7487421") and [this]("http://ubuntuforums.org/showpost.php?p=7550250&postcount=21").

Well it appears I have Version 3.08  installed right now so looks like I have some updating to do!

Thanks for the tutorial and info!

---

### Post by Sukotto on 2009-07-03
I have 3.5 on my vista laptop and it works perfect, tonight I am going to upgrade to 3.5 on my Ubuntu desktop.

---

### Post by kooldino on 2009-07-05
> **linux_lover69 said:**
> Well I have found firefox 3.5 is kinda buggy. For example when I try to play stuff on like Hulu and try to play full screen, it crashes. Its up to you if you think you should install it.

Ditto.  3.011 didn't do this.  I'm super annoyed.

---

### Post by kooldino on 2009-07-05
@lovinglinux - Thanks a ton.

---

### Post by lovinglinux on 2009-07-06
> **kooldino said:**
> Ditto.  3.011 didn't do this.  I'm super annoyed.

Check the lat line of post [#7](http://ubuntuforums.org/showpost.php?p=7557677&postcount=7) for solution links.

> **kooldino said:**
> @lovinglinux - Thanks a ton.

You are welcome.

---

