---
title: "HELP! Computer, Network Icons not working! Volumes not visible!"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-10-27
Ok I have no idea what's going on. I am running Ubuntu 10.10 64-bit. Everything was working just fine.

Suddenly, I double-click the Computer icon on the desktop and it gives me an error saying **Could not display "computer:///". The file is of an unknown type.**

Did the same thing for the network icon too. When I go to the Places menu and Computer, it says **Nautilus cannot handle "computer" locations.** 

None of my volumes/partitions are listed either. When I go to /media, nothing is in there! What's happening? Please help!

---

### Post by seventhsamurai on 2010-10-27
Screengrab of error attached.

---

### Post by seventhsamurai on 2010-10-27
I am able to mount my volumes by going through disk utility. But they do not automount. Is this a nautilus issue?

---

### Post by seventhsamurai on 2010-10-27
*bump*

Come on somebody please help me!

---

### Post by seventhsamurai on 2010-10-27
Still no takers?

---

### Post by seventhsamurai on 2010-10-28
And the problem has been solved after much more googling. So if anyone else is having the same issue, here is the solution.

Basically, the issue happened because I installed the latest version of **glib** which was demanded by a video streaming software I was trying to install. It was throwing Nautilus off.

All you gotta do is go to the source directory from which you installed glib. If you deleted it, then download glib tarball again, extract it to the desktop, and as root, install it again with the usual procedure as outlined in the readme and install files.

Once you have completed the reinstall, just

```
sudo make uninstall
```

Restart Ubuntu and voila! You have everything back to normal. All volumes show up, and double clicking the icons works just like before!

---

