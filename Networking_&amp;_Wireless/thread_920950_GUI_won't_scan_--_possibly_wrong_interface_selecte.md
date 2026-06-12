---
title: "GUI won't scan -- possibly wrong interface selected"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by karat on 2008-09-15
Hi.  I know very little about networking and wireless, so I'm just trying to follow along various FAQs and troubleshooting guides.

The basic problem (in Ubuntu 8.04 LTS) is that the network-manager GUI can't find new networks when I try to scan (by selecting the dropdown for networks).  I've been following along some guides posted here, and I've noticed something:

1) I can find networks with 'sudo iwlist eth1 scan'
2) 'sudo lshw -C network' only lists wmaster0 (wireless) and eth0 (twisted pair -- not currently plugged in).
3) wmaster0 can't scan

Is this the problem?  Am I loading the wrong interface?

I can read, but there are a *lot* of different guides for different problems, and I don't have the basic knowledge to know which one is appropriate.  Can someone please point me at the right guide for this sort of problem?

PS On a potentially related problem, I have previously caught the GUI listing the WEP password cleared but not actually clearing it in the command line.  However, I'm not convinced this is the problem currently.

---

### Post by gregphil on 2008-09-15
These probably apply (ignore "ADS" in titles and read the whole threads)

[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26") 

[Bug #207072 in gvfs (Ubuntu): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072") 

In ubuntu the gnome GUI library gvfs has a bug in the authentication functions and therefore gnome GUI applications can't do "browsing" correctly (unless anonymous connections are allowed).  Command line tools (or KDE GUI apps) work just fine.

I have not been using wireless on ubuntu, so I will leave it up to you to decide if these bugs apply.  They definately apply to hardwired networking.

---

### Post by karat on 2008-09-15
I'm not sure that bug would affect wireless detection.

In any case, I suspect that there might be a simple solution if I am indeed loading the wrong interface.  It's just that I don't have enough know-how to determine if that is correct or how to change it.

---

