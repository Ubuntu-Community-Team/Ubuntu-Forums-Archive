---
title: "Unable to get Exclusive lock &amp; 'msttcorefonts'"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Bearz66 on 2011-05-24
Hi, Today I tried to download 'msttcorefonts" via  Ubuntu (ver 10.4)Terminal program, it *always* seems to get stuck on the user agreement without  downloading or installing, so I chose to cancel the hung-up download  attempt.
 

Q: Tried to use SPM but got the following error "This usually means  that another package management application (like apt-get or aptitude)  is already running. Please close that application first.'
 

What do I need to do, to clear the 'get-ap' process & to free up 'Synaptic Package Manager?'
 

Thank you in advance 

 -Bearz

---

### Post by wildmanne39 on 2011-05-24
> **Bearz66 said:**
> Hi, Today I tried to download 'msttcorefonts" via  Ubuntu (ver 10.4)Terminal program, it *always* seems to get stuck on the user agreement without  downloading or installing, so I chose to cancel the hung-up download  attempt.
 

Q: Tried to use SPM but got the following error "This usually means  that another package management application (like apt-get or aptitude)  is already running. Please close that application first.'
 

What do I need to do, to clear the 'get-ap' process & to free up 'Synaptic Package Manager?'
 

Thank you in advance 

 -Bearz
Hi, the process is still running just restart the computer then if it give you another error message post it back here. You can only have one install program open at a time, like software center or synaptic not both, the same for the terminal.

---

### Post by Bearz66 on 2011-05-24
> **wildmanne39 said:**
> Hi, the process is still running just restart the computer then if it give you another error message post it back here. You can only have one install program open at a time, like software center or synaptic not both, the same for the terminal.

Right, I thought the 'get-ap' was most likely still running, even though I canceld the download attempt. Okay, going to restart now.

---

### Post by Bearz66 on 2011-05-24
> **wildmanne39 said:**
> Hi, the process is still running just restart the computer then if it give you another error message post it back here. You can only have one install program open at a time, like software center or synaptic not both, the same for the terminal.


Okay on restart - Synaptic Package Manager (Error Message)

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

---

### Post by Paqman on 2011-05-24
Open up a terminal window and paste in:
```
sudo dpkg --configure -a
```

---

### Post by Bearz66 on 2011-05-24
> **Paqman said:**
> Open up a terminal window and paste in:
```
sudo dpkg --configure -a
```

Reply: 

Okay after cutting & pasting into terminal 'sudo dpkg --configure -a' reply was  desktop:~$

---

### Post by Bearz66 on 2011-05-25
You guys are fantastic, it's solved! lol Thank you, I'm so stoked about Ubuntu, installed 8.10 from cd yesterday, loved it so much I upgraded this morning. Great community, thank you again everyone. 
-B

---

