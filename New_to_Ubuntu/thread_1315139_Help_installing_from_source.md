---
title: "Help installing from source"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Nico0020 on 2009-11-05
I have always stuck with .deb and the repos as ive never gotten anything to install from source before.  but for this i have to so im trying and failing.  there is a game called kaiten patissier i want to play and it comes with the source.  i go into the source dir and run ./configure and it tells me no such file.  then when i run make it tells me this

```
make: *** No rule to make target `/usr/local/mingw32/include/SDL/SDL.h', needed by `ram.o'.  Stop.

```

I am not sure what is wrong, am I lacking something that I need to install from source?  

here is a link to the freeware game I am trying to install.  
[http://www.geocities.jp/dij4121/alpha/data/rg_103.zip](http://www.geocities.jp/dij4121/alpha/data/rg_103.zip)

and a link to the site itself if it helps.
[http://maglog.jp/alpha-secret-base/Article313069.html](http://maglog.jp/alpha-secret-base/Article313069.html)

---

### Post by dearingj on 2009-11-05
Try installing the packages build-essential and libsdl1.2-dev:

```
sudo apt-get install build-essential libsdl1.2-dev
```

Build-Essential will cause your system to install a number of packages which are useful for compiling programs, and I see from the error message you posted that make is looking for the SDL library.

---

### Post by Nico0020 on 2009-11-05
still coming across the same errors.  any other ideas?

---

### Post by KIAaze on 2009-11-05
I just managed to compile and play it.
This should do:
```
sudo apt-get install build-essential libsdl1.2-dev libsdl-mixer1.2-dev libsdl-gfx1.2-dev
unzip rg_103.zip
cd rg_103/src
rm .depend
make -f Makefile.linux
cd ..
./src/RotateGear

```

Thanks for the indirect tip. It's a fun little game. :)

My Japanese isn't good enough, but here are the controls I figured out so far:
-arrows for movement
-Z=select/rotate
-X=jump
-C=call up menu
(menus in English help by the way. :) )

---

### Post by kixome on 2009-11-05
try cmake install

---

### Post by Nico0020 on 2009-11-05
sweet it worked.  thanks alot!  I love this game very much, and it has several sequels.  

two more questions. how do I add this to my applications list?  Usually I just select the name of the game from it's directory (the new file in the src dir) when creating a new application launcher.  But when i do the program starts up with just a black screen (same thing happens if i double click the new file) 

and why exactly do I have to be in the root dir of the program and type "./src/RotateGear" ?

---

### Post by KIAaze on 2009-11-05
> **Nico0020 said:**
> sweet it worked.  thanks alot!  I love this game very much, and it has several sequels.  

Where are the sequels? :D

> **Nico0020 said:**
> and why exactly do I have to be in the root dir of the program and type "./src/RotateGear" ?
The binary (RotateGear) searches for the game data in the "working directory".
That's why you have to run it from where the game data is, i.e. the program's root directory.
You run "./src/RotateGear" because that's where the binary is located relative to the program's root directory.

You can copy it into it if you want:
```
cp ./src/RotateGear .
chmod +x ./RotateGear

```
(actually it seems there already was a precompiled binary in the .zip file. It just wasn't made executable. ^^')

> **Nico0020 said:**
> 
two more questions. how do I add this to my applications list?  Usually I just select the name of the game from it's directory (the new file in the src dir) when creating a new application launcher.  But when i do the program starts up with just a black screen (same thing happens if i double click the new file) 


First, create a simple launch script:
RotateGear.sh:
```
#!/usr/bin/env bash
cd PATH_TO_GAMEDATA
PATH_TO_BINARY/RotateGear
```

Make it executable:
```
chmod +x RotateGear.sh
```

Then put that script as command for the launcher instead of the binary.

---

### Post by Nico0020 on 2009-11-05
cool, I'll give it a try tomorrow as I need to get some sleep.  Thanks so much for the help.  I'm not sure if all the sequels have a linux version, but I know at least one of em does.  Here is the official site, just click the image of the game and it will take u to a page about it with the download info.  You can also buy the games on the xbox live marketplace in the "indie games" section for 1 dollar each.

---

