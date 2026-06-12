---
title: "keyboard modification"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by almagr on 2009-06-15
my @ key doesn't work (spilt water on it)  Is there a way to simply modify the keyboard configuration?

---

### Post by masux594 on 2009-06-15
water?? hmm.. well, using the xmodmap command you can manually modify the result of every single key of the keyboard.. ..Do you want to change the key for the '@' character?

A

---

### Post by almagr on 2009-06-15
yes. id like to change the key for the '@' character. ideally the ¬ key (to the left of the 1 key)

---

### Post by masux594 on 2009-06-15
sorry, i don't understand what "¬" key stand for.. well, do u want that the characters appears with a single keypress or with a combo [es: Alt Gr + Key  or others ]?

A

---

### Post by almagr on 2009-06-15
a single keypress would be great

---

### Post by masux594 on 2009-06-16
Well, this is vary simple.. the only thing that separate you from the solution is "what is the keycode or the key that i wnat to modify?" .. Ok, then open a terminal en type ```
xev
```
now a little window will open, with the mouse cursor go in.. you will see a sort of log window.. now, press the key u want to substitute with '@'.. in the log file [when u press the key], the log add a line like "KeyPress event [..] keycode=[number] [..]"! Whell This is the number you must use in the following command to update the key 
```
xmodmap -e "keycode [number] = at"
```
But, **BEFORE**, i want that u do a backup of the current keyboard layout by typing [in the home directory]
```
mv .Xmodmap .backup-Xmodmap
```
so, if something go wrong u can restore the previous settings!

A

P.s. Try to see if xev capture the event for the old "@" that u say 'is broken'.. if u see adding the event, means that is not broken at all!

---

### Post by almagr on 2009-06-16
Ok.  The key was coded 49.  But this happens.

alex@alex-laptop:~$ xmodmap -e "keycode [49] = at"
xmodmap:  commandline:1:  bad keycode value
xmodmap:  1 error encountered, aborting.

I tried using the codes of some other non inportant keys, with same result

---

### Post by masux594 on 2009-06-16
Well, I mean without '[' and ']'.. 
```
xmodmap -e "keycode 49 = at "
```A

---

### Post by almagr on 2009-06-16
Thanks. works a treat

---

### Post by almagr on 2009-06-16
[LIST]
[*]How do i make the changes permanent.  When i restarted my laptop, the keyboard change had been undone
[/LIST]

---

### Post by masux594 on 2009-06-17
To make the changes permanently, open a terminal and type 
```
sudo gedit /usr/X11/xinit/XmodMap/.xmodmap
```for creating[if doesen't exists]/editing the file that the sistem boot to load the changes..
add the line the 
```

keycode 49 = at

```save & exit.. Now you're retured in the terminal, type

```

xmodmap /usr/X11/xinit/XmodMap/.xmodmap

```to load the changes, if an error occured, means that the "grammar" of the inserted line was wrong.. if everything go right, now u have the key 49 with the '@'.. Finally try to reboot by typing 
```
sudo reboot
```and see if the changes loads automatically at every start..If not, make me know!

Sysc, A

---

### Post by almagr on 2009-06-17
i opened the xmodmap box.     i entered  keycode 49 = at       and then tried to exit and save it says                                                                        Could not find the file /usr/X11/xinit/XmodMap/.xmodmap.

---

### Post by masux594 on 2009-06-17
Ok, then try that..type ```
sudo gedit
```, add the lines, save the file name as '.xmodmap' into the directory that i told before..

Sysc, A

P.s. Now i'm out of home, typing from a winzoz machine.. So i cannot try directly on ubuntu.. this evening [if this solution doesn't work] i'll try at home then post the exact code!

---

### Post by almagr on 2009-06-17
sorry, i dont understand

---

### Post by masux594 on 2009-06-17
Follow me..
```
sugo gedit
```
into the editor that appears, add the line 
```
keycode 49 = at
```
after paste this line, save the file with the name '.xmodmap' in the folder of your system directory
```
/usr/X11/xinit/XmodMap/
```
.. now close the editor and you will be return to the terminal right?

now[in the terminal] type
```
xmodmap /usr/X11/xinit/XmodMap/.xmodmap
```
for load the changes you save before in the .xmodmap file..
If this command does not return some kind of error, theoretically everything works fine.. If you press the "key 49" that you told before, does appear the '@' character? 

If doesen't work let me know!

Else, if the '@' appears, reboot the machine and try pressing the "key 49" to see if the "key 49" keep the '@' character permanently or not!!

Sysc, A

---

### Post by almagr on 2009-06-17
I cant save in this file, 
/usr/X11/xinit/XmodMap/ as the destination doesnt exist.   my folder xmodmap is located in /usr/share/xmodmap   and contains files such as base.xml and xmodmap.am      Is this where i should save the file? Im aware changes to where the file is saved affects following events

---

### Post by masux594 on 2009-06-17
Hmm.. Save the file into your home directory.. with the name that i told before..
```
/home/YOURUSERNAME/
``` .. Now type the command
```
xmodmap /home/YOURUSERNAME/.xmodmap
``` to load the changes of the file.. and go on with the rest of the previous post [see if that key that you set type the @ character]..

..I'm so sorry but i'm away from home.. In this moment i can't try on ubuntu.. I'm going to try the commands this evening ..

Sysc, A

---

### Post by almagr on 2009-06-17
job done.   thanks a lot for your time

---

### Post by masux594 on 2009-06-17
Don't worry.. the important is not waste it!

Sysc, A

---

