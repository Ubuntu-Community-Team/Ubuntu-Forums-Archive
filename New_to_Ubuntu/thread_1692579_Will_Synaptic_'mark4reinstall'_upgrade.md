---
title: "Will Synaptic 'mark4reinstall' upgrade?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by degarb on 2011-02-21
I am trying to install midori but errors: libatk1.0-0 (>=1.29.3) but 1.28.0-0ubuntu1 is to be installed
  Depends: libfontconfig1 (>=2.8.0) but 2.6.0-1ubuntu12 is to be installed
  Depends: libglib2.0-0 (>=2.23.5) but 2.22.3-0ubuntu1 is to be installed

in synaptic if I search libatk, I only get 1.0 not 1.29.3 or greater.  If I mark for reinstall, I am guessing it wont upgrade only reinstall.

My ugrade center is useless since I get deluged with upgrades when I am hovering between 200 meg and 600 meg free on drive. Also, turning off updates doesn't really work with ubuntu 9.10.   I still get nagged to death, and my gui freezes for 2 minutes as the poor little machine loads the useless and unwanted upgrade center.

---

### Post by maqtanim on 2011-02-21
> **degarb said:**
> I am trying to install midori but errors: libatk1.0-0 (>=1.29.3) but 1.28.0-0ubuntu1 is to be installed
  Depends: libfontconfig1 (>=2.8.0) but 2.6.0-1ubuntu12 is to be installed
  Depends: libglib2.0-0 (>=2.23.5) but 2.22.3-0ubuntu1 is to be installed

in synaptic if I search libatk, I only get 1.0 not 1.29.3 or greater.  If I mark for reinstall, I am guessing it wont upgrade only reinstall.

My ugrade center is useless since I get deluged with upgrades when I am hovering between 200 meg and 600 meg free on drive. Also, turning off updates doesn't really work with ubuntu 9.10.   I still get nagged to death, and my gui freezes for 2 minutes as the poor little machine loads the useless and unwanted upgrade center.

Use [this page]("http://packages.ubuntu.com/") to search for the necessary packages. You can download the packages of .deb format and install it manually...

---

### Post by degarb on 2011-02-21
> **maqtanim said:**
> Use [this page]("http://packages.ubuntu.com/") to search for the necessary packages. You can download the packages of .deb format and install it manually...

This might just work,  I am assuming to stick with 9.1

---

### Post by stoneage on 2011-02-21
Where are you trying to install from, or where did you get the support libs? It is obviously a versioning mismatch.

Why can't you install the older version of midori, and why do you need the newer dependencies? 

The version of libatk in the 9.10 repo is 1.28, so, why do you need 1.29 for midori when the midori version in the repository should install without issues?

---

### Post by sandyd on 2011-02-21
> **degarb said:**
> I am trying to install midori but errors: libatk1.0-0 (>=1.29.3) but 1.28.0-0ubuntu1 is to be installed
  Depends: libfontconfig1 (>=2.8.0) but 2.6.0-1ubuntu12 is to be installed
  Depends: libglib2.0-0 (>=2.23.5) but 2.22.3-0ubuntu1 is to be installed

in synaptic if I search libatk, I only get 1.0 not 1.29.3 or greater.  If I mark for reinstall, I am guessing it wont upgrade only reinstall.

My ugrade center is useless since I get deluged with upgrades when I am hovering between 200 meg and 600 meg free on drive. Also, turning off updates doesn't really work with ubuntu 9.10.   I still get nagged to death, and my gui freezes for 2 minutes as the poor little machine loads the useless and unwanted upgrade center.
turn it off in system -> prefrences -> startup apps

---

### Post by degarb on 2011-02-22
> **stoneage said:**
> Where are you trying to install from, or where did you get the support libs? It is obviously a versioning mismatch.

Why can't you install the older version of midori, and why do you need the newer dependencies? 

The version of libatk in the 9.10 repo is 1.28, so, why do you need 1.29 for midori when the midori version in the repository should install without issues?

Dunno, I gave up tried installing everything from everywhere.  I installed Epiphany instead.  

I like the speed and compatibility of Epiphany, but it lacks the toolbar (with site icons), which I need for my two little kids.   I suppose, I could write a startup page with the logos, but this will take much time, and was having trouble finding the logos of the first two links after 15 minutes of searching.  Put that off for another rainy day.

---

### Post by qyot27 on 2011-02-22
For hard drive space, go into Synaptic and under Preferences->Files tab, tell it to both flush whatever cache is there, and then set it to delete packages after installation.

That may clear up enough so you don't have to worry about updates making you run out of space.  And give you a greater share of free space, period.

Otherwise, you can update in chunks - select some, install them, select more, install, etc.  You can do this in either Synaptic or in Update Manager.

---

