---
title: "Electric Sheep Not Working..."
date: 2009-06-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-11
I'm trying to get Electric Sheep running on Jaunty x64 but it wont work...]

I've tried running it from command line but I get the shortest error I've ever seen...;)

```
carl@carl-desktop ~ $ electricsheep
Terminated

```

lol please help =[

I also get this error when running Electric Sheep Preferences:

```
electricsheep-preferences
```

although it still opens

---

### Post by kd0afk on 2009-06-24
I get the same error when running on a 32 bit system. I have posted on the ES forum but no help. Emailed Scott Draves on his request if it didn't work and he said to stop bothering him. 
Nice huh?

I get this return on debug:

[B]shawn@HAL:~$ electricsheep --debug 1
=====================================
electric sheep v2.7b11
time start Wed Jun 24 17:22:15 2009
initial play counts: 16079:17 16081:33 16324:17 16418:19 16456:31 16457:30 16497:10
updating cache path=/home/shawn/.electricsheep/
updating cache path=/home/shawn/.electricsheep/
begin delete cached 0
time display loop Wed Jun 24 17:22:15 2009
idx=1 ncached_sheep=7 best_atime
found new anim id=16324.
play anim x=1 id=16324 iters=2 path=/home/shawn/.electricsheep/
bumped 16324 to 18, page=31
writing play counts
writing dirty page 31
set atime of 1 to 1245878535
playing /home/shawn/.electricsheep/00243=16324=16324=16324.avi
cleanup_and_exit 1
handle_sig_term display 0
cleanup.
writing play counts
handle_sig_term main 15
cleanup.
writing play counts
handle_sig_term download 15
cleanup.
writing play counts
handle_sig_term display 15
cleanup.
writing play counts
Terminated
shawn@HAL:~$ 

[/B]

---

### Post by kamitsukai on 2009-06-24
Yer I didn't receive much help on there forums...

---

### Post by Chemical Imbalance on 2009-06-24
See this thread:  [http://ubuntuforums.org/showthread.php?t=1196191](http://ubuntuforums.org/showthread.php?t=1196191)

---

### Post by kd0afk on 2009-06-24
I just ran electricsheep - preferences in terminal and I got the preferences, clicked on the "online help" button and it took me to this page.
[http://img514.imageshack.us/img514/3590/screenshotxzl.png](http://img514.imageshack.us/img514/3590/screenshotxzl.png)

---

