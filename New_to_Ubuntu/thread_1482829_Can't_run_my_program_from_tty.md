---
title: "Can't run my program from tty?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by kapmsd on 2010-05-14
Hi guys!
I developed a small C++ application with Qt for GUI.
It is in /Pjt and I can run from command line using ./Pjt.
But whenever I go to Ctrl+Alt+F1, it fails to execute saying that
"Could not execute ./Pjt from tty's.(err:CANNOT CONNECT TO X SERVER)"

How to solve this?

Thanks in advance for your inputs.

---

### Post by cariboo on 2010-05-14
Put the program in /user/local/bin, make sure it is owned by root and executable, then press Alt-F2 and type the program name.

---

### Post by mhgsys on 2010-05-14
Well ; you could run it from tty; 

(Maybe comes in handy when running it from ssh as well)

be sure to 
```
export DISPLAY=:0
```

edit: and run the command you want to run afterwards ;....

---

