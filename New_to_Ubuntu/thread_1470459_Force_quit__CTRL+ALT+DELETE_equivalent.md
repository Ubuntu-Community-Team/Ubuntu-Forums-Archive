---
title: "Force quit / CTRL+ALT+DELETE equivalent?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ajk95 on 2010-05-02
How do I force an application to quit?

---

### Post by racie on 2010-05-02
One way is to hit alt+f2, then type xkill and hit enter.  Now click on the program you would like to force quit.

---

### Post by rabid9797 on 2010-05-02
click it's exit button, you should get a window asking if you want to force quit the application. otherwise you can go to system->administration->system monitor

find the application and kill it

---

### Post by paul88 on 2010-05-02
I find that the best way is to right click the menu bar at the top some were in the middle with nothing there, and then click 'add to panel' this will give you a menu. Simply select force quit. Now when you click the icon which should be added to your menu at the top you will be able to click the window that you want to quit.

---

### Post by armoftheland on 2010-05-03
theres also a neat icon you can add to your task bar that's actually called force quit. then when you run into issues you click that icon then click the window of the program that is beinig a jerk et voila, all better :)

---

### Post by armoftheland on 2010-05-03
oh oops... sorry someone beat me to it #-o

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/newreply.php
my fav way is 
1. Gives the applications eating most of your cpu and mem 
```
top
```

2. Note the name or pid of the process 

[I]if you noted the process name
[/I]```
killall *processname*
```
[I]if you noted the pid
[/I]```
kill *pid*
```

---

