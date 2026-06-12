---
title: "Open program in ssh after closing putty session"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by jchevin on 2010-10-21
Hi all,
i am new to Ubuntu Terminal so this may be a basic question. Say i start a program such as Minecraft server through putty. then i close putty but Minecraft server is still running, can i connect to the server through putty again and access the program again? at the moment it continues to run in the background but i cant actual get to it.
Thanks,
Jchevin

---

### Post by marshmallow1304 on 2010-10-21
You can use the screen command for this.

Basically,
```
screen -S descriptive-name
command-to-run
```
Hold Ctrl and press a then d to detach from the screen.  Now you can
```
exit
```
When you connect again, use
```
screen -dr descriptive-name
```
and you're back where you left off.


Protip: You can also do
```
screen -S descriptive-name command-to-run
```
and the screen session will terminate when the command does.

---

