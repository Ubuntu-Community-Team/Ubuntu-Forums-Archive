---
title: "shell question"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by deko220 on 2010-10-14
I've just installed ubuntu server 10 and want to customize my shell prompt.  does US10 run bash?  what files need to be modified to change my prompt from me@hostname$ to something else?

---

### Post by lykwydchykyn on 2010-10-14
I'm pretty sure it's running bash, or maybe dash.  Try "echo $0" to see what shell you're running.

To change your shell prompt you need to set the PS1 variable in your ~/.bashrc file.  

Here's a good tutorial [http://www.funtoo.org/en/articles/linux/tips/prompt/](http://www.funtoo.org/en/articles/linux/tips/prompt/)

---

