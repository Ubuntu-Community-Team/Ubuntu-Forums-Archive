---
title: "Install packages without internet"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by starwed on 2009-11-04
I have a desktop computer I recently installed 9.10 on.  I wish to install some additional software (most importantly texlive and related packages), but I don't have an internet connection at home.

I know I can simply download the packages individually from a website, but handling all the dependencies looks like it would be a nightmare.  Is there an easy way to get all the files I need?

---

### Post by KIAaze on 2009-11-05
[Installing packages without an Internet connection]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection")

---

### Post by starwed on 2009-11-07
This is exactly what I hoped existed, only the very first step under those instructions makes little sense:
> # Open synaptic
# Select the packages you wish to install.
#Click on File->Generate package download script 

Unless it's been online, my desktop only knows about those packages which are already installed!  I can't select a package it doesn't know about, and so can't generate a download script.

Is there an easy solution to this?

---

### Post by KIAaze on 2009-11-08
YES! :) (well, almost easy solution)
-> [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Basically, it consists in creating your own local repository, except that it won't contain the packages themselves, only the dependency information. :)

The problem is that when you generate the package download list using this method, it will try to get the packages from your local repository and obviously fail.

The solution is to post-process the script by replacing the URLs with the correct one.

Assuming you created the local repository at "/home/username/repository" and got the different files from "http://archive.ubuntu.com/ubuntu/", this can easily be done with the following command:
```
sed 's/file:\/\/\/home\/username\/repository/http:\/\/archive.ubuntu.com\/ubuntu/' download_script.sh > download_script2.sh
chmod +x download_script2.sh

```
or directly without creating a second script:
```
sed -i 's/file:\/\/\/home\/username\/repository/http:\/\/archive.ubuntu.com\/ubuntu/' download_script.sh

```
or simply with any text editor featuring search&replace. ^^
_________________________________________________________________
More links gathered while googling:
[http://www.linuxquestions.org/questions/linux-software-2/offline-update-package-lists-in-ubuntu-658508/](http://www.linuxquestions.org/questions/linux-software-2/offline-update-package-lists-in-ubuntu-658508/)
[https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045455.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045455.html)
[http://ubuntuforums.org/archive/index.php/t-80974.html](http://ubuntuforums.org/archive/index.php/t-80974.html)
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)
[http://www.linuxquestions.org/questions/linux-software-2/how-apt-get-update-offline-707287/](http://www.linuxquestions.org/questions/linux-software-2/how-apt-get-update-offline-707287/)
[http://wiki.debian.org/AptMedium](http://wiki.debian.org/AptMedium)
[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[http://forums.debian.net/viewtopic.php?f=10&t=45990](http://forums.debian.net/viewtopic.php?f=10&t=45990)
_________________________________________________________________
P.S.: I think someone should set up a service to make this easier. Ideally, it should be on packages.ubuntu.com (or debian equivalent).
ex: You want to install package foo, so you enter foo and the site give you a file to download, which you can then take to your offline PC.
There you open it with some special program (maybe synaptic?) and it creates a package download script (ideally cross-platform) which you can then use on the online machine to download the packages and bring them back to your offline machine.

edit:
Idea added: [http://brainstorm.ubuntu.com/idea/22014](http://brainstorm.ubuntu.com/idea/22014)
Wiki updated: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

---

### Post by mac9416 on 2009-11-09
> P.S.: I think someone should set up a service to make this easier. Ideally, it should be on packages.ubuntu.com (or debian equivalent).
ex: You want to install package foo, so you enter foo and the site give you a file to download, which you can then take to your offline PC.
There you open it with some special program (maybe synaptic?) and it creates a package download script (ideally cross-platform) which you can then use on the online machine to download the packages and bring them back to your offline machine.

That already exists in a desktop application called [Keryx]("http://keryxproject.org"). It is a "portable package manager" in that you can make a Keryx "project" on your offline computer, take it to any online computer, and download any software you could on an online computer - Keryx takes care of getting the dependencies. Another plus is that Keryx is cross-platform. So, if you want to download packages on a library computer running Windows, you can.

Hopefully you find Keryx to be of some use. Let me know if you have any questions!

---

### Post by KIAaze on 2009-11-09
Thanks for the tip. This looks like a very useful tool. :)

I quickly tested it locally and found what looks like a bug to me: [https://bugs.launchpad.net/keryx/+bug/479445](https://bugs.launchpad.net/keryx/+bug/479445)

I'll add it to the wiki later, unless someone else feels like doing it for me before. ;)

---

### Post by egalvan on 2009-11-09
how about apt-on-cd?

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)



or buy a copy of the 
*Ubuntu 9.10 Software Repository*
found at

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)

here is a quote:

"Product Description
The Complete Ubuntu Software Repository, as of Nov 4, 2009. Compatible with any Ubuntu 9.10 based distribution, including Ubuntu 9.10, Kubuntu 9.10, Xubuntu 9.10, Edubuntu 9.10, Ubuntu 9.10 Server, Ubuntu Studio 9.10, and Mythbuntu 9.10.

This DVD set allows you to install thousands of applications directly from the DVDs using Add/Remove Applications.

This is perfect for those with slower internet connections, or no connection at all."

---

### Post by mac9416 on 2009-11-09
> **KIAaze said:**
> Thanks for the tip. This looks like a very useful tool. :)

I quickly tested it locally and found what looks like a bug to me: [https://bugs.launchpad.net/keryx/+bug/479445](https://bugs.launchpad.net/keryx/+bug/479445)

OK, I'll take a look at the bug. Thanks for reporting it. It really makes a developer's life easier. :)

> I'll add it to the wiki later, unless someone else feels like doing it for me before. ;)

Thanks very much! I had considered doing that, but since I don't have a lot of experience with Wikis, I didn't attempt it.

> how about apt-on-cd?

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I think that too much emphasis is put on APTOnCD as a solution for offline Ubuntu (or any debian-based distro) users. 
These are APTOnCD's shortcomings:
[LIST]
[*]It does not allow you to select single applications to download with dependencies (like in Synaptic)
[*]It is not portable - you can't carry it around on your flash drive
[*]It is not cross-platform
[/LIST]
I in no way want to bash APTOnCD. I have found it useful on several occasions. However, its purpose is different from that of Keryx. APTOnCD allows you to put an (or part of an) APT repository on a CD and take it to offline computers. Keryx downloads the packages that go into that CD repository (or are installed by some other means).

> or buy a copy of the
Ubuntu 9.10 Software Repository
found at

[http://www.osdisc.com/cgi-bin/view.c...untu/repo.html](http://www.osdisc.com/cgi-bin/view.c...untu/repo.html)

here is a quote:

"Product Description
The Complete Ubuntu Software Repository, as of Nov 4, 2009. Compatible with any Ubuntu 9.10 based distribution, including Ubuntu 9.10, Kubuntu 9.10, Xubuntu 9.10, Edubuntu 9.10, Ubuntu 9.10 Server, Ubuntu Studio 9.10, and Mythbuntu 9.10.

This DVD set allows you to install thousands of applications directly from the DVDs using Add/Remove Applications.

This is perfect for those with slower internet connections, or no connection at all." 

That to me seems to be a great idea! However, at $30, many would prefer to take the extra trouble to use a combination of Keryx and APTOnCD to achieve the same result with fewer packages.


Sorry about the long, rambling post. Hopefully someone finds all these random thoughts useful. :)

---

