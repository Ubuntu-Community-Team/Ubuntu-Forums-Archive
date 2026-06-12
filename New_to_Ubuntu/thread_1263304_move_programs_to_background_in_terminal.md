---
title: "move programs to background in terminal"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Tconnors123 on 2009-09-10
I have been using the MPG123 command in terminal to play mp3 files.  I know there is a way to send the MPG123 program to run in the background so i can continue to use my terminal window.  What is the command i use to send a program to the background and also bring back to the forground?

---

### Post by neurostu on 2009-09-10
There are a few options, if you append:
```

 &

```
then you can keep using the same terminal

if you run a command with 
```

screen <command>

```
you can actually close the terminal and the command will keep running.

if you close the terminal and open a new one, you can regain control of the previous screen session with:
```

screen -R 

```

---

### Post by wojox on 2009-09-10
CTRL Z usually puts a job to the background and you get a bash prompt back , then if u type:```
jobs
``` , all the backgrounded processes are given a job # the you can type:```
fg#
``` and that job will be brought to the fore.

---

### Post by Bachstelze on 2009-09-10
> **Tconnors123 said:**
> What is the command i use to send a program to the background

Ctrl+Z

> **Tconnors123 said:**
> and also bring back to the forground?

[font=monospace]fg %mpeg123[/font]

---

### Post by Tconnors123 on 2009-09-11
thanks for the help

---

### Post by Liolikas on 2009-09-11
It is quite mess to deal with mp3 in this way. 
Better try **mpd** (mpc command for control). ;)

---

### Post by The Cog on 2009-09-11
Ctrl-Z freezes the running command and gives you a command prompt. To let the program carry on in the background, give the command **bg**. To return it to the foreground id **fg**.

---

