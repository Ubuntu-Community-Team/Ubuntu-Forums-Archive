---
title: "Lynx keeps freezing"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-08
This has happened several times since my install a few days ago: Lynx keeps freezing: i can move the cursor, and whatever it is over will respond (e.g. the hand will change for hyperlinks, buttons and menus will be highlighted, but keystrokes or clicking won't respond. Sometimes i can Cntrl+Alt+Del and select Suspend, but that doesn't always work.
Why is this happening and how can i stop it?
FYI, i dual boot with Win 7; i'm running a Dell Inspiron 14r with 500GB hard drive, 4GB DDR2 Memory, and an Intel Pentium Duo Core. (not sure if those specs help, but hey... if there's anything else i need to add, let me know)
Also, no error messages come up.

---

### Post by Bölvaður on 2011-04-08
Can you explain this a little better?

Can you test this when your ubuntu install freezes up:

[LIST]
[*]press ctrl+alt+f5 to go to a terminal
[*]press ctrl+alt+f7 to go back to your desktop
[/LIST]

Is there anything special you do when it freezes?
Does the mouse pointer lag about when you move it when it happens?

---

### Post by RememberWhenItRained on 2011-04-08
> **Bölvaður said:**
> Can you explain this a little better?

Can you test this when your ubuntu install freezes up:

[LIST]
[*]press ctrl+alt+f5 to go to a terminal
[*]press ctrl+alt+f7 to go back to your desktop
[/LIST]

Is there anything special you do when it freezes?
Does the mouse pointer lag about when you move it when it happens?
ill try that next time and see if it works;

no, not doing anything special, but every time i usually have 3 apps open: terminal, firefox with two or three tabs up, and perhaps something else.

the pointer does not seem to lag; not much at least.

---

### Post by Bölvaður on 2011-04-08
I would guess there is some program that is hogging the cpu. 
When you do control+alt+f6 (you can use almost any "f" button), write down your user name and password and then write ```
killall firefox
```
or ```
top
``` and see what program is hogging the cpu and kill it either by writing down the number next to the name of the program or ctrl+c (to close the top program) and write killall and then name name of the program, you should use TAB to auto complete the name of the program.. so if it is firefox you would write "fir[TAB]" and after pressing the TAB button after writing fire it should auto complete it to firefox-4.0 or what ever it is.

---

### Post by RememberWhenItRained on 2011-04-09
> **Bölvaður said:**
> I would guess there is some program that is hogging the cpu. 
When you do control+alt+f6 (you can use almost any "f" button), write down your user name and password and then write ```
killall firefox
```or ```
top
``` and see what program is hogging the cpu and kill it either by writing down the number next to the name of the program or ctrl+c (to close the top program) and write killall and then name name of the program, you should use TAB to auto complete the name of the program.. so if it is firefox you would write "fir[TAB]" and after pressing the TAB button after writing fire it should auto complete it to firefox-4.0 or what ever it is.
it's interesting: sometimes keystrokes will work, and the cursor moves, but clicking doesn't do anything. anyway, i opened a new terminal with Cntrl+Alt+T and used ```
 killall firefox-bin
``` with the TAB like you said. that seemed to unfreeze it. still...

---

### Post by RememberWhenItRained on 2011-04-09
results of "top" command. shows the top processes correct? what is "Xorg?"

---

### Post by idoitprone on 2011-04-10
> **RememberWhenItRained said:**
> results of "top" command. shows the top processes correct? what is "Xorg?"

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

X org is the parent process for the gui. If you will xorg, you also kill many of you desktop apps and window manager

---

### Post by Bölvaður on 2011-04-11
> **RememberWhenItRained said:**
> results of "top" command. shows the top processes correct? what is "Xorg?"
6 % cpu, dont worry about it... or was the system clogged up at this time?
If it is clogged up then opening a terminal shouldnt work, doing the alt+ctrl+f5 should work but take some time to wait for it.

But yes what is firefox doing when it freezes?
It is starting to seem like there is some website you are on that is doing this, perhaps some script or flash.

---

### Post by mastablasta on 2011-04-11
> **Bölvaður said:**
> , perhaps some script or flash.
 
 
this would explain it as i get the freezes as well on certain sites. I guess FF4 and Flash are not linux ready yet. at least not fully.
 
Oh another thing you might try is (if script is causing the freeze) to install Sun-Java instead of Iced tea or opensource java. It seems to have solved some of my other issues.

---

### Post by RememberWhenItRained on 2011-04-11
> **mastablasta said:**
> this would explain it as i get the freezes as well on certain sites. I guess FF4 and Flash are not linux ready yet. at least not fully.
 
Oh another thing you might try is (if script is causing the freeze) to install Sun-Java instead of Iced tea or opensource java. It seems to have solved some of my other issues.
 yes, every time it has frozen, i have been listening to internet radio which uses flash. that might explain it.

---

### Post by Bölvaður on 2011-04-13
well your computer should handle flash, try to find out when exactly it gets clogged up and do what I told you alt+ctrl+f5 and then use top to find out which program it is that is hogging the cpu, but only while your computer is crawling to a stop.
If it is flash then you'll see that, if it is a script then firefox will be the one using the cpu.

---

