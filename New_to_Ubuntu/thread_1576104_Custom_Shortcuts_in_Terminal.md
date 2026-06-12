---
title: "Custom Shortcuts in Terminal?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by malenkylizards on 2010-09-16
I would like to figure out how to create a new terminal command as shorthand for another.  For instance, have "zork" replace "frotz /home/username/Documents/zdungeon.z5"  Can this be done?  If so, how many times would I have to type the longer command to make up the effort involved in making the new command?  :)

---

### Post by s.fox on 2010-09-16
Hello,

I would use an alias.  [Here]("https://help.ubuntu.com/community/AdvancedCommandlineHowto#''alias''%20Command") is a wiki page with more information on how to do so.

-Silver Fox

---

### Post by de Bacon on 2010-09-16
There may be a similar feature already in the keyboard shortcut command structure. For recent commands already used "ctrl"+"p" will bring up the previous command entered/used. Do it a second time it will go to the command entered previous to that, etc.... 

I don't know that this is even helpful to you?  It isn't a canned command but if it is something you use repetitively it can be quite helpful/

---

### Post by malenkylizards on 2010-09-16
de Bacon, that's not quite what I'm looking for.  It's not something I would do repetitively in sequence.  The situation is more like when I would want to play Zork for a few minutes on the bus here and there, but not have to type out a long command or mentally trace the path.

s. Fox, alias is TOTALLY what I'm looking for except it doesn't seem to persist? When I close and reopen the terminal, it doesn't recognize the command.

---

### Post by s.fox on 2010-09-16
> **malenkylizards said:**
> 
s. Fox, alias is TOTALLY what I'm looking for except it doesn't seem to persist? When I close and reopen the terminal, it doesn't recognize the command.

Hello,

I thought that was what you were after. :)

Try putting your alias in ~/.bashrc 

Glad to be of help.

-Silver Fox

---

### Post by marshmallow1304 on 2010-09-16
You can put aliases in ~/.bash_aliases so they'll be persistent.

If it doesn't work at first, check ~/.bashrc to make sure it has something like this:
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```


EDIT: Putting them directly in ~/.bashrc is fine as well.

---

### Post by de Bacon on 2010-09-16
Maybe this thread: [http://ubuntuforums.org/showthread.php?t=1576104](http://ubuntuforums.org/showthread.php?t=1576104) has what you are looking for?

---

### Post by uRock on 2010-09-16
The alias command will do what you want. This [link]("http://www.computerhope.com/unix/ualias.htm") gives a brief description of the command.

Example: I want use **now** instead of the **date** command.

```
rabbit@rabbit-desktop:~$ alias now=date
rabbit@rabbit-desktop:~$ now
Thu Sep 16 15:41:26 PDT 2010
rabbit@rabbit-desktop:~$ 
```**unalias** will undo the alias.

Edit: Sorry s.fox, I didn't look at your link first.

---

