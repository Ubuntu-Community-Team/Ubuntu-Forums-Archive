---
title: "How to run a process in background?"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-21
I tried doing
$ gedit &

but it opens right in front of me. I thought it will get hidden!!

---

### Post by Lateralis on 2010-12-21
Adding the ampersand to the command will run the command in the background, so you retain use of the command line.  But the action itself is still performed.  If you tell Ubuntu to open Gedit, it will open Gedit.  That's what you did and Ubuntu complied. 

Question: why do you want to start Gedit but have it "hidden"?  What are you trying to achieve?

---

### Post by NightwishFan on 2010-12-21
From my experience, most applications do not hide when I do that, they still output to the terminal. However if I do (for example)
```
gedit & exit
```

I can close the terminal.


If I do not run another command after, the command (mostly) just functions normal. Not sure if that is a bug or what, I remember it working before though. (Like in 7.10 or 8.04). It also does this on other distros.

---

### Post by Lateralis on 2010-12-21
Hmmm? 

```

gedit & exit

```

should close the terminal after you hit enter.  I just ran a test and Gedit opens and the terminal closes by itself.  

I really have no idea what you mean by

> 
If I do not run another command after, the command (mostly) just functions normal. Not sure if that is a bug or what, I remember it working before though. 


---

### Post by john77eipe on 2010-12-21
I was not trying to achieve anything my running gedit in the background. All I wanted to do was try how the "command &" works and also the bg command.

I guess i'll have to write a script just for this purpose. 

But my question still stays. Why didn't it work? In fact gedit got focus also. (I wouldn't have cared much if it opened and remained minimized or un-focused)

---

### Post by matt_symes on 2010-12-21
Hi

> **Lateralis said:**
> Hmmm? 

```

gedit & exit

```

should close the terminal after you hit enter.  I just ran a test and Gedit opens and the terminal closes by itself. 

Not if you are running a screen session. It will terminate screen first. It will close the terminal if the command is then run again.

> I tried doing
$ gedit &

but it opens right in front of me. I thought it will get hidden!!

What do you mean by you thought it would get hidden? It is a GUI application. How did you expect to interact with it?

Kind regards

---

### Post by john77eipe on 2010-12-21
So i guess there is no way one could run a GUI application hidden.

---

### Post by CharlesA on 2010-12-21
You can minimze it or move it to a different workspace.

---

### Post by NightwishFan on 2010-12-21
I was just saying GUI apps do not obey giving up control of the terminal. Usually not anyway.

---

