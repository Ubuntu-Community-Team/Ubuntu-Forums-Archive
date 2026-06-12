---
title: "Flash issues"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Servb0t on 2010-09-30
Hello,

I'm pretty new to ubuntu(hence the beginner talk) and am having issues with flash.

I installed Swfdec 0.8.2 for firefox and now when I want to watch videos in youtube, I can only watch Vevo videos(the other videos simply won't play back, black screen). Is there an easy solution or fix for this?

I would greatly appreciate some help if possible. I apologize in advance if I didn't include some critical piece of information(like I said, new to ubuntu :D), just let me know and I'll do my best to find that info.

Thank you in advance

---

### Post by catlover2 on 2010-09-30
uninstall swfdec,
and install adobe flash player, as swfdec doesn't work very well

---

### Post by Servb0t on 2010-09-30
I actually have adobe flash installed (I don't know why I have both), but I don't actually know how to uninstall swfdec :X

---

### Post by catlover2 on 2010-09-30
system>administration>synaptic package manager.

search for "swfdec"

right click on gstreamer0.8-swfdec check "Mark for removal"

and say apply.

---

### Post by sikander3786 on 2010-09-30
For possible issues with flash, see here. (courtesy of forum member lovinglinux)

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Servb0t on 2010-09-30
Uninstalling swfdec fixed it. thank you so much for the help!

---

### Post by catlover2 on 2010-09-30
your welcome!!

---

### Post by beew on 2010-09-30
You can watch Youtube videos without flash (and without web browser) by using minitube. The advantage is that it uses quite a bit less cpu resources. You may want to give it a try if flash hogging cpu is a concern to you.

There is a very old version in the Ubuntu repo, to get an up to date version you can add this ppa to your sources list and then install it from synaptic.

[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/~nilarimogard/+archive/webupd8")

---

