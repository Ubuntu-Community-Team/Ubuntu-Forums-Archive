---
title: "Make bash script in panel output to terminal"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Cerapter on 2011-02-22
To make my Ubuntu life easier, I've made some simple bash scripts to start up different sessions of software. I put them in the top panel so that I only need one click. However, some of them are rather... skittish, and might fail if the sleep commands aren't long enough. So I would really like to see their progress in a terminal when I click the buttons, to better know what to do in case of a problem.

So. I already have all the commands in the bash script. Is there a line I can add, that can tell the script to act as if I called it from a terminal? OR might I add something in the shortcut in the top panel?

---

### Post by tjwoosta on 2011-02-22
I think this is what you mean..

If you run gnome-terminal with the -e switch it will execute the command that you give it.

example 
```
gnome-terminal -e firefox
```
(will execute a gnome terminal with firefox running within)

---

### Post by Cerapter on 2011-02-23
Thank you, that is very related, but unfortunately I found it to be unsuccessful for a range of commands. Here's the command I now have in the panel:

```
gnome-terminal -e "/home/cerapter/audio.sh start piano"
```Where audio.sh is a 60-line script. Only the first of these is run, and then the gnome-terminal dies and vanishes! The rest of the commands are not even run in the background. It puzzles me, because I thought this should work.

---

