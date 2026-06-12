---
title: "Tethering"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Majiq on 2009-03-04
Hi everyone,

So I think most of my questions end up being about random behavior that I want to know how to do or see if it is feasible. So here goes:

As a prelude, I know about screen. Screen is not what I want. I just want to assemble some pieces to a puzzle, and this is one of them.

You can start a program in the terminal and send it to the background. Fairly common, fairly easy. From the same terminal, you can bring it back to the foreground. If you were to tell the process to not be told of interrupts (nohup) and you closed the terminal, it would still run. If you were to just type exit (which doesn't send the hup to the background process), it would also close the terminal leaving the process in the background.

If I were to open up a new terminal, is there a way to use, for example, the PID and tether a process to the terminal and then bring it to the foreground, so that, for example, debugging output would end up going to the terminal?

---

