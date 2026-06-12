---
title: "Super-R problem"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by newbie.poster on 2009-05-22
For about a year I was running 7.10, and I had my computer set up to lock the screen when I hit Super-R and a launch a terminal window when I hit Super-L.  I upgraded to 9.04 recently and now the Super-L works, but Super-R does not.  What gives?  Does anyone else experience this problem after upgrading?

---

### Post by coffeecat on 2009-05-22
Have a look in System > Preferences > Keyboard Shortcuts. The option to lock the screen is still there. Try resetting this to your choice of keyboard shortcut if you don't like the default one. Perhaps the upgrade to a newer version of gnome reset the key combination because of a change in the underlying code.

---

### Post by newbie.poster on 2009-05-26
That's what I am saying.  I changed it from the default (whatever that was) to Super-R and it does not work.  Pressing Super-R doesn't do anything although it is supposed to lock the screen now.

---

### Post by anewguy on 2009-05-26
And hence why you need to go through that file and assign the keystrokes you want to the actions.

Dave:)

---

### Post by meindian523 on 2009-05-26
I had created key combinations in gconf-editor and found (kinda) the same problem.Try changing the WM back to metacity if you are using compiz-fusion,the key combinations of Metacity are overridden by Compiz if they clash,and if you are not using Compiz,go right back,delete the key combinations,then set them the same again.Mine worked that way.

---

### Post by newbie.poster on 2009-05-26
> **meindian523 said:**
> Try changing the WM back to metacity if you are using compiz-fusion

Great idea.  How does one switch between Windows managers in Ubuntu?

---

### Post by meindian523 on 2009-05-27
```
sudo aptitude install fusion-icon
```Launch from System>>System Tools.Will appear in tray.Right click>>Select Window manager>>Metacity.

edit: Or simply in CLI ```
metacity --replace
```

---

### Post by newbie.poster on 2009-05-27
Funny, I still cannot get this to work.  I have installed the app you suggested and used it to switch to metacity.  I have then edited the metacity specific gconf-editor section to 

create a command
associate the Super R with the command

And I have also ensured that the lock command was associated with the same key through System --> Preferences --> Keyboard Shortcuts.

Still, hitting that key doesn't work!  What else could it be?  Is there anyway to enable debug logging for keys pressed to see what is happening?

---

### Post by meindian523 on 2009-05-29
Have you done the following:
Alt+F2>>gconf-editor
Navigate to />>apps>>metacity>>keybinding_commands
Select a free command_x
Plug in ```

gnome-screensaver-command --lock
```Then navigate to 
/>>apps>>metacity>>global_keybindings 
Select run_command_x (x is the same as the command_x you selected in keybinding_commands) and type in ```
<Super>R
``` and press return.Upon closing gconf-editor,your keybinding must have taken effect.Otherwise,logout and log back in,and your keybinding should have taken effect.

---

### Post by WorLord on 2009-06-09
> **meindian523 said:**
> Otherwise,logout and log back in,and your keybinding should have taken effect.

YESSSS.  Thank you.  Worked for me.

---

### Post by zcacogp on 2009-06-12
> **meindian523 said:**
> Have you done the following:
Alt+F2>>gconf-editor
Navigate to />>apps>>metacity>>keybinding_commands
Select a free command_x
Plug in ```

gnome-screensaver-command --lock
```Then navigate to 
/>>apps>>metacity>>global_keybindings 
Select run_command_x (x is the same as the command_x you selected in keybinding_commands) and type in ```
<Super>R
``` and press return.Upon closing gconf-editor,your keybinding must have taken effect.Otherwise,logout and log back in,and your keybinding should have taken effect.MeIndian, 

Picking up an old thread ... I've just tried this, using '<Super>e' to try and run nautilus, and '<Super>t' to run gnome-terminal (both of which I am familiar with from XP), but neither of them work ... and I am having the same problems with Keyboard Shortcuts that newbie.poster described. 

I'm running compiz ... is this relevant? 


Oli.

---

### Post by meindian523 on 2009-06-12
Yup.Sometimes keybindings for compiz conflict with gconf-editor keybindings.I had Alt+C for gnome-terminal,but using it in Compiz would center the mouse pointer on the screen(very unnoticeable).Try changing the keybinding to something that doesn't conflict,because I just tested my keybindings after enabling Compiz,and all of them work.

---

