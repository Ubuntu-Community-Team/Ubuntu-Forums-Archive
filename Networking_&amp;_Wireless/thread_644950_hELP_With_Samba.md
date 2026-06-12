---
title: "hELP With Samba"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Lord DarkPat on 2007-12-19
I have set up sharing betwwen XP and Kubuntu. It shows up in Samba shares in Linux, but when I try to access, it says it doesn't exist. Now when I try from XP, it asks for a pass, and I have no IDEa!
Help Please!:(

---

### Post by gilf on 2007-12-19
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by reckless2k2 on 2007-12-19
in add/remove menu is a nice samba GUI that is much more user friendly than bugging around in the terminal if that's not for you. the principals are the same though. Editing in the terminal is much more powerful but i doubt you need it.

---

### Post by Lord DarkPat on 2007-12-19
I followed the guide and 1/2 of it worked :)
But, I can't access my windows share, but I can do vice versa. And I can handle terminal, and don't think I dont cuz I can :popcorn:

---

### Post by gilf on 2007-12-19
> **reckless2k2 said:**
> in add/remove menu is a nice samba GUI that is much more user friendly than bugging around in the terminal if that's not for you. the principals are the same though. Editing in the terminal is much more powerful but i doubt you need it.

Sounds good but I can't find it on "Add-Remove" and you didn't provide a name for it. Did a search on All for "Samba". Nothing there.

Maybe you mean Synaptics?

> But, I can't access my windows share, but I can do vice versa. And I can handle terminal, and don't think I dont cuz I can 

Check your firewall in XP if you are running one -- maybe add the ubuntu machine to trusted hosts?

---

### Post by gilf on 2007-12-19
Found the gui program in Synaptics -- 

system-config-samba

Tried it.

I like it. Shows up in System>Administration>Samba

---

