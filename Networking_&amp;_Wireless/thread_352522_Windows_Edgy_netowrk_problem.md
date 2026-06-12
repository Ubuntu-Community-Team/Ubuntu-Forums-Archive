---
title: "Windows Edgy netowrk problem"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by thegrimgod on 2007-02-03
Here is my problem ,i have  aworking network between my edgy machine and the rest of the windows. I can write to the shared windows folderes , i can copy from them , they can see my share , they can write , use printer , which is attaced to linux machine ..etc.
But when i try to read from a shared windows folder , it always fails :
"Could not open the file smb://myserver/share/back.txt  unexpected error:internal error"
The same goes for any file , i couldnt open my mp3s , my movie files...for that matter, i dont even see a path to open them when i try to use mplayer..i only see my linux machine, after i copy them to desktop , works with no problems  
HELP!! and im new to linux too :P

---

### Post by pay on 2007-02-04
What filesystem are you using?

---

### Post by thegrimgod on 2007-02-04
Funny , i dont even manage that computer , my brother does , and its a server , dont want to connect screen to it now , to see ,and i dont know how to check remotley...in any case i solved it upon reading some more(that is always good)--- all i had to do was edit my fstab file in /etc/ to mount does shares (didnt know that was necessary but app mounting makes the link...zz)..in any case it works now , mounts them corectly upon booting ty for the replay :)

---

