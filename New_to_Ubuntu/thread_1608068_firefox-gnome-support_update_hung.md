---
title: "firefox-gnome-support update hung"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Tighearna on 2010-10-28
I was updating via the update manager.
The update hung.
The window in the update manager states that it is "Unpacking replacement firefox-gnome-support ..."
It's said that for the last 3 hours and hasn't gone any further.

I opened a terminal and ran ```
sudo apt-get update; sudo apt-get upgrade
```
It updates sources but then is unable to get a lock and asks if another process is using it.

What do I do now?

Thanks,
Tighearna

---

### Post by ajgreeny on 2010-10-28
That is because you still have update-manager running, I expect, and only one application using apt can run at any time.

Shutdown update-manager and try the commands again, that may work.

---

### Post by Tighearna on 2010-10-28
Right, I appologize, I forgot to mention.
I tried that. :(
I was however able to reboot and that let me access a terminal and was able to upgrade.
I know that's not what I'm suppose to do but it seems to have worked.

Ran
```
sudo apt-get update; sudo apt-get upgrade
```
then ran
```
sudo apt-get autoclean
```

Seems to have worked

---

