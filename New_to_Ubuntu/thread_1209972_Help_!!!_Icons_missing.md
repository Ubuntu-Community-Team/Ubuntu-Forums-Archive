---
title: "Help !!! Icons missing"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-10
I am missing my trash can on lower right and the 2 desktops that were there also...

in addition on the upper right all icons are gone too... the clock and all icons such as net connection, monitor, and whatever else used to be there are also gone...

maybe other missing items that i just havent noticed yet ???

what could i have done this time ???  is there possibly a fix ???

thanks...

---

### Post by koleoptero on 2009-07-10
Perhaps you've deleted the configuration for gnome-panel accidently? One possible solution is putting everything back manually by right clicking each panel and selecting "add to panel" and then choosing what to add from the list.
To add launchers to specific programs you can right click on any program in the main menu and select "add this launcher to panel". If you've lost the main menu too, you can add it by selecting it from the list.

---

### Post by earthpigg on 2009-07-10
this will remove all modifications to the gnome panels, thus causing GNOME to resort to the default panel setup next time it starts:

> 
rm -r ~/.gconf/apps/panel

then log out and back in


edit: as always with the infamous 'rm' command, make sure you actually take a look at what it is about to do, and verify that this is what you want to do. dont take my word for it, i could be a terrorist for all you know. :P

---

### Post by koleoptero on 2009-07-10
> **earthpigg said:**
> this will remove all modifications to the gnome panels, thus causing GNOME to resort to the default panel setup next time it starts:



then log out and back in


edit: as always with the infamous 'rm' command, make sure you actually take a look at what it is about to do, and verify that this is what you want to do. dont take my word for it, i could be a terrorist for all you know. :P

I testify that this rm command will do what earthpigg says. :p

---

### Post by earthpigg on 2009-07-10
i looked through some of your previous posts, notageek. you seem to like poking and prodding :D

general advice on how to undo most poking and prodding that you do that does _**not**_ require you to enter your password:

go to places -> home folder -> view -> show hidden folders.

all those folders and files that start with a period, such as .gconf, are the settings and personalizations done to something by whatever user is logged in. some have obvious names (guess what .openoffice.org has the settings for?), some have semi-obvious names (gconf = gnome configuration), and some appear completely random: ._purple_ is the custom settings, buddy lists, etc, for _pidgin_ instant messanger client.

if you delete any of those, it will _completely_ remove settings for whatever program it is associated with.... next time the program starts, it will see that it has no custom settings, and resort to the default as if it where freshly installed.

_be warned_ that it will remove any saved games in a game, any bookmarks in a web browser, any _*panel changes to gnome panels*_, etc etc.

but it is also something you can try that is safe enough that it will _*not*_ break your system itself.


again, this will _not_ undo any poking and prodding you did after entering "sudo ______" in the terminal.... but most random clicking around and 'hrm, i wonder what this does?' can be fixed by this method.

---

### Post by NOTAGEEK on 2009-07-10
> **earthpigg said:**
> this will remove all modifications to the gnome panels, thus causing GNOME to resort to the default panel setup next time it starts:



then log out and back in


edit: as always with the infamous 'rm' command, make sure you actually take a look at what it is about to do, and verify that this is what you want to do. dont take my word for it, i could be a terrorist for all you know. :P



i did and got this------>rm: cannot remove `/home/my name/.gconf/apps/panel': No such file or directory

so i clicked the "x" in the upper right to log out and it wont log out or even give me the choice to---it just goes to a mostly blank desktop----yikes !!!

---

### Post by earthpigg on 2009-07-10
run

> killall gnome-panel

the panel should pop right back up. if it doesnt, then run:

> gnome-panel

---

### Post by koleoptero on 2009-07-10
Have you tried to add them again manually like I said?

And if you like tinkering with things like earthpigg menitoned you can also do regular backups of your home directory to save settings :)

There was a tarball command for this but I can't remember it...

---

### Post by earthpigg on 2009-07-10
> rm: cannot remove `/home/my name/.gconf/apps/panel': No such file or directory

