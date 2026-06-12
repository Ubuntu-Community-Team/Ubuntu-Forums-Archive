---
title: "Can't connect to the software center"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by wrivera on 2011-07-04
Hi. For some reason I'm unable to connect to the** Ubuntu Software Center.** When I start the application it just shows the "progress circle" if you can call it like that, but nothing happens. Can't even see the list of the installed software. 

"progress circle image" Just in case.  [http://profile.imageshack.us/user/wrivera/](http://profile.imageshack.us/user/wrivera/)

**When I try to use Synaptic I get a small dialog window with the following messages: **

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

**If i run the update manager  I get this messages below: **


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

The only thing I've done recently was to change ISP from DSL to Cable. 

Thanks for any help you can provide.

---

### Post by wrivera on 2011-07-04
Please, ignore the post since I was able to find the solution posted an hour before my post by **amchornet **another forum member. I did searched for the solution prior to posting my request but I guess not well enough. 

thanks, 

Wilfredo

---

### Post by Rubi1200 on 2011-07-06
Hi and welcome to the forums :-)

Open a terminal with Ctrl+Alt+T and run the following commands:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

This should fix the problem.

---

