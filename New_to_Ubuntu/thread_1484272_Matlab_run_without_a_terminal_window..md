---
title: "Matlab run without a terminal window."
date: 2010-05-15
forum: New to Ubuntu
---

### Post by sluker on 2010-05-15
I just loaded MatLab R2010a and finally got it to run.  The only thing is it only runs when a terminal window is present.  I'm fairly new at Linux in general but I have seen this before and I don't know what I did to fix it.  Any help?

---

### Post by XCan on 2010-05-15
I suspect you mean that you need to have the terminal window, in which you type "matlab", open as long as you want matlab to run? I can see two easy fixes for this:

1) Start matlab from ctrl+f2
2) Create a launcher on your desktop (more or less a shortcut in Windows). Right click on your desktop -> Create Launcher -> Type in a name in the "Name:" field and the command you start matlab with in the "Command:" field. Now you should be able to start Matlab by simply double-clicking on the launcher.

---

### Post by quadproc on 2010-05-15
> **sluker said:**
> I just loaded MatLab R2010a and finally got it to run.  The only thing is it only runs when a terminal window is present.  I'm fairly new at Linux in general but I have seen this before and I don't know what I did to fix it.  Any help?
I am not exactly sure of what you need but you can put a job into the background this way: run matlab from a terminal command prompt, type ctrl-Z into the terminal [the screen will say "stopped"], and type bg.  The task is now running in the background.

This will only work if matlab can run without a terminal.  Some programs can and some cannot; I do not know about matlab.

quadproc

---

