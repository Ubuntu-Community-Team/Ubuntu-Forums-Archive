---
title: "Help installing et-linux-2.60.x86.run'"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by iNeeed on 2008-12-21
Hi I was hoping someone could help with the install process?

I have the file saved to my desktop.
and when I try to run it I get this error message

Could not open the file /home/bryan/Desktop/et-linux-2.60.x86.run using the Unicode (UTF-8) character coding.

Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.


I don't know what this means or what to do.  help?

---

### Post by northern lights on 2008-12-21
This is indeed a binary and you're so far been trying to open it in a text-editor, most likely gedit.

It would need to be made executable (either from the GUI menu, by right clicking the file) or by running```
sudo chmod 774 /home/bryan/Desktop/et-linux-2.60.x86.run
```When double-clicking it now, you should be asked whether you want to run it or view it, alternatively you can run it by executing```
sh /home/bryan/Desktop/et-linux-2.60.x86.run
```

What application is this though? There might be a better and/or easier way of installing.

---

### Post by logos34 on 2008-12-21
try this is terminal:

> cd Desktop 

sudo sh et-linux-2.60.x86.run

---

### Post by iNeeed on 2008-12-21
> **northern lights said:**
> This is indeed a binary and you're so far been trying to open it in a text-editor, most likely gedit.

It would need to be made executable (either from the GUI menu, by right clicking the file) or by running```
sudo chmod 774 /home/bryan/Desktop/et-linux-2.60.x86.run
```When double-clicking it now, you should be asked whether you want to run it or view it, alternatively you can run it by executing```
sh /home/bryan/Desktop/et-linux-2.60.x86.run
```

What application is this though? There might be a better and/or easier way of installing.

Thanks! This got the ball rolling!  Its a game.  Wolfenstein enemy territory
Now I'm stuck in installation.

It says

usr/local/games/enemy-territory

I click ok

Then it says 

No write permission to usr/local/games

Arghh!!

---

### Post by northern lights on 2008-12-21
If you've only set execution rights for the superuser (744, for instance), you need to execute it as root. I.e. make it ```
sudo sh /home/bryan/Desktop/et-linux-2.60.x86.run
```

logos had included that in his post also. It's just that it probably wouldn't have worked before setting permissions either, unless the file was already made executable, which it isn't out of the box after downloading. Your OS trying to open it in an editor right away suggests the same.

---

### Post by iNeeed on 2008-12-21
> **northern lights said:**
> This is indeed a binary and you're so far been trying to open it in a text-editor, most likely gedit.

It would need to be made executable (either from the GUI menu, by right clicking the file) or by running```
sudo chmod 774 /home/bryan/Desktop/et-linux-2.60.x86.run
```When double-clicking it now, you should be asked whether you want to run it or view it, alternatively you can run it by executing```
sh /home/bryan/Desktop/et-linux-2.60.x86.run
```

What application is this though? There might be a better and/or easier way of installing.

Thought I did that, but I guess I didn't because now its working.

Gracias.

---

### Post by northern lights on 2008-12-21
> **iNeeed said:**
> Thought I did that, but I guess I didn't because now its working.

Gracias.

Fair enough. Sorted.

---

### Post by Zimmer on 2008-12-21
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

