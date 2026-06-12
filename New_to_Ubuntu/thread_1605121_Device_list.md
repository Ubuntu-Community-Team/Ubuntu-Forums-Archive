---
title: "Device list"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by thinkLinuX on 2010-10-24
Hi all,

How can i see the detail on my processor, hdd, ram and maybe some devices attached?

Thank you

---

### Post by SuaSwe on 2010-10-24
> **thinkLinuX said:**
> Hi all,

How can i see the detail on my processor, hdd, ram and maybe some devices attached?

Thank you

Try 'lshw' in Terminal. Not sure if that gives you all the info you need but it'll contain some!

---

### Post by jdmcclung on 2010-10-24
You can see some information including CPU & Memory usage in the menu going to System/Administration/System Monitor

---

### Post by drs305 on 2010-10-24
I like *lshw* as well.

If it's not installed and to make a nice html file on your Desktop:
```
sudo apt-get install lshw
cd ~/Desktop && sudo lshw -html > myhardware.html
```

There's also the gui: lshw-gtk, run with "sudo lshw-gtk -X" or "sudo lshw -X"

---

### Post by thinkLinuX on 2010-10-24
thank you all for the prompt reply :)

---

