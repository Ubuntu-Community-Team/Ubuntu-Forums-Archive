---
title: "I kinda broke Unity.."
date: 2011-08-02
forum: New to Ubuntu
---

### Post by adamhum3 on 2011-08-02
So I disabled Unity and a few other things whilst I was enabling desktop cube, and I'm sure a lot of people have had this problem before, however - I can't re-enable it.

I'm stuck with this Firefox window open, and because my 'start bar' isn't there, I cant close it, or even minimize it, and the ccsm window is actually behind it. Also, none of the keyboard shortcuts work. 

My best bet I suppose is to reboot, however then I probably wont be able to launch ccsm...

Any ideas guys?

---

### Post by Jouke S on 2011-08-02
try installing the gdm package (gnome-display-manager)
if you can get a terminal open simply type sudo apt-get install gdm
else install it via software centre

edit: you can probably get into nautilus via firefox's download menu (ctrl-D I think). From there just search for terminal

---

### Post by adamhum3 on 2011-08-02
> **Jouke S said:**
> try installing the gdm package (gnome-display-manager)
if you can get a terminal open simply type sudo apt-get install gdm
else install it via software centre

Cant open anything. I would reboot and try but I don't want to lose this firefox window...

---

### Post by Frogs Hair on 2011-08-02
you can reset Unity with with the following command from the terminal or by using Alt +F2.```
unity --reset
```

If you can not get into a terminal for some reason The command can be run from the recovery console . 

Restart with the button on the computer , when the login screen comes up select your user name and enter the password . 

Before login , select the recovery console from the session list below the greeter box on the bottom panel.

Enter Code:```
unity --reset
```

and restart the computer . When login screen comes up again select Ubuntu from the session list .

To enable the cube in Unity see this guide.[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by adamhum3 on 2011-08-02
> **Frogs Hair said:**
> you can reset Unity with with the following command from the terminal or by using Alt +F2.```
unity --reset
```If you can not get into a terminal for some reason The command can be run from the recovery console . 

Restart with the button on the computer , when the login screen comes up select your user name and enter the password . 

Before login , select the recovery console from the session list below the greeter box on the bottom panel.

Enter Code:```
unity --reset
```and restart the computer . When login screen comes up again select Ubuntu from the session list .

To enable the cube in Unity see this guide.[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Where am I meant to be entering this code? My log on is automatic, however I can get to the switch users screen, allowing me to select the recovery console, however when I log in, there is no difference.

---

### Post by adamhum3 on 2011-08-02
I've got a few shortcuts now, but not many. I can bring up what looks like the command prompt when I press CTRL+ALT+F1/2/3/4/5/6

---

### Post by Frogs Hair on 2011-08-02
Sorry you kind of lost me.  

As I wrote , the command is meant to be entered in the terminal , recovery console , or the command prompt found by using Alt + F2 

If you can't reset While logged in , then you will have to reboot and try the command from recovery console .

I 'm not clear as to weather you have done this because you first asked where you were to enter the code .

---

### Post by fidelandche on 2011-08-02
I had the same problem, before I reset Unity, I entered this command first 

sudo apt-get install ubuntu-desktop

then followed by

unity --rest

and then I let unity -- reset run for thee minutes before closing the terminal and then rebooting and it all worked fine.

Cheers

Andy

---

### Post by adamhum3 on 2011-08-02
> **Frogs Hair said:**
> Sorry you kind of lost me.  

As I wrote , the command is meant to be entered in the terminal , recovery console , or the command prompt found by using Alt + F2 

If you can't reset While logged in , then you will have to reboot and try the command from recovery console .

I 'm not clear as to weather you have done this because you first asked where you were to enter the code .

The recovery console looks no different to when I log in normally, infact all of the options come up the same as just logging in to Ubuntu.

And I can't open up a terminal, at all. I can open programs, by creating a document on my desktop, and opening it with a program, however, I would need the location of the terminal in the file system in order to open it up.

Cheers.

---

### Post by Frogs Hair on 2011-08-02
A terminal _should_ open when you enter the recovery console . You wrote that you where able to get a command prompt using Alt + F2 . If that is the case run the command from there or enter ```
gnome-terminal
``` 
and run the command from there .

---

### Post by adamhum3 on 2011-08-02
Nope. I'm in recovery console now it's the exact same as before, ctrl+alt+t doesn't do anything.

Also I don't think it is a command prompt, the screen goes black with white text saying:
> Ubuntu 11.04 Adam-PC tty2
Adam-PC login:

---

### Post by adamhum3 on 2011-08-02
Bump. Still got the problem... :|

Edit: Fixed! I created a text document on the desktop, then used that to run 'gnome-terminal'.

Thanks for everyones help, much appreciated.

---

### Post by Frogs Hair on 2011-08-02
> **adamhum3 said:**
> Bump. Still got the problem... :|

Edit: Fixed! I created a text document on the desktop, then used that to run 'gnome-terminal'.

Thanks for everyones help, much appreciated.

Glad it is fixed , I didn't know you were in tty .

---

### Post by cbennett926 on 2011-08-02
Log out and go into Ubuntu Classic no add ons and enter reset -unity from the terminal and reset computer

---

### Post by pritam_par on 2011-08-10
> **adamhum3 said:**
> So I disabled Unity and a few other things whilst I was enabling desktop cube, and I'm sure a lot of people have had this problem before, however - I can't re-enable it.

I'm stuck with this Firefox window open, and because my 'start bar' isn't there, I cant close it, or even minimize it, and the ccsm window is actually behind it. Also, none of the keyboard shortcuts work. 

My best bet I suppose is to reboot, however then I probably wont be able to launch ccsm...

Any ideas guys?


Goto compiz setting manager and enable **move window** and **window decoration**. Close button tab will appear again.

----------------------------------------------------------------------------------------------------
[My blog]("http://opensource-sidh.blogspot.com/") on open source

---

