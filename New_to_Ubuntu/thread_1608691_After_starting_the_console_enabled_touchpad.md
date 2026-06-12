---
title: "After starting the console enabled touchpad"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Angel_ok on 2010-10-29
Hello.
To disable the touchpad, I have the script in my home folder
```
#!/bin/bash
id="12"
if xinput list-props 12 | grep -i "device enabled.*1$" &> /dev/null ; then # if on
	xinput set-int-prop 12 "Device Enabled" 8 0
else # if off
	xinput set-int-prop 12 "Device Enabled" 8 1
fi
```

He also successfully loaded with the system up and running on a hotkey.
But when I log into the console (Ctrl + Alt + F1-F6) and exit (Ctrl + Alt + F7) the touchpad is turned on. 
Every time they use the hot key, which is not very convenient.
In what may be the problem?
Thank you.

---

### Post by Angel_ok on 2010-10-30
Up

---

### Post by Angel_ok on 2010-11-01
Up

---

### Post by Angel_ok on 2010-11-03
Up

---

### Post by Angel_ok on 2010-11-16
Up

---

