---
title: "[SOLVED] Antivirus said gdm was a virus"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-12-30
This is the background (i think) to my problem. A week ago a run a recursive check of the file system with Clamtk. I set it to quarantine possible viruses and it said it found 3. I tried to delete them but coudn't. The name of one of the files was gdm which i didn't know at the time it was very important. Since then i've got trouble booting the system. Instead of going straight to the log-in window it stops half way and a black screen with lots of lines with numbers and the words ASSUMING DRIVE CACHE: WRITE THROW. In the end i manage to log in, after a couple of minutes. Also I can't switch screens any more, and I don't know if this is part of the same problem.

---

### Post by wolfen69 on 2008-12-30
first off, there are no known linux viruses in the wild. i'm going to assume that your antivirus app removed some needed files. if i were you, i would not use an antivirus program. the only people that may need one are people that pass files along to windows users. and yes, gdm is part of the login process.

perhaps you could remove clamtk and see what happens.

---

### Post by jorge ortega on 2008-12-30
wolfen69: amazing, it really was as simple as that. I removed clamtk as you advised and rebooted. Totally fine, I rebooted again just to be sure: perfect. More than that, I can switch screens again and the log-out window (which i forgot to mention had its issues too) is back to normal. You really made my day, I had already plan to reinstall the whole thing tomorrow. 
I had since learn that linux doesn't have viruses but i never thought of removing clamtk. The rhetoric question is: why on earth there is a linux antivirus program if there isn't any linux viruses? I don't understand that.
Never mind, thatks a lot again.

By the way the irony is, I don't even know what a virus looks like, I had been only three months or less on Windows before switching to Ubuntu.

---

### Post by BatsotO on 2008-12-30
Q :
> the rhetoric question is: Why on earth there is a linux antivirus program if there isn't any linux viruses? I don't understand that.
a :
>  the only people that may need one are people that pass files along to windows users.


---

### Post by Hydrid on 2008-12-30
Virus in Linux? There is no virus IN LINUX and there will NEVER BE ONE ! :)

---

### Post by Skripka on 2008-12-30
> **jorge ortega said:**
> wolfen69: amazing, it really was as simple as that. I removed clamtk as you advised and rebooted. Totally fine, I rebooted again just to be sure: perfect. More than that, I can switch screens again and the log-out window (which i forgot to mention had its issues too) is back to normal. You really made my day, I had already plan to reinstall the whole thing tomorrow. 
I had since learn that linux doesn't have viruses but i never thought of removing clamtk. The rhetoric question is: why on earth there is a linux antivirus program if there isn't any linux viruses? I don't understand that.
Never mind, thatks a lot again.

By the way the irony is, I don't even know what a virus looks like, I had been only three months or less on Windows before switching to Ubuntu.

You don't want to know either.  

Viruses/trojans come in all flavors and possible symptoms/looks.....if you're incredibly lucky-you find the virus before it kills your computer or steals all your personal data-or kills every Win machine on your network-and those of your friends.

---

### Post by LowSky on 2008-12-30
> **Hydrid said:**
> Virus in Linux? There is no virus IN LINUX and there will NEVER BE ONE ! :)

Actually there are linux viruses, but to be infected the virus needs root privaleges, which Ubuntu takes barely allows in the first place.

If linux was more popular then maybe someone would look for a back door or something else, but at 1% (Windows/Apple being the rest) worldwide computer use, infections wont be any time soon.

---

