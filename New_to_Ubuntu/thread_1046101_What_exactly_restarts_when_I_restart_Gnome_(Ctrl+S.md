---
title: "What exactly restarts when I restart Gnome? (Ctrl+Shift+Alt+Backspace)"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by primaxx on 2009-01-21
Hello,

This have probably been answered earlier, but I was unable to find the answer.
As I wrote in the heading, I need to know what programs and services that restart when I restart Gnome. (Without rebooting the computer.) 
-If it's relevant, I'm trying to figure this out on Ubuntu 8.04 LTS

Thanks in advance for the help! :-)

---

### Post by TheLions on 2009-01-21
it restarts X-server, it acts like you just logged off.

---

### Post by primaxx on 2009-01-21
> **TheLions said:**
> it restarts X-server, it acts like you just logged off.

Thanks for the reply! 
Does this mean that all services that don't have a gui keeps running?

---

### Post by mcduck on 2009-01-21
yes, it does. Only the X server and anything running (or started) inside it will stop (meaning pretty much everything graphical).

So if you open a gnome-terminal and start a CLI program inside it, that program will close as well even though it doesn't have a GUI. It was started inside X session, meaning that the X session is it's parent process. Killing a process will kill all it's child processes as well.

Things running as daemons will of course keep on running no matter how you start them, as daemons detach themselves from their original parent processes and run on their own (init as parent process).

By the way, the shortcut is Ctrl-Alt-backspace, the Shift key isn't needed. ;)

---

### Post by primaxx on 2009-02-03
> **mcduck said:**
> yes, it does. Only the X server and anything running (or started) inside it will stop (meaning pretty much everything graphical).

So if you open a gnome-terminal and start a CLI program inside it, that program will close as well even though it doesn't have a GUI. It was started inside X session, meaning that the X session is it's parent process. Killing a process will kill all it's child processes as well.

Things running as daemons will of course keep on running no matter how you start them, as daemons detach themselves from their original parent processes and run on their own (init as parent process).

By the way, the shortcut is Ctrl-Alt-backspace, the Shift key isn't needed. ;)

So much to do, have forgotten to thank you, sorry! :)

---

