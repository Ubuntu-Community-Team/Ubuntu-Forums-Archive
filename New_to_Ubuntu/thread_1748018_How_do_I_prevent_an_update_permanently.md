---
title: "How do I prevent an update permanently?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by NJames99 on 2011-05-03
I don't want the Chromium update as long this is the case > With this version (like with 10.0.648.204), you may notice that the saved
  passwords are no longer accessible in Chromium.
So the question is, how can I get Update Manager to stop bringing it up?

...Ubuntu 10.04

---

### Post by EGamerHDK on 2011-05-03
There may be some way to code an update from not showing but, I believe Ubuntu finds this as a security update because I went into the update manager, selected settings and unchecked "Important Security Updates" and the update went away. Either way I guess you could always just not install it, but I could see how this could annoy people. I do know that the option to "hide update" is available in windows, but then again, windows does not provide software updates for different programs.

---

### Post by plucky on 2011-05-03
> **NJames99 said:**
> I don't want the Chromium update as long this is the case 
So the question is, how can I get Update Manager to stop bringing it up?

...Ubuntu 10.04

You could try locking the package.

Open Synaptic Package Manager and search for the package you would like to keep and select it.Then navigate to **Package** and select "Lock Version".

See [Pinning Howto](https://help.ubuntu.com/community/PinningHowto)

Never tried this,so can't say if it will work.

Good Luck

---

### Post by Paqman on 2011-05-03
Locking updates in a browser is potentially a bit dangerous. You need to be getting security updates. If you do lock it in Synaptic then make sure you keep a close watch on that one issue, and as soon as it's resolved unlock the package.

Personally i'd advise not locking it. Chromium updates pretty often, you're bound to get the bug fixed soon enough without missing out on all the other bugfixes and improvements.

If you want a more stable browser than Chromium, consider switching to Chrome.

---

