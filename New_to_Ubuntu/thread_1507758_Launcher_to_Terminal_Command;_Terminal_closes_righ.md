---
title: "Launcher to Terminal Command; Terminal closes right away?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by frustratednerd on 2010-06-12
Hi, I'm trying to create a launcher to pwgen (a random password generator that runs in terminal), but every time I launch it, Terminal opens, and then closes right away. 

How do I get Terminal to stay open?

---

### Post by inameiname on 2010-06-12
I add this to whatever script I want to run in the terminal that is in my nautilus-scripts, which I think would work for you too.

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi

If it's a launcher to some script, add that at the beginning of the script, and voila. 

Now, if it's an actual program that was installed, perhaps find the program file (like an .exe would be in Windows, which opens the thing), then right click and select properties, and set it to open in terminal. Just an idea.

---

