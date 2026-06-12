---
title: "Upgrade from Karmic Not Exactly Right"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by dmaxel on 2010-05-02
Hi everyone,

I tried upgrading my laptop from Karmic to Lucid yesterday and for the most part it worked fairly well. However, two main things that I saw that went wrong were that the icon on the top panel for Firefox (not inside the menu) had a red X and that all the windows didn't have a border, so no way to close out of them, move them, etc., and it looks just plain stupid without the border (also suggesting something is broken). So I ended up reinstalling Lucid from scratch, and now it works just fine. However, I have a desktop that is also running Karmic, and I cannot afford for that upgrade to go wrong. Any tips to get the upgrade to go right?

---

### Post by nhasian on 2010-05-02
i dont think it was a big problem.  you could have just recreated the firefox shortcut on your taskbar and went to appearance and chosen the default theme to fix your other issue.

---

### Post by wekebu on 2010-05-03
This problem is being reported in different threads because we all describe it differently.  Visually, what happens is any open application window covers up the top menu panel and the open window can NOT be moved or resized.  You have to do Alt F for File menu and Quit Firefox.

I have a temporary fix:  Go into System> Preferences> Appearance> Visual Effects Tab.  Your setting is probably at None.  Change it to Normal or Extra.  This will give you back your Close, Minimize, Maximise options and give you a border around the window.

When you reboot, this setting disappears.  It's my understanding tht there is something in the Home folder causing a prob.  Keep searching, but this will atleast allow you to use Lucid. (sorry for mispellings)

---

### Post by dmaxel on 2010-05-03
OK, so I went ahead and upgraded my desktop to Lucid as well, and everything is good except for one problem...

I turn on my system, boot up, and during the boot splash a message shows up that says ```
An error occurred while mounting /proc/bus/usb

Press S to skip mounting or M for manual recovery
```Help? I can press S to skip mounting and everything *seems* to work fine, but I don't want any errors to appear whether visible or hidden, nor do I constantly want to press S during boot.

---

### Post by nhasian on 2010-05-03
looks like a solution for your usb problem is here:

[http://ubuntuforums.org/showthread.php?t=1468486](http://ubuntuforums.org/showthread.php?t=1468486)

---

### Post by dmaxel on 2010-05-03
Works great now. Thanks!

---

