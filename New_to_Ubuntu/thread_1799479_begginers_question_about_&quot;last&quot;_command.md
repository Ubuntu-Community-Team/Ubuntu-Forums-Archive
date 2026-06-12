---
title: "begginers question about &quot;last&quot; command"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by werty2010 on 2011-07-07
so i tried the "last" command today and part of the output was:
```

any      pts/0        :0.0             Thu Jul  7 23:46   still logged in   
any      tty7         :0               Thu Jul  7 23:45   still logged in   
reboot   system boot  2.6.38-8-generic Thu Jul  7 23:44 - 23:46  (00:01)    
any      pts/1        :0.0             Thu Jul  7 15:53 - 15:57  (00:03)    
any      pts/0        :0               Thu Jul  7 11:28 - 18:55  (07:26)    
any      tty7         :0               Thu Jul  7 11:28 - 18:55  (07:27)    
reboot   system boot  2.6.38-8-generic Thu Jul  7 11:27 - 18:55  (07:27)   

```

so my questions are:
1)what are pts/0-1 and tty7 ?
2)on the 4th line it tells me "15:53 - 15:57", 
but on the the previous line it tells me "11:28 - 18:55". I think this probably will be answered by the 1st but it gives me the impression of going back and forward..anyway if you know please reply.

---

### Post by grahammechanical on 2011-07-07
My guess is that pts = Pseudo Terminal Slave.

Here is a link

[http://en.wikipedia.org/wiki/Pseudo_terminal](http://en.wikipedia.org/wiki/Pseudo_terminal)

And good luck to understanding what it is about.

Regards.

---

### Post by sisco311 on 2011-07-07
> **werty2010 said:**
> 
1)what are pts/0-1 and tty7 ?


The file names of the terminal.

tty - [teletypewriter]("http://en.wikipedia.org/wiki/Teleprinter"). Usually the first six [virtual consoles]("http://en.wikipedia.org/wiki/Virtual_console") (tty1-tty6) provide a text terminal with a login prompt to a shell and the graphical X Window System starts in the seventh virtual console (tty7).

pts - [pseudo terminal]("http://en.wikipedia.org/wiki/Pseudo_terminal"). It indicates that you are logged in in a pseudo terminal application like gnome-terminal, xterm or a similar [terminal emulator]("http://en.wikipedia.org/wiki/Terminal_emulator").

---

