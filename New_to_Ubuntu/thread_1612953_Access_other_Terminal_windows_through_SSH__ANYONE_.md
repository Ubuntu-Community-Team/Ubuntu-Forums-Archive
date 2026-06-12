---
title: "Access other Terminal windows through SSH  *ANYONE? PLEASE HEEELP!*"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by tusharsingal on 2010-11-03
Hello Guys,

I am running Ubuntu 10.04 on my desktop, and Mac OS 10.6 on my laptop. I would like to know a way to view my current open terminals on my desktop from my laptop.

Normally, I use SSH from my Mac to operate the desktop terminal. But, lets say I'm running a server with no GUI (think: Minecraft) and whenever I want to view remotely, I have to physically go to the desktop and shut the current running server down then start it up from my Mac.

**Is there a way, that when I access my desktop through SSH, that I can switch to another terminal window (currently open on the desktop)? **

A native command/program will be fine, but if there is none, then 3rd party is my last resort.

Cmon, pros, help a helpless noob. :(

P.S. I love how :( is under smilies.

---

### Post by alang184 on 2010-11-03
I think you can use the -x switch to initiate a GUI ssh session. Example:

ssh -x user@192.168.1.10

*CORRECTION:*

ssh -X [email]user@xxx.xxx.xxx.xxx[/email]

---

### Post by tusharsingal on 2010-11-03
> **alang184 said:**
> I think you can use the -x switch to initiate a GUI ssh session. Example:

ssh -x user@192.168.1.10

it says "-bash: -x not found"

---

### Post by tusharsingal on 2010-11-03
> **tusharsingal said:**
> it says "-bash: -x not found"

What do I do now?

---

### Post by yeats on 2010-11-03
You can use screen to start a session on the desktop, then when you SSH in, do 

```
screen -x
```

which will allow you to connect to your running terminal.

You can also run multiple screen instances.

---

### Post by yeats on 2010-11-03
> I think you can use the -x switch to initiate a GUI ssh session. Example:

ssh -x user@192.168.1.10

This should be ssh **-X** user@192.168.1.10.  Capital X.

---

### Post by tusharsingal on 2010-11-03
> **chrissharp123 said:**
> This should be ssh **-X** user@192.168.1.10.  Capital X.

And this works from my Mac terminal?

---

