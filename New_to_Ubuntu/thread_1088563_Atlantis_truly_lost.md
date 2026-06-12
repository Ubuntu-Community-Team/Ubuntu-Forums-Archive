---
title: "Atlantis truly lost?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by marshall1001 on 2009-03-06
I've set up compiz fusion no bother, and my friend was showing me his alternative to the cube gears, the Atlantis plugin.

I searched the web for this and it's not downloadable to my knowledge, however the effect is not listed in my compiz fusion effects menu/

Halp?

---

### Post by BOZG on 2009-03-06
First of all, make sure you have the dependencies:

```
sudo apt-get build-dep compiz
sudo apt-get install git-core compiz-fusion-dev compiz-bcop

```

Go to: [http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=summary](http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=summary) to get to the plug in page.  You need to get the first url at the top.

Open terminal and cd to whatever directory you'd like to save the file to. Then type:

```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
```

This should have created a folder wherever you choose to save the file called atlantis2.  cd to that folder and use "make && make install" and it should now appear in the Compiz Settings manger.  If there are any problems during make, it should tell you what other libs are necessary to download.

---

### Post by howefield on 2009-10-15
Add the following repository (instructions on the page) and install compiz-fusion-plugins-unsupported


[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

Ooops,. wrong thread. Now, where did it go

---

### Post by tommytomato on 2009-11-15
> **BOZG said:**
> First of all, make sure you have the dependencies:

```
sudo apt-get build-dep compiz
sudo apt-get install git-core compiz-fusion-dev compiz-bcop

```

Go to: [http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=summary](http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=summary) to get to the plug in page.  You need to get the first url at the top.

Open terminal and cd to whatever directory you'd like to save the file to. Then type:

```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
```

This should have created a folder wherever you choose to save the file called atlantis2.  cd to that folder and use "make && make install" and it should now appear in the Compiz Settings manger.  If there are any problems during make, it should tell you what other libs are necessary to download.

> Go to: [http://gitweb.compiz-fusion.org/?p=u...tis2;a=summary](http://gitweb.compiz-fusion.org/?p=u...tis2;a=summary) to get to the plug in page. You need to get the first url at the top.

what do you mean please ? download ? snap shot

TT

---

