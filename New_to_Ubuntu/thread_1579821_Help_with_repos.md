---
title: "Help with repos"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by skipper38 on 2010-09-22
Hope someone can help, I was using Rookcifer's guide to installing Tor and gor to step 5...
it was late so i switched laptop off to carry on today, problem was that I couldn't get into etc/apt/sources.list and now ive got a "No Entry" sign at top of my screen and I can't access Synaptic or update manager......really miffed at what to do, this is the error message im getting:

Synaptic: E: Type ‘PASSWORD’ is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Update manager: Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘PASSWORD’ is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Running 'Lucid Lynx' hope someone can help thanx

---

### Post by andrewthomas on 2010-09-22
post the output of 

```
cat /etc/apt/sources.list
```

---

### Post by ibizatunes on 2010-09-22
sudo gedit  /etc/apt/sources.list
hash out any changes you have made
Do you need a working copy of a source list?

---

### Post by bodhi.zazen on 2010-09-22
I moved your post as it is unrelated to TOR.

You have some kind of typo in your configuration.

Open /etc/apt/sources.list with any editor and fix the problem.

Post the output of 

```
sed -n 54p /etc/apt/sources.list
``` and we can see the problem.

---

