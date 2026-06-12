---
title: "Are there patches or updates?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by whatworks on 2009-11-06
I just installed 8.04 Server.
 
I looked at the documentation and I ran "apt-get update" to update my packages. However, I see nothing about updates for the OS itself. Are there security patches like there are for Windows? I see I can use "do-release-upgrade" to upgrade to a newer version (e.g. 9.10). Is that the only option for updating the OS?
 
I would have just installed 9.10, except I saw 8.04 would be supported longer, and thought that would be better suited for a server environment.

---

### Post by BQAggie2006 on 2009-11-06
apt-get update is used to update the list of available packages from the repositories. To perform software updates, you will need to run apt-get upgrade after you finish running apt-get update. If you notice any packages that are held back from being updated, run apt-get dist-upgrade.

---

### Post by ubudog on 2009-11-06
```
sudo apt-get upgrade
```

---

### Post by whatworks on 2009-11-06
I've run "apt-get upgrade" too. That updates the OS actually? I'm Windows user, this is my first real venture into using Linux. I'm used to having to install updates to Windows as well as the other programs I install. I've played around a little with FreeBSD before and there were seperate commands to apply OS updates and package updates.

---

### Post by BQAggie2006 on 2009-11-06
Yes, apt-get upgrade updates everything on the system that has been installed from the Ubuntu repositories, "OS", applications, everything.

Now, I say "from the Ubuntu repositories" because the package manager is not aware of software installed manually (outside the apt-get process, except for .deb packages using dpkg) or compiled from source. For these packages, updates will have to be applied manually in the form of installing the most up-to-date package.

---

### Post by ranch hand on 2009-11-06
To answer your question, linux in general is not big on patches, particularly in security.  What you are getting are updates.

8.04, bless its pointy little head, is getting a little old.  You should check your /etc/apt/sources.list and make sure that "backports" are uncommented.

---

### Post by SunnyRabbiera on 2009-11-06
For a server it might be unwise to update to 9.04, on one hand you get more up to date apps but on the other hand it might not be as stable as 8.04
8.04 does get security updates and will do so until its end of life.

---

