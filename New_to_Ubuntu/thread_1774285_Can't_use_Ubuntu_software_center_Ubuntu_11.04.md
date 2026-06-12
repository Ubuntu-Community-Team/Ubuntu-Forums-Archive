---
title: "Can't use Ubuntu software center Ubuntu 11.04"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by srvxid on 2011-06-03
I've just installed Ubuntu using Wubi. But I can't seem to search for any softwares in software center, it just shows the screen as shown in attachment...
i cant install any plugin basically including the banshee music player and flash and so on...
please help...

---

### Post by srvxid on 2011-06-03
there is also this error while opening synaptic packet manager

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Rubi1200 on 2011-06-03
Hi and welcome to the forums :-)

Open a terminal and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by r3d_E on 2011-08-29
I have the same issue it's a starting to get annoying that I haven't been able to solve it on my own sooo I'm hoping I could get a little insight on the problem :) I have tried also to update it but all I get is the following error: 
Could not initialize the package information

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/deluge-team-ppa-natty.list'

---

### Post by Rubi1200 on 2011-08-30
Hi and welcome to the forums r3d_E :-)

Open a terminal and post the output of the following command (copy/paste the results here):

```
gksudo gedit /etc/apt/sources.list.d/deluge-team-ppa-natty.list
```

Thanks.

---

### Post by mwbrown on 2011-10-04
> **Rubi1200 said:**
> Hi and welcome to the forums r3d_E :-)

Open a terminal and post the output of the following command (copy/paste the results here):

```
gksudo gedit /etc/apt/sources.list.d/deluge-team-ppa-natty.list
```Thanks.


Hello, I did what was said above (sudo rm /var/lib/apt/lists/* -vf)
and tried to do the (sudo apt-get update)
 I got these errors on the command line.
E: Malformed line 2 in source list /etc/apt/sources.list (URI)
E: The list of sources could not be read.

I also got this error when I tried to update through the GUI
'E:Malformed line 2 in source list /etc/apt/sources.list (URI)'

---

### Post by wildmanne39 on 2011-10-04
Hi, post your source list here please:
```
cat /etc/apt/sources.list
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

