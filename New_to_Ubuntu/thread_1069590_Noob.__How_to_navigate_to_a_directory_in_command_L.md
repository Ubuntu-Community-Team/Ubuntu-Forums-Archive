---
title: "Noob.  How to navigate to a directory in command Ln"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-14
(SOLVED)
What I'm trying to do is follow instructions I found here to get an M-Audio Ozone working in Studio.  The directions are clear, but long.  I got pretty far in, but don't know how to get to the directory where something called "Madfuload" is, which is located somewhere on my computer.  It is an exe or something.  I'm not even sure if I'm accessing the command line area properly!  Do you hit ctrl-alt-F2 as I've been doing? Is a re-boot neccessary to get back to the desktop?  
Back to the issue... I put the madfuload download onto my home folder; and when asked to "navigate there" within the command line, I put in "cd /home/my folder name.  This brought me back from the previous directories, but it appears the command lines that followed could not find madfuload.  Help!  The guy who got me started on this stuff (who I need to thank profusely) has just departed for Cali.

---

### Post by Joeb454 on 2009-02-14
Try ```
cd
ls

```

On 2 separate lines. The first will take you back to your home directory, and the 2nd lists all the files in the current directory

---

### Post by Gelateria Punk on 2009-02-14
Thanks to you, profusely as well.

---

### Post by rburkartjo on 2009-02-14
gel to try to locate where you have this file. open the terminal and type whereis (one word) then hit the space bar and then type in the file you are looking for. that should let you know where it is than you can cd to that directory/cheesemaker

---

### Post by thunk77 on 2009-02-14
The "Command Line" is the Terminal. Terminal is located at Applications -> Accessories -> Terminal.
As a default, the Terminal starts you off in your home directory, so if you have the file in there you should see it by typing
```
ls
```
This command lists the files in the directory you are in.
Otherwise, the cd (change directory) command is the way to navigate around your filesystem.

---

### Post by Gelateria Punk on 2009-02-14
O.k.,  thanks for that...  BUT NOW,
I was in the right place, the file is there.
I'm getting this error message, " -bash: syntax error near unexpected token 'newline'  "
I don't think this should happen....

---

