---
title: "Wine help please?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Cpu12340 on 2010-06-17
Hey guys im new to linux and i kinda messed up i was installin WoW (world of warcraft) via wine and when starting the process i didnt install within the program files folder and justed installed in "C:" andnow the folder is locked and unable to open or move please help i need to feed my addiction(lol jk, but seriously help)


YOUR FRIEND
/CPU12340

---

### Post by ubunterooster on 2010-06-17
press Ctrl+Alt+T and type```
nautilus .wine/drive_c
```Press Enter,

Delete the  WoW files and reinstall WoW

---

### Post by Cpu12340 on 2010-06-17
okay i trust you there isnt any other option

---

### Post by Cpu12340 on 2010-06-17
I just tried what you told me to do and it says i do not have permisions ....i am on the admin account

---

### Post by ubunterooster on 2010-06-17
sudo will do the job: (it opens nautilus as a complete admin)

So press Ctrl+Alt+T and type```
sudo nautilus .wine/drive_c
```Press Enter,

Delete the  WoW files and reinstall WoW

---

### Post by Cpu12340 on 2010-06-17
> **ubunterooster said:**
> sudo will do the job: (it opens nautilus as a complete admin)

So press Ctrl+Alt+T and type```
sudo nautilus .wine/drive_c
```Press Enter,

Delete the  WoW files and reinstall WoW
Not to one up you but i found that after the fact i did "sudo" i was able to open "World of Warcraft" file folder i just from the copied files dragged to new folder and now i am able to run the game .....i am still grateful you help 
THANKS 

Yours Truely
/cpu12340

---

### Post by ubunterooster on 2010-06-17
LOL, you thought of something I did not. Pat yourself on the back. [IMG]http://www.easyfreesmileys.com/smileys/lol-039.gif[/IMG]

---

