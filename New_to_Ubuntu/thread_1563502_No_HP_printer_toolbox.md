---
title: "No HP printer toolbox"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Hymer E 650 on 2010-08-29
Hi,
 

 I am a newbie to Ubunto and have searched the forum for an answer but cannot find one.
 

 I have a Dell 1300 Inspiron with an HP 3840 printer that in itself works just fine but I cannot open the toolbox or check ink levels etc.
 

 I followed the instruction ie...


Hewlett-Packard (HP) printers:
    Press Alt+F2, type 
    hp-toolbox and click Run. 
    Select the Supplies tab in the HP Device Manager 
    window which appears to view a summary of ink levels.
    


 but what I got was this.....


Could not open location 'file:///home/owner/hp-toolbox'

Error stating file '/home/owner/hp-toolbox': No such file or directory

 Has anyone got any ideas??
 

 many thanks.

---

### Post by varunendra on 2010-08-29
Have you got hplip-gui installed? It is in Synaptic.

If you have it installed, then you should have its shortcut icon under System>Preferences. Click on it (after installing hplip-gui, if you already haven't) & see if it returns the same error.

If it is already installed, try reinstalling it and then retry opening it.

---

### Post by Hymer E 650 on 2010-08-29
Hi,
 

 Thanks for the fix I did what you said and it worked, brilliant.
 

 For me the strength of Ubunto is this forum it has never failed to fix a problem, many thanks.

---

### Post by varunendra on 2010-08-29
You're welcome!

Sometimes it's just luck & chance. Looks like you've a good luck with Ubuntu. :)

---

