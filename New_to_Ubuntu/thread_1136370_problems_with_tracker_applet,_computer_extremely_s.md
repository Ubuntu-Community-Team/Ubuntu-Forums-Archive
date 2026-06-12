---
title: "problems with tracker applet, computer extremely slow"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-04-25
ever since I upgraded from 8.10 intrepid to 9.04 jaunty, My computer has been much slower and every time I login to a session, I get this window titled "tracker applet" which says:

tracker
there was an error while performing indexing:
index corrupted

and there are three options: "reindex all contents", "cancel", and "ok".

"cancel" makes the same window pop up again, "ok" makes the same window pop up again, and "reindex all contents" brings up the same window also.

something tells me that the reason my computer is acting so slow is due to this issue.

---

### Post by Dirigo on 2009-04-25
I get this Tracker error message as well, but have not noticed any slowness.  I disabled Tracker in the Startup Options, to save time closing it myself, but I'd like to use it if a solution is available.

---

### Post by Didius Falco on 2009-04-25
Tracker was problematic for me, too when I first installed Ubuntu 8.10. Then I found this:

[http://fosswire.com/post/2009/4/enable-desktop-search-on-ubuntu/](http://fosswire.com/post/2009/4/enable-desktop-search-on-ubuntu/)

Watch the video (it's only a 2-3 minutes long) and follow what he does. 

It'll take a while the first time, and you'll want to just sit back (or go do something else for a few minutes, depending on how much it has to index) and relax until it's done with the initial index. After that, it only takes Tracker about 30 seconds or less to check for changes on my system, and it's 750 Gigs of files. 

Tracker has been working so well that I reinstalled it when I installed 9.04 to a separate partition, since they took it out as the default search application.

---

### Post by Dirigo on 2009-04-25
Thanks for the link.  I followed the video.  I guess I knew it anyways, but interestingly my version of the "Tracker Preferences" dialog has no option for "Enable Watching" under Indexing Options.  Hmmm...

---

### Post by Didius Falco on 2009-04-25
> **Dirigo said:**
> Thanks for the link.  I followed the video.  I guess I knew it anyways, but interestingly my version of the "Tracker Preferences" dialog has no option for "Enable Watching" under Indexing Options.  Hmmm...

What version are you using? I'm using V0.6.93.

---

### Post by Dirigo on 2009-04-25
Yes. Same version you have. Hopefully the screenshot attached...

---

### Post by Didius Falco on 2009-04-25
It's under the next tab, the "files" tab.

---

### Post by Dirigo on 2009-04-25
Ah. I see it now and it's checked.  I still get the error described above...

---

### Post by Didius Falco on 2009-04-25
I'd try uninstalling it completely from Synaptic and then reinstalling it.

Either that or use the new default search, but I like tracker better, now that I know how to set it up.

---

### Post by Dirigo on 2009-04-25
Tried Uninstall/Reinstall.  Still no joy.  Thanks for the suggestions, though.

---

### Post by 311005901 on 2009-04-26
I got the same problem since updating from Intrepid to Jaunty.
[This post]("http://ubuntuforums.org/showthread.php?t=1135040") says to run ```
rm -rfv ~/.cache/tracker
```

This fixed the problem for me.

---

### Post by Dirigo on 2009-04-26
Thanks, 311005901!!  That did the trick exactly!  Much appreciated.

---

