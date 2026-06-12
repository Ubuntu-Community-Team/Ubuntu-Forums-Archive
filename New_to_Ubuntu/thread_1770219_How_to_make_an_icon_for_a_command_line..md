---
title: "How to make an icon for a command line."
date: 2011-05-28
forum: New to Ubuntu
---

### Post by ngubk on 2011-05-28
Hi! I have some very nice games: Steel Storm episode I, Narcissu, M.A.R.S. But all of it run by commands from terminal. For example: 
cd ~/Games/steelstorm
./steelstorm

I've use .bashrc to make it easier but I want these games to be like any other apps from Ubuntu Software Center: have an icon to click in to start the game, or show up when i use Gnome-do to search.
I use Ubuntu 11.04 classic desktop.
BTW, i highly recommend these games, you can google and download it for free.

---

### Post by wildmanne39 on 2011-05-28
> **ngubk said:**
> Hi! I have some very nice games: Steel Storm episode I, Narcissu, M.A.R.S. But all of it run by commands from terminal. For example: 
cd ~/Games/steelstorm
./steelstorm

I've use .bashrc to make it easier but I want these games to be like any other apps from Ubuntu Software Center: have an icon to click in to start the game, or show up when i use Gnome-do to search.
I use Ubuntu 11.04 classic desktop.
BTW, i highly recommend these games, you can google and download it for free.
Hi,under Launcher and Quick Lists in the powers users guide in my signature below this text it tells how to make launchers for terminal applications. Just click on powers users guide.

---

### Post by webofunni on 2011-05-28
I never played it. But did you try the package

[http://archive.ubuntugames.org/dists/ubuntugames/main/binary-i386/steelstorm-episode1-v.1.00.01723_i386.deb](http://archive.ubuntugames.org/dists/ubuntugames/main/binary-i386/steelstorm-episode1-v.1.00.01723_i386.deb)

?

---

### Post by dcsoldschool53 on 2011-05-29
> **ngubk said:**
> Hi! I have some very nice games: Steel Storm episode I, Narcissu, M.A.R.S. But all of it run by commands from terminal. For example: 
cd ~/Games/steelstorm
./steelstorm

I've use .bashrc to make it easier but I want these games to be like any other apps from Ubuntu Software Center: have an icon to click in to start the game, or show up when i use Gnome-do to search.
I use Ubuntu 11.04 classic desktop.
BTW, i highly recommend these games, you can google and download it for free.

I am not familar how to do this in 11.04 Natty, but in Maverick, in a terminal, type```
alacarte
```When it opens, click games. Then, click New Item, a create launcher popup should open.
```
Type: application in terminal
``````
Name: steelestorm
``````
Command: ~/Games/steelstorm/./steelstorm
```Comment it with whatever you want, same with icon. You can also right click on Applications > Edit Menus to do the same thing.
Hope this works for you.

---

### Post by ngubk on 2011-05-29
> **wildmanne39 said:**
> Hi,under Launcher and Quick Lists in the powers users guide in my signature below this text it tells how to make launchers for terminal applications. Just click on powers users guide.
Thanks for your reply. I've read the instruction. But i think the guide is for Unity Launcher.I'm using Ubuntu Classic( Unity just cost more CPU so i don't like it)

---

### Post by beew on 2011-05-29
Try  do this, in Unity, right click the "log off" button on the upper right corner, in the drop down choose System Settings, this will open the control Centre, in it choose "Main Menu" and open it.
On the left panel choose "Games", and then click "New Item".  In the dialogue box enter the Name of the game (it can be anything btw), in the "command" box enter > ~/Games/steelstorm/steelstromNote that there is no "." before the second steelstorm. I don't know if this will work, but I have a program like that and in the terminal I have to run ./program  but in the launcher just path to the program's executable.

EDITED: In the classical desktop you find the Main Menu in System > Preference

---

### Post by ngubk on 2011-05-30
```
~/Games/steelstorm/steelstrom 			 		
```
It doesn't work for me. The terminal shows up and pops up an error:
```
Failed to execute child process "~/Games/steelstorm/steelstorm" (No such file or directory)
```

When i try this in Main Menu: ```
Command: ~/Games/steelstorm/./steelstorm
```

The game shows up but it's a black screen and an only option to quit due to an error.Dunno why :((

---

### Post by dcsoldschool53 on 2011-05-30
> **ngubk said:**
> ```
~/Games/steelstorm/steelstrom                      
```It doesn't work for me. The terminal shows up and pops up an error:
```
Failed to execute child process "~/Games/steelstorm/steelstorm" (No such file or directory)
```When i try this in Main Menu: ```
Command: ~/Games/steelstorm/./steelstorm
```The game shows up but it's a black screen and an only option to quit due to an error.Dunno why :((

Try it in the terminal from the command line only```
~/Games/steelstorm/./steelstorm
```to see if the same thing happens. If that works, then the problem is with the main menu. Remember, there is no spaces between steelstorm/./steelstorm

---

### Post by hijiz on 2011-05-30
as far as i remember right click aplications then edit menus. then new item and write name, command and add a icon then click and drag the item to games. hope it helped.

---

### Post by dcsoldschool53 on 2011-05-30
In the menu, try changing from```
Type: Application in Terminal
```TO```
Type: Application
``` And,
```

Name: Steelstorm
Command: ~/Games/steelstorm/./steelstorm

```leave them just the way that you have them. See if that made the differences.

---

### Post by ngubk on 2011-05-30
I've figured out a way!!!. Cost me a lot of time though.
I make a shell script file in the same folder: name it steelstorm.sh
```
#!/bin/sh

# Change to game directory
CANONPATH=`readlink -f "$0"`
cd "`dirname "$CANONPATH"`"


MACHINE=`uname -m`
if [ "$MACHINE" = x86_64 ]
then
    LIBS=./libs64
    BIN=./steelstorm64
else
    LIBS=./libs32
    BIN=./steelstorm
fi

# Run the game:
export LD_LIBRARY_PATH=$LIBS:"$LD_LIBRARY_PATH"
$BIN $@
```Then put this into Main Menu:
```
Name: Steelstorm Command: ~/Games/steelstorm/steelstorm.sh
```Thank you for your help so far. I will mark this thread as solved

---

