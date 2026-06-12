---
title: "keyboard shortcuts"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-19
In Mac OS, I used to set up keyboard shortcuts for typing in some text, launching applications and running scripts. Below are some examples of what I want to do:

1. Type a keyboard shortcut that will fill in my system password whenever a dialog box pops up asking for it. 

2. Type a keyboard shortcut to launch an application, specifically function keys like F1 for Browser, F2 for Email client F3 for Text Editor etc

3. Scope the above keyboard shortcuts: If a particular application uses F2 as a shortcut for doing something then I should be able to disable the F2 shortcut which opens Email client only for that application.
Likewise, I want to scope some keyboard shortcuts in a way that they work only in a particular application and not others. 

Let me know if I am not clear on what I want. 
Basically, Mac applications are developed according to guidelines specified by an Apple. So almost 99% of the applications follow the same trend. For example, the location of the menu item "Preferences" will always be in a particular menu and will always have the same shortcut (Command+,) no matter which application you use. That way you always know most of the shortcuts in any new application even before launching it. Secondly, they avoid using function keys and some other keys completely in any application so that the users can use them globally. 

I would love to know the closest I can get to, doing all this, using Ubuntu.
Thanks.

---

### Post by stoogiebuncho on 2009-11-24
Check out System > Preferences > Keyboard Shortcuts if you haven't already.  You can click the "Add" button to add new ones (I only say that because I somehow didn't see the "Add" button for an embarassingly long time).

I don't know about a shortcut to insert your system password, but there's plenty of options for launching programs.  And, since the shortcut is linked to a command, if you wanted to you could write scripts to do exactly what you want and link the shortcuts to those scripts.

---

### Post by iRounak on 2009-11-25
Thanks for the reply. I had almost lost hope of getting one.
What to Enter in name and command column after clicking "add"?

---

### Post by stoogiebuncho on 2009-11-25
Ok, just for an example, let's set up a shortcut for firefox.

Click "Add".  In the Name field, enter whatever you want ("Firefox Shortcut", or "Firefox" or whatever.  Just to help you remember what the shortcut is for).

In the Command field, enter ```
firefox
```.  This is the command that launches the program or script that you want.

Click OK.  Now find that shortcut in the list of shortcuts.  It will say that it is disabled.  Click on the word "Disabled" and it will become a new field.  Press the key combination that you want the shortcut to be.  It will capture it and set it to your new keyboard shortcut.

Clear as mud?

---

### Post by iRounak on 2009-11-25
Thanks for the reply. I think there is no way I can disable shortcuts set by this method in some specific applications(in other words, when a particular application is active and frontmost) while allowing them to work in other applications. Also, I need shortcuts for launching some files as well, not just applications.

---

### Post by stoogiebuncho on 2009-11-25
This doesn't help with disabling in certain applications but not in others, but you can use this method to open files as well as applications.  Usually the command to do this is the command to open the application you want to use, followed by the location of the file you want to open.  For example, I have a file in my home folder called beep.wav.  If I want to assign a keyboard shortcut to open that in the totem media player, I would enter the following into the "Command" field:

```
totem /home/<computer name>/beep.wav
```

See what I mean?  You can use this to open any type of file in any application.  Anything you can do in the terminal can be linked to a keyboard shortcut, which is just about anything.  You just have to know the command.

---

### Post by iRounak on 2009-11-29
Thanks for the reply.
> This doesn't help with disabling in certain applications but not in othersOne of the other problems I am facing in Ubuntu is this:
If I set a command for launching Firefox and assign it a shortcut like "F1" key, then a new instance of Firefox opens unlike in Mac where if the application was already open, it was merely activated.

---

