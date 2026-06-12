---
title: "installing things from getdeb"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-17
I've installed the getdeb package, but when i click on the install this now button firefox says it dosen't know how to open this address since the protocal (apt) isen't associated with any program.

---

### Post by ukripper on 2009-11-17
> **Falc7 said:**
> I've installed the getdeb package, but when i click on the install this now button firefox says it dosen't know how to open this address since the protocal (apt) isen't associated with any program.

What package you downloaded?

---

### Post by Falc7 on 2009-11-17
From this page:
[http://www.getdeb.net/updates/Minitube](http://www.getdeb.net/updates/Minitube)
I clicked 'Click here to learn how to install applications from GetDeb'

Then i installed the package listed in step 1

---

### Post by ukripper on 2009-11-17
> **Falc7 said:**
> From this page:
[http://www.getdeb.net/updates/Minitube](http://www.getdeb.net/updates/Minitube)
I clicked 'Click here to learn how to install applications from GetDeb'

Then i installed the package listed in step 1

Are you running Karmic (9.10)?

---

### Post by camaron1 on 2009-11-17
that is some kind of bug which i got from 9.4.
 
Just download the package (on the desktop or wherever) and click on it. It should install no problem. (I mean you've got the option to either install straight away or just download: take this option)

---

### Post by blazemore on 2009-11-17
yeah it's weird.
Try installing the apt-url package, but I don't think it will make a difference, it's a bug you see.

Anyway, I hate when people put their PPA information in a deb file. it's easier just to use Software Sources.

---

### Post by Falc7 on 2009-11-17
> **ukripper said:**
> Are you running Karmic (9.10)?

Yep

> **camaron1 said:**
> that is some kind of bug which i got from 9.4.
 
Just download the package (on the desktop or wherever) and click on it. It should install no problem. (I mean you've got the option to either install straight away or just download: take this option)

I don't see the opportunity to download a deb file like you could before

---

### Post by camaron1 on 2009-11-17
> I don't see the opportunity to download a deb file like you could before     1-Change your preferences in Firefox: go to EDIT>PREFERENCIES>APPLICATIONS, scroll down to Deb or Debian packages and change to either DOWNLOAD or ALWAYS ASK. I think this should solve the problem.
2-The new GETDEB site is in beta I think (maybe something wrong with them?). If you are using this one try downloading from the old one which you can find [here]("http://old.getdeb.net/")
3-The new GETDEB site gives you the possibility to add all their packages as a repository which would make the whole thing easier for future downloads too. Look [here ]("http://www.getdeb.net/updates/#how_to_install")

If all this fails maybe you could point us to the package you are trying to install?

Hope it helps

---

### Post by Falc7 on 2009-11-17
> **camaron1 said:**
> 1-Change your preferences in Firefox: go to EDIT>PREFERENCIES>APPLICATIONS, scroll down to Deb or Debian packages and change to either DOWNLOAD or ALWAYS ASK. I think this should solve the problem.
2-The new GETDEB site is in beta I think (maybe something wrong with them?). If you are using this one try downloading from the old one which you can find [here]("http://old.getdeb.net/")
3-The new GETDEB site gives you the possibility to add all their packages as a repository which would make the whole thing easier for future downloads too. Look [here ]("http://www.getdeb.net/updates/#how_to_install")

If all this fails maybe you could point us to the package you are trying to install?

Hope it helps

1. Debian packages were on always ask, i changed it to 'download' but the problem persists.
2. Will try the old one now.
3. I've added their packages as a repository by doing point number one on the link you posted (by installing the deb package)

I am trying to install this [http://www.getdeb.net/updates/minitube](http://www.getdeb.net/updates/minitube)

---

### Post by blazemore on 2009-11-18
I can never get on getdeb.... it always just hangs. At uni I can, but at home, nothing.

---

### Post by camaron1 on 2009-11-18
> I've added their packages as a repository by doing point number one on the link you posted (by installing the deb package)


No, just add the new repository as you would with any other: 
open **synaptyc>settings>repositories>other software** and click **add**. On the window that will appear write **deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps **(I'm supposing you are on Karmic) and then copy and paste this on a terminal: [B]wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add - 
[/B]Press enter and that is you, **all the packages** from GETDEB have been added to your repositories, just look for them via Synaptic

On the other hand, that package **minitube **might actually disappoint you, but that is a different issue.

Good luck

---

### Post by camaron1 on 2009-11-18
> **blazemore said:**
> I can never get on getdeb.... it always just hangs. At uni I can, but at home, nothing.
That is really estrange, isn't?

---

### Post by blazemore on 2009-11-18
Yes it's strange. It works through a proxy like TOR.

---

### Post by Falc7 on 2009-11-18
> **camaron1 said:**
> No, just add the new repository as you would with any other: 
open **synaptyc>settings>repositories>other software** and click **add**. On the window that will appear write **deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps **(I'm supposing you are on Karmic) and then copy and paste this on a terminal: [B]wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add - 
[/B]Press enter and that is you, **all the packages** from GETDEB have been added to your repositories, just look for them via Synaptic

On the other hand, that package **minitube **might actually disappoint you, but that is a different issue.

Good luck

Ah yes i can install the getdeb software through synpatic, thats cool, i just won't use FF to install packages from getdeb, thanks :)

---

### Post by camaron1 on 2009-11-18
I'm glad you got there ;)

---

### Post by lamego on 2009-11-18
Hello,
firefox will only support installing from apt: urls if you install the firefox-gnome-support package.

Best regards

---

### Post by Falc7 on 2009-11-20
I've installed that package now, still can't install from firefox though, i'm using kde if thats relevant

---

### Post by camaron1 on 2009-11-20
> **Falc7 said:**
> I've installed that package now, still can't install from firefox though, i'm using kde if thats relevant

Why would you want to install from FF when you can via Synaptic?

---

### Post by Falc7 on 2009-11-25
Because in some situations, like there are some guides, as well as getdeb itself, it is easier to click install, and have the program install, then starting up synaptic

---

