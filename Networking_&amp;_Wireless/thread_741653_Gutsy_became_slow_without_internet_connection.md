---
title: "Gutsy became slow without internet connection"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by nichpakaich on 2008-03-31
I have ubuntu 7.10 installed on my Lenovo G400, dual boot with Win*P (I still don't know why am I keeping that other OS).

Recently, I discovered a new issue with my ubuntu. Everytime I boot it up, everything run very slow. Some application even won't opened (Amarok only show splash screen, then nothing showed up -- there's this blank area on the task bar and the mouse pointer just in idle state on that spot).

So I wen't to my friend's internet cafe to get connected to the internet (this forum), but hey .. everything runs like a dream. What did I do wrong at my place? (I wonder). Then I start to investigate, and came with this conclusion:

[INDENT]Everytime I plug the network cable (which provides internet connection), my ubuntu runs smoothly. But if I unplugged it, everything became sooo slow :confused:[/INDENT]

What could be the problem?

---

### Post by SlavKv on 2008-03-31
I have the same problem on my ASUS 5200A laptop. 
When I work with unpluged wire all applications start very slow.

For example, I wait about 15 sec to start **terminal**, and about 40 sec to start **mc** in terminal.

What's wrong ?

---

### Post by nichpakaich on 2008-04-01
I've search and search, finally I reached  [this thread]("http://ubuntuforums.org/showthread.php?t=230534&page=4") in ubuntuforums as well.

The solution that is working for me:
[INDENT]I change my workgroup, as well my host name for 127.0.1.1
To do this, you got to open System-->Administration-->Network
on general tab, delete workgroup entry,
then on the host tab, change the trailing workgroup name (including the period) 
[/INDENT]
that steps solve my problem :)

---

