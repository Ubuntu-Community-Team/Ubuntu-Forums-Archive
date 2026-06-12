---
title: "koffice package broken in jaunty."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by casbahdk on 2009-04-24
I get the following when I try to install Koffice:

```
$ sudo apt-get install koffice
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  koffice: Depends: kformula (>= 1:1.6.3-7ubuntu6) but it is not going to be installed
E: Broken packages
```

I have done a search, but Jaunty is just off the presses and I don't see anything posted about this issue.

BTW, I have a suggestion for the forums. I would like to see an absolute beginner section for new KDE users. It takes a lot of time and effort to find KDE programs similar to the GNOME apps I have been using and there doesn't seem to be a migration guide.

Cheers

---

### Post by RichardLinx on 2009-04-24
> KOffice is currently available as version 1.6.3 designed to run with KDE 3.3 or later. KOffice is released separately from the rest of KDE, so KOffice releases are not in sync with those of KDE. If you wish to use a newer development version, then you will need to compile from source.

You wont be able to install KOffice straight from the package manager because of some unresolved dependancies. The only way you can get it to work if you're using KDE 4 is to compile it from source.

The source code and instructions on how to compile it can be found here: [http://www.koffice.org/download/source.php](http://www.koffice.org/download/source.php)

I'm not sure about this but you may be able to install some KDE3 libs and it might work, but I wouldn't count on it.

---

### Post by casbahdk on 2009-04-25
I managed to get the following components of Koffice installed by installing them one at a time with Aptitude:

Kspread
Kpresenter
Kplato
Kjots
Kexi also got installed as a byproduct of installing the other apps.

I got some error connected with installing some latex and ruby stuff needed by the apps:

No CIDSpplement font bla, bla.

Cheers

---

### Post by solar george on 2009-04-26
Try installing [koffice-kde4]("apt://koffice-kde4")

---

### Post by casbahdk on 2009-04-26
> **solar george said:**
> Try installing [koffice-kde4]("apt://koffice-kde4")

Great. Thanks. It says that it is release candidate 1, but it seems to be well behaved :-)

---

### Post by cmfrtblynmb on 2009-05-09
koffice 2 does not have a formula editor, which is a "must" for me

I gave it a try, I liked koffice2, especially its ability to draw lines and graphs is astonishing, comparing to MS word or OO writer. 

But as I said it lacks a formula editor. Then I decided to give a try to koffice 1, but I can not install it, since kformula package tries to uninstall all kde4 desktop. 

I guess this package needs to be fixed

---

### Post by YQ002lc2 on 2009-05-12
Hey Guys,

I know the problem isn't technically fixed yet, but here's how I installed the package koffice:

sudo apt-get install kformula
sudo apt-get install koffice


I first tried sudo apt-get install koffice and I got the same message everyone else is getting, but I then tried to install kformula first and it worked. 
Hope that helps!

---

### Post by elpadredude on 2009-05-26
Hi there,

Question from a Kubuntu (Jaunty Jackalope) newbie: does  the apt-get command automatically detects and installs the correct packages for a 64-bit system as the KPackageKit does, which  displays only 64-bit packages?

 Koffice install via KPackageKit queries and queries for its dependencies with no success. So I'm left with the option of trying jpinson's suggestion.

Jim

---

### Post by casbahdk on 2009-05-27
I am pretty sure that KPackage is just a front-end for apt-get. The same with Synaptic. There are differences in performance, Synaptic is still #1 in reliability, in my opinion. Maybe someone else can answer your question more coherently than I can? I mainly use aptitude with the CLI. Aptitude and apt-get also do more or less the same thing.

---

### Post by scott_audio on 2009-07-18
I tried to install kformula, then koffice, and it removed almost every package, the system was unrecoverable... what a waste, I just spent two days getting my system just right.  I was going to try koffice, because I couldn't get openoffice to work well with a dark theme

---

