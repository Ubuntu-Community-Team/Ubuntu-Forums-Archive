---
title: "I need information ASAP"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by princennamdi on 2010-06-23
i was running ubuntu 9.04 a while ago, but i just installed version 10 in another partition because i couldnt do the online upgrade and the cd upgrade. 

my question is, i do not want to re-download any of the softwares i had in version 9, is there any way to copy my softwares to the new installation? i mean is there any folder that needs to be copied, and then my softwares will be back?:confused::confused:

---

### Post by princennamdi on 2010-06-23
i was running ubuntu 9.04 a while ago, but i just installed version 10 in another partition because i couldnt do the online upgrade and the cd upgrade. 

my question is, i do not want to re-download any of the softwares i had in version 9, is there any way to copy my softwares to the new installation? i mean is there any folder that needs to be copied, and then my softwares will be back?

---

### Post by overdrank on 2010-06-23
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by Rubi1200 on 2010-06-23
I think this is what you are looking for:

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

Just read carefully and make sure it is version independent.

Good luck.

---

### Post by maizuddin35 on 2010-06-23
i think you can try using aptoncd? 
but , it does need a cd , right, like a waste of time because you've installed it in the same hard disk right...?

---

### Post by maizuddin35 on 2010-06-23
wonderful link @Rubi1200.:)

---

### Post by bingobingo on 2010-06-23
I do not get it, the only reason to upgrade or install the next version of Ubuntu is newer versions of kernel/programs. Otherwise, stay with your current version, I am assuming is 9.10. What was your reason to do a install at all? You Must be confused.:confused::confused::confused:

---

### Post by princennamdi on 2010-06-24
[SIZE=5]**@bingobingo the thing is i dont want to start hunting for new versions of all my softwares, i just want some of them the way they are....ps i just migrated from windows, and it is possible in windows>>"program files"** "appdata" etc...[/SIZE]:mad::confused::confused:

---

### Post by tarps87 on 2010-06-24
If it is just a case of hunting for the new versions
On the old install:
```
sudo dpkg --get-selections | grep '[[:space:]]install$='| awk '{print $1}' > installedpackages
```
copy the file installedpackages to the new install or just point to it on the old install partition
On the new install:
```
cat installedpackages | xargs sudo aptitude install
```
This will install the latest versions of all the software that you previously installed using the repos, usually the majority of your software.
It is not always just a case of finding the files an copying them as they have shared dependencies, this reduces the programs size but these dependences have to be handled some how. In the case of Ubuntu and other Debian based distros this is using aptitude (package manager)
Please note that just copping installed programs on windows is not guaranteed to work as they may depend on registry keys which would have to be found and copied separately

---

### Post by Paqman on 2010-06-24
> **tarps87 said:**
> 
This will install the latest versions of all the software that you previously installed using the repos

> **princennamdi said:**
> i do not want to re-download any of the softwares i had in version 9

Probably not quite what the OP was after, then. I suspect this is a bandwidth and/or cost issue.

---

### Post by tarps87 on 2010-06-24
> **Paqman said:**
> Probably not quite what the OP was after, then. I suspect this is a bandwidth and/or cost issue.

That was my first assumption but after their last post it seems like it is the searching for them that is the issue, admittedly this doesn't make sense if apt is being used.

@princennamdi If it is a bandwidth issue the yes don't follow my post as it will not do what you want

---

### Post by princennamdi on 2010-06-24
> **Paqman said:**
> Probably not quite what the OP was after, then. I suspect this is a bandwidth and/or cost issue.

[SIZE=4]**its bandwidth issues....i had no problem few months ago, until my company implemented a firewall restriction policy, whereby all traffic is routed to a proxy server in netherlands that does the filtering and stuffs, so it ll take bout 2 hours for me to download stuffs like eclipse for java, which usually take less than 30 minutes.......so u see why i need to migrate my softwares**[/SIZE]:mad:

---

### Post by CharlesA on 2010-06-24
The thing is that most packages in 10.04 are newer versions than the ones in 9.04, and you'd just end up downloading new packages if you somehow managed to migrate and install the packages from 9.04 onto a 10.04 machine.

You'd probably be better off just setting it to do an install of the same packages overnight if it is going to take a long time to download.

---

