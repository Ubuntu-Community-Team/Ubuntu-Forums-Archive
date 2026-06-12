---
title: "aMule Problem"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by lixianlee1988 on 2011-02-17
[SIZE=3]   Hello All Friends! 
i used aMule to download some files, after it,  i want to copy the files i just downloaded to another directory ,  but, i can not find the directory where the files located
 finally, i find all the files i download or shared in a directory called [/SIZE][SIZE=3][COLOR=Red]Incoming[/COLOR][/SIZE][SIZE=3], the pathname is "[/SIZE][SIZE=3][COLOR=Red]/home/lixian/.aMule/Incoming/[/COLOR][/SIZE][SIZE=3]" 
 
 it seems ok, but then i can't find [/SIZE][SIZE=3][COLOR=Red].aMule[/COLOR][/SIZE][SIZE=3] directory in[/SIZE][SIZE=3][COLOR=Red] lixian(my username)[/COLOR][/SIZE][SIZE=3] directory.

 of course, i use terminal to locate the files and copy it.

 but most of my files' names are so long (also including some chinese character), so type hand by hand is a little kinda boring...:p


 so what  should i do to locate the "[/SIZE][SIZE=3][COLOR=Red].aMule[/COLOR][/SIZE][SIZE=3]" directory just by Graphic Interface(mean click and drag)?


                                                                 LiXian
[/SIZE]

---

### Post by lixianlee1988 on 2011-02-17
Hope some one can help

 i still can not figure it out~~!

---

### Post by Vaphell on 2011-02-18
.aMule is hidden, you need to press ctrl+h to unhide

---

### Post by lixianlee1988 on 2011-02-18
> **Vaphell said:**
> .aMule is hidden, you need to press ctrl+h to unhide


thanks i will try later, hope it does works.

 but why they made this files hidden? i wonder

---

### Post by Vaphell on 2011-02-18
they simply put the Incoming together with Temp in amule config folder (if i remember correctly it was like that in windows too) which is hidden, just like config folders for all other apps (when you do ctrl+h you'll be seriously amazed how much hidden stuff is there in your home :)). Maybe developers thought it's trivial to change destination folder so why bother setting it in a user friendly manner?

---

### Post by gandaran on 2011-02-18
in the amule preferences option set the home user 'downloads' folder (or any other folder) as the default download folder for files then all downloads will be on you visible home folder where you want them to be..

---

