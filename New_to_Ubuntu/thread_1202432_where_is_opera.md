---
title: "where is opera?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-02
i typed ..:
> sudo apt-get install opera
and then it gave ..:> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate


so where is opera?

---

### Post by clive littlewood on 2009-07-02
Hi

Install Opera from the repos or the latest from the Opera site.

The site has a .deb file so when you download just double click the file and Voila !!

Clive

---

### Post by heyyy on 2009-07-02
> **clive littlewood said:**
> Hi

Install Opera from the repos or the latest from the Opera site.

The site has a .deb file so when you download just double click the file and Voila !!

Clive

yes i know 
the point is why i dont have opera on the repos?
because if i dont have opera i'll probably wont have have other apps avaliable as well

---

### Post by frunns on 2009-07-02
And if you open Synaptics then? And what source you got enabled in Software Sources?

---

### Post by sisco311 on 2009-07-02
you have to enable the *partner* repository or use the generic Opera repository:
[uhelp]community/OperaBrowser[/uhelp]

---

### Post by adam_kimber on 2009-07-02
I would install from a Repository in case of updates. I am not sure if a static downloaded Deb would update from Repo. 

Opera should be avaible in the Canonical add-on Repository. Go to Software sources and check the boxes. 

[IMG]http://cybernetnews.com/wp-content/uploads/2007/10/ubuntu-software-sources-proprietary-drivers.jpg[/IMG]

You can also add a Third Party Repo for this (I get my Wine straight from WineHQ this way). This method is not recommended at there MIGHT be potential conflicts, though generally there are not if you use the right ones. I do not recommend using Debian Repos in Ubuntu as this can lead to all sorts of problems. Have a look at [http://deb.opera.com/](http://deb.opera.com/)

---

