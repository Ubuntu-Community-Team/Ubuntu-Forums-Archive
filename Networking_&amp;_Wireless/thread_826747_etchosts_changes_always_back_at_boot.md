---
title: "/etc/hosts changes always back at boot"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by sdesousa on 2008-06-12
I know this subject must be tedious by now :( I even found many threads discussing it, same questions/same (non)solutions until I finally came across a thread that was labeled "SOLVED" but had nothing that could point me in the right direction.- or to an actual explanation or solution!

Granted, I am still using gutsy and I have no clue if this is resolved or not, already.

Well, the problem is simple, but frustrating: my /etc/hosts is always rewritten when I log off, discarding all changes I made aliases. It does keep the commented out remarks, though!!!

Could anyone please tell me what is changing it, what can I do to change my hostname alias?

I grep'ed and looked around and I could not figure out where in heck did the system keep the local domain info to rewrite my hosts file back!! It obviously is not just restoring a mere backup, cuz my commented-out remarks do remain there all the time and it apparently just rewrites the lines for localhost and localdomain.

Since I could not find my answers yet (I have been searching for a few days already) I surrendered and decided to just ask for help here. Appreciated!!

---

### Post by forger on 2008-06-12
I'm not sure about this, so try it **at your own risk**.
[Before proceeding, you have to know how to mount and edit files, in case something goes wrong]

say my hostname is "ubuntu"

open up gnome terminal:
```
gksu gedit /etc/hosts /etc/hostname
```

In hosts you should have something like "**127.0.1.1	ubuntu**"
change the "ubuntu" (hostname alias) to your liking, i.e. "linux"

save and close gedit, then do:
```
sudo hostname linux
```

then type:
```
hostname -v
```
see if it changed, it should say "linux" instead of "ubuntu"

after that use terminal to reboot:
```
sudo reboot
```

if the machine doesn't boot, open up a live cd, mount your root partition and change the /etc/hosts and /etc/hostname to use the old hostname ("ubuntu")

---

### Post by sergio_desousa on 2008-06-18
> **forger said:**
> I'm not sure about this, so try it **at your own risk**.
[Before proceeding, you have to know how to mount and edit files, in case something goes wrong]



Thank you, forger. I appreciate the effort in trying to help. In fact I do know how to use a linux system fairly well including editing of files :) and I had already tried what you explained as my first shot at changing my hostname.

However, maybe I did not express myself properly and caused some confusion, so that you didn't in fact reply to exactly what I was asking.

The problem is EXACTLY that when I change hostname or edit it directly in /etc/hosts, both for 127.0.0.1 and 127.0.1.1, after the system reboots or logs-off, the entries disappear and are replaced with the one(s) I entered at installation/setup time :(

This isn't just annoying... it's keeping me from doing some serious stuff.

Anyways, I heard that this could be due to network-admin storing some default system values within gnome settings, but editing it simply didn't wield any results (I couldn't find any entry for "network" in there).

I continue at a total loss here and, I confess, I am totally surprised no one had the same issue (??) and that there is no easily available or known solution.

All my computers running ubuntu 7.10 behave in the exact same manner.

So, my questions remain: what is causing it? where does the system store the host or network name in order to revert it back any time it boots? How can I change it permanently?

As I wrote before, I looked everywhere, grep'ing files for it, and found nothing!

Thank you all and you forger in special for your help.

---

