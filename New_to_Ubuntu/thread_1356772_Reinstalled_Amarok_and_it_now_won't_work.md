---
title: "Reinstalled Amarok and it now won't work"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-12-16
I was running Amarok 2.2.0 (which came installed with Kubuntu 9.10) but was having trouble ripping CDs.  I saw on the Amarok website that version 2.2.1 was available so I installed it from the Kubuntu backports repositories to see if that helped, but unfortunately the newer version seemed to introduce more bugs than it fixed.  Therefore, I removed the backports repositories, removed Amarok, and reinstalled from the normal repositories.  However, when I try to run Amarok I now get the message

> The Amarok collection database was created by a newer version of Amarok, and this version of Amarok cannot use it.

I tried

```
sudo aptitude purge amarok amarok-common amarok-utils
```

to try to remove every last trace of Amarok, then

```
sudo aptitude install amarok
```

again (the other two packages are added automatically as dependencies), but I still get the error message.

When installing from the backports, various libraries were upgraded (but I now don't know which ones they were, to downgrade them again).  Could this be the problem?  Either way, could someone help me fix this?

Thanks.

---

### Post by Dark_Stang on 2009-12-16
Open up a terminal. Run ```
ls -a
```
That will list all files and folders, including hidden ones, in your home folder. See if there is a folder called ".amarok". If there is, delete it with the following command ```
rm -R .amarok
```
This will delete all the configuration files for amarok and should get it working again. If the folder isn't there it may be in the ".kde" folder.

---

### Post by EssexEagle on 2009-12-16
Excellent, all fixed!

I'd already tried looking for a folder called *~/.amarok* but it didn't exist, but I hadn't thought of looking inside *.kde*
Turned out it was located at *~/.kde/share/apps/amarok*

Thanks for your help :-)

---

