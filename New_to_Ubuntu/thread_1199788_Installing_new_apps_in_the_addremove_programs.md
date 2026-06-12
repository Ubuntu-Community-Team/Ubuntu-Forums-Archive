---
title: "Installing new apps in the add/remove programs"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by cntrygrl17 on 2009-06-29
I go to Applications>Add/Remove... and from there I select a program and click Apply Changes. A box will appear showing the changes I have selected and I click Apply. Then I type in my password and it starts to install. Then a box appears saying "an error has occured.  The following details are included: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.    it does this even if I select only one app. and on every app. someone please help me?!?

---

### Post by halitech on 2009-06-29
open a terminal and run
```
sudo dpkg --configure -a
```

seems there was an issue installing something recently that has to be completed before you can install anything else

---

### Post by cntrygrl17 on 2009-06-29
But what? And I do I complete it...

---

### Post by halitech on 2009-06-29
hard to say. you could open Synaptic and go to Edit - Fix Broken packages or run the command it give you in the error

---

### Post by cntrygrl17 on 2009-06-29
problem...where do I find this Synaptic thing at? Im new to ubuntu...can ya tell? lol

---

### Post by halitech on 2009-06-29
I'm not completely sure as I'm running Debian with XFCE but I think its under Admin - System - Synaptic Package manager or System - Admin - Synaptic.

---

### Post by cntrygrl17 on 2009-06-29
All i want to do is install java so i can play runescape...do you know how to help me with that?

---

### Post by halitech on 2009-06-29
first you need to fix the current issue, then use synaptic to install ubuntu-restricted-extras

---

### Post by mikewhatever on 2009-06-29
> **cntrygrl17 said:**
> All i want to do is install java so i can play runescape...do you know how to help me with that?

Close all open windows first. Go to Applications->Accessories->Terminal, copy/paste the following command and hit enter, then type your password, hit enter and wait.

**sudo dpkg --configure -a**

---

### Post by cntrygrl17 on 2009-06-29
ok i downloaded the restricted extras...now wat do i do?

---

### Post by halitech on 2009-06-29
I thought java was part of the extras. If its not showing as installed search synpatic for java and install it

---

### Post by cntrygrl17 on 2009-06-29
i did...and i have java enabled on my web browser and it is still showing that i don't have it installed when i try to play runescape

---

