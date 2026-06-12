---
title: "XBMC flickering"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by cocodave on 2008-12-11
Hi.
I have installed XBMC onto my ubuntu 8.10 set up, and although it worked initially, it now flickers horribly as soon as i open it. Is there any reason for this too occur?

---

### Post by binbash on 2008-12-11
disable compiz before opening XBMC

---

### Post by cocodave on 2008-12-11
How can i disable compiz without "ending" it in task manager?

---

### Post by emshains on 2008-12-11
Go on to your desktop, right click it, pick "Change desktop background", then, click the tab "Effects", then choose none.

---

### Post by cocodave on 2008-12-11
I have read there is a way to run a script so that the setting changes every time you open a problem which causes a conflict. 

However, is there no way to solve the conflict between compiz and XBMC? Or do I have to choose one or the other to be running at the same time.

---

### Post by emshains on 2008-12-13
Well, all you need to do is make a text file, write this in it ```

#!/bin/bash
metacity --replace
*the command you need to run xmbc*

```


And after that you can do ```

#!/bin/bash
compiz --replace

```
To check what kind of command is used to run xmbc, check the icon on the desktop, or in the "Programs" tab, then drag it to the desktop, and then right-click it, then pick the tab "Launcher", then copy the text from the line "Command", and that will be it.
Then save the files, and make them executable, the graphical way of doing this, is right-clicking them, then selecting "properties", then going to the tab "Permissions", then ticking the boxes under "Execute" or "Run" *Again, I don't remember the right one, because I have a different language set up"

I don't really know how to make just one script out of two of them, but this could just be it.

---

### Post by sanjit on 2008-12-14
Umm...Couldn't you just install 'fusion-icon'? I just change the windows manager to metacity whenever I use XBMC.

To install:

```
sudo apt-get install fusion-icon
```

To run at start up:

System > Preferences > Sessions

Select 'Add'.

Set 'Name' to 'Compiz-Fusion' or something.

Set 'Command' to 'fusion-icon'.

Whenever Compiz is in the way, right-click the Compiz box on the panel and set the window manager to metacity.

---

### Post by emshains on 2008-12-14
> **sanjit said:**
> Umm...Couldn't you just install 'fusion-icon'? I just change the windows manager to metacity whenever I use XBMC.

To install:

```
sudo apt-get install fusion-icon
```

To run at start up:

System > Preferences > Sessions

Select 'Add'.

Set 'Name' to 'Compiz-Fusion' or something.

Set 'Command' to 'fusion-icon'.

Whenever Compiz is in the way, right-click the Compiz box on the panel and set the window manager to metacity.


The compiz-icon never really worked for me though.

---

