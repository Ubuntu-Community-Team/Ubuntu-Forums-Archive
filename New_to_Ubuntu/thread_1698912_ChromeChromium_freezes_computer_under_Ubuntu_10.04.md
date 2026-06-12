---
title: "Chrome/Chromium freezes computer under Ubuntu 10.04."
date: 2011-03-02
forum: New to Ubuntu
---

### Post by eurekabru on 2011-03-02
Hello,

Until last night I was running chrome without any problems until I clicked on a link in Empathy and it froze my computer. I made nothing of it, tried it again today and every time i click on a link my computer freezes. I have tried in both Empathy and Pidgin and both crash. At some points the computer crashes just by opening Chrome or by simply closing it. Chromium does the same. I have tried removing Chrome through Synaptics and reinstalling and the problem persists. Before I reinstalled I tried disabling all the extensions and it did not make a difference. I have now removed both Chrome and Chromium through Synaptics and Firefox has worked flawlessly. 

I am running Ubuntu 10.04. Ubuntu updated ''stuff'' through Update manager twice in the last two/three days. 

Googling didn't offer much other than disabling the extensions.

I'd much rather go back to Chrome. Has anyone experienced something similar lately?

Thanks 
eurekabru

---

### Post by eurekabru on 2011-03-03
I think I solved my problem.

It was the Network manager applet that was the issue. I installed Wicd and removed Network manager and it now seems to be working fine.

This bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871)

led me to this one:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130)

Hope this helps someone.
eurekabru

---

### Post by eurekabru on 2011-03-04
Well it turns out my fix was only temporary. The computer froze again when trying to open an external link.

Any ideas?

---

### Post by gandaran on 2011-03-05
> **eurekabru said:**
> Well it turns out my fix was only temporary. The computer froze again when trying to open an external link.

Any ideas?
I also use chromium and thought it was responsible for the freezes during the last two days but now I think it was the last kernel update, I am booting from the older kernel now and still no freezes today so if you still have the old kernel boot it and see if the problem go's away.

---

### Post by eurekabru on 2011-03-06
Thanks. This seems to have solved my problem.

---

