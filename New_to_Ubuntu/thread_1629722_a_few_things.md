---
title: "a few things"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by gr4viton on 2010-11-24
Hi,
I've got a few really noob questions, but i did't find any answers by searching.


First of all, where can I find out which script or application is ran when I press "any" key-shortcut?
I use compiz hotkeys, and recently I've installed xbindkeys.. but in niether of their config i find the hot-key Ctrl+F.. 
(or more precisly i've looked in commands, bcs search throught all the "plugins" is time consuming, or I can say I think there must be better way to search) ( I tried to set another action under hotkey C-f but compiz-config didn't recognize any conflict, so C-f is not set in config ) 
(and in xbindkeys-config there isn't niether )
It started to drive me up the wall when it appeared yasterday, because I use C-f to search in firefox, evince and other app, and now when I press it a "terminal" comes up, but not the usual "gnome-terminal" but some other which is I think it can be described as xfce style because it's bacground is white and the text little smaller than normal. 
So I tried the only thing that I know
```
$ tail -f /var/log/messages 
```Althought this didnt show any line per the application which started.
----------SO MY QUESTION IS---------
Is there a way to find where is the script or which application is controling which keystroke, and change the current behaviour of C-f ?


Next question is really lame, and it hasn't almost any connection with ubuntu itself.
Can I put more lines in one CALC / GNUMERIC / EXCEL cell (Or latex table) and the lines are not aligned to the neighbouring cell?
I do not want to join two cells (one over the others)
I want to have something like
A1 = Three lines, every line have got another font- size -- "vertically centered"
A2 = Two lines, every line can have got another font-size -- "vertically centered"
and the first line of A1 is not on the same "level" as first line in A2 and the same conditions for the others.

If it's not possible it's quite lame, because you are scr**ewed if you want to do something like this (for example in latex)..
[http://www.euroekonom.cz/foto/nhl-tabulka.gif](http://www.euroekonom.cz/foto/nhl-tabulka.gif)
Mind the five last rows (first column = two lines, second col = one line --> and its 'decentralized to each other' )



Another question is about the "gnome-main-menu". About it's changeabilty by the "clicking" manager.
R-Click on the "gnome-start" and "edit menu" or somethings, brings us very not-user-friendly programed manager.. if I want for example make a new folder OOo in Office "folder" and put there all OOo apps (calc..) I must one after the other for every app
Drag-n-drop app to the newly created folder in the left-side tab (it took me some time to find out that it cannot be d-n-d to the folder in the right-tab, bcs if you do so the app dont' copy it self in the folder, it only move it self "up or down" near to the folder..)
so if you dnd the app to the left tab you are than redirected to the "OOo" folder so if you want to move another app you must click on the "office" folder agai.
Its time-consuming, and the final effect is that the original app, stays where it was (in the "office" folder) and it's only copied to the other folder ("OOo") so you must hide it in the office folder. It's not good though because when you now trie to open some file with "another application" and you see the list, you find out that you have 2 same lines for the "OO calc" or anything.
(I know that the "copiing and not moving" thing is probably because of the deletion of "link of the app" in gnome menu after it's uninstallation) 
----------SO MY QUESTION IS---------
Is there a way or another click-application or a config file where I can edit the folders and applications in the gnome-menu, that is not SO NOT-user-friendly?


I know it's maybe very simple but I just cant solve these in my oppinion basic problems of mine.
I would be glad for any suggestions :)
have a nice day !

---

### Post by gr4viton on 2010-11-24
I've overlooked the hotkey ctrl-f, it is in the xbindkeys. 
```
 xbindkeys -k 
``` 
does the trick of getting me know what command is set to what keystroke in xbindkeys 
My question remains.  Where can be detected what command is done when  you press any hot-key and/or which applications is launching this command.

---

