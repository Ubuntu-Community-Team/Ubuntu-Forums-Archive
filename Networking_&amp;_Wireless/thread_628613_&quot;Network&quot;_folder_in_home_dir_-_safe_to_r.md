---
title: "&quot;Network&quot; folder in home dir - safe to remove?"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by maybeway36 on 2007-12-01
DISCLAIMER: I'm actually on Linux Mint, but unless I'm mistaken, this issue applies to Ubuntu too.
I have a folder in my home directory called "Network". Inside is the name of my workgroup, and inside that are the names of my computers and shared folders. However, I get an access denied error when going inside them, and they work just fine in Places>Network (or Daryna>Network in Mint), so what's the point of this folder tree? Can I delete or hide it somehow?
P.S. It's owned by user root and my group.

---

### Post by micro_mx on 2008-03-13
yup, same problem here on linux mint :]

---

### Post by Oldsoldier2003 on 2008-03-13
> **maybeway36 said:**
> DISCLAIMER: I'm actually on Linux Mint, but unless I'm mistaken, this issue applies to Ubuntu too.
I have a folder in my home directory called "Network". Inside is the name of my workgroup, and inside that are the names of my computers and shared folders. However, I get an access denied error when going inside them, and they work just fine in Places>Network (or Daryna>Network in Mint), so what's the point of this folder tree? Can I delete or hide it somehow?
P.S. It's owned by user root and my group.

nope no network folder in ~ or /home  in Ubuntu  ( Gutsy)

---

### Post by micro_mx on 2008-03-13
I found the problem, its with fusesmb installed and enabled by default... 
the quick solution that I found was to delete the folder ".smb/" in your home...

you delete that and the Network folder will be empty :]

I have gutsy on the desktop (wich doesn't have this feature) but the laptop has linux mint and I just did that...

Sorry for my bad english...

---

### Post by micro_mx on 2008-03-13
lol, there's the Network folder full again, I think im just going to delete the fusesmb package... I dont need it anyway...

---

### Post by maybeway36 on 2008-03-23
You can turn it off in the mintDesktop preferences.

---

