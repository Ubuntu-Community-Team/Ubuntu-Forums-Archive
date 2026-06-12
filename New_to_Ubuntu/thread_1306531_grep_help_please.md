---
title: "grep help please"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by greiner3 on 2009-10-30
I'm taking a class at the local Community College involving Ubuntu 8.10. We're into files and one of the assignments involves grep commands. The actual problem involves;

Display the lines (in a text file) that contain at least five asterisks *****.

I've tried many times, gone online and quizzed Google, searched my notes from class and tried the 2 Ubuntu books I have; Linux in a Nutshell and Linux+. I get close, try something else which makes my search results worse and then try something else. I've been on this for 5 hours today and while I'm not giving up, I also have 2 other classes this quarter. Lol, one of them is going for Cisco CCNA cert so any help with this would be greatly appreciated for saving me some time.

Thanks.

---

### Post by alphaniner on 2009-10-30
```
grep '\*\*\*\*\*' file
```

Maybe not the only way, maybe not the ideal way, but it seems to work.

Explanation:  Quotes are so the shell does not 'expand' the *.  \ is so the * is treated as the character itself, rather than a 'repetition character' as grep would usually interpret it.

---

### Post by cariboo on 2009-10-30
It is against forum policy to answer homework questions. This thread is closed.

---

