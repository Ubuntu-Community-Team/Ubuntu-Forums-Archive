---
title: "Tried compiling glabels from source"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-01-16
No luck, as usual. I'm something like 0 for 23 with compiling from source. Anyhow, this was version 2.2.4 from SourceForge, a tarball. I extracted, ./configure, make, sudo make install... everything was copy and paste, and by and large everything seemed to be doing what it was supposed to do, but glabels won't launch. It appears to be trying, but it just won't.

There may be some problem, from what I gathered googling around, with some program called gettext. It screw up the compiling process. Whatever.

What I really want to know is if some kind soul while turn that tarball from SourceForge into a debian package so that the truly needy (and truly incompetent) such as myself can benefit from these new magicks you sages have concocted. I could swear that GetDeb had glabels before, but not now.

If not, can someone explain to me how to get rid of all of the installation garbage that I now have in my Home folder thanks to this failed attempt? Some variety of "autoclean" command would be lovely. I thank you all in advance.

---

### Post by zvacet on 2009-01-16
> There may be some problem, from what I gathered googling around, with some program called gettext. 

Do you get any messages that you need that package (gettext)for compile?It is good thing before you start to compile package to run (from directory where your source package is)

```
sudo apt-get build-dep package_name
```


> explain to me how to get rid of all of the installation garbage

In same folde where you are compiling type

```
sudo make uninstall
```
 
if you wish try again runing **sudo apt-get build-dep package_name **command to get all dependencies.

---

### Post by ricardisimo on 2009-01-16
I already did that during compiling. I actually suspect that this time the problem wasn't me... I don't know. If someone else on Ibex would be kind enough to shoot over to SourceForge and try compiling version 2.2.4, I would be very interested to see where I went wrong. Thanks, by the way.

---

### Post by ricardisimo on 2009-01-16
Anyone? Is there no kind wizard out there willing to transmogrify the installation tarball in question into a friendlier .deb? Thanks again.

---

### Post by cariboo on 2009-01-16
Is there as reason why you want to compile glabels in stead of installing the version that is in the repositories?

```
sudo apt-get install glabels
```

Seems to be way easier, then trying to compile from source, especially since you seem to have such a problem doing it.

Jim

---

### Post by ricardisimo on 2009-01-16
Yeah, there's a bug fix in the newer version that, for the purposes of my work, would save me as much as several hours a day.

---

### Post by drpjkurian on 2009-08-15
> **cariboo907 said:**
> Is there as reason why you want to compile glabels in stead of installing the version that is in the repositories?

```
sudo apt-get install glabels
```

Seems to be way easier, then trying to compile from source, especially since you seem to have such a problem doing it.

Jim

Hi jimi

The command does'nt work

It gives this output


rejy@rejy-laptop:~$ sudo apt-get install glabels
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package glabels is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glabels has no installation candidate
rejy@rejy-laptop:~$ 




Regards
Dr Kurian

---

### Post by zvacet on 2009-08-15
@ **drpjkurian**

In system>admin>sofrware sources enable **universe** and **multiverse** repo.Then try to install again.

---

### Post by jmszr on 2009-08-15
drpjkurian,

Also, you could use this: [http://www.getdeb.net/search.php?keywords=glabels](http://www.getdeb.net/search.php?keywords=glabels) .

---

### Post by ricardisimo on 2009-08-16
Especially if you have many fonts installed on your system, I STRONGLY recommend the getdeb version. The repo version of glabels is largely unusable if you do have many hundreds or 1000+ fonts.

---

### Post by AlexanderDGreat on 2010-02-25
Hi I'm using Linux 2.6.31-19-generic 32 bit Ubuntu JJ.

I can't make glabels work: When I increase font size, the labels disappear, I can't import images, and other weird things, but it works well on Karmic!

Anyone has similar issues? Help!

---

### Post by ricardisimo on 2010-02-25
I don't understand fully if you are 9.10, or 9.04, but I think for Jackalope you should be using [this version]("http://old.getdeb.net/search.php?keywords=glabels").

---

### Post by AlexanderDGreat on 2010-02-25
Great your version works well! I'm sorry. I'm using Jaunty.

---

