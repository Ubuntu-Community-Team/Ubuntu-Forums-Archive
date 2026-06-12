---
title: "installing packages not from software center"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by kamelyan on 2011-03-20
having trouble installing some packages after down loading them . am making the exercutable in preferences but some still still dont install - have looked in read me file but still novice in terminal- tried cut and pasting some commands but not working .

---

### Post by marcelo.matos on 2011-03-20
What kind of packages are you trying to install? Looking at the file extension should help.

[B].DEB
[/B]If your package extension is ".deb" it is (or should be) easy.

A double-click must open the package manager. Also, you might need to enter the administrator password.

**.RPM**
If the package extension is ".rpm", you'll need to convert it to .deb.

Here's a how to from the community documentation:
[https://help.ubuntu.com/community/RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto")

I hope it helps!

---

### Post by -kg- on 2011-03-20
And if you're installing from a "tar.gz" the process will be a bit more complicated.  You'll have to handle dependencies and conflicts yourself.  The readme file in the .tar file should tell you what dependencies and all you have to meet to successfully install the package(s).

What are you trying to install, and into what version of Ubuntu, and on what hardware?

---

### Post by kamelyan on 2011-03-21
i have this problem with a number of files would be great to have somwhere that install info for all file types  . at the moment-

vboxgtk-0.5.2.tar.gz

embedly.1.4.zip

system-

 ubuntu 10.10 -installed yesterday on new hard drive

hp dv7

processor 0: AMD turion X2 dual-core mobile rm 70

processor 1: AMD turion X2 dual-core mobile rm 70

memory3.7 Gig

thanx

---

### Post by Paqman on 2011-03-21
> **kamelyan said:**
> 
vboxgtk-0.5.2.tar.gz


Are you trying to install Virtualbox? If so go [here]("http://www.virtualbox.org/wiki/Linux_Downloads") and download the Ubuntu .deb package. I would also recommend doing the steps listed under "Debian-based Linux distributions", including installing dkms if it isn't already.

---

### Post by kamelyan on 2011-03-21
not in particular .this is a beta version not in ubuntu software center . was just giving example of filetypes i cant install .thanx for the reply. K

---

