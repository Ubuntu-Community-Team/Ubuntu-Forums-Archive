---
title: "visual effects!!!!!!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-27
i have ububtu 10.1o installed in my laptop.in the beginning itself i set the visual effects to extra but from last few days i am facing a problem.everytime i switch on my laptop the visual settings automatically change to none and i have to reset everytime.once reset it works fine till my machine is not switched off,,anybody please tell me what the problem might be:(:(:(:(:(

---

### Post by Zlatan on 2011-01-27
What kind of laptop you have (specs) and did you check System-Preferences-Additional Drivers?

---

### Post by realzippy on 2011-01-27
..you could add a program to System/Settings/Startup Applications:

Name it what you want,command should be:
 
[B]compiz --replace
[/B]

---

### Post by vivek.pandey on 2011-01-27
> **Zlatan said:**
> What kind of laptop you have (specs) and did you check System-Preferences-Additional Drivers?


thanx for your help
my laptop is a dell inspiron,i3,300 gb hard disk,3 gb ram,1gb graphic card...i saw my additional driver it is ati/amd grahics driver

i dont think its anything to do with drivers or specifications of my laptop.its mostly about some settings that have been changed accidently

---

### Post by realzippy on 2011-01-27
Please look at my post and test this.

---

### Post by vivek.pandey on 2011-01-27
> **realzippy said:**
> Please look at my post and test this.

thanx for your solution it worked:P:P:P:P
but i have one more problem.at first  i thought of posting it a new thread but now i am posting in this thread 
i have configured compiz to desktop cube but here also whenever i am switching on my laptop it automatically changes to desktop wall and i have to reset evrytime i switch on my lapi.. so please help

---

### Post by realzippy on 2011-01-27
?

Other compiz-plugins remain after you set them and rebooted?

---

### Post by vivek.pandey on 2011-01-27
> **realzippy said:**
> ?

Other compiz-plugins remain after you set them and rebooted?

oooo here is a point none of the compiz settings are able to keep themselves once laptop is switched off meaning compiz is the problem .. so do i need to install it once more?

---

### Post by realzippy on 2011-01-27
Have you ever hit (do not do this!) the
"Remember currently running applications" button in System/Settings/StartupApplications/Options?

---

### Post by robertcoulson on 2011-01-27
I am having the same problem on my desktop (not my laptop)..I will be trying that idea realzippy the next time I log onto it...Thanks for the idea.
Robert

---

### Post by vivek.pandey on 2011-01-27
> **realzippy said:**
> Have you ever hit (do not do this!) the
"Remember currently running applications" button in System/Settings/StartupApplications/Options?

may be yes because i thought doing that my system will remember the settings i have done

---

### Post by realzippy on 2011-01-27
*.. so do i need to install it once more?*

Delete the config files,log out.

```
cd $HOME && rm -rf .compiz/ .config/compiz/
```

When logging in again,new vanilla configs are created.

Do not set the desktop effects with right-click desktop aso,use
the compizconfigsettingsmanager(love tool's name),and set your cube and stuff..

---

### Post by realzippy on 2011-01-27
> **neo_aryan said:**
> may be yes because i thought doing that my system will remember the settings i have done

So have a look and uncheck the checkbox if checked   ;-)

---

