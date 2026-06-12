---
title: "where to get americas army for ubuntu?(deb file hopefully?)"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by djmh on 2009-05-23
i can not find out where to get americas army for linux.

[http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654](http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654)

i get an error when trying to download from there.

so if anyone knows where to get americas army in deb file,or really anything i guess i would appreciate it.

---

### Post by Yvan300 on 2009-05-23
I had your same problem, i had to spend all day googling just to find a mirror that worked for the linux download. I don't think i remember right but the new version of america's army is not supported by linux and you have to find the old one. But once you do, it's pretty easy to install.

P.S The installer is not a deb. file, i think it's a run. file

Cheers

---

### Post by lovinglinux on 2009-05-23
[http://aaotracker.com/downloaddb.php?file=123](http://aaotracker.com/downloaddb.php?file=123)

It's a run file. Keep in mind that it is version 2.5, since newer versions are not ported anymore.

---

### Post by ALIENDUDE5300 on 2009-05-23
You can set it up using the terminal. Try this:
Download and save the file to your home directory by browsing the website then try running the following in a terminal:
```
cd ~
sudo chmod +x armyops250linux.run
./armyops250linux.run
```

Tell me if that works. ;)

Edit: If the .run file is an installer, you may have to run it as root, so substitute the last line with:
```
sudo sh armyops250linux.run
```

---

### Post by Yvan300 on 2009-05-23
Hey i guess i was right about the whole not being supported anymore thing, but just in case your wondering sudo chmod +x armyops250linux.run makes the .run file executable as a program. YOu can do this in the GUI by right clicking the .run file, selecting properties, switching to the permissions tab and ticking off allow executing as a program your on your way to installing a game sponsered by the us government.

---

### Post by djmh on 2009-05-23
well im downlaoding the zip file from the site that one guy gave me...so ill let you know what happens once thats done...about a 2 hr download
thanks for the link man !

---

### Post by ALIENDUDE5300 on 2009-05-23
> **djmh said:**
> well im downlaoding the zip file from the site that one guy gave me...so ill let you know what happens once thats done...about a 2 hr download
thanks for the link man !

you shouldn't need a zip file if that .run file works properly. If you already downloaded it, I'd recommend trying that first.

---

### Post by llamakc on 2009-05-23
> **ALIENDUDE5300 said:**
> you shouldn't need a zip file if that .run file works properly. If you already downloaded it, I'd recommend trying that first.

The game IS archived in a zip file, which he is downloading.

---

### Post by lovinglinux on 2009-05-23
> **Yvan300 said:**
> Hey i guess i was right about the whole not being supported anymore thing, but just in case your wondering sudo chmod +x armyops250linux.run makes the .run file executable as a program. YOu can do this in the GUI by right clicking the .run file, selecting properties, switching to the permissions tab and ticking off allow executing as a program your on your way to installing a game sponsered by the us government.

It's not supported anymore, but 2.5 version should work. The problem is finding servers with enough players.

---

### Post by izizzle on 2009-05-25
I was thinking about trying it out as well. How many people still play v2.5?

---

