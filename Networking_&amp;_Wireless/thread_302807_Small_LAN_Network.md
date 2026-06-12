---
title: "Small LAN Network"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by philo23 on 2006-11-19
well, a while ago i was trying to access my windows pc from my ubuntu pc and all worked well, i opened up places -> network servers and i saw my windows pc, opened it up all worked well.
I shared another folder all was well, i was connected and could edit and make new files, however, 4 weeks from the i opened up places -> networks servers and windows network was showing, i clicked on it and my windows pc had disapeared, not to be found, i havent changed any setting on my router but now no windows pc listed, any one have any ideas how i could get this back.

thank you in advance to any one who helps.
I was using 6.06 then it disapeared before updating to 6.10, now its still not there

---

### Post by dmizer on 2006-11-19
if you're not afraid of a little command line.  try the 3rd link in my sig.  if you can't work it out, post in the thread and i'll be happy to help you figure it out.

---

### Post by philo23 on 2006-11-19
well i'm a bit confussed by the second part where i need something called "netbios name" and "share name", i have no clue how to get them and looking at the second post doesnt help. thanks for helping out by the way.
also could you describe what your tutorial is for, i think it might be for what i need, but i'd like to confirm.

Personally, i think theres a problem trying to connect to my windows pc via samba, i ran this in the terminal

nmblookup *

and it returned

querying file/folder name on 192.168.1.255
name_query failed to find name file/folder

where file/folder was anything in my shared folder on my ubuntu pc.

---

### Post by dmizer on 2006-11-19
yes cifs is for connecting to windows shares from ubuntu (ubuntu ---> windows)
if you need windows to view shares on the ubuntu machine (ubuntu <--- windows) then you'll need to use the first link in my sig.

to find the netbios name in windows xp:
start > my computer > view system information (under "system tasks" on the left) > computer name (tab)

the netbios name is next to "full computer name"

to find the share name in win xp, right click on the shared folder and select "properties", and click on the tab that says "sharing".  the share name is listed under "network sharing and security" next to "share name".

nmblookup won't work because you need to know the name of the computer you are trying to connect _TO_ not from.  so it doesn't matter a hill of beans what your ubuntu machine is called.

---

