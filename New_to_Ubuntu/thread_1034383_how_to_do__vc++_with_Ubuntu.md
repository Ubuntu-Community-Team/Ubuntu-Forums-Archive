---
title: "how to do  vc++ with Ubuntu"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by navaneethan on 2009-01-08
How to use Vc++ in ubuntu like windows ...Is any possible to work with UBUNTU,,,,

---

### Post by RobsterUK on 2009-01-08
Just to confirm, do you mean DC++ filesharing, or Visual C++ programming?

---

### Post by navaneethan on 2009-01-28
> **RobsterUK said:**
> Just to confirm, do you mean DC++ filesharing, or Visual C++ programming?

Visual C++ programming...friend can you explain how to do ....gradually

---

### Post by cariboo on 2009-01-28
You can't use the MS vc++ ide in linux, but here is a [guide]("http://www.yolinux.com/TUTORIALS/MicrosoftVisualC++Tips.html") for porting your code to linux.

Jim

---

### Post by resander on 2009-01-28
You cannot run VC++ under Linux.

However, you can run VC6 under Wine, but debugging did not work when I tried it some 2 months ago.

You can however get away from working from the command and using make files if you use the code::blocks IDE.

Info at [www.codeblocks.org](www.codeblocks.org).

You can download from synaptic using codeblocks as searchkey.

To get latest codeblocks version (usually best choice):

i) enter 'sudo gedit /etc/apt/sources.list' (without the quotes) and when in editor
add lines

deb [http://apt.jenslody.de/](http://apt.jenslody.de/) any main
deb-src [http://apt.jenslody.de/](http://apt.jenslody.de/) any main
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) etch-wx main

at the end of /etc/apt/sources.list

OR

select Software Sources from the GUI Administration menu,
select Third Party Software and add the three lines above

ii) enter 'apt-get install jens-lody-debian-keyring' from terminal

iii) enter 'wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -' from terminal

iv) use apt-get update and apt-get install codeblocks OR use
update and install via Synaptic manager
resander is offline   	Reply With Quote

---

### Post by ibuclaw on 2009-01-28
Or you could always use VirtualBox and run Windows inside Ubuntu.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Regards
Iain

---

### Post by navaneethan on 2009-05-15
Thanks

---

