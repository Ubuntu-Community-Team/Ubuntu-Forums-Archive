---
title: "Uninstalling things"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Quake_Murphy on 2010-05-02
Hey guys, I had Ubuntu on a while back but ended up getting rid of it. I've now re-installed and to be honest I'm quite enjoying it, the problem was, and now is, I have no idea how the whole thing works, I mean I had a fairly advanced grasp of how windows worked but little to no Linux experience. I've installed a game called vegastrike, it doesn't work and I want it gone but it doesn't show up in the software centre or the synaptic package manager. It was installed with a .sh and said something about binaries in an extra little window. I've tried ./uninstall in the directory it's in but no luck. Am I good to just delete the folder or is something more technical required?

cheers

---

### Post by quixote on 2010-05-04
Yup, you can just delete the folder.  Any folders that it's made.  (Although be sure that's all you're doing!)  There may also be a hidden config directory under your home dir (i.e. /home/your-login-name/.vegastrike or whatever name they use).  You can see all dirs in the file manager (nautilus) either by hitting Ctrl-H or going to View > Show Hidden Files.  You can delete that too without hurting anything.  (The joys of a non-Registry based OS. :D)

---

### Post by Gone fishing on 2010-05-04
Quite often if you install using a script. If you look at the read me file they also have an uninstall script.

---

### Post by itisachilles on 2010-05-04
> **Gone fishing said:**
> Quite often if you install using a script. If you look at the read me file they also have an uninstall script.
yes but if it didnt work at all then the were probably terrible developers how wouldnt have the good sense to include a read-me at all

---

