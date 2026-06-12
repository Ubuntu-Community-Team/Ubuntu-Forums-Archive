---
title: "install kde desktop from kubuntu cd"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by mdewet on 2009-01-01
I have Hardy 8.04 running with gnome, but I want to take a look at KDE and play around.  I got my hands on a Kubuntu cd (7.10), and was wondering if I can install the KDE desktop from that or do I have to download the package files?

---

### Post by xjcannonx on 2009-01-01
all you have to do is ```
sudo apt-get install kubuntu-desktop
```

EDIT : sorry i misread, I've heard this works:

> To install kubuntu-desktop  on existing Ubuntu 
insert Kubuntu  CD
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
Session or Session Type choose KDE, then login.

Let me know if it works

---

### Post by mdewet on 2009-01-01
Is it possible to use the cd instead? the internet connection at home is still on dial-up! technology is on the fore-front on the african plains :D

---

### Post by mdewet on 2009-01-01
> **xjcannonx said:**
> all you have to do is ```
sudo apt-get install kubuntu-desktop
```

EDIT : sorry i misread, I've heard this works:



Let me know if it works

thanks, I tried it, but it gave me the following

```
muerte@muerte:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kde-guidance but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Recommends: kde-guidance-powermanager but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
E: Broken packages

```

I guess I'll have to download the packages as you said in your first reply..oh well, I do have all the time in the world

thanks for the help!
meiring

---

### Post by Bachstelze on 2009-01-01
You forgot the first step ;)

```
sudo apt-cdrom add
```

---

### Post by the yawner on 2009-01-01
Wait. Wont there be any problems with the different versions?

---

### Post by Bachstelze on 2009-01-01
Only way to know is to try. If there are dependencies problems, Apt will warn about them.

But yeah, it would be better to install from the same version if possible...

---

