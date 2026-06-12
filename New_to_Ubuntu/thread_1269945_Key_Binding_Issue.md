---
title: "Key Binding Issue"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Excedio on 2009-09-18
Hey Everyone
 
Trying to do a few key binds using gconf. I want to be able to open OOo Word with F2 Spreadsheet with F3 and so on. Here is how I have it setup...
 
global_keybindings > run_command_5 > F2
keybinding_commands > command_5 > ooffice -writer %F
 
This doesn't seem to produce any results. Can someone tell me if i'm doing something wrong?

---

### Post by Excedio on 2009-09-19
Bump

---

### Post by drs305 on 2009-09-19
If you run that command in a terminal does it work?

I set up metacity's keybindings with the same key/command combination but used the default command which is used in the Applications > Office > OpenOffice.org Writer menu. You can get it by right clicking the main menu, Edit Menus, then selecting the OpenOffice app you want and choosing Properties.

For me, that command was:
> 
openoffice.org3 -writer %U



*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Excedio on 2009-09-19
> ooffice -writer %FIs the command that is used in my menu... :???:

However, I just setup the same thing with my wife's laptop, and it works. I originally tried to use:
> openoffice.org3 -writer %Ubut that actually didn't work. When I used:
> openoffice.org3 -writerit worked beautifully.

The difference between my wife's lappy and my desktop is that my wife uses OOo 3.0 and my desktop uses OOo 3.1... maybe the fact that they use slightly different commands is what's causing it...I wonder what will happen if I remove the %F as I did when I removed the %U from my wife's lappy...

---

### Post by drs305 on 2009-09-19
If you get the command used in Applications, Office, OpenOffice Writer it will work on your version. 

Recently it seems each version uses a slightly different command. The one in your main menu will of course be set up to work with the default installation and will work unless you have installed a newer version as a separate application.

---

