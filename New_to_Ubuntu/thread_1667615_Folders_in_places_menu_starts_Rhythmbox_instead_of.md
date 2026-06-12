---
title: "Folders in places menu starts Rhythmbox instead of Nautilus"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by livit on 2011-01-15
Recently I started using Ubuntu 10.10 (my first serious Linux-test:)), and I think it is fantastic. But a strange problem I have, is that all folders in the Places menu seems to be linked to Rhythmbox. When I click on Desktop or Home Folder, Rhythmbox starts... All the locations in the places menu, except Network and Computer, have the same problem. 
Is there a way to relink the menu items to Nautilus?

---

### Post by vanadium on 2011-01-15
Open a file browser window (does "Places - Computer work? otherwise, press Alt+F2, type "nautilus" then press Enter).

Right-click a folder, select "Open with other application". Select "File Browser" and make sure "Remember the application..." is checked.

Recently, this problem pops up frequently. I do not know, however, how new users could unadvertently change that association easily.

---

### Post by livit on 2011-01-15
Thank you very much! :)

It worked perfectly well and Alt+F2 could be good to know even though Computer worked.
I don't think that I changed the association, but I have played around so much so it is possible...

---

### Post by shifttome on 2011-01-26
thank you very much for a quick  response it worked perfectly! :P

---

### Post by Tobis84 on 2011-02-03
Great quick fix. I guess there was a loss of association at some point. 

It has also been filed as a bug in Launchpad. Perhaps it should be suggested there as well.

[bug #674953]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/674953")

---

### Post by omegaFil on 2011-02-22
I had the same problem and did the steps described, but it didn't work.
I had to change manually file-apps associations editing 

.local/share/applications/mimeapps.list

and removing rhythmbox in **inode/directory** line.

Hope it helps

---

### Post by sjs_bebop on 2011-03-05
[INDENT]> **omegaFil said:**
> I had the same problem and did the steps described, but it didn't work.
I had to change manually file-apps associations editing 

.local/share/applications/mimeapps.list

and removing rhythmbox in **inode/directory** line.

Hope it helps
[/INDENT]    
This worked for me too.  Thanks!

---

### Post by omegaFil on 2011-03-06
> **sjs_bebop said:**
> This worked for me too.  Thanks!

'welcome ;-)

---

