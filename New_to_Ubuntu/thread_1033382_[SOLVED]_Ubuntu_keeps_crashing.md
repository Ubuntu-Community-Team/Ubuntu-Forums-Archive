---
title: "[SOLVED] Ubuntu keeps crashing"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by mac98aop on 2009-01-07
I'm new to Ubuntu on a Dell Mini 9.

All was brilliant but it has started crashing and I can spot no rhyme nor reason? Sometimes the whole thing freezes. Other times just the app and I still have a moving cursor but can't click anything?

1. Is there any key command to force a reset?
2. Is there any command line for the Terminal you can tell me that will give a hint as to what caused the freeze?

Thanks

---

### Post by oilchangeguy on 2009-01-07
you may want to post this in main support, dell ubuntu support.

---

### Post by wizard10000 on 2009-01-07
> **mac98aop said:**
> I'm new to Ubuntu on a Dell Mini 9.

All was brilliant but it has started crashing and I can spot no rhyme nor reason? Sometimes the whole thing freezes. Other times just the app and I still have a moving cursor but can't click anything?

1. Is there any key command to force a reset?
2. Is there any command line for the Terminal you can tell me that will give a hint as to what caused the freeze?

1.  Yup  :)

Ctrl-Alt-Backspace will kill an X session and take you back to gdm.

Ctrl-Alt-Delete will begin an orderly reboot.

If nothing else works Alt-PrtScr-r e i s u b will gracefully restart your machine.  Hold down the Alt and Print Screen keys and type r e i s u b allowing a few seconds between keystrokes.

2.  You can look in system logs for the cause of the freeze.  System --> Administration --> System Log

Or you can do one or more of these in a terminal window -

```
dmesg
```

```
tail /var/log/messages
```

You'll find all your system logs in /var/log - looking there might help as well.

Good luck -

---

### Post by mac98aop on 2009-01-07
> **wizard10000 said:**
> 1.  Yup  :)

Ctrl-Alt-Backspace will kill an X session and take you back to gdm.

Ctrl-Alt-Delete will begin an orderly reboot.

If nothing else works Alt-PrtScr-r e i s u b will gracefully restart your machine.  Hold down the Alt and Print Screen keys and type r e i s u b allowing a few seconds between keystrokes.

2.  You can look in system logs for the cause of the freeze.  System --> Administration --> System Log

Or you can do one or more of these in a terminal window -

```
dmesg
```

```
tail /var/log/messages
```

You'll find all your system logs in /var/log - looking there might help as well.

Good luck -

What is gmd?
The System Log is complicated - what am I looking for?
Ctrl-Alt-Del does nothing.
Nor does Alt-PrtScr?
HELP!

---

### Post by decoherence on 2009-01-07
you can force the graphics system to reset using CTRL ALT Backspace -- unsaved work will be lost, of course.

CTRL ALT Del will restart unless the kernel has panicked.

You can also try CTRL ALT F1 (or another F-key up to F6) which will drop you to the console but leave the graphical desktop running. You can log in and run a program like 'top' to see if something is bogging down the system. If you have a working net connection, type

```
sudo apt-get install htop
```

for a much nicer version of top. (type 'htop' to run it, of course)

Also, you can check the logs which are located in /var/log. For example

```
less /var/log/messages
``` will show you major system events and can give you a clue to some problems.

Interpreting the output is not for the faint of heart and beyond the scope of a single post. Best thing to do is plunge in and ask questions as needed.

---

