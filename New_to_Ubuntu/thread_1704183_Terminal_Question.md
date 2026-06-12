---
title: "Terminal Question"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by castelinop on 2011-03-10
Hey Everyone,

  Just out of curiosity I was wondering if I could type something in the terminal to open up 
the Passwords and Encryption Keys setting instead of going to 



 Applications->Accessories->Passwords and Encryption Keys


Thanks,

---

### Post by Nickjpost on 2011-03-10
Press ALT + F2 and search for the Passwds and encryption keys launcher there and select 'run in terminal'. This will show the terminal command to execute the launcher for that app

---

### Post by mcduck on 2011-03-10
The "Passwords and Encryption keys"-tool is actually called Seahorse, so running "seahorse" in a terminal will open it.

---

### Post by bwallum on 2011-03-10
> **castelinop said:**
> Hey Everyone,

  Just out of curiosity I was wondering if I could type something in the terminal to open up 
the Passwords and Encryption Keys setting instead of going to 

 Applications->Accessories->Passwords and Encryption KeysYou could try going to System>Preferences>Passwords and Encryption Keys, then left click and hold, drag to the top panel and release. It gives you a shortcut.

You can use this technique for any menu item.

---

### Post by mciverza on 2011-03-10
> **bwallum said:**
> You could try going to System>Preferences>Passwords and Encryption Keys, then left click and hold, drag to the top panel and release. It gives you a shortcut.

You can use this technique for any menu item.

You can also right-click on any menu item to create a desktop shortcut or place a shortcut in a panel.

Was there a particular reason you wanted to run that application from the terminal

If you add a shortcut to your desktop or panel, you will be able to see what the actual application is named by right-clicking on the shortcut and then selecting properties. A new window will open up. The "command" field will contain the application's name (in case you want to run that from a terminal).

---

### Post by castelinop on 2011-03-10
> **mcduck said:**
> The "Passwords and Encryption keys"-tool is actually called Seahorse, so running "seahorse" in a terminal will open it.

Hi thnx, this was what I was looking for. Typing seahorse in the terminal opened it up. No particular reason I wanted to run it from the terminal just was curious if it was possible. I only use Docky and not the panel bar as I removed it so also the Alt+F2 is disabled so kinda stuck using only the terminal. But oh well its not too much of a problem. Probably should not have removed it but will undo my actions if need be.

---

### Post by mcduck on 2011-03-11
> **castelinop said:**
> Hi thnx, this was what I was looking for. Typing seahorse in the terminal opened it up. No particular reason I wanted to run it from the terminal just was curious if it was possible. I only use Docky and not the panel bar as I removed it so also the Alt+F2 is disabled so kinda stuck using only the terminal. But oh well its not too much of a problem. Probably should not have removed it but will undo my actions if need be.

You can easily replace the Alt-F2 dialog from Gnome-Panel with a standalone program that handles the same task. For example Alawalk, Gmrun and GRun provide similar Run dialogs, and you can bind them to launch with the Alt-F2 shortcut... ;)

---

