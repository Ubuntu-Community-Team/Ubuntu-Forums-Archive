---
title: "help installing adour 2.7.1 on intrepid"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by jitup on 2009-02-23
hello,
I am trying to set up a linux based studio and I want to try and use ardour 2.7.1, and I can't figure out how to install it (or other programs in linux, first day for linux for me) I tried reading some guides but I keep messing up. can some one explain it in noob speak? thankyou.

Also is there any free program for linux that is compareble to reasons?

Thank you

---

### Post by llamabr on 2009-02-23
I don't know what adour is.  What does it do?

To search for programs, use apt-cache.  so if I want to install a tetris game, I'll go:

apt-cache search tetris

and that'll tell me these options:


atris - tetris-like game with a twist for Unix
bastet - Free clone of Tetris, featuring a ******* level
blockattack - a puzzle game inspired by Tetris
bsdgames - a collection of classic textual unix games
crack-attack - multiplayer OpenGL puzzle game like "Tetris Attack"
cuyo - Tetris-like game with very impressive effects
cuyo-data - data files for the game cuyo
ghextris - A Tetris-like game on a hexagonal grid
gpe-tetris - tetris game for small screens and embedded devices
gtetrinet - multiplayer tetris-like game
gtkboard - many board games in one program
ltris - very polished Tetris clone with CPU opponents

Then i'll pick one, say ltris by using apt-get, like this:

sudo apt-get install ltris

it'll ask me for my password, install it for me, and I'm done.

what does adour do?

---

### Post by llamabr on 2009-02-23
I see.  You spelled it wrong:

brock@vader:~$ apt-cache search digital audio workstation
ardour - digital audio workstation (graphical gtk2 interface)
ardour-i686 - digital audio workstation (graphical gtk2 interface) [i686]
brock@vader:~$ 

So use the instructions above to install.  Report back when you've solved your problem, by ammending the subject line.

---

### Post by jitup on 2009-02-23
ardour is a multi track music recording and production suite, I think it also has midi capabilites now. It is supposed to be really good, like on par with cubase 4 (soon to be 5) and Protools, but it is donation ware, and since I am broke, free until I get my paycheck. 

I am not at my studio computer (or will be my studio computer) at the moment but I think I can figure it out from there thank you, now, do I install Jack and the jack grahic wrapper or do I have to download the programs?

is there a tutorial to make ardour vst compatible somewhere?
thank you

---

