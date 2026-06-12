---
title: "cmd for printing terminal view"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by crazypeppo on 2009-05-26
Uh boy I feel dumb... how do I print the contents of my terminal window? I don't want a screen shot, I just want to print what I see in terminal. I know I can copy and paste into open office etc... but is there a command?

---

### Post by nandemonai on 2009-05-26
> **crazypeppo said:**
> Uh boy I feel dumb... how do I print the contents of my terminal window? I don't want a screen shot, I just want to print what I see in terminal. I know I can copy and paste into open office etc... but is there a command?

You can print the output of a command to a txt file like so:

```
ls /home/ > ls.txt
```

That's a real basic example. Instead of showing the output from the 'ls /home/' command on screen it will stick it in a file called ls.txt in the directory you're currently in. The main bit here is the '>' that tells terminal to put the output to a file rater than show on screen.

There may be a way to dump exactly what you see on terminal to a file without doing it this way but I'm not sure how.

Hope that helps.

---

### Post by Bölvaður on 2009-05-26
if you want to copy text from the terminal and paste it onto these forums then:


[LIST=1]
[*]highlight the desired text
[*]right click and select copy
[*]paste by right clicking onto here or use ctrl+v
[/LIST]

alternitivly


[LIST=1]
[*]highlight the desired text
[*]open a place to paste it to.. like click reply to this post, and press middle mouse button (mouse wheel) to paste the highlighted text
[/LIST]


to copy a text into the terminal:


[LIST=1]
[*]Copy the desired command.
[*]select the terminal
[*]press ctrl+alt+v
[/LIST]

---

### Post by crazypeppo on 2009-05-28
Thank you that is what I was looking for nandemonai!

```
ls /home/ > ls.txt
```

---

