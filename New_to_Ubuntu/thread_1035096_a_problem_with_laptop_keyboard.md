---
title: "a problem with laptop keyboard"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by xieu90 on 2009-01-09
hi everyone
i have bought a lenovo laptop SL500
so far everything works quite well
except one thing

there is a key on the keyboard,when i press it, a menu will pop up like the right button of mouse. i dont know what is the name of that key. it lies between Alt Gr and Ctrl 

in ubuntu when i press this key it wont do anything so i went and check if it is broken physically. in vista (during installation ^^ ) i pressed it and it worked
and then in ubuntu i went to make hotkey, so i chose mute and pressed that key and it changed too
so the key is good.
now how or what i should do so that when i press that key it will work like normal ?
i dont want to press the right button of mouse

---

### Post by jsroth on 2009-01-09
Did you have a look at [Xbindkeys]("http://hocwp.free.fr/xbindkeys/xbindkeys.html")? This one could really help you since you can identify the key and then bind it to a new command, but it needs some time for you reading the manual.

(It's in the repositories, just use 'sudo apt-get install xbindkeys')

---

### Post by xieu90 on 2009-01-09
hi i installed it
but what is it and what should i do now
i dont even see it in the program menu ^^

---

### Post by jsroth on 2009-01-09
I think the best help for you will be to have a look at the website, there even is a quite good example how to use it (its down with a trackball [here](http://linux-trackball.dreamhosters.com/)) this shows how the programm is used for almost every need.

Hope this helps you.

---

### Post by Michael.Godawski on 2009-01-09
hi

you are not the first and not the last:

[http://ubuntuforums.org/showthread.php?t=1024001](http://ubuntuforums.org/showthread.php?t=1024001)



[[IMG]http://hocwp.free.fr/top.png[/IMG]]("http://hocwp.free.fr/xbindkeys/xbindkeys.html#top")  **Configuration**   **xbindkeys** uses a configuration file to link a command to a key on your keyboard.
Usually this (file) is : **$HOME/.xbindkeyrc**

You can edit it yourself or you can have a default one created by using :
**xbindkeys --defaults > $HOME/.xbindkeysrc** 

Look at this as an example :  
[LIST]
[*][**xbindkeysrc** (default)]("http://hocwp.free.fr/xbindkeys/xbindkeysrc_d")
[*][**xbindkeysrc** (1)]("http://hocwp.free.fr/xbindkeys/xbindkeysrc")
[*][**xbindkeysrc** (2)]("http://hocwp.free.fr/xbindkeys/xbindkeysrc_2")
[*][**xbindkeysrc.scm**]("http://hocwp.free.fr/xbindkeys/xbindkeysrc.scm.html") The default guile configuration file
[*][**xbindkeysrc-combo.scm**]("http://hocwp.free.fr/xbindkeys/xbindkeysrc-combo.scm.html") An example of combination keys
[/LIST]

---

### Post by xieu90 on 2009-01-09
i still dont get how to do it
just found this grammar

"(Scheme function)"
    m:0x10 + c:151
    Mod2 + XF86WakeUp

I think i will have to write right mouse button at the place of scheme function, but i wonder what the command is

about the other two line, i have no idea what they means

but right now i just want that key to work

---

### Post by xieu90 on 2009-01-09
cant anyone help me ?
now i just need the command
like open the menu or right button of mouse
somehow i need the command, please !!!

---

### Post by jsroth on 2009-01-09
Since shift + F10 gives you, what you're looking for adding this to your .xbindkeysrc
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Shift_L]\[F10]""
    m:0x0 + c:151
    XF86WakeUp 
```
should help, but first install xvkbd.

---

### Post by xieu90 on 2009-01-09
hi that is exactly what i wanted 
Shift + F10
so how can i do it so that button will do like shift + F10

thank you jsroth
i copied it to /home/ace/.xbindkeysrc
but your code somehow didnt work for me

are there any other method ?

---

### Post by xieu90 on 2009-01-10
isnt there anyone ?

---

### Post by linux_tech on 2009-01-10
If you know the command that you want to bind to the keys you can use gnome-do

---

### Post by linux_tech on 2009-01-10
how to bind keys to command using gnome-do:
[https://wiki.ubuntu.com/GnomeDo/Use](https://wiki.ubuntu.com/GnomeDo/Use)

---

### Post by arjuntank on 2009-01-10
if you are talking about the button having the menu and the mouse pointer on the right than that button is working as it should for me..(ubuntu 8.10)
i wonder why is is not working for you

---

### Post by arjuntank on 2009-01-10
if you are talking about the button having the menu and the mouse pointer on the right than that button is working as it should for me..(ubuntu 8.10)
i wonder why it is not working for you

---

### Post by xieu90 on 2009-01-10
the problem is i dont know what the command is 
can anyone tell me what the command that key has ?

or what the command of Shift +F10 ?

---

### Post by xieu90 on 2009-01-12
please someone !!

---

