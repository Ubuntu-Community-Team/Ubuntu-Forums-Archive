---
title: "Install PRO/Wireless3945BG in Linux issue"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by rimoka87 on 2007-12-16
this is my first post in this forum so i hope i would get support from you guy.Here is my problem, want to install a driver for my Intel(R) PRO/Wireless 3945BG Network Connection Adapter in Linux system, i'm a newbie so i really need a detail instruction, this is the quick INSTALL struction i get from the MS site
[http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945)
code:
                     % tar xzvf ieee80211-1.1.14.tgz
	% cd ieee80211-1.1.14
	% make 
	# make install   <--- You may need to be root
	% cd ..

what do i do at the first step, should i put those command in Konsole?
and where do i have to extract those file that i downloaded from the web?

---

### Post by ubutufan on 2007-12-17
> **rimoka87 said:**
> this is my first post in this forum so i hope i would get support from you guy.Here is my problem, want to install a driver for my Intel(R) PRO/Wireless 3945BG Network Connection Adapter in Linux system, i'm a newbie so i really need a detail instruction, this is the quick INSTALL struction i get from the MS site
[http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945)
code:
                     % tar xzvf ieee80211-1.1.14.tgz
	% cd ieee80211-1.1.14
	% make 
	# make install   <--- You may need to be root
	% cd ..

what do i do at the first step, should i put those command in Konsole?
and where do i have to extract those file that i downloaded from the web?

Yes you will have to open a console window.
the command tar will extract the file to a directory by the name ieee80211-1.1.14
then you must cd (change directory)
make will compile the code
and sudo make install will include it in the kernel
reboot your system

---

