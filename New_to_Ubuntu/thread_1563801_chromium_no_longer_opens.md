---
title: "chromium no longer opens??"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-08-29
I have a problem with Chromium. I have been using it just fine, and then all of a sudden it won't open. I tried to re-install it, no luck. I tried to remove it completley, then put it back....nothing. Firefox opens fine, and I have not noticed anythign else acting funny. Kinda sucks, i was enjoying the speed.

---

### Post by Pollox on 2010-08-29
Does it give any error message when you run it from the terminal?  What version of chromium do you have installed?  If you're running the nightly build, have you tried a more stable version?

---

### Post by jtarin on 2010-08-29
>  **tried** to remove it completley, then put it back....nothing.Were you successful? ```
updatedb
```then ```
locate <nameoffile>
```to see if everthing is removed.In your /home/username/.config <a hidden file> there are some configs for chromium to be removed. Careful your bookmarks are there.Remove them before deleting the folder and any others "locate" finds. Then run "updatedb" again.

---

### Post by AndyP79 on 2010-08-29
> **Pollox said:**
> Does it give any error message when you run it from the terminal?  What version of chromium do you have installed?  If you're running the nightly build, have you tried a more stable version?

What do I write in the terminal to open it?

---

### Post by Pollox on 2010-08-30
> **AndyP79 said:**
> What do I write in the terminal to open it?

```
chromium-browser
```

---

### Post by AndyP79 on 2010-08-30
it just says segmentation fault..... i am guessing that is something wrong?

---

### Post by jtarin on 2010-08-30
> What version of chromium do you have installed? If you're running the nightly build, have you tried a more stable version?You were asked but did not answer.

---

### Post by AndyP79 on 2010-08-30
> **jtarin said:**
> You were asked but did not answer.

Sorry, I missed that somehow. I am using the daily builds, installedd from Ubuntu Tweak. How can I add a more stable version?

---

### Post by Pollox on 2010-08-30
> **AndyP79 said:**
> Sorry, I missed that somehow. I am using the daily builds, installedd from Ubuntu Tweak. How can I add a more stable version?

A stable version of chromium-browser is already in the Lucid repos.  To install it, remove chromium-browser, disable the chromium daily ppa (through Ubuntu tweak or software sources) and update your package list (you should be prompted to do so), and install chromium-browser again.

If you want a less stable version, but more stable than daily, check out [https://launchpad.net/chromium-browser](https://launchpad.net/chromium-browser) (there's stable, beta, dev, and daily).  This would be a good opportunity to learn how to add a ppa without using Ubuntu tweak, if you do not know how to do so already.

As a final note, you may want to be more careful adding third-party ppa's in the future, and avoid adding them unless necessary.  The daily-build ppa for chromium is designed for people who want to test the program for bugs, and don't mind that it might not work at all sometimes.

---

### Post by AndyP79 on 2010-08-30
> **Pollox said:**
> A stable version of chromium-browser is already in the Lucid repos.  To install it, remove chromium-browser, disable the chromium daily ppa (through Ubuntu tweak or software sources) and update your package list (you should be prompted to do so), and install chromium-browser again.

If you want a less stable version, but more stable than daily, check out [https://launchpad.net/chromium-browser](https://launchpad.net/chromium-browser) (there's stable, beta, dev, and daily).  This would be a good opportunity to learn how to add a ppa without using Ubuntu tweak, if you do not know how to do so already.

As a final note, you may want to be more careful adding third-party ppa's in the future, and avoid adding them unless necessary.  The daily-build ppa for chromium is designed for people who want to test the program for bugs, and don't mind that it might not work at all sometimes.

Cool, thanks for the help. I will check these out.

---

### Post by AndyP79 on 2010-08-30
Okay, so none of this helped. I have tried all the items suggested, even tried to add regular Chrome, and that won't even launch. So, I am stuck with Firefox. Is this something maybe to do with 10.04.1? I have just done a fresh install. Here is what I wonder. When things like this happen, and I just choose to ignore them and keep trucking cause nothing else is f'd up, will it effect things later? Speed performance or does the program sit there in a dormant state until it is purged?

---

### Post by jtarin on 2010-08-30
It's difficult to tell if it will affect things now or later. I'm running Chromium-5.0.375.125 (53311) Ubuntu 10.04 and have had no problems. Using the 2.6.32-21-generic Kernel. I would imagine your upgrade might possibly have something to do with it. Learn to upgrade wisely if at all.

---

### Post by Pollox on 2010-08-30
I am running both chrome stable and chromium unstable on an up-to-date 10.04 install (don't know what 10.04.1 that you refer to is, but I don't think that is a thing), so I can tell you that they do work.

It is difficult to tell what has gone wrong on your end.  My final guess is that one of the third party repositories you installed is causing an issue (i.e. a nonstable version of some library that chrome/chromium depend on).  You could open Synaptic, remove all the third-party repos and then uninstall local/obsolete packages, and then install chromium again.  This may or may not solve your problem and could cause other issues.

Another option is to do a fresh install and don't mess with Ubuntu Tweak (or at least its options for adding repos).

As to your question of what happens when you try to launch a program and it doesn't work, in this case you should not experience any additional issues since chromium is seg faulting (and therefore exiting).  You can always check your list of running programs via System Monitor to make sure it actually exited.  Rebooting will definitely remove this concern, and if you have not tried rebooting at all since you experienced this problem, I highly recommend you do so.

---

