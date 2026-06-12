---
title: "[SOLVED] problems installing programs"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by kyalee on 2008-12-24
I was trying to install a program (Buddi, it's a financial program) on this computer (not mine, my Dad's new Dell, it came with Ubuntu preinstalled). I downloaded the .deb file, clicked on it, and tried to install the program. It went okay, but it hung forever while it was trying to get the Java. Eventually I had to do a force quit of the install.

I did a restart of the computer and tried to start again. But this time it tells me that only one software management program is allowed to run at one time. As far as I know, I don't have any other programs running.

I tried a test of installing something from the repositories, but it that too is giving me errors, I think it also thinks that I have an additional program running. What it says in the error notice box is: 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

I've reinstalled several times, but other than that I don't know how to troubleshoot this. I'm totally lost here. I don't install programs except through the repositories or apt-get in the terminal. I've never tried to install using a .deb file before. Help?

---

### Post by mkvnmtr on 2008-12-24
Have you un the command it told you to in the terminal?

---

### Post by atngplusultra on 2008-12-24
sudo dpkg -i [location of .deb file]
although, if it complains about other program managers or whatnot, it may or may not give you a hassle still.

---

### Post by kyalee on 2008-12-24
> **mkvnmtr said:**
> Have you un the command it told you to in the terminal?

No. Since I'm a little out of my league, I didn't want to try that before getting advice and an idea of what the problem might be.

---

### Post by The Cog on 2008-12-24
Try this command at the command line:
> sudo dpkg --configure -a
It usually fixes it.

---

### Post by kyalee on 2008-12-24
Okay, I ran sudo dpkg --configure -a and it seems to be letting me install a test program from the repositories. However, just before it started the install it told me that I have a broken package on my computer and to use the broken filter to find it. Any ideas where I can find that?

---

### Post by smuggly on 2008-12-24
Admin/Synaptic Pkg Mgr/Broken Will Be on the left side under custom sections..smuggly Mark Broken For Removal!

---

### Post by ercferret18 on 2008-12-24
try restarting the computer

---

### Post by balaknair on 2008-12-24
Open Synaptic--> In the left hand pane select 'Custom Filters'--> Now select 'Broken Packages'--> this shows you the broken packages

To fix these, Edit> Fix Broken Packages

---

### Post by kyalee on 2008-12-24
As always, this forum is the best. Thank you all very much for your help. It's fixed now. :)

---

### Post by balaknair on 2008-12-24
Glad to help.

Happy Holidays

---

