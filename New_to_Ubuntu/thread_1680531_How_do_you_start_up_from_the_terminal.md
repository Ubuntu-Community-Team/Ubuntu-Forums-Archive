---
title: "How do you start up from the terminal"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by john geary on 2011-02-02
I was having problems with freezing mouse and keyboard in 10.04 and 10.10 but could start with no problems in recovery mode and failsafe graphics mode, and so changed the login to auto recovery mode,The desktop now appears without the menu bar,but with the terminal,the question is can I complete the startup to alter the login back to default and get the normal startup.thanks in anticipation.

---

### Post by wojox on 2011-02-02
In 10.04 type in the terminal "gnome-control-center" 

Then go to Login Screen and reset it there.

---

### Post by john geary on 2011-02-03
Thanks WOJOX I did as you suggested and got into the login,but unfortunately when I pressed unlock,it just stayed greyed out,and the box asking for the password did not appear,any ideas?

---

### Post by wojox on 2011-02-04
> **john geary said:**
> Thanks WOJOX I did as you suggested and got into the login,but unfortunately when I pressed unlock,it just stayed greyed out,and the box asking for the password did not appear,any ideas?

Try:

```
gksudo gedit /etc/gdm/gdm.conf
```

Look for "AutomaticLoginEnable" and change it to "false"

Save and reboot.

---

### Post by john geary on 2011-02-05
wojox,I,m afraid your going to have to spell it out for me,step by step.I entered the "gksudo gedit"  etc and up came a screen headed---"gdm.conf(/etc/qdm)-gedit" The screen was blank except for the flashing cursor,do I need to enter something else,before or after?I tried this out in KARMIC (which is working perfectly) as well,same thing.

---

### Post by wojox on 2011-02-06
Really?

Alt+F2 

Enter "gdmsetup"

Doesn't let you unlock it?

---

### Post by john geary on 2011-02-07
I found "automaticenablelogin" it was already set at "false".Sorry about the delay in replying but I sometimes have to have numerous tries before the mouse and keyboard does'nt lock up.

---

### Post by john geary on 2011-02-07
Sorry ,I forgot to mention, ALT +F2 doesnt appear to work if the terminal screen is up or the desktop is not fully up.I tested it in Karmic,it worked perfectly.

---

### Post by P4man on 2011-02-07
Sounds to me like this is the wrong solution anyhow (booting in to safe mode). Check the link in my signature and experiment with the various kernel options, especially noapic/nolapic.

---

### Post by john geary on 2011-02-08
The terminal is locked in the top corner of the screen,the menu is not visible so I cant quit and get to the desktop.Is there a terminal command to get to the desktop?

---

### Post by john geary on 2011-02-15
Wojox, many thanks for your help which although it did'nt work because of the nature of the problem,you taught me some useful things,once again thanks.P4man,I reinstalled Meercat using nolapic and nomodeset and its running well,I have marked the bug report which surprisingly says only 3 have reportedthe problem when in fact there are many in absolute beginners!!!many thanks for pointing me in the right direction.

---