wait, did you run the origional command i gave you _*twice*_?

you where supposed to run it once, then log out and back in :P

---

### Post by NOTAGEEK on 2009-07-10
> **earthpigg said:**
> i looked through some of your previous posts, notageek. you seem to like poking and prodding :D

general advice on how to undo most poking and prodding that you do that does _**not**_ require you to enter your password:

go to places -> home folder -> view -> show hidden folders.

all those folders and files that start with a period, such as .gconf, are the settings and personalizations done to something by whatever user is logged in. some have obvious names (guess what .openoffice.org has the settings for?), some have semi-obvious names (gconf = gnome configuration), and some appear completely random: ._purple_ is the custom settings, buddy lists, etc, for _pidgin_ instant messanger client.

if you delete any of those, it will _completely_ remove settings for whatever program it is associated with.... next time the program starts, it will see that it has no custom settings, and resort to the default as if it where freshly installed.

_be warned_ that it will remove any saved games in a game, any bookmarks in a web browser, any _*panel changes to gnome panels*_, etc etc.

but it is also something you can try that is safe enough that it will _*not*_ break your system itself.


again, this will _not_ undo any poking and prodding you did after entering "sudo ______" in the terminal.... but most random clicking around and 'hrm, i wonder what this does?' can be fixed by this method.



yes---guilty as charged... just trying to learn an os---its very interesting stuff...  perhaps 1 of these days i can give back by helping others...


> **earthpigg said:**
> run



the panel should pop right back up. if it doesnt, then run:

i need to answer another ? first... thx...


> **koleoptero said:**
> Have you tried to add them again manually like I said?

And if you like tinkering with things like earthpigg menitoned you can also do regular backups of your home directory to save settings :)

There was a tarball command for this but I can't remember it...

yes---and i actually got some of them back too... also learned how to move stuff...



> **earthpigg said:**
> wait, did you run the origional command i gave you _*twice*_?

you where supposed to run it once, then log out and back in :P

yes i messed up and did run the command twice---oooops...

---

### Post by koleoptero on 2009-07-10
> **NOTAGEEK said:**
> yes---and i actually got some of them back too... also learned how to move stuff...

I've messed the panel several times too and I can say for sure that the manual way is the best way to get things back, if not the easiest. :)

---

### Post by earthpigg on 2009-07-10
> **NOTAGEEK said:**
> 
yes i messed up and did run the command twice---oooops...

restart your computer or log out and back in, and your panels should pop back up the way they where when you first installed ubuntu.

```
gnome-session-save --logout
```

will log you out, if you can get to a terminal... if you cannot, it should work in the alt+f2 box.

edit: nevermind, it looks like you already got back on your feet.

---

### Post by NOTAGEEK on 2009-07-10
> **earthpigg said:**
> restart your computer or log out and back in, and your panels should pop back up the way they where when you first installed ubuntu.

```
gnome-session-save --logout
```will log you out, if you can get to a terminal... if you cannot, it should work in the alt+f2 box.

edit: nevermind, it looks like you already got back on your feet.



yes earthpig i got my feet with one exception...  the logout button used to give me choices of hibernate and others---now i just got the choice of logout or switch users... perhaps when i logout and in i might have the other choices back ???

thank you and everyone posting to this thread for having my back on this one... itis starting to be less stress and more fun again (likely temporary) thanks to you all... i like 9.04 the more i learn the more enjoyable it is... thanks---ill log out and in now

---

### Post by NOTAGEEK on 2009-07-10
WOW !!!

Thanks to everyone here all is fine again...

i learned 3 things---the first time i logged out/in i only had half a screen... the second time i went off/on again all was fine except the screen res was huge...

i learned :
1. the control and minus key brings the size down to right where i want it... maybe i wont have to mess with video drivers for awhile which might be what nessed me up in the first place...

2. if i hit the f11 key all the toolbars and such on top go away and i can work with a full screen... another hit of the f11 key brings the toolbars etc right back...

3. all kinds of great helpful tips from those that posted here...  now for reference i can always pull up my threads and review...

thanks to all again...

---

