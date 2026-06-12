---
title: "Linker in a Terminal?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by VHDLnub on 2009-10-21
Noob question: How, or can we, run a pointer/linker to a program in a terminal, i.e. bash. Preferably at an elevated permission. (sudo) ;p

---

### Post by eilios on 2009-10-21
For a temporary alias(typing a command will do something), you use the command alias (alias)="(action)", for example ```
alias lol="echo lol"
``` would result in any time you type lol, the word lol appears on screen. For a windows-like shortcut, make a file(call it anything you want, I have a file called " " so the icon is more prominent), open it with gedit(or kate for KDE[or nano for command line]) and do something like this:
```

#!/bin/bash
#The above thing was a shebang, it's important to have it in shell scripts
cd (location) #reduces glitches
./(program) #runs the program

```
If you meant something else, please clarify

---

### Post by VHDLnub on 2009-10-21
Thank you eilios for your quick response, I'll be trying this out...

I'm trying to get the avast/linux "avastgui" pointer to run in sudo so that the avast program will check the files that it does not have permission to run at user level. Prolly' wasting my time cause we know Linux is hard pressed to get/run viruses. I'm not too liberal with root permissions, I don't run my system with sudo on all the time.

---

### Post by eilios on 2009-10-21
> **VHDLnub said:**
> Thank you eilios for your quick response, I'll be trying this out...

I'm trying to get the avast/linux "avastgui" pointer to run in sudo so that it will check the files that it doesn't have permission to run at user level. Prolly' wasting my time cause we know Linux is hard pressed to get/run viruses. I'm not too liberal with root permissions, I don't run my system with sudo on all the time.
If you use ls it will show you(colour wise) which you can run and what(typo'd =P) you can not, if that's what you mean.

---

### Post by VHDLnub on 2009-10-21
Ok, tell me if I'm wrong:

This is the linker location and name: 

```
~/avast_linux/avast4workstation-1.3.0/bin/**avastgui**
```

This is the where the linker points to and it's name:

```
~/avast_linux/avast4workstation-1.3.0/lib/avast4workstation/bin/**wrapper-script.sh**
```

This is my "script" file name and location:

```
~/avast_linux/**" "**
```

This is what my "script" looks like, I want it to run "wrapper-script.sh" in sudo. I think I'm close...But I'm not sure what I'm doing wrong.

```
#!/bin/bash
*#The above thing was a shebang, it's important to have it in shell scripts*
cd ~/avast_linux/avast4workstation-1.3.0/lib/avast4workstation/bin/wrapper-script.sh *#reduces glitches*
./avastgui* #runs the program*
```

---

