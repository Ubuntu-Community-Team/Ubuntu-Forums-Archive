---
title: "Natty Narwhal 11.04 terminal Launch commands? no right click?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by marcoftheknight on 2011-06-01
I'm not familiar with Unity and in gnome I was able to put launchers on the desktop and right click and get the terminal commands. In Natty Narwhal I have no clue how to get the terminal command or how to change it for the applications that are in the launcher any clues?

1- Get the launch command fast for the terminal so I can for example open fstab with (terminal command to launch text editor)
2- Change the terminal command ( for example I imagine CCC ati launchs with a command close to this su amdccle for the admistrative one but where the heck is it?)

FYI my control center is frozen if you happen to know a code to kill this process that would be much appreciated also

FYI ctrl-alt-T launches the terminal

Thanks again

---

### Post by frankbooth on 2011-06-01
I'm not sure if I understand what you want to do, but I'll give it a try...
> **marcoftheknight said:**
> In Natty Narwhal I have no clue how to get the terminal command or how to change it for the applications that are in the launcher any clues?

It's usually the name of the application, might be a bit shortened in some cases. Maybe the best way would be to google for the applications you need, or ask here and we might know it. 
> **marcoftheknight said:**
> 
1- Get the launch command fast for the terminal so I can for example open fstab with (terminal command to launch text editor)

Terminal command to launch a text editor:
```

nano file.txt
#or a graphical texteditor:
gedit file.txt

```
> **marcoftheknight said:**
> 
FYI my control center is frozen if you happen to know a code to kill this process that would be much appreciated also

```

#launch a terminal...
top
kill -9 PID

```

---

### Post by marcoftheknight on 2011-06-01
Thanks for the response will try when I get back home. 

What im asking is previously I could check the destop launchers for the terminal code but now Natty narwhal doesn't have that option and I can never remeber the codes to launch the programs in the terminal. How can I find the code quickly in natty narwhal?

Is this more clear?

---

### Post by TerribleLIar on 2011-06-01
Desktop icons seem to have the command to launch from terminal for me, unless they're some different kind of desktop icon. If the program is from the software center, you can look up the application, and under details - version, the terminal command should be in parentheses.

---

