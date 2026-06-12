---
title: "ssh self"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by c0nrad on 2010-04-25
Hey,

This might be a little random, but, what is happening when I ssh into my own computer?
Like, my computer's name is conrad-laptop, and if i type in:

```
ssh conrad@conrad-laptop
```Thanks,
c0nrad

---

### Post by tom.swartz07 on 2010-04-25
> **c0nrad said:**
> Hey,

This might be a little random, but, what is happening when I ssh into my own computer?
Like, my computer's name is conrad-laptop, and if i type in:

```
ssh conrad@conrad-laptop
```Thanks,
c0nrad

All that youre doing is using ssh to connect to your own computer. Im sure you couldve guessed that. Really theres nothing too fascinating about it other than the fact that it is looping it back into itself over the local network, allowing you to use ssh commands (bash commands) as if it were a remote computer. 


Sometimes people use this ability to copy files from their own computer to a remote through a tunnel on another remote computer.
IE- you connect to a remote computer and then to another one from there. you use the remote computer's connection to securely transfer your files from the computer in front of you to the first host and then to the final host destination. its a bit more secure and a bit harder to trace.

---

