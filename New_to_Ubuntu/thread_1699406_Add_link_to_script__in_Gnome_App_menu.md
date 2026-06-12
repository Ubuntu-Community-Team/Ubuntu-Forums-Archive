---
title: "Add link to script  in Gnome App menu?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Deadboy420 on 2011-03-03
Pretty simple...all I want to do is add an item to the Gnome Applications Menu, which I know how to do, BUT the problem is the syntax for the command. It's an executable script in my home folder, and I need a single command to enter the folder and execute the script so I can add it to the Gnome menu. I figured it out in a terminal window but the same command won't work from the Gnome App menu. This is the terminal command:

```
cd /home/john/Programs/ && sudo ./script
```

So, how can I get this same command (or one which does the same thing) to work as a shortcut item in Gnome menu?

---

### Post by turtle153 on 2011-03-03
The problem may come from the sudo in the script

Create a .sh file like```

cd /home/john/Programs/
./script
``` and call it .menu_script.sh or something (a dot . before the name makes it hidden)

You can then call gksudo /home/john/.menu_script.sh

ACTUALLY....... why dont you just run gksudo /home/john/Programs/script ?

---

### Post by Deadboy420 on 2011-03-03
I forgot to mention the actual error I receive is:   "Failed to execute child process "cd" (No such file or directory)"   but it works in terminal.  It seems like it's the path to the file has to be fixed but I don't know what it could be since it works in a terminal window.

---

### Post by turtle153 on 2011-03-03
I got that error when testing, but why cant you direct link to the file? gksudo /home/john/Programs/script surely would be more efficient.

---

### Post by PunkLV on 2011-03-03
Gnome itself cant **cd**.
```
sudo gedit /usr/bin/**call_script**
```
insert
```
#!/bin/bash
# Myscript for something
cd ~/Programs/
sh my_script.sh
```
After relog add launcher with *Command*:
```
**call_script**
```
or test it (Alt+F2) without reloging:
```
sh /usr/bin/**call_script**
```
Brutal way of doing this. Actually any info about that script of yours might fasten things up to a neater solution.

---

### Post by Deadboy420 on 2011-03-03
> **turtle153 said:**
> I got that error when testing, but why cant you direct link to the file? gksudo /home/john/Programs/script surely would be more efficient.

I tried it but nothing happens. Let me give you some more information. The script i'm trying to add to the App Menu is a WepCrackGUI gtk script. It executes by simply cd into the folder and "sudo ./wepcrack" Here is the contents of the script: 

```
#!/bin/sh
GKSU=`which gksu`
test $GKSU && OPT=-k
export MONO_DISABLE_SHM=1
exec $GKSU $OPT mono "./GWepCrackGui.exe" "$@"
```

---

### Post by Deadboy420 on 2011-03-03
> **PunkLV said:**
> Gnome itself cant **cd**.
```
sudo gedit /usr/bin/**call_script**
```insert
```
#!/bin/bash
# Myscript for something
cd ~/Programs/
sh my_script.sh
```After relog add launcher with *Command*:
```
**call_script**
```or test it (Alt+F2) without reloging:
```
sh /usr/bin/**call_script**
```Brutal way of doing this. Actually any info about that script of yours might fasten things up to a neater solution.

I don't know if it's a brutal solution but it is certainly a solution. Got it working, thanks!

---

### Post by PunkLV on 2011-03-03
So, basically, your script does:
```
export MONO_DISABLE_SHM=1
gksudo -k mono ./GWepCrackGui.exe $@
```
Soo this makes things easier.
```
sudo gedit /usr/bin/**WCG**
```
```
#!/bin/bash
# Launch WCG
cd ~/Programs
GKSU=`which gksu`
test $GKSU && OPT=-k
export MONO_DISABLE_SHM=1
exec $GKSU $OPT mono "./GWepCrackGui.exe" "$@"
```
and the rest stays the same.

Btw stealing interwebs is bad.

---

