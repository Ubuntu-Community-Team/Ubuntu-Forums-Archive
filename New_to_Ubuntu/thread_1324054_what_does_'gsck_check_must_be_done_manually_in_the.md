---
title: "what does 'gsck check must be done manually in the maintinance mode'?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by SheroEg on 2009-11-12
believe it or not, Linux crashes as [windows]("http://eglug.org/glossary/term/87"), even worse.. 
two mega crashes took place in three days in my xubuntu.. the most recent took place right after i installed new necessary updates from the net for my newly-reinstalled system.. 
after i restared the system for the new effects to appear, suddenly i found the system didnt work, leaving me some sort of pla-pla ended as a message appeared in the end : gsck or gcsk check must be done manually in the maintainance mode.. 
my simple questions as a linux novice are: 
1-does this mean that i have to reinstall xubuntu for the second time in three days? 
2-how can i access the maintainance mode? 
3-how can i do the check as the error message told me? 
4-and finally, is this scene frequent after installing updates from the internet, given that the system crashed in the first time when i tried to install xubuntu 9.10 from the internet as well? 
i'd be very grateful for your answers, wishing it could mitigate my shock in my beloved xubuntu..

---

### Post by philinux on 2009-11-12
> **SheroEg said:**
> believe it or not, Linux crashes as [windows]("http://eglug.org/glossary/term/87"), even worse.. 
two mega crashes took place in three days in my xubuntu.. the most recent took place right after i installed new necessary updates from the net for my newly-reinstalled system.. 
after i restared the system for the new effects to appear, suddenly i found the system didnt work, leaving me some sort of pla-pla ended as a message appeared in the end : gsck or gcsk check must be done manually in the maintainance mode.. 
my simple questions as a linux novice are: 
1-does this mean that i have to reinstall xubuntu for the second time in three days? 
2-how can i access the maintainance mode? 
3-how can i do the check as the error message told me? 
4-and finally, is this scene frequent after installing updates from the internet, given that the system crashed in the first time when i tried to install xubuntu 9.10 from the internet as well? 
i'd be very grateful for your answers, wishing it could mitigate my shock in my beloved xubuntu..

Did it say with device/partition e.g /dev/sda1 or sdax whatever. It's fsck by the way. Look it up for an explanation.

If so then at the command prompt do this

```
fsck -v /dev/sd??
```  replace the ? with the correct partition name. If it offers to fix things hit the y key.

---

### Post by SheroEg on 2009-11-13
1-thanks a million, it really worked..:p:p

2-second, what will be the case if the pc gave me a message of failure to mount any drive, as happened to me in the first crash?

---

