---
title: "New Karmic installed odd crash problem"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Zerxez on 2010-02-17
Hi,
I am having a couple problems with my new clean Karmic install.  I have a dual boot setup Karmic and Windows 7.  Both boot fine, but my Ubuntu install hard crashes (total screen freeze).  After 5-60 minutes.  If I keep using it trackpad input, installs, it seems to remain stable, but leave it alone for a few minutes (only in Ubuntu) it crashes.  I have installed all updates including the correct video drivers, I have turned off the screen saver and power/sleep options.
It is very unlikely it is a hardware problem, because I don't have issues when running Windows 7, and I ran the startup memory tests without issue.
Please help.

---

### Post by cariboo on 2010-02-17
I have a feeling your problem is probably video driver problem. Have you checked /var/log/Xorg.0.log to see if anything stands out. You can check the log by going to System->Administration->Log File Viewer, or:

```
cat /var/log/Xorg.0.log | less
```

---

### Post by kouter on 2010-02-17
laptop? maybe check power management/screen saver as the defaults on those are usually around 5 minutes default.  I know I had an issue somewhat like this on my laptop with fedora, never resolved it though... just went to ubuntu and it worked.

---

### Post by woodmaster on 2010-02-17
[http://ubuntuforums.org/showthread.php?t=1309015&page=15](http://ubuntuforums.org/showthread.php?t=1309015&page=15)

---

