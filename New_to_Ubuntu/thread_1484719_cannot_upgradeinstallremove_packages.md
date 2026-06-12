---
title: "cannot upgrade/install/remove packages"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by sundays211 on 2010-05-16
hi
i cannot use any package management programs as they all pop up with a message every time i open them stating that another package management program is open, when this is not true (as far as I know).
can anyone help?

---

### Post by TironN on 2010-05-16
Ok. Restart and try again.

This will happen if you force close a install/upgrade.

If it's still happening try

```
sudo killall dkpg
```

and try again

---

### Post by sundays211 on 2010-05-16
restarted, now it come up with this error
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I entered the command into the terminal, then the terminal froze after saying:
"setting up openoffice.org-filter-binfilter (1:3.2.0-7ubuntu4) ...

---

### Post by TironN on 2010-05-16
> **sundays211 said:**
> restarted, now it come up with this error
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I entered the command into the terminal, then the terminal froze after saying:
"setting up openoffice.org-filter-binfilter (1:3.2.0-7ubuntu4) ...

This is a sign that when installing openoffice.org-filter-binfilter it was quit. Try:

```
sudo apt-get remove openoffice.org-filter-binfilter
```

also try apt-get update/upgrade. Then reboot and tell me whats going on!

---

### Post by sundays211 on 2010-05-16
cant run apt-get until I run "sudo dpkg --configure -a", which obviously doesn't work

---

### Post by TironN on 2010-05-16
Ok try this

```

cd /var/libdkpg/updates
rm *

```

---

### Post by sundays211 on 2010-05-16
no such directory "/var/libkpg", although there is a directory "/var/lib"

---

### Post by Elfy on 2010-05-16
Perhaps try running the command it gave you give us errors 

```
sudo dpkg --configure -a
```

---

### Post by TironN on 2010-05-16
Sorry that was my typing. I meant:

/var/lib/dpkg/updates/

Sorry again. But try clearing that out!

---

### Post by sundays211 on 2010-05-16
accidentally misspelled "sudo apt-get remove openoffice.org-filter-binfilter", but now it has frozen at "setting up openoffice.org-emailmerg (1:3.2.0-7ubuntu4) ..."

---

### Post by TironN on 2010-05-16
Repeat the process and tips until all the failed packages are gone then reboot and hope!

---

### Post by sundays211 on 2010-05-16
well... it seems to have worked. I hope that these packages aren't necessary.

---

### Post by Elfy on 2010-05-16
What were you doing just before you started having problems? You can check in Synaptic - File - History or if you were using the terminal up or up arrow will show you the history of what you have been doing in there.

The package you removed is there in a default install. You can get it back if necessary later.

---

### Post by TironN on 2010-05-16
It was obviously a problem during the first install of it. You can get it back again if you notice issues!

---

### Post by sundays211 on 2010-05-17
this file was first a problem when I upgraded form 8.04 to 10.04. It froze the entire installer, untill I pressed ctrl-c to stop it installing the particular file.

---

### Post by TironN on 2010-05-17
Ahhh. Yeah an old ctrl-c will screw it about right old.

---

### Post by sundays211 on 2010-05-28
if anyone is still watching this thread, It didnt work. when I upgraded just before, It froze yet again on openoffice.org-emailmerge.

---

### Post by TironN on 2010-05-28
Yeah I'm still here but as lost as you. You may need to install JRE as I have seen a lot of issues relating to openoffice and Java.

---

### Post by sundays211 on 2010-05-29
well.. I have removed both openoffice and jre.can you tell me how to re-install them please.

---

