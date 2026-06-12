---
title: "How to Disable 3D (Compiz) from Terminal (Karmic)"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by ylooF on 2009-12-28
Original post: [http://ubuntuforums.org/showthread.php?t=1365803&highlight=Ubuntu+(Karmic)+isn%27t+loading](http://ubuntuforums.org/showthread.php?t=1365803&highlight=Ubuntu+(Karmic)+isn%27t+loading)



Ok, I login to my Ubuntu 9.10 (Karmic), but it will not go past the loading screen...
I talked to a guy on the forums about what it could be, we tried a few things & then he told me to post a new Thread asking for someone to help me Disable 3D (Because it was not his area of expertise). So right now I am running off of Jaunty's Live CD (Because I upgraded from Jaunty to Karmic) and I'm looking for someone to help me Disable 3D Compiz from the Terminal. And if not, can someone help me backup my apps that I have installed so I can uninstall and Re-install?

---

### Post by sandyd on 2009-12-28
```

metacity --replace
```

or if your using kde...
Its in the control panel.

---

### Post by natravis on 2009-12-28
From [http://ubuntuforums.org/showthread.php?t=574092](http://ubuntuforums.org/showthread.php?t=574092), if you use ```
metacity --replace
```
you will turn off compiz and use metacity, another window manager. For your backup purposes (if that doesn't work), all of your apps should have a .deb file store at
[/var/cache/apt/archives](/var/cache/apt/archives)
unless something major changed of which I am unaware. If nothing else, you can put all installed packages into a file (as a list, not the actual debs) and I would back up your entire /home folder. See [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) for info on the list of packages. Both were found by first post googling ;-)

---

### Post by ylooF on 2009-12-28
I'd like to just do a clean install and add my apps back afterward. But under my Live CD I do not have full permissions, so I cannot copy my entire Home Folder...

Does anybody know a command that will allow me full permissions from a Live CD?
 So that I can backup my Home Folder.

---

### Post by ylooF on 2009-12-28
Ok, I figured it out. I'm create a separate Partition right now so that I can put my /Home folder on it. And then I'm going to Reinstall. Thanks anyway.

---

### Post by natravis on 2009-12-28
> **ylooF said:**
> Does anybody know a command that will allow me full permissions from a Live CD?
 So that I can backup my Home Folder.

AFAIK, you can use sudo or gksu commands from the LiveCD but I could be wrong.

---

