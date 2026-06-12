---
title: "Quodlibet EOF error / Quodlibet wont start"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by woofleboofle on 2010-07-01
Hi, 
There was a previous thread about the EOF error where Quodlibet will not start. Anyway, it is some issue with the library loading and they suggested to remove the songs.py file. This works fine, but for some you may get this error every single time u want to load quodlibet, and of course you dont want to have to delete the file everytime manually. 
So, i made a quick command for newbies like myself that you can put in a launcher to remove the songs.py and load quodlibet at the sametime. 

Right click the desktop, click "create launcher". Name it quodlibet or whatever, and in command, input:

sh -c "rm -rf /home/Johnsmith/.quodlibet/songs && quodlibet"

The "&&" allows you to first remove songs.py, followed by starting up quodlibet. the sh -c allows you to run shell commands from a launcher. 
Now you can have one icon on the desktop for quodlibet, and it will load everytime!

I hope that helps someone like me who cant find a better music player and was going crazy with frustration!! P.s i would have posted this in the other thread but it wouldn't let me cos its solved.

---

