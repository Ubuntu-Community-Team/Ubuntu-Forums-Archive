---
title: "[SOLVED] Strange share problem, windows shares just up and dissapeared"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Tamjay on 2008-06-12
I have a very strange problem....

a couple of weeks ago my shares on one of two windows computers (both vista) that are on my home network just vanished.  the computer name is there, but when clicking on it through nautilis file browser, nothing shows up, not even the login promt. (both computers require log in to access on network).  had not had this problem since my initial install of hardy when it was at alpha 3.  what has me stuck, is the fact that my kubuntu 4.1 beta (same machine, different partition) sees the windows computer and all it's shares just fine. even more strange, when in gnome (the partition on the install i'm having this problem with), i can access the laptop's vista and all it's shares, as well as log into it, just fine.  i've searched high and low for a salution to this and tried many things.  usually i eventualy figure it out, but this one has me completely stumped.

the install with the problem is ubuntu 8.04 hardy heron.  network card hard wired to router (d-link).  everything else on the network functions perfectly.  thanks ahead for the help and thanks for sticking with this rather lengthly post.

---

### Post by Tamjay on 2008-06-12
ok, update here..

after doing some more searching i have found that if i enter smb://<computer name>/<shared folder name>, i get a prompt for my username and password and low and behold... there are my folders.  great workaround, but if anyone else has encountered this, i'd like to know if there is a fix so i can just click into em like my other computers(i know, lazy but hey, making stuff work is why i love linux =o) ) on the network.  looks like it's a problem exclusively in nautilus to me...

---

