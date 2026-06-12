---
title: "Chrome opens unmaximized"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by josephellengar on 2010-06-01
Sorry about posting in the ABT forum.  I just figured it was the appropriate area for this thread.  Anyway, my google chrome always opens unmaximized (not minimized, it just takes up about 1/4 of the screen).  I tried adding the --start-maximized flag to the end of the launch command, but it didn't do anything.  Anybody know of a quick solution?  gnome, karmic, I think my window manager is metacity, I do have compiz running

---

### Post by lavinog on 2010-06-01
how did you install it?
Is it chrome or chromium?

---

### Post by josephellengar on 2010-06-01
> **lavinog said:**
> how did you install it?
Is it chrome or chromium?

It's chrome.  I installed it from the repository and this problem only showed up recently.  I'm not sure exactly when, but it might have been with Google's update to v5.0.x beta.

---

### Post by cbecker78 on 2010-06-01
[STRIKE]This may be a silly question, but is it maximized when you close it?  Often programs are set to default to the window spacing optimized when you last closed them.[/STRIKE]

If not, try finding the profile folder and setting the prefered sized manually.  Scroll down to the linux/unix section of the page below to see where that file should be:
[http://kb.mozillazine.org/Profile_folder_-_Firefox](http://kb.mozillazine.org/Profile_folder_-_Firefox)

[/STRIKE]

Edit: oops, I gave info for wrong browser.  Sorry, don't know much about chrome... but I'd bet there is a similar profile type folder somewhere

---

### Post by josephellengar on 2010-06-01
> **cbecker78 said:**
> [STRIKE]This may be a silly question, but is it maximized when you close it?  Often programs are set to default to the window spacing optimized when you last closed them.

If not, try finding the profile folder and setting the prefered sized manually.  Scroll down to the linux/unix section of the page below to see where that file should be:
[http://kb.mozillazine.org/Profile_folder_-_Firefox](http://kb.mozillazine.org/Profile_folder_-_Firefox)

[/STRIKE

Edit: oops, I gave info for wrong browser.  Sorry, don't know much about chrome... but I'd bet there is a similar profile type folder somewhere

It is always maximized when I close it.  I've tried all sorts of things- closing it when it is minimized, closing it when it is nearly fully maximized, closing when maximized, etc  And I actually have been searching for a "google" or "chrome" directory in my home directory for a while and there doesn't seem to be one there.  Strange.  And there is not an option in the browser options that regards this.

---

### Post by cbecker78 on 2010-06-02
Buggers... I never could get the silly strikethrough to work in my previous post.  Oh well.

I think the profile file used for chrome is in ~/.config/google-chrome.  So that would be in the hidden .config file in your home directory.  You need to use "control+H" to see that file.  Hope that helps some.

---

### Post by cbecker78 on 2010-06-02
look at post #8 in this forum thread from chrome forums:
[http://www.chromeboard.com/showthread.php?t=2016](http://www.chromeboard.com/showthread.php?t=2016)

If not, maybe some of the other posts on that site will be useful

---

### Post by lavinog on 2010-06-02
Does this problem exist with chromium?

---

### Post by josephellengar on 2010-06-02
> **cbecker78 said:**
> look at post #8 in this forum thread from chrome forums:
[http://www.chromeboard.com/showthread.php?t=2016](http://www.chromeboard.com/showthread.php?t=2016)

If not, maybe some of the other posts on that site will be useful

Bizarre solution, but it works.  For googlers out there: you exit using the wrench menu.  Thanks.  I've marked the thread solved.

---

