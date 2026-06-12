---
title: "Unity has left the building!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by dannymoro on 2011-08-23
Hi I need your help in getting unity back. Been gone for 2 long days.

I installed compwiz , fooled :P with some settings and all that appears is a new backround screen.  No indicators, no unity sidebar.   tried ctrl alt t, but no t appeared.  where's the mf 'n undo key dude? just kidding.  ii would appreciate some technical assistance.
i was just starting to use the screen splitter.
                                                       Danny

---

### Post by hookitup on 2011-08-23
are u using CCSM ?

---

### Post by mcduck on 2011-08-23
Sounds like you enabled some Compiz plugin thatching conflicted with the Unity plugin. You should get a warning when a plugin conflicts with another, it's usually wise to pay close attention to those messages.. ;)

Luckily there is a simple command that should reset the Unity plugin and any conflicting other plugins to default settings. Just open a terminal and run "unity --reset" and it should start working again.

Also the Compizconfig Settings Manager allows you to save, import and export configurations so it's often a good idea to save your working Compiz profile before making any changes to the settings. That makes it lot easier to get back to your old setup if something breaks or after tweaking the settings you decide that they were better before.

---

### Post by hakermania on 2011-08-23
> **mcduck said:**
> Sounds like you enabled some Compiz plugin thatching conflicted with the Unity plugin. You should get a warning when a plugin conflicts with another, it's usually wise to pay close attention to those messages.. ;)

Luckily there is a simple command that should reset the Unity plugin and any conflicting other plugins to default settings. Just open a terminal and run "unity --reset" and it should start working again.

Also the Compizconfig Settings Manager allows you to save, import and export configurations so it's often a good idea to save your working Compiz profile before making any changes to the settings. That makes it lot easier to get back to your old setup if something breaks or after tweaking the settings you decide that they were better before.
Just to add: and as Ctrl+Alt+T doesn't work, just use Ctrl+Alt+F1 and just use
```
DISPLAY=:0 command_here
```
Ctrl+Alt+F7 to return to the GUI!

---

### Post by dannymoro on 2011-08-25
Hi, 
 When I type unity reset as advised unity appeared,  but once i closed out the terminal, unity disappeared again.    
Next, i unistalled compiz . and rebooted.  now all i can see is my screensaver with a black x for the mouse.  ctrl alt t does nothing . i haven't been able to do anything .

thanks for the help. i am working on getting unity back when i have the time.
                                                  Danny

---

### Post by alphacrucis2 on 2011-08-25
> **dannymoro said:**
> Hi, 
 When I type unity reset as advised unity appeared,  but once i closed out the terminal, unity disappeared again.    
Next, i unistalled compiz . and rebooted.  now all i can see is my screensaver with a black x for the mouse.  ctrl alt t does nothing . i haven't been able to do anything .

thanks for the help. i am working on getting unity back when i have the time.
                                                  Danny


The standard Unity requires compiz. Not a good idea to remove compiz. After unity --reset you should have just logged out and back in.

---

