---
title: "can open gedit as root"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-02-19
hi :)
I have a problem.
I cant open gedit as root.
i mean, if I just run
```
gedit
```
it works but if I run
```
sudo gedit
```
nothing happens. 
what to do?

---

### Post by nick_goodfate on 2011-02-19
try
```
gksu gedit
```

---

### Post by Avidanborisov on 2011-02-19
still, nothing happens...

---

### Post by TeoBigusGeekus on 2011-02-19
Any error messages?

---

### Post by Avidanborisov on 2011-02-19
no,
just nothing happens..

---

### Post by TeoBigusGeekus on 2011-02-19
Could gedit be already open by root?
Output of
```
ps aux | grep gedit
```
?

---

### Post by Avidanborisov on 2011-02-19
OK, gedit is opened by root.
how do I close it?

---

### Post by TeoBigusGeekus on 2011-02-19
```
sudo killall gedit
```
Repeat ps command. If it's still open, repeat killall command.

---

### Post by Avidanborisov on 2011-02-19
Ok thanks :)
problem solved.

---

### Post by TeoBigusGeekus on 2011-02-19
Brilliant! Don't forget to mark the thread as solved.

---

### Post by Avidanborisov on 2011-02-19
hey,
I ran gedit again as root from terminal.
then when I went back to terminal i wanted to be able to write commands to it so I pressed Ctrl+Z.
This brought me back to the normal "user@machine$"
but it made gedit unresponsive so I closed it with Force Quit.
But then the same problem, I couldn't run gedit as root again.
When I typed
```
ps aux | grep gedit
```
it showed that the process is still running so I tried to do
```
sudo killall gedit
```
but that didn't help. The process was still running.
What to so?

---

### Post by TeoBigusGeekus on 2011-02-19
```
sudo killall -s 9 gedit
```
Don't press ctrl-z; press the x button on the gedit window.

---

### Post by Avidanborisov on 2011-02-19
Ok that helped :)
but just a general question:
when I launch a program from the terminal and I dont want to close the program but I want to be able to write again commands to terminal, what should I do?

---

### Post by TeoBigusGeekus on 2011-02-19
You could just open another terminal.

---

### Post by sisco311 on 2011-02-19
> **Avidanborisov said:**
> Ok that helped :)
but just a general question:
when I launch a program from the terminal and I dont want to close the program but I want to be able to write again commands to terminal, what should I do?

Launch it in the background:
```
command **&**
```

You may want to redirect its output to /dev/null:
```
command &> /dev/null &
```

Check out:
[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)
and
[http://mywiki.wooledge.org/BashGuide/JobControl](http://mywiki.wooledge.org/BashGuide/JobControl)

---

### Post by cgroza on 2011-02-19
gnome-terminal supports multiple tabs, just open another one and do you things there.

---

### Post by ajgreeny on 2011-02-19
Actually, it is much less confusing to start gedit with the Alt+F2 run utility and command **gksu gedit**, rather than terminal.  That way you are not left with an open terminal under the gedit window.

---

### Post by TeoBigusGeekus on 2011-02-19
> **ajgreeny said:**
> Actually, it is much less confusing to start gedit with the Alt+F2 run utility and command **gksu gedit**, rather than terminal.  That way you are not left with an open terminal under the gedit window.
...or add a launcher in your menus (something like "gedit as root") with 
```
gksu gedit
```
as its command.

---

### Post by Avidanborisov on 2011-02-19
> **TeoBigusGeekus said:**
> ...or add a launcher in your menus (something like "gedit as root") with 
```
gksu gedit
```
as its command.

actually I already did that :)
I was just wondering if there is anyway to continue work in the terminal without quiting.
nevermind, I will just use a new tab.

---

