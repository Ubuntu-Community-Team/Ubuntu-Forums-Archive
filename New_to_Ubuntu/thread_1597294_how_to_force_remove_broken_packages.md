---
title: "how to force remove broken packages"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by beew on 2010-10-15
I just installed Lyx from the Maverick repo, the package texlive-pstrick-doc somehow "got stuck". It is marked for upgraded but it can't upgrade, but I can neither remove it nor pin it. When I try to remove it,  dpkg says it is in a bad state of inconsistency and need to be reintalled before removal. But when I try to reinstall it it will get stuck with a warning "filelist file for the package missing" and the system would struggle and then freeze.

I tried to lock the version, but whenever I try to install something Synaptic (or apt-get if I use the terminal) would automatically try to upgrade the package and the system eventually would get frozen as a result.

I need to somehow get rid of the package, please help.

This,--broken packages in the official repos,-- seem to happen quite a bit in Maverick, I have done a clean installation before because of another package getting stuck like this (from eclipse I think). That has never happened in Lucid.

---

### Post by NightwishFan on 2010-10-15
You can force remove it but I would not recommend it. Seeing the output of reinstalling it from a terminal would help unless it freezes the system.

This is to force remove, however I would wait until it can be "installed fully" to do it.
```
sudo dpkg --force-all -P texlive-pstrick-doc
```

---

### Post by NightwishFan on 2010-10-15
Sorry corrected the command above.

---

### Post by beew on 2010-10-15
> **NightwishFan said:**
> You can force remove it but I would not recommend it. Seeing the output of reinstalling it from a terminal would help unless it freezes the system.

This is to force remove, however I would wait until it can be "installed fully" to do it.
```
sudo dpkg --force-all -P texlive-pstrick-doc
```

It doesn't work, it says textlive-pstrick-doc is not installed??!!

When and how is it going to be installed fully?

---

### Post by NightwishFan on 2010-10-15
Give me the output of installing it with:
```
sudo apt-get -f install texlive-pstricks-doc
```

EDIT: Darn it i forgot the S above pstricks.. ;/ This will force remove it.

Use ```
sudo dpkg --force-all -P texlive-pstricks-doc
```

---

### Post by beew on 2010-10-15
Ok, I just fixed it but it is probably not the most elegant approach, I have been asked to upgrade to the same version as the one that is apparently installed but every time I try installing the system struggles and freezes so i think may be the package in the repo is broken. 

So I added the Lucid repo to my sources list and downgraded the package, then I managed to remove it successfully.

But thanks for the help. I am sure it will be useful in the future. I have started downgrading when I saw your reply so I couldn't have tried your method.

---

### Post by NightwishFan on 2010-10-15
As long as it works my friend, and in a safe way.

---

### Post by Calculon64 on 2011-11-28
The force remove instructions for this was great help.  Thank you so much.

---

