---
title: "Why can't I paste a folder?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by MidiJake on 2009-08-04
[FONT="Verdana"][SIZE="3"]I just installed Ubuntu 8.04 then added aMSN. I downloaded a skin for it, extracted the skin folder to Desktop but I can't seem to cut/paste this folder to usr/share/amsn/skins. Permission denied... Why?[/SIZE][/FONT]

---

### Post by Soulcage on 2009-08-04
you have to use: sudo mv to move it.

---

### Post by ubudog on 2009-08-04
You don't have the right privileges.  Open a terminal Applications>Accessories>Terminal and type sudo nautilus.  Enter your password and then try.  You'll have to click on "File System" and then try. :)

---

### Post by deeplee403 on 2009-08-05
Right clicking and changing the properties might help

---

### Post by ubudog on 2009-08-05
> **deeplee403 said:**
> Right clicking and changing the properties might help

Maybe :wink:

---

### Post by credobyte on 2009-08-05
```
sudo mv $HOME/Desktop/skin_folder /usr/share/amsn/skins/

```
[COLOR=DimGray]** Replace *skin_folder* ..[/COLOR]

---

### Post by ubudog on 2009-08-05
> **credobyte said:**
> ```
sudo mv $HOME/Desktop/skin_folder /usr/share/amsn/skins/

```
[COLOR=DimGray]** Replace *skin_folder* ..[/COLOR]

Yes that will work :P

---

### Post by Elep.Repu on 2009-08-05
The main problem Ubudog is that you're editing the system,
in case you're wondering about the terminalism.

Linux doesn't want the wrong people doing this, so you will do so through terminal, and with password.

There are nautilus extensions for opening the current window in terminal.
[http://tinyurl.com/yqjmhk](http://tinyurl.com/yqjmhk)

---

### Post by CatKiller on 2009-08-05
> **MidiJake said:**
> I just installed Ubuntu 8.04 then added aMSN. I downloaded a skin for it, extracted the skin folder to Desktop but I can't seem to cut/paste this folder to usr/share/amsn/skins. Permission denied... Why?

You might want to read [this page]("https://wiki.ubuntu.com/RootSudo").

---

### Post by MidiJake on 2009-08-07
> **ubudog said:**
> Yes that will work :P

It did. Thanks everyone for your help.

---

### Post by colau on 2009-08-16
Or cp command with -R option
```

sudo cp -R $HOME/Desktop/skin_folder /usr/share/amsn/skins/

```

---

