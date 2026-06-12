---
title: "need help installing java"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Atroposu on 2009-03-16
my streaming videos had some horizontal "lines" but only the streaming ones , the other ones worked

im installing the codecs using the 
```
sudo apt-get install ubuntu-restricted-extras
```

when it gets to java 


[IMG]http://pic.leech.it/i/50ca3/6063d419screenshot.png[/IMG]

i cant click the Ok button or press enter , i tried even scrolling to the bottom then pressing enter , if i press esc , it appears again

i got the open source ATI drivers. Ubuntu 8.04

---

### Post by orethrius on 2009-03-16
If you press the right arrow key, it doesn't highlight Ok?

Explaining in more detail: apparently, one of the maintainers down the line (could be Sun, could be Ubuntu, could be anyone really) didn't bother to include a real GUI for this install, opting for ncurses instead.  That's okay for the command-line, but it causes problems like what you're experiencing when used as a substitute GUI.

---

### Post by Atroposu on 2009-03-16
gah ! that worked :D 

im pretty noob at the terminal so didnt know that O.o

thanks a lot



damn , that didnt fixed my steaming vid flickering :\
it seems its the same with opera and/or firefox 

altho normal vids work perfectly , and i got the open source ati drivers.

---

### Post by orethrius on 2009-03-16
It just happens to be one of my peeves; I mean, why go to the trouble of using a GUI if people just keep throwing CLI applications at us?  Granted, the Terminal has its place, but isn't using it to display an EULA a bit much?  Not like I automatically knew to hit "right" the first time, either... :lol:

---

### Post by billgoldberg on 2009-03-16
> **orethrius said:**
> but isn't using it to display an EULA a bit much?  Not like I automatically knew to hit "right" the first time, either... :lol:

Ditto.

Space should work fine also.

---

### Post by Atroposu on 2009-03-16
hmm i managed to install the codec , but i still get something like a bad refresh rate to streaming videos , altho the offlines videos work

it happens both with FF/Opera

i got the open source ATI drivers

---

### Post by billgoldberg on 2009-03-16
> **Atroposu said:**
> hmm i managed to install the codec , but i still get something like a bad refresh rate to streaming videos , altho the offlines videos work

it happens both with FF/Opera

i got the open source ATI drivers

The closed source drivers from ATI work better.

I use them and the streaming of video is much smoother.

---

### Post by Jonathan E-D on 2009-03-16
I'm a complete beginner.  Like others I wanted to install CODECS in order to watch my videos.  I did the Sudo apt-get install ubuntu-restricted-extras routine and was stopped when I got to the part about installing JAVA and the fact that there was no OK to click on.  After waiting for 15 minutes I figured it was installed and closed everything.  Now I'm informed that I have a broken package and am instructed to manually get 'dpkg --configure -a'  I don't have the slightest idea what to do.  Could somebody help me please?:(

---

### Post by Atroposu on 2009-03-16
> **billgoldberg said:**
> The closed source drivers from ATI work better.


I use them and the streaming of video is much smoother.

do i need to remove them (-.-) or just click the checkbox on the restricted drivers ?

i had a hard time just installing them (had problems with xorg.conf >.>) i had the envy ones which i couldnt watch movies with them.

---

### Post by orethrius on 2009-03-16
> **Atroposu]do i need to remove them (-.-) or just click the checkbox on the restricted drivers ?[/quote]

Just click the checkbox and that should take care of that.  I believe you have to reboot to switch the display drivers over, though.

[QUOTE=Jonathan E-D said:**
> I'm a complete beginner.  Like others I wanted to install CODECS in order to watch my videos.  I did the Sudo apt-get install ubuntu-restricted-extras routine and was stopped when I got to the part about installing JAVA and the fact that there was no OK to click on.  After waiting for 15 minutes I figured it was installed and closed everything.  Now I'm informed that I have a broken package and am instructed to manually get 'dpkg --configure -a'  I don't have the slightest idea what to do.  Could somebody help me please?:(
You can't click OK because the UI was programmed in ncurses.  You have to hit the right arrow key (or space, per bill) to select OK before hitting enter to agree to the EULA.

As for the broken package, run this (hold Alt and hit F2 to bring up the Run prompt) to fix the situation:
```
xterm -e 'gksudo dpkg --configure -a'
```

With any luck, that'll fix the broken extras package or pull it entirely, allowing you to try again.

---

### Post by Atroposu on 2009-03-16
well i got the closed source ati drivers but i think they're conflicting with the other ones

i get a white screen after loggin in , can move mouse , im using now the failsafe gnome login 

im gonna remove them , and remove the Vesa too

is there any command to show you what video drivers have you got atm ?

---

