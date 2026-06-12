---
title: "gksu not working after hostname change, ubuntu 9.04"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by gdoc on 2009-08-13
Hi Everybody,

So I wanted to change the name of my laptop. I googled and saw somewhere that I should change the name of the pc in  etc/hosts and /etc/hostname.
The problem is that I opened hostname first using gksu gedit hostname, changed the name, saved it, then tried to open hosts. It wouldn't work. Now I try the command gksu gedit hosts I get the following error
INVALID MIT-MAGIC-COOKIE-1 keyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
(gedit: 14478): Gtk-WARNING **: cannot open display: 0.0 yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

So I think the problem is that the name of the PC is different in each file. I think I should have opened them both at the same time, like this gksu hosts hostname.

Does anybody have any idea how to fix this? I had a look on the forum but didn't manage to see a solution.

Thanks,

G

---

### Post by gdoc on 2009-08-13
Hi, 
I just managed to fix it. I changed the hostname back to the original using the command hostname oldname. I was then able to access the hosts & hostname files using gksu gedit hosts hostname. In these files I changed the name back to the original, saved and exited. 

So sorry for clogging up the forum, I obviously should have looked harder before posting!

G

---

### Post by asmoore82 on 2009-08-13
It is noteworthy that in 8.04 LTS, the NetworkManager Profiles store the
local hostname and will change it whenever you change locations -
in other words, you must change it through the GUI if you want the change to "stick."

I don't think this is the case in Jaunty but I'm not sure.

---

