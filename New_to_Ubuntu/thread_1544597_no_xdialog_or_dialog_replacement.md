---
title: "no xdialog or dialog: replacement ?"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-02
Hello,

I look for a way that a script detects the tty or xterm 
and prompt dialog or xdialog

problem

xdialog and dialog have been removed from repositories :(

---

### Post by frenchn00b on 2010-08-06
```
#!/bin/bash


if [ -z "$DISPLAY" ] ; then
        DIALOG=${DIALOG=dialog}
else
        DIALOG=${DIALOG=Xdialog}
fi

echo "$DIALOG selected due to screen or display checking"





```

---

### Post by kerry_s on 2010-08-06
ubuntu uses zenity.

example:
zenity --info --text="Hello World \!"

---

