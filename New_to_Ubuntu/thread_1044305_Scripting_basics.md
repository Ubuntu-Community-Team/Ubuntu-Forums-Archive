---
title: "Scripting basics"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ray field on 2009-01-19
Trying to get my feet wet with basic bash scripts, with strange results.  Two things I want to be able to do with some frequency:

1) launch Midnight Commander with a mouse click or two

2) edit my dosemu.conf file 



So, I created a file called mc.sh which consists of



#1/bin/bash

mc



Pretty simple.  I put it in /home/me/.gnome2/nautilus-scripts and did sudo chmod 777 mc.sh.  It shows up in the desktop popup under Scripts, but when I choose it, nothing happens at all.



Strangely, when I open a view of the nautilus-scripts folder and click on the file, the dialog asking me if I want to run or display it -- when I choose "run in terminal" it does what I want it to and opens MC; when I choose "run," nothing happens, and when I ask to display it in gedit, nothing at all happens.

---

### Post by emarkd on 2009-01-19
That first line should be 

```
#!/bin/sh
```

---

### Post by ray field on 2009-01-19
> **emarkd said:**
> That first line should be 

```
#!/bin/sh
```

oops, I neglected to say I had tried that.  changed it back again, same behavior!

---

### Post by emarkd on 2009-01-19
Well, does the script work from the terminal?  Try running

```
/home/me/.gnome2/nautilus-scripts/mc.sh
```

and see what happens.  If it works from here, the script is fine and the issue is with how Nautilus is handling it, which I know nothing about.

---

### Post by Sorivenul on 2009-01-19
mc is Midnight Commander, yes? If so, it is a terminal application but will not open a terminal automatically. Try:
[PHP]#!/bin/bash
xterm -e mc[/PHP]

Also make sure the script is executable:
```
chmod +x mc.sh
```

---

### Post by ray field on 2009-01-19
> **Sorivenul said:**
> ms is Midnight Commander, yes? If so, it is a terminal application but will not open a terminal automatically. Try:
[PHP]#!/bin/bash
xterm -e mc[/PHP]

thank you! I changed to gnome-terminal, cause it looks a bit better until I tweak xterm's look.

---

