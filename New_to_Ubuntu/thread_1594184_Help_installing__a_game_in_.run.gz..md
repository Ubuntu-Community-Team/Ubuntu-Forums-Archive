---
title: "Help installing  a game in .run.gz."
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Laxman_prodigy on 2010-10-12
Hi.

I just downloaded from the site of Truecombatelite a .run.gz file that I cannot install in 10.10.

I tried these suggestions on googling:

```
daulat@Softspace:~/Downloads$ gunzip TrueCombatElite_v049_Linux.run.gz 

gzip: TrueCombatElite_v049_Linux.run.gz: not in gzip format
```

```
daulat@Softspace:~/Downloads$ tar zxf TrueCombatElite_v049_Linux.run.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
daulat@Softspace:~/Downloads$ 
```


What to do now?

---

### Post by Ctrl-Alt-F1 on 2010-10-12
Have you tried extracting it using file roller?  It's a built in GUI tool.

Just right click the file and choose "extract here".

---

### Post by Laxman_prodigy on 2010-10-12
> **Ctrl-Alt-F1 said:**
> Have you tried extracting it using file roller?  It's a built in GUI tool.

Just right click the file and choose "extract here".


Hi.

When I right click and click on "extract here", it returns a window which says, " not in gzip format:.....".

---

### Post by Ctrl-Alt-F1 on 2010-10-12
Interesting.  Maybe just "sudo ./TrueCombatElite_v049_Linux.run.gz"
from the directory that it's in.

---

### Post by Laxman_prodigy on 2010-10-12
> **Ctrl-Alt-F1 said:**
> Interesting.  Maybe just "sudo ./TrueCombatElite_v049_Linux.run.gz"
from the directory that it's in.
Here is what it says:
```
daulat@Softspace:~$ cd Downloads
daulat@Softspace:~/Downloads$ ls
Doom_3_for_Linux_FULL.3965933.TPB.torrent
NVIDIA-Linux-x86_64-256.53.run
TrueCombatElite_v049_Linux.run.gz
World_Of_Goo_-_Linux_Version.4735059.TPB.torrent
WorldOfGoo.tar.bz2.part
daulat@Softspace:~/Downloads$ sudo ./TrueCombatElite_v049_Linux.run.gz
[sudo] password for daulat: 
sudo: ./TrueCombatElite_v049_Linux.run.gz: command not found
daulat@Softspace:~/Downloads$ 
```




Here is a screenshot of what happened when I used file roller.

---

### Post by Ctrl-Alt-F1 on 2010-10-12
That's bizarre.  I'm wondering if the file is corrupt.

---

### Post by gandaran on 2010-10-12
> TrueCombatElite_v049_Linux.run.gz
this package doesn't look right! try adding .tar to the extension package format then try extracting it
```
TrueCombatElite_v049_Linux.run.tar.gz
```

---

### Post by Script Warlock on 2010-12-24
try the ftp..

[ftp://ftp.kraft-s.ru/pub/games/et/tcetest049.zip](ftp://ftp.kraft-s.ru/pub/games/et/tcetest049.zip)

---

### Post by Jim_in_Omaha on 2010-12-27
Same problem here.

10.10 64

Trying to install True Combat Elite.

---

### Post by Jim_in_Omaha on 2010-12-27
I figured it out.

Set the permissions to executable then,

It needs to be ran with sudo sh ./NAME OF FILE

Read this
[http://ubuntuforums.org/showthread.php?t=1246836&highlight=true+combat+elite]("http://ubuntuforums.org/showthread.php?t=1246836&highlight=true+combat+elite")

---

