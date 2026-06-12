---
title: "Opening Program in Wine"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by ProfessorUnicorn on 2011-07-28
I'm trying to open replay media catcher 4 in the terminal. I get this: 

"cannot find L"C:\\windows\\system32\\Replay.exe"

What am I doing wrong? It seemed to install correctly to me... :p

---

### Post by Jonny87 on 2011-07-28
> **ProfessorUnicorn said:**
> I'm trying to open replay media catcher 4 in the terminal. I get this: 

"cannot find L"C:\\windows\\system32\\Replay.exe"

What am I doing wrong? It seemed to install correctly to me... :p

What's the command that your using to run it?

---

### Post by ProfessorUnicorn on 2011-07-28
shane@ProfessorUnicorn:~/Desktop$ wine Replay Media Catcher 4

---

### Post by Jonny87 on 2011-07-28
> **ProfessorUnicorn said:**
> shane@ProfessorUnicorn:~/Desktop$ wine Replay Media Catcher 4

Ok well I get a similar error running one of my apps the same way, Have you tried browsing to the Programs folder to try and find the launcher and clicking it manually?

The location should be something like;
~/.wine/drive_c/Program Files

---

### Post by ProfessorUnicorn on 2011-07-29
In program files I don't see replay.exe... :/ I installed it again but its still the same

---

### Post by CatKiller on 2011-07-29
> **ProfessorUnicorn said:**
> shane@ProfessorUnicorn:~/Desktop$ wine Replay Media Catcher 4
> **ProfessorUnicorn said:**
> 
"cannot find L"C:\\windows\\system32\\Replay.exe"

What am I doing wrong?

You aren't typing what you think you're typing. Notice how you're typing in "Replay Media Catcher 4" but wine is looking for "Replay.exe"? It's because you haven't specified the file properly and Wine is doing its best guess.

Assuming you really do have the executable on your Desktop (which doesn't seem that likely since you said that you'd installed it), you need to run something more like

```
wine ~/Desktop/Replay\ Media\ Catcher\ 4.exe
```

Whatever it is, you might want to check that it actually works in Wine by checking the [AppDB]("http://appdb.winehq.org").

---

