---
title: "Help With Networking Terminal"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Shawn7 on 2008-07-19
Alright I posted the other day about help with my dell laptop I couldnt get a wireless connection. So somebody answered my post with some instructions and it was to follow a lot of command via the terminal, but I'm new to working with a terminal so I need some help on understanding what some of it means so here it goes. OK I had to download a driver which was R151517.EXE so they told me to    unzip -a R151517.EXE  then it says to change directories to the DRIVER directory that was just extracted and gave me this command      cd YOUR-DRIVER-DIRECTORY
             sudo ndiswrapper -i bcmwl5.inf
             sudo ndiswrapper -l
but when I type in cd Driver it says no such directory so heres where I'm confused.

---

### Post by daimaru on 2008-07-19
EDIT: while your on command prompt (eg in terminal) just hit the "TAB" (tabulator) button twice and it should list all the files in the directory. 
basically he told you to unzip the .exe file if that worked you should have a directory in your working path. mabe it is called R151517 just like the exe but without the .exe extension. easiest way is to just issue the ls command in terminal. assuming your in terminal and you are where your R151517.exe file is located you should get this:
```
ls
$R151517.exe
unzip -a R151517.exe
ls
$ R151517/ (means its a directory)
--- now you should be able to cd (change directory) into your new folder
cd R151517 (or what is shown when you issue ls command. the folder that the R151517.exe file extracted to)
--- once your inside the folder you can issue the commands concerning ndiswrapper
sudo ndiswrapper -i bcmwl5.inf
             sudo ndiswrapper -l

```

---

