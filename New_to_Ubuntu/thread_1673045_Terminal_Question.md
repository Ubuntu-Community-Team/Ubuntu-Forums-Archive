---
title: "Terminal Question"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by jhargis1012 on 2011-01-21
Hello.

Sometimes when I'm using the terminal, I get stuck in a program and can't figure out how to get back to the prompt.

For example: when I start VIM, I can view files and whatnot, but can't get out once I'm in. I hit ESC to get to "command mode" and then hit "q" and enter, but nothing happens.

Also, is there some standard way to end a program you're in in the terminal and get back to the prompt? I find myself just clicking File and then close window, which I know is like cheating. :)

---

### Post by Smart Viking on 2011-01-21
Usually, <ctrl>+<c> or pressing "q" will exit.

In vim, you press esc, then write ":q", if you haven't saved with ":w" and still want to quit, use ":q!".

---

### Post by Paqman on 2011-01-21
> **jhargis1012 said:**
> 
Also, is there some standard way to end a program you're in in the terminal and get back to the prompt?

It'd be nice if there was, but no.

---

### Post by zeroseven0183 on 2011-01-21
You can open another Terminal (on a new window or a new tab) then "kill" the process.

---

### Post by resqguy on 2011-01-21
> Also, is there some standard way to end a program you're in in the terminal and get back to the prompt?

You can also try <control> <z> which will suspend the program.  You can put the program in the background by typing "bg".  This comes in handy when you want to wait for the program to run while you do other things from the command line.

If you use the bg command note the number next to program/process.  This will be the process number that you reference if you want to kill it.

---

### Post by jhargis1012 on 2011-01-22
Thank you everyone, that is very helpful.

---

