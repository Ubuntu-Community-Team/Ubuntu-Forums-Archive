---
title: "Killing processes with hotkeys?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Xeoncross on 2010-02-14
I come from windows XP and am used to swiftly killing bad apps with **ctrl + alt + del**. While the Linux core is just as stable as XP - the apps I use on Ubuntu crash just as often as their windows counterparts (actually *more* it seems).

The leaves me with no option but restarting since I can't find any hotkey to take back control of the system and kill the offending app.

What do I have to do to find/enable some sort of proc monitor that can get me out of a locked-up PC?

Found [the answer]("http://www.linuxforums.org/forum/ubuntu-help/74391-ctrl-alt-delete.html#post704064"):

> Click System > Preferences > Hotkeys (Something like that. I dont use english ubuntu sorry for that  )

Click Add and type something to Name section (like TASKMANAGER)
and copy and paste that to command section:

```
gnome-system-monitor
```

come to end of list and set a hotkey for TASKMANAGER (like CTRL ALT DEL)

However, when running the command from anything but the desktop it doesn't work. How do you admin programs that are fullscreen or take over the keyboard keys with their own keys?

---

### Post by lucasart on 2010-02-14
[B]1/ In almost all cases

[/B]System => Administration => System Monitor
is basically the equivalent ot the Task Monitor in Windows, and allows to see the CPU memory usage, which programs are running etc.

**2/ If GNOME isn't answering** (ie the desktop and panels dont respond to clicks etc)

Then it's time to switch to the dark side, very very unfriendly to newbies: type Ctrl+Alt+F2... There you have a Linux terminal, and you'll get all you want with commands: "ps aux|less" to have a detailed report like System Monitor ("q" to exit). To kill a process, use "kill -9 #" where # is the process id (as given by ps aux), or by name with "killall name". But normalle you should never have to resort to that, it's just good to know that even when the interface is ****** up, the invincible Pinguin is still there! Oh type Ctrl+Alt+F7 to come back to GNOME.

---

### Post by Xeoncross on 2010-02-14
That isn't useful if your PC is frozen. 

However, I found another fun command to setup (same as above)

> End a non responsive program without using Ctrl+Alt+Delete [Run Command 5]
"xkill" with super+delete

But it too suffers from only working on the desktop...

**UPDATE**

Part 2 wasn't there when I posted.

---

### Post by lucasart on 2010-02-14
if it is frozen, then you need to try solution number 2/

The terminal, and "ps aux|less" or "ps aux|grep xxx" (xxx is a part of the name) to get the **name** or the **process id**, and kill it via "kill -9 processid" or "kilall name". These commands make o mercy, and will not ask you to wait a split second like Windows Vista tends to do. They will kill anything instantly, even the terminal from which they were launched !!!

i know the terminal isn't a pleasant solution, but if it's frozen... there's nothing else :-(

---

### Post by Xeoncross on 2010-02-14
Thanks, ya I just need to crash something now and try that. ;)

**UPDATE**

Nope, no dice. The terminal only opens when you are on the desktop. If you are inside an app like a fullscreen game or something the key doesn't work.

**UPDATE**

Duh, I had F-lock on which is why it didn't work. Thanks that is the answer.

---

### Post by Xeoncross on 2010-02-15
A friend told me..

Use **Ctrl+Alt+F2** to get a terminal, login as root and use **pkill -f "processname"**. **Ctrl+Alt+F7** to get back.

which also works great (as long as I'm on the desktop) I just need to see if it also works when a fullscreen app freezes.

**UPDATE**

Yep, this solves all my problems. I don't know why it isn't publicized more. Unstable programs are everywhere!

---

