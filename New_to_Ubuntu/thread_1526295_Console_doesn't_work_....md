---
title: "Console doesn't work ... ?"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by noworkflow on 2010-07-07
Hello.

I have two quick questions related to Terminal and Console:


1- I read somewhere that to access the console (not the terminal - to shut down an application for example) I had to press CTRL + ALT + F2.

When I do that, a black screen with a blinking dash shows up, but I can't type anything. I am forced to press ALT + F7 to exit.

Is this normal? Or am I doing something wrong?



2 - A similar thing happens once in a while in the TERMINAL... where I will have a blinking cursor (in this case it lets me type, but it will not execute any commands....

Thanks for your help.

---

### Post by azertyh on 2010-07-08
hi,
console and terminal work like that. you need to type the command.
read these links about terminal and console : [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) and [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
to shut down an application from a console, type killall name_of _the application, and hit ENTER key.

---

### Post by noworkflow on 2010-07-08
Thanks azertyh,
but I think I didn't explain my problem very well.

I know how to use the terminal pretty well.

But when I try to open the console instead of the terminal (ALT + CTRL + F2), I get a blinking dash, but I DOES NOT let me type..

---

### Post by oldos2er on 2010-07-08
I've encountered this same bug from time-to-time, in the Nvidia drivers. After this last update a day or two ago, ttys are once again working for me. If you're using Nvidia, it's possible you're suffering from this bug too. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282068](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282068)

---

### Post by jerenept on 2010-07-08
try CTRL_ALT_F3?

This works for me.

---

### Post by KdotJ on 2010-07-08
I too have the same problem, I have the ATI open drivers

---

### Post by noworkflow on 2010-07-08
It does the same thing for CRTL + ALT + F{1..6} {8..12}
I have an ATI video card.

---

### Post by noworkflow on 2010-07-10
Anyone else has had this problem ? (bump = )

---

### Post by mcphargus on 2010-07-10
As a workaround to this, I'll typically just use fullscreen terminal windows. Alt+f2->'gnome-terminal'->Enter key and then when the terminals open hit f11. It's nice because you can use Ctrl+Shift+"=" and Ctrl+"-" to change the size of the text, or you can still access term profile attributes and set the colors of your terminals to whatever is most comfortable on your eyes.

Lots of emacs sessions strung together without leaving tty7(GUI) and still having options like workspace switching to run from fullscreen emacs to Devhelp or website documentation is really convenient.

I lost my love of using the other ttys as soon as it stopped working for me and haven't missed it much.

---

### Post by noworkflow on 2010-07-10
Thanks mcphargus.

I actually already use the Gnome terminal in full screen, but if the GUI freezes, the terminal freezes too. 

Earlier today, I had dozens of google chrome windows open, and the GUI wasn't responding. I wanted to get to the terminal so I could terminate all the processes, but the terminal wouldn't respond. Thats when I found our that my console doesn't' work... had to reboot

---

### Post by noworkflow on 2010-07-13
Weird...
I had to reinstall ubuntu last night, and now the console works again.

Thanks everyone.

---

### Post by lxtwin on 2012-01-20
For information I have the same issue and the only way that I can get any console is by booting with ACPI=off. I have tried ACPI=ht and that does not work.

I have an nVidia card.

---

### Post by oldos2er on 2012-01-20
Closed, necromancy.

---

