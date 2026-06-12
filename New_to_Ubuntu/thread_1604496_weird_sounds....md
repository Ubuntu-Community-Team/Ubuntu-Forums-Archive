---
title: "weird sounds..."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by linux_noob0 on 2010-10-24
There are weird sounds coming from my computer (not from the speakers) when I try some action and it cannot be done... For example when editing some file in the terminal, when i reach the end of it and try to scroll down, it does that irritating sound like something's wrong... Any way to fix this?
Thanks!

---

### Post by ankspo71 on 2010-10-24
Hi,
Does your sound work good from the speakers?

I think maybe your 'system beep' is enabled, a sound that comes from the built in internal speaker, something that normally doesn't get used unless the speakers are not working (or not attached). Try what it says to do here to see if it works: [http://beyondteck.blogspot.com/2009/01/disable-annoying-system-beep-on-linux.html](http://beyondteck.blogspot.com/2009/01/disable-annoying-system-beep-on-linux.html) (note that you should use 'kdesudo kate' to do this, not 'sudo gedit' like the article used)

---

### Post by ankspo71 on 2010-10-24
Hi Again,
Also, make sure that the System Bell is disabled:
For Kubuntu 10.10:
Go to System Settings > Application and System Notifications > System Bell. Here you can turn off system bell (the beep noise instead of notifications).

In earlier versions of Kubuntu (before KDE4.5), it was located at System Settings > Sounds and Multimedia > System Bell. [http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#sound-systembell](http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#sound-systembell)

---

