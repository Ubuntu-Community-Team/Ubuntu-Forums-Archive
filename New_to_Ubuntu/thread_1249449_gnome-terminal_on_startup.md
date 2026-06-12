---
title: "gnome-terminal on startup"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by marius_vt on 2009-08-25
Hi Guys,
 
How can I get a gnome-terminal to open at startup.
 
I want to do this with a script
 
Thanks in advance

---

### Post by loomsen on 2009-08-25
Well, create a script, place it somewhere, for example in ~/bin and add a startup entry calling it.

System -> Preferences -> Sessions or StartupApplications (depending on the version of gnome you're running the actual label may vary, but Sys->Pref will be the submenu to look into)

hit add, command: 
~/bin/myscript.sh


inside the script put something like

```

#!/bin/bash
gnome-terminal --options

```

run 
gnome-terminal --help 
to get a list with available options, like geometry for example.

---

### Post by drs305 on 2009-08-25
Edit: Too slow.

For others that don't want a script, or you can just reference the script in the following:

System, Preferences, Startup Applications (or Sessions in older releases).
Add.
For the command: gnome-terminal # or enter the script path/name

Welcome to Ubuntu and the Ubuntu Forums, Marius.

---

### Post by marius_vt on 2009-08-25
Thank you so much for the help,

I get the following
marius@Marius:~/Desktop$ sudo sh ./Dynamips.sh
Failed to contact the GConf daemon; exiting.

This is what I have in my script

#!/bin/bash
gnome-terminal --window

Works great when I run it from a terminal but not when I execute the script

---

### Post by mcduck on 2009-08-25
> **marius_vt said:**
> Thank you so much for the help,

I get the following
marius@Marius:~/Desktop$ sudo sh ./Dynamips.sh
Failed to contact the GConf daemon; exiting.

This is what I have in my script

#!/bin/bash
gnome-terminal --window

Works great when I run it from a terminal but not when I execute the script

There's absolutely no reason to use "sudo" with that script.

You only need it wehnyou need root permissions (and should never use "sudo with graphical applciations anyway, that's what "gksudo" is for).

edit:Also, Gnome-terminal doesn't have such option "--window"..

---

### Post by marius_vt on 2009-08-25
Sorry but I am not using the sudo command,

U have any suggestion for me how to get this working

---

### Post by mcduck on 2009-08-25
> **marius_vt said:**
> Sorry but I am not using the sudo command,

U have any suggestion for me how to get this working

based on your above post you were using sudo.

marius@Marius:~/Desktop$ **sudo** sh ./Dynamips.sh
Failed to contact the GConf daemon; exiting.


If the commands you posted are not commands you try to run, please post run the script in a terminal and post the output here so we can see what you are doing.. :)

---

### Post by marius_vt on 2009-08-25
> **mcduck said:**
> based on your above post you were using sudo.

marius@Marius:~/Desktop$ **sudo** sh ./Dynamips.sh
Failed to contact the GConf daemon; exiting.


If the commands you posted are not commands you try to run, please post run the script in a terminal and post the output here so we can see what you are doing.. :)

OOPS my bad, really sorry.

I am an idiot, ran the command without sudo and work like bom.

Now lets hope it will open when I add this to startup.

Could I run another script after the terminal has launched,

Example:

#!/bin/bash
gnome-terminal --execute /home/marius/Desktop/Dynamips.sh 

I get, "There was an error creating the child process for this terminal"

---

### Post by kaibob on 2009-08-25
> **marius_vt said:**
> Could I run another script after the terminal has launched,
The answer to your question is yes. For example, see this thread:

[http://ubuntuforums.org/showthread.php?p=7841937#post7841937](http://ubuntuforums.org/showthread.php?p=7841937#post7841937)

The manner in which you configure gnome-terminal with the --execute or --command options depends on what the script does.

---

