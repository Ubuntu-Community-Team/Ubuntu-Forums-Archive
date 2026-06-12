---
title: "Removed Vital Package By Accident"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Da-Chosen-One on 2010-05-21
I was browsing through the Software Manager and saw two entries for Touch Screen software. I thought I don't need that, and just to keep things clean (and save a few Kb) I decided to remove them. When I clicked one I was informed another package would be removed and it sounded important (graphics related maybe or some kind of hardware acceleration) so I cancelled. I tried the other one, titled: Touchscreen common files or something along those lines, and it said the other touch screen package would also be removed. I unthinkingly very stupidly thought 'Great get rid of them both' not realizing the other package would be removed too. I pressed remove and it uninstalled the packages and I am assuming it removed the other one too and suddenly the screen jumped to a black screen with white text. I shutdown and restarted, and when Ubuntu (10.04) tried to boot it warned me about a low graphics mode and asked me to decide whether to "Run in low graphics mode", "Go to terminal", "Shutdown" and "Reconfigure graphics". 
I simply request that someone clicks remove on the touchscreen package and see what the other package it removed was so I can reinstall it! Don't REMOVE it or you may end up like me.... The package to try to remove is the touchscreen one that doesn't have 'common' in it. 
I am assuming I can install them from terminal using 'sudo apt-get install *********' I would appreciate the full names of the three packages and the correct command, if that one isn't right. 
Thanks for reading this poor Ubuntu user's thread, 
Regards Craig

---

### Post by -humanaut- on 2010-05-21
It sounds like your removed important dependencies which happens sometimes on seemingly "useless" programs. sudo find / -mtime -3

see if you can find what dependencies it deleted.

---

### Post by Paqman on 2010-05-21
Without knowing exactly what you removed a good catch-all to start with would be:
```
sudo apt-get install xorg ubuntu-desktop
```

---

### Post by Da-Chosen-One on 2010-05-21
[QUOTE=-humanaut-]It sounds like your removed important dependencies which happens sometimes on seemingly "useless" programs. sudo find / -mtime -3

see if you can find what dependencies it deleted.[/QUOTE]

It turned out I read it wrong and it was actaully "Logon with Console" I tried 'sudo find / -mtime -3' But it just seemed to list every file on my computer.

[QUOTE=Paqman]Without knowing exactly what you removed a good catch-all to start with would be:
```
sudo apt-get install xorg ubuntu-desktop
```[/QUOTE]

It turned out I read it wrong and it was actaully "Logon with Console" I tried 'sudo apt-get install xorg ubuntu-desktop' but I don't think I have any internet access when I login through console.

In the startup log at the end it says:
```
DdxSigGiveup: closing log
```

I would really appreciate it if someone just typed 'touch' into the Software manager and told me the full title (the one that could be entered in console) of the two packages installed by default and the one that it says will also be removed if you remove one of the 'touch' ones.
Thanks again, Craig

---

### Post by Da-Chosen-One on 2010-05-22
*bump* I am going to have to do a full reinstall **(which I have a question about** [**_[COLOR="Blue"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1490552")**)** if someone doesn't help soon and I am sure everyone knows how annoying it is having to do that....

---

### Post by fooman on 2010-05-22
have you tried booting up into the "low graphics mode"....then reinstalling your graphics driver when/if that gets back to the desktop?

---

### Post by Da-Chosen-One on 2010-05-22
No I get nowhere near my desktop. :( It just crashes when I try to go into low graphics mode.....

---

### Post by fooman on 2010-05-22
have you tried choosing recovery mode from the grub menu?

if you can get there....choose "netroot" from the menu (make sure you have ethernet connection),  then try the command paqman suggested above:

```
 sudo apt-get install xorg ubuntu-desktop
```

see where that gets you.

---

