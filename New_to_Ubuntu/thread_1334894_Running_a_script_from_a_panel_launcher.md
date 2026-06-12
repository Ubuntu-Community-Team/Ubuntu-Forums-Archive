---
title: "Running a script from a panel launcher"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by hobo14 on 2009-11-22
I have a script: /path/to/my/script.sh
It's executable (755), and runs fine if I navigate to /path/to/my and double click on the icon for script.sh

I want to run it with a single click on a panel launcher, so I made a custom launcher, with the command "/path/to/my/script.sh" but it doesn't run; nothing happens...

I've tried changing the command to 
"sh /path/to/my/script.sh"
and
"bash /path/to/my/script.sh"

but they didn't help.

What am I doing wrong?

---

### Post by falconindy on 2009-11-22
What does the script do? What (and where) is the output expected? Are there any errors?

If you're expecting a terminal to pop up and output text, it won't happen. You'll need to make the launcher something like "gnome-terminal -x /path/to/script"

This will launch gnome-terminal and immediately fire off the script. However, gnome-terminal will exit after the script finishes. So, add something like this to the end of your script:
```
echo -n "Press enter to quit"
read nil
```

There's also another option (simpler?) using xterm, seen [here](http://ubuntuforums.org/showthread.php?t=276502)

---

### Post by hobo14 on 2009-11-22
It's just a script to launch a java class file that is a little app that I wrote, in the same directory.

Nothing happens at all.  No errors, absolutely nothing.
(But like I said, works fine if I navigate there and double click on the script file)

EDIT: no, not hoping for a terminal, but maybe I should be...?

---

### Post by brij on 2009-11-23
try cd to that directory and run it. I mean before you run actual script add a line which changes working directory to the directory where the script is.

---

