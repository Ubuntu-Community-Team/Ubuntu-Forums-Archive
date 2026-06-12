---
title: "Using Terminal and sudo"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-10-04
I think the difficulty I and lots of other beginners have with Ubuntu is using the terminal. I know how to open it and do sudo or gksudo nautilus when I need permissions. But often I get a not authorized and enter sudo or gksudo nautilus and it doesn't seem to grant permissions. I am not sure what the next step is after sudo for example to mount a device or copy a file or paste. It seems as though the sudo doesn't give permissions oe else I need to know how to study what to do after sudo. I am willing to study a lot but get very frustrated when I can't do normal operations on my own computer.

---

### Post by Pjotrovitz on 2009-10-04
Depends a lot on what you mean by 'normal operations'. Usually, if you need to do something specific, you check the command by the 'man' command. Try typing 'man sudo' for instance.

---

### Post by beastrace91 on 2009-10-04
Care to elaborate on what exactly you are trying to do that you are unable to in terminal? If you have super user permissions it means your issue(s) is(are) stemming from somewhere else, as the super user has permission to do what ever (s)he wants to on the system.

~Jeff

---

### Post by LewRockwell on 2009-10-04
[http://ubuntuforums.org/showthread.php?t=1255407](http://ubuntuforums.org/showthread.php?t=1255407)

.

---

### Post by pedro3005 on 2009-10-04
The command sudo will only execute as root the command on the same line. You can't for instance run sudo then run a bunch of other commands that require root privilegies. For that you need a root shell. To get one, you can run 'sudo -i'.

---

### Post by LewRockwell on 2009-10-04
> **pedro3005 said:**
> The command sudo will only execute as root the command on the same line. You can't for instance run sudo then run a bunch of other commands that require root privilegies. For that you need a root shell. To get one, you can run 'sudo -i'.

so congrats on the circus coming to YOUR town...

.

---

### Post by pedro3005 on 2009-10-04
> **LewRockwell said:**
> so congrats on the circus coming to YOUR town...

.
?

---

### Post by cmcanulty on 2009-10-04
To clarify, I have read a lot about the commands but I don't know how to tell when to uses spaces or/ or when to hit enter, how you know when it's done. That kind of super basic stuff seems to be left out of all the explanations.I am trying to run this set of commands which worked before and I just reinstalled my operating system so I need to do this to set up wireless but when I try it now I get error messages. And yes the folder is still on my desktop.
cd Desktop
cd broadcom-wl-4.80.53.0
cd kmod

sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o
Here is what I get from terminal
cmcanulty@Gateway:~$ cd Desktop
cmcanulty@Gateway:~/Desktop$ cd broadcom-wl-4.80.53.0
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0$ 
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0$ cd kmod
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0/kmod$ 
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0/kmod$ sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o
sudo: b43-fwcutter: command not found
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0/kmod$ 
cmcanulty@Gateway:~/Desktop/broadcom-wl-4.80.53.0/kmod$

---

### Post by Tomone on 2009-10-04
Because of the line:
```
sudo: b43-fwcutter: command not found
```
I would guess that b43-fwcutter isn't installed on your system. Hopefully it's that simple.

Also, the commands:
```
cd Desktop
cd broadcom-wl-4.80.53.0
cd kmod
```

can be combined into a single command:
```
cd Desktop/broadcom-wl-4.80.53.0/kmod
```

---

### Post by wdzieczny on 2009-10-05
Bash is a pain buddy, I've read A Practical Guide To Red Hat Linux and A Practical Guide to Ubuntu Linux to fully understand the xterm and bash shells (and C,Ksh,Ssh,etc...) Permissions are usally R-Read W-Write X-Execute It's kind of confusing but easy to grasp if your willing to take the time to learn it if you go to the piratebay.org you can download a free LPIC-1 guide that will teach you alot about the shell.

---

### Post by credobyte on 2009-10-05
[COLOR=Gray]Command not found[/COLOR] should result in writing a new command:
```
sudo apt-get install b43-fwcutter
```

---

