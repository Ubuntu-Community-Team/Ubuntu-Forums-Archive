---
title: "No desktop, no panel, just a black screen"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-09-29
As described in [this thread]("http://ubuntuforums.org/showthread.php?t=1274419"), to which no-one was able to respond, I had a problem with Kubuntu 9.04 - *viz.* although I could run programs, I had no desktop (i.e. no wallpaper and no icons), no panel, and no title bar on windows.

I thought the problem might have been because I installed the Kubuntu backports repos and kind of part-upgraded to KDE 4.3.  I've now upgraded fully to 4.3 from the command line, which appears to have worked because I have a new login screen.  But I still have no desktop and no panel.  I do now have title bars on my windows though, and Kubuntu is semi-usable in that I can press Alt+F2, run Konsole, and then run programs from there (I have to Alt+Tab between windows, since obviously I have no task manager widget without a panel).

Clearly KDE is broken in some way - how can I fix it?

---

### Post by Hospadar on 2009-09-29
I upgraded to kde 4.3 and it totally Effed up my system.  I eventually just re-installed the whole system using an ubuntu server disk, then added the 4.3 ppa, then installed KDE.

Maybe if you try totally removing KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
then re-installing kubuntu-desktop, you can get things working.

---

### Post by EssexEagle on 2009-09-29
> **Hospadar said:**
> I upgraded to kde 4.3 and it totally Effed up my system.  I eventually just re-installed the whole system using an ubuntu server disk, then added the 4.3 ppa, then installed KDE.

Maybe if you try totally removing KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
then re-installing kubuntu-desktop, you can get things working.

If I remove KDE as described on the Psychocats tutorial what will happen, since I don't have Gnome installed?  I'll have no desktop environment at all, so would I just have to boot to a command line rather than GUI, from which I could then reinstall KDE?

---

