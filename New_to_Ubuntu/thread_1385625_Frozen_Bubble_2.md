---
title: "Frozen Bubble 2"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by donaldshelton on 2010-01-19
I downloaded and love to play Frozen Bubble 2 game.

I find, however, that it freezes (pardon the pun) and I can't close it.

Where do I go to get fixes for the game?

What is the command to force close a program that refuses to close?

---

### Post by blackened on 2010-01-19
> **donaldshelton said:**
> I downloaded and love to play Frozen Bubble 2 game.

I find, however, that it freezes (pardon the pun) and I can't close it.

Where do I go to get fixes for the game?

First you should figure out why it's freezing. Try running it from the terminal and watching the output when it freezes.

> What is the command to force close a program that refuses to close?

```
killall frozen-bubble
```

or you could install and use xkill if you prefer the graphical method or just can't figure out the name of the process you want to exterminate:

```
sudo apt-get install xkill
```
and use it by alt+F2, then xkill, then click on the window you wish to kill.

---

### Post by PenguinInside on 2010-01-20
There's also a panel applet you can use.

Right click on the panel, Add to panel, then choose "Force Quit".

Once it's on the panel, click the icon, then click the pointer on the window of the program you want to terminate.

---

### Post by donaldshelton on 2010-01-20
I followed your directions--I ran the program using the terminal.

The program froze, without any additional info in the terminal.

I removed the program, re-downloaded it, and re-installed it.

It still freezes-I don't get past the menu of type of game to play.

It's really too bad, as the game is fun and addictive!!!!!!

---

### Post by donaldshelton on 2010-01-20
The program freezes (again, pardon the pun) when I am at the 1 player menu.  It doesn't allow me to choose from the menu, nor does the game start.

I have to use xkill to force quit the program.

Too bad, cause it's a really fun game!  I got as far as level 10 of 100 levels..

Please advise!!  I am using ubuntu 9.10, I downloaded the game from synaptic, and I really want to play!!!!

---

### Post by adam814 on 2010-01-20
Try running it from the terminal to see if it gives any error messages.

---

### Post by donaldshelton on 2010-01-20
I filed a bug with launchpad, and found that this problem has already been reported.

Look forward to when they fix the bug!!

---

### Post by donaldshelton on 2010-01-20
> **adam814 said:**
> Try running it from the terminal to see if it gives any error messages.

I tried this, and no error messages are reported.

---

### Post by adam814 on 2010-01-20
[http://www.frozen-bubble.org/downloads/](http://www.frozen-bubble.org/downloads/)

Why not try building it from the stable or developer sources?

---

### Post by pajamabama on 2010-02-01
I'm having the same issue.  Another point to note is that while open, frozen bubble is consuming over 100% CPU (not sure how that's possible - but that's what 'top' reports).  Why should it be doing that?

---

### Post by greenwom on 2010-02-08
Same problem, I've also tried to remove frozen bubble and install from source.

```
sudo apt-get remove frozen-bubble 
```

install development files. (I think these are correct, if not search in synaptic)

```
sudo apt-get install libsdl-1.2-dev libsdl-mixer-1.2-dev libsdlpangodev
```

download the tar ball (from the previous post)

```
http://www.frozen-bubble.org/data/frozen-bubble-2.2.0.tar.bz2
```

extract it

```
tar jxf frozen-bubble-2.2.0.tar.bz2
```

install it 

```

./configure
make
sudo make install
```

run it
```
./frozen-bubble
```

boom same problem.  something else in the Ubuntu install 
Love to see the bug fixed

---

### Post by adam814 on 2010-02-08
You might need to pull in the other dependencies before doing the actual build.

Try this:
```
sudo apt-get build-dep frozen-bubble
```Then try configuring and building again.

---

### Post by greenwom on 2010-02-08
I believe the correct command to install the dependencies is this 

```
sudo apt-get build-dep frozen-bubble
```

Still no go.  

I installed from source and through the repos...  so I'm at a loss.  
There are no errors when ran through the terminal other than.  

```
Eye-candy animation is too slow, disabling.
```

I can go through the menu and it doesn't freeze untill I try to start a game.

---

### Post by mc4man on 2010-02-08
Runs fine here, maybe try ....
search libsdl in synaptic and if not already installed then mark libsdl1.2debian-pulseaudio for install and click apply.

(will automatically remove libsdl1.2debian-alsa and or libsdl1.2debian-all - no matter, not needed when you install the above

---

### Post by adam814 on 2010-02-08
You're correct, I've updated my post

---

