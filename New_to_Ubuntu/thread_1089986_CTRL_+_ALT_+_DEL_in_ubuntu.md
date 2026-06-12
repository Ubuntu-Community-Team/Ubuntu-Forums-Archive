---
title: "CTRL + ALT + DEL in ubuntu?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-07
Is there a kind of Task manager or CTRL ALT DEL function for Linux if need be?

How do I end processes etc.. if I need too?

---

### Post by Rolcol on 2009-03-07
You can try System > Administration > System Monitor.  As far as I know, there aren't any key combinations defaulted to open it.

---

### Post by Dr Small on 2009-03-07
```
ps aux | grep programname
kill *pid_id*

::or::

killall programname
```

:D

---

### Post by johnjb on 2009-03-07
Try Ctrl+Alt+Backspace

---

### Post by Rolcol on 2009-03-07
> **johnjb said:**
> Try Ctrl+Alt+Backspace

That restarts X (The window manager).  It will make you have to log back in.  It's not what you want, Gp.

---

### Post by ekaqu on 2009-03-07
there is a Task manager like program in the terminal called top.  it has ways in it to kill processes.

if you know what program is causing the issue, you could use pkill or pgrep to get the process id and use that in the kill command.

ps -ef and ps aux are the same as top but they give a snapshot of all processes where as top is dynamic but only shows what fits on the screen (orders based on cpu%).

---

### Post by The Cog on 2009-03-07
Also, if the errant program has a GUI, you can use the command **xkill** then the next window you click will have its application killed.

---

### Post by anapob on 2009-03-07
Add SYSTEM MONITOR to the panel. So by that way you can activate it by clicking on it and end the "non responding" programs easily without having to go to the terminal.

---

### Post by RedSingularity on 2009-03-07
> **anapob said:**
> Add SYSTEM MONITOR to the panel. So by that way you can activate it by clicking on it and end the "non responding" programs easily without having to go to the terminal.

Thats exactly how i like it.  Nice easy access at the bottom.

---

### Post by aw4lly on 2009-03-08
Theres also a "force quit" icon you can add to the panel, I find that better for killing unresponsive programs. You just click on that button and then on the window you want to kill.

---

