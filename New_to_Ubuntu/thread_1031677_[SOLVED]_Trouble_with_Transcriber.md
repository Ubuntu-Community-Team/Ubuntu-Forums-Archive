---
title: "[SOLVED] Trouble with Transcriber"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by martynmoore on 2009-01-05
Hi all. Happy new year.

I want to use Transcriber and have tried downloading it via Add/Remove, Synaptic and a .deb package.

All appear to install successfully and the program appears in the applications menu under Sound and Video.

But when I try to start the program nothing happens. It's like the command does nothing.

I've checked the properties of the menu item and the command says "Transcriber". The Transcriber folder has been installed to /etc

Any ideas?

---

### Post by donkyhotay on 2009-01-05
Try running the program from the terminal and see if any error messages appear.

---

### Post by martynmoore on 2009-01-05
Brilliant. Thanks very much. I'm not up to speed with Terminal commands, having copied and pasted all the helpful examples from posts, so I tried:

sudo transcriber

Terminal told me it couldn't find "snack" so I installed "libsnack2" via the Synaptic manager.

Transcriber fires up great. Thanks again.

---

### Post by donkyhotay on 2009-01-05
Do *not* use sudo when running normal applications. Sudo gives you root access that can (potentially) damage your system if there is a problem. Whenever you're running a program from the command line just type the command in this case
```
transcriber
```
this will run it regularly (like you would as if from the GUI) but provide the benefit of also giving you any error messages if it doesn't run properly so you can figure out why it won't launch (which you did). Just remember that although we often put sudo in front of the terminal commands here that is because when making system changes they are required. If sudo isn't required don't use it, if your not certain try it without or ask.

---

### Post by martynmoore on 2009-01-06
That's why these forums are so great. Helpful, informative and patient. I've learned so much in two months.

As soon as I'm confident, it will be good to post a few answers for others.

Great community.

---

### Post by donkyhotay on 2009-01-06
Linux teaches you a lot about how a computer really functions. When I started I posted a lot of questions and ended up learning more about X then I really wanted to know (had problems with my radeon x700 when I first installed). If you keep working with it you'll be answering questions rather then asking them in no time.

---

