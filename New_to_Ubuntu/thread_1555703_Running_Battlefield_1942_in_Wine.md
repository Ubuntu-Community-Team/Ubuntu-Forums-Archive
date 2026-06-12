---
title: "Running Battlefield 1942 in Wine"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Guffmeister on 2010-08-18
Hi! I'm trying to run the classic and excellent Battlefield 1942 on my Ubuntu machine in Wine, but with one major snag which is causing me problems.

The game loads up fine, plays the intro video, and then goes into the main menu. A minor issue here is the fonts aren't quite right, and some letters are hard to read, but I know my way round the menus well enough for this not to be a problem. I then load up a game, which seems to take a little longer than on my previous Windows machine but not too bad, and then enter a game, where the main problem pops up. Suddenly, all the colours are completely wrong and the graphics are very poor. Everything is a shade of blue, and I can only vaguely make out the details of the immediate surroundings.

Does anyone have any ideas of how to fix it? I've been searching Google and the Wine websites and can't seem to find a solution, or anyone else who's had this problem. I'm hoping it's just something simple to fix, or maybe graphics card drivers are old or not installed properly or something. I also installed Project IGI, which is running absolutely fine now after I ironed out a number of issues I had.

Any clues would be excellent!

Thanks in advance.

---

### Post by Zorgoth on 2010-08-18
Are you using the d3dx* packages from winetricks?

And please show the terminal output of

wine <path/to/battlefield/1942's/exe>

---

### Post by Guffmeister on 2010-08-18
How do I know if I am using the d3dx packages? I haven't really got a clue.

I can't seem to run Battlefield from the terminal. It comes up with the error "Cannot Find Fingerprint". I have to run it from the dropdown menu Applications>Wine>Programs....etc.

---

### Post by fbobraga on 2010-08-18
> **Guffmeister said:**
> How do I know if I am using the d3dx packages? I haven't really got a clue.
(...)

see: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

