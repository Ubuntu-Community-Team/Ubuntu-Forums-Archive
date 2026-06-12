---
title: "SUDO and AIX Installation"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Thunderchild001 on 2009-09-09
Hello all. I am new to sudo and am having a hell of a time getting it to work on my system. Particulars:
 
AIX 6.1
 
Downloaded the PMR (binaries) sudo-1.6.9p15-2noldap.aix5.2.ppc.rpm.
 
These are the binaries that don't require installation, only configuration.
I cannot get past this point. I don't see the config.h I am supposed to see. can someone please help me with this install so I can get this up and running?
 
Thanks in advance.

---

### Post by Excedio on 2009-09-09
You are trying to install sudo? It is not pre-installed?
 
Open a terminal and see if
```
sudo apt-get moo
```
does anything

---

### Post by Thunderchild001 on 2009-09-09
I did that and this is the reply:
 
[B](/opt/freeware/bin)> sudo apt-get moo
sudo: apt-get: command not found
[/B]
I am in the directory where the command is found.

---

### Post by Thunderchild001 on 2009-09-09
OK I changed the permissions. They were wrong. Now I get this message:
 
(/home/ywilson)> sudo root
sudo: must be setuid root
 
We don't have a root group on our systems. Could this be an issue?

---

### Post by cariboo on 2009-09-09
You have to convert the rpm to a deb using alien. Alien is in the repositories: the command you would use will look something like this:

```
alien -d sudo-1.6.9p15-2noldap.aix5.2.ppc.rpm.
```

Just a note, the above package is for a PPC cpu based computer, so it will not run on a system with an Intel or AMD cpu

Edit: I just read the rest of the thread while adding this post, I take it you aren't running Ubuntu, so the above info may not help.

---

### Post by Thunderchild001 on 2009-09-09
No it is an IBM AIX system. We aren't running ubuntu. Is anyone familiar with this? Thanks though!!

---

### Post by oldos2er on 2009-09-09
> **Thunderchild001 said:**
> No it is an IBM AIX system. We aren't running ubuntu. Is anyone familiar with this? Thanks though!!

 You might want to try IBM for help.

---

