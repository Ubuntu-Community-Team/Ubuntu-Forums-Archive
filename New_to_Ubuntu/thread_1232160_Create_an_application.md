---
title: "Create an application"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by mosquetero on 2009-08-05
Hi everyone!

The buttons that control the brightness of my laptop's screen do not work. In order not to get blind I have to write a command in the terminal every time I turn on my computer or it comes from suspension. The first week it is ok but now it is getting annoying. Is it possible to create an application that executes that command automatically every time the computer turns on, so I don't have to bother?

Thanks

---

### Post by LunaticHiatus on 2009-08-05
I use LXDE, but I believe in Gnome you can get access to the keyboard hotkeys. In which case you can type in a combination (like ctrl + l) and type in any command from terminal to run when you hit ctrl + l

---

### Post by jerrrys on 2009-08-05
will create an application under "add to panel" do it?

---

### Post by rideburton56 on 2009-08-05
I don't have a lot of experience, but wouldn't a better way to make a bash script to startup?  I have a couple set up (conky & autostart the terminal) but I am at work and dont have access to my ubuntu box, and i dont remember the format.  

To mosquetero, the way I am reccomending, you would make a small script (3 lines), and then set it up as a startup process.  It would basically do what your doing now, automatically, behind the scenes.  If nobody else responds, I will get back to you in like 8 hours (just started my workday).

What is the command you type into the terminal?

---

### Post by amac777 on 2009-08-05
You can also add a program (or script) to startup under SYSTEM->PREFERENCES->Startup Applications.

---

### Post by LunaticHiatus on 2009-08-05
oh yeah... what amac777 said..

---

### Post by rideburton56 on 2009-08-05
> **amac777 said:**
> You can also add a program (or script) to startup under SYSTEM->PREFERENCES->Startup Applications.

thats what I meant, im a little hazy right now, and not on ubuntu, I need to look at my scripts for the format of the code.

What is the command you type into the terminal to change the brightness?

---

### Post by mosquetero on 2009-08-05
Thank you everyone!

The command I type is:

$ /usr/local/bin/nvclock -S -55

I will try to find how to do that bash script because I think it is the best solution. If I get it, I will let you know rideburton56 otherwise I will appreciate your help.

Thank you again everyone

---

### Post by mosquetero on 2009-08-05
It is done! Thank you very much, I didn't have to create a bash script since I could just write the command in the startup application menu you told me. Thanks a lot everyone

---

### Post by rideburton56 on 2009-08-05
Great!  I had no idea you could just have a custom command run our of startup apps!

---

