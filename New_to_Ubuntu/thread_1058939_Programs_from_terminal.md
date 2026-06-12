---
title: "Programs from terminal"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-02-03
how do i start a program using the terminal and then automatically return control of the terminal so i can start another program from terminal

Right now I type

```
opera
rythymbox

```

or use an alias 

when I do this I can't type anything into command line until I close opera or rythymbox.

---

### Post by ibutho on 2009-02-03
Put an ampersand at the end of the command e.g.
```
opera &
```

---

### Post by sowelie on 2009-02-03
Like this:

```
rhythmbox &
```

The thing to remember is that when you close the terminal, whichever program you executed will close as well.  A better solution is to press ALT+F2, which brings up a run dialog.

---

### Post by freak42 on 2009-02-03
> **sowelie said:**
> 
The thing to remember is that when you close the terminal, whichever program you executed will close as well.

This is not true, at least not for all programs.

gedit & 
runs fine after exiting the terminal.

---

### Post by cerealtx on 2009-02-03
the & makes the program your running run as a daemon so it should not be exited when u close terminal unless it was not finished loading

---

### Post by mcduck on 2009-02-03
> **cerealtx said:**
> the & makes the program your running run as a daemon so it should not be exited when u close terminal unless it was not finished loading

It makes the program run in background, not as a daemon.

Daemons are processes that run in background, are not under user's direct control, usually run as their own users and have init as host process.

edit: anyway, there's a way to start any program from a terminal and keep it running even if the terminal is closed:
```
nohup command &
```

---

### Post by S0m3th1ngw13rd on 2009-02-03
cool thanks everyone

---

