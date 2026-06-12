---
title: "Orange tint in background of youtube videos?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Sephiroth9000 on 2011-03-02
I am using Ubuntu 10.01 and just randomly today, youtube videos started playing with this random orangish tint in the background. How do i remove this? Is it a problem with adobe flash player?

Pic: [http://img809.imageshack.us/i/orangel.png/](http://img809.imageshack.us/i/orangel.png/)

---

### Post by Ksho on 2011-03-02
I have the same problem. It happened after today's updates.
Included kernel and FF updates.

ETA:
It's a Firefox problem. Opera and Chrome are working fine.

Ubuntu 10.04 LTS

ETA2:
Only happens on youtube. Other video sites are Ok.

---

### Post by Dago96 on 2011-03-02
I'm seeing this as well (running Lucid): Opera, Chrome, Firefox all show the same problem since yesterday's update.

---

### Post by nyser on 2011-03-03
I have the same problem. It only seems to be happening on the youtube website, but does not affect youtube videos embedded elsewhere. Other video sites (like dailymotion) work fine.

I have the problem on both firefox and chromium. I reinstalled Adobe flash and it played one video without the orange, then went right back to orange tinting all YT videos.

---

### Post by a1ek5ant3ri on 2011-03-03
I have noticed the same problem.  Clearing the cookies fixes it for one video, then it goes back to being orange.

---

### Post by nyser on 2011-03-03
I tried the solution found here: [http://www.google.co.nz/support/forum/p/youtube/thread?tid=776b91a8fb990410&hl=en](http://www.google.co.nz/support/forum/p/youtube/thread?tid=776b91a8fb990410&hl=en)
It worked for me as a temporary fix, but blocking YouTube cookies makes commenting (and any other logged-in activity) a pain. I'm still hoping for a permanent fix

---

### Post by Ksho on 2011-03-03
Moar Information:
[http://www.google.com/support/forum/p/youtube/thread?tid=776b91a8fb990410&hl=en](http://www.google.com/support/forum/p/youtube/thread?tid=776b91a8fb990410&hl=en)

Bug Report:
[https://bugzilla.mozilla.org/show_bug.cgi?id=638337](https://bugzilla.mozilla.org/show_bug.cgi?id=638337)

---

### Post by NCLI on 2011-03-03
Please press alt+F2, write "ubuntu-bug firefox", then follow the guide to report this bug to Ubuntu as well.

---

### Post by jfloydb on 2011-03-03
Does anyone think that Forcing an older version of Flash (through the Synaptic Package Manager) might help?

---

### Post by Paddy Landau on 2011-03-04
See this thread:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

---

### Post by logruszed on 2011-03-04
> **Paddy Landau said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)


The fix on the last page of this thread worked for me. Short-story: disable hardware acceleration in Flash settings.

---

### Post by jfloydb on 2011-03-04
The fix, for me, was to go to the Synaptic Package Manager, choose the flashplugin-installer 10.2, goto the Package menu, click Force Version..., and "downgrade" to Flash 10.0; after which, I clicked Lock Version, so it will not "upgrade" with the next updates. That's it; everything is working fine.

I know many Windows users who have never upgraded their Flash plugin, and they never seem to have any problems. For all they (or I) know, they are using Flash version 1, or 5, or whatever. So I'm not concerned about using an older Flash plugin. I might "upgrade" when the current problems are fixed.

---

### Post by stmiller on 2011-03-05
Here some more info:

[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

