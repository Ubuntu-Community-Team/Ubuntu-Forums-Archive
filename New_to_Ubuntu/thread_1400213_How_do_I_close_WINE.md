---
title: "How do I close WINE ?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by verachion on 2010-02-06
I have installed WINE version 1.138, I use it so that I can run utorrent. the only problem is that once it has opened the only way I can close it is by going in to task manager - processes. I have to use this method as the **closed line is greyed out**

---

### Post by JackRock on 2010-02-06
Did you close all programs and systray icons within Wine?  Usually, mine doesn't close until all sub-processes are closed.

---

### Post by mushwars on 2010-02-06
[s]killall `ps aux | grep wine`[/s]

you will have to do it manually

do 

```
ps aux | grep wine 
```
then killall the program.exe such as Utorrent.exe

---

### Post by verachion on 2010-02-07
> **mushwars said:**
> [s]killall `ps aux | grep wine`[/s]

you will have to do it manually

do 

```
ps aux | grep wine 
```then killall the program.exe such as Utorrent.exe

Instead of using the script above, would it be ok to kill the utorrent.exe process via task manager? why doesn't wine close?

---

### Post by ks07 on 2010-02-07
> **verachion said:**
> Instead of using the script above, would it be ok to kill the utorrent.exe process via task manager? why doesn't wine close?
Killing utorrent from task manager should make no difference compared to killing it from the terminal. The only thing is, you may miss some Wine programs that you would have found using the command given.

---

### Post by verachion on 2010-02-07
> **ks07 said:**
> Killing utorrent from task manager should make no difference compared to killing it from the terminal. The only thing is, you may miss some Wine programs that you would have found using the command given.

OK thanks for your tip I have been learning alot in the last few days.

---

