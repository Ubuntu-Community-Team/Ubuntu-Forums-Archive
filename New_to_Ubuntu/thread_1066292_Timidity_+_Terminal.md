---
title: "Timidity + Terminal"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Glurf on 2009-02-10
In order to use Tux Guitar, I have to start Timidiy via the terminal with

timidity -iA -Os

This keeps timidiy running as long as the terminal is open. So if I close the terminal, Timidity shuts down, and I have to restart it. Instead, I'd like a way to have a script start it up when I log on, and keep it hidden, not in a terminal window. Is there a way to do this, with an .sh file?

---

### Post by thinking2loud on 2009-02-10
If you type:
```
timidity -iA -Os &
```
in a terminal, it will start as a separate process instead of running under your shell.

Stick this line in a file called .bash_login in your home directory.

---

### Post by stoogiebuncho on 2009-02-10
You might be interested in this.  It has some information about how to start Timidity automatically.

[http://www.funnestra.org/ubuntu/gutsy/#timidity]("http://www.funnestra.org/ubuntu/gutsy/#timidity")

---

