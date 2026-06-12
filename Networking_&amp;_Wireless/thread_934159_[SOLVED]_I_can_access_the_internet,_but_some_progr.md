---
title: "[SOLVED] I can access the internet, but some programs cannot"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by TallTreeRunningMoose on 2008-09-30
So, I can go online fine - firefox loads pages and I can ping websites.

But, some (not all) of my programs cannot.  For example, if I want to download an update for a firefox add-on, that times out.  Also, I use python-feedparser for some stuff, and that times out. To give an example of programs that CAN go online, I do distributed computing through BOINC, and that seems to be able to access the internet fine.**not the case - see edit**

To give some background, I've been having some issues recently that probably caused this.  First, a few days ago, Symantic Package Manager decided to remove a ton of packages, most but not all of which are part of ubuntu-desktop.  I think I replaced all of the packages that were removed, but I may have missed some.

Also, I have been having some hostname issues when trying to access my computer over ssh, and I saw somewhere that uninstalling and reinstalling network-manager would help.  I removed the packages using apt-get, but then I didn't think ahead far enough to realize that I would not be able to download the packages again, so I had to do them manually using the .deb packages from the ubuntu site.  I think I did it correctly (I got all the dependencies and checked for updates after I was back online) but there is likely something still broken from that.

Any help will be appreciated.

EDIT:  It turns out BOINC actually can NOT access the internet.  So, it looks like I can access the internet if I do it, but any program cannot.  Could it be some sort of permissions issue?  Where my user is able to access it, but the background user cannot?  I don't know if that made any sense, or if ubuntu works that way, but its just an uninformed hypothesis.

---

### Post by TallTreeRunningMoose on 2008-09-30
OK, I fixed it.

In /etc/network/interfaces, there was a line commented out that was kinda important.

To give the exact information...

**BEFORE**
```
# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

**AFTER**
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Simple fix, but what it did was amazing.

---

