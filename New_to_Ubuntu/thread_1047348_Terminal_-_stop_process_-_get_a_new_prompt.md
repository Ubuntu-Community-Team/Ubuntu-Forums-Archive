---
title: "Terminal - stop process - get a new prompt"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by melbs on 2009-01-22
I tried searching and did not find my answer - I may be searching the wrong words.

When I have a terminal open and I have put in a command and it either keeps listing and listing things OR it takes forever and just gives me the black, blinking cursor and I can not enter in any command how do I just get a new prompt? How do I get it to stop whatever it's doing and start over with a new [user@localhost]# ...thanks!! :popcorn:

---

### Post by taurus on 2009-01-22
<Ctrl>c or <Ctrl>z

What was the command that you ran anyway?

---

### Post by roger_1960 on 2009-01-22
Hi

For commands such as "top", pressing the letter Q works (for Quit)

---

### Post by Michael.Godawski on 2009-01-22
hi,

ctrl + c should terminate the command, although it may be too late then.
What are you trying to do and run ?

---

### Post by melbs on 2009-01-22
Well right now I just ran rpm -Va but I have run into this thing a lot and I don't remember which commands they were. I used to just exit out and start another Terminal or tab but figured I might as well just ask here! I am just learning and practicing command line (using vmware) so I am doing exercises along with a book! Thanks for the answer!

---

### Post by arjuntank on 2009-01-22
i have had the same problems it seems that its not the command that is creating the problem but the terminal.
when i open man pages in a maximized terminal window everything appears blank with only the cursor at the bottom of the screen, but when i press the up/down arrows it displays it again, but hey u can have different problems based on may be the command you give
which command did you gave?

---

### Post by The Cog on 2009-01-22
Ctrl-Z will pause the current application and give you a prompt. You can do other things, then enter the command **fg** (short for foreground) to resume the paused task, or **bg** (background) to set it running in the background and give you a new prompt. 

For all the gory details, look at the JOB CONTROL section in **man bash**.

---

### Post by cariboo on 2009-01-22
To exit from a man page press q.

Jim

---

### Post by bsharp on 2009-01-22
> **melbs said:**
> Well right now I just ran rpm -Va

Just so you know, Ubuntu uses the APT package managing system because it is derived from Debian, not Red Hat.

Try looking at
```
man apt-get
```
to learn how to install software in Ubuntu via the command-line.

---

### Post by melbs on 2009-01-22
I am actually using Fedora (the book uses it) but I normally use Ubuntu! I figured it would be the same on both. I should have mentioned that!

---

