---
title: "Using Terminal"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by dvdjchvz on 2010-08-04
Hello,

I have been using Ubuntu for about a year now and I am loving it more and more everyday. While I do not have a lot of trouble using the GUI, I have not learned anything about the Terminal.

I have run into some problems that require installing from Terminal but I have never successfully installed anything. My latest frustration has been trying install Palm SDK for webOS. I have invested hours and have gotten nowhere.

So my question-- any recommendations for how I can learn the Terminal? I know I am missing out on a lot because of my inexperience. Any help would be greatly appreciated.

Pc!

---

### Post by jmszr on 2010-08-04
dvdjchvz,

These are a good place to start: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro) and: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners).

Hope they help.

---

### Post by ankspo71 on 2010-08-04
Hi,
Before installing any software, it is always best to refresh the repositories with this command.
```
sudo apt-get update
```
(note that this does not update the system, just the repositories)

To install downloaded deb packages you use the dpkg command.
```
sudo dpkg -i /path/to/file.deb
```

To install or uninstall software from the repositories, you can use the apt-get (or aptitude) command.
```
sudo apt-get install packagename
sudo apt-get remove packagename 

```

To search for a package to install you can use the apt-cache search command.
```
apt-cache search packagename
```

For more information on these commands you can look in the man pages in the terminal.
```
man dpkg
man apt-get
man apt-cache
```

Here is some useful links that cover the basics of commands.
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://www.unixmen.com/linux-command/linux-command-for-beginners.html](http://www.unixmen.com/linux-command/linux-command-for-beginners.html)

Also the book called "Ubuntu Linux Toolbox: 1000+ Commands for Ubuntu and Debian Power Users" is great for learning the commands. It's a long title but it best describes the book. I think it's good for regular users too.

---

### Post by David Andersson on 2010-08-04
Google *ubuntu terminal guide* seems to find some starting points. Just dive in.

---

Maybe an examples to wet your appetite. Open a terminal, copy a code line from here, paste it into the terminal, and press Return.

These three commands do very little, and apparently they do the same thing:
```
echo Hello World
```
```
echo 'Hello World'
```
```
echo "Hello World"
```
After a few months you should be able to tell the difference.

Tips: if you want to run the same command again, maybe with small changes, press Up-arrow to get the previous command back, and then Left- and Right-arrows to make changes to the command before pressing Enter.

Tips: regularly backup of your files, in case something goes horribly wrong. It could be as simple as copy them all to one of two usb-sticks, unless you have tens of gigabytes of data or more.

---

### Post by slooksterpsv on 2010-08-04
The terminal is a powerful tool, it can also be very dangerous. What I'd do, and this is how I learned, is install VirtualBox, virtualize Ubuntu and play with the terminal, that way if you do something wrong like a remove all command you won't have messed up your OS, just the virtual.

Try these fun commands:
```

cat *filename*
tac *filename*
ls
l
df
ps aux
ps aux | grep gnome
ps aux | grep Xorg
cat *filename* | grep *keyword*
echo "Hello World"
top

```

All these commands are safe, they output information

---

### Post by David Andersson on 2010-08-04
Tips: what to do when you get stuck?

With some commands you will not immediately get back to the command prompt. The **man** and **less** commands will stay active until you press the **q** key. The **nano** command stays until you press Control-x. If you type **cat** or **grep** without a filename argument, they will read data from the keyboard, and stay active until you press Control-d or Control-c.

Example (end with q)
```
man grep
```
```
ls -a | less
```
Example (end with ctrl-d or ctrl-c)
```
cat
```

Some commands takes so long time that you might think they are stuck, but they will eventually finish and the command prompt will return. Press Control-c if you think it will take longer than you can wait (like hours or months) or if you think it is stuck.

Example (may take 10-60 seconds, cancel by pressing ctrl-c)
```
factor 12345678901234567891
```

One problem with the terminal is that sometimes there is no easy way to tell if a command is working and will finish by itself, or if it waiting for me to do something.

Most commands (but not man and less) can be canceled by pressing Control-c. So remember Control-c.

---

### Post by Drenriza on 2010-08-04
i have been working on a guide for new users to the terminal.
But to be honest i "ran, dead in it" since the forum didn't show alot of interest. And wasn't really interested in contributing, which i thought was a shame. Thus haven't been working on it since 25 may 2010.

I don't know if you can use it, and it isn't finished.

If you can use it, good. If not, thats not the end of the world.

I'm thinking about starting on it again and actually Finnish it.
But i don't see a point, if the forum thinks that the same information is available else where / better locations.

Let me know, what you think. If you read it.
Kind Regards

---

### Post by da burger on 2010-08-04
One last thing I will recommend, which is how I got into using the terminal. If there is something you do really often (installing software, extracting tar-balls or even just moving file around) learn how to do it in the terminal. Then every time you do that do it using the terminal. Keep doing this until the terminal is the most comfortable way for you to do this task, then find other stuff you want to learn to do in the terminal. Fairly quickly you'll be able to do everything you want to in the terminal.
Hope this helps.
Angus

---

### Post by slooksterpsv on 2010-08-04
> **da burger said:**
> One last thing I will recommend, which is how I got into using the terminal. If there is something you do really often (installing software, extracting tar-balls or even just moving file around) learn how to do it in the terminal. Then every time you do that do it using the terminal. Keep doing this until the terminal is the most comfortable way for you to do this task, then find other stuff you want to learn to do in the terminal. Fairly quickly you'll be able to do everything you want to in the terminal.
Hope this helps.
Angus

Sad part is, when you learn to use the terminal, you have a hard time using the GUI to go find your files or that. I actually do locate or ls -R | grep filename - instead of opening nautilus and going to the directory. To me its easier to cd ~/Downloads ; ls -R | grep somefile.zip ; unzip somefile.zip ; cd somefilefolder ; etc...

---

### Post by dvdjchvz on 2010-08-04
Thanks everyone.

This is a lot of useful info. Drenriza, thanks for making your work available. I will definitely let you know!

---

### Post by malspa on 2010-08-04
> **da burger said:**
> One last thing I will recommend, which is how I got into using the terminal. If there is something you do really often (installing software, extracting tar-balls or even just moving file around) learn how to do it in the terminal. Then every time you do that do it using the terminal. Keep doing this until the terminal is the most comfortable way for you to do this task, then find other stuff you want to learn to do in the terminal. Fairly quickly you'll be able to do everything you want to in the terminal.

I kinda did this in using **rsync** for backups.  Seemed daunting at first (quite a long manpage) but in the end it's such a quick and easy back-up tool.

---

### Post by Someone uk on 2010-08-04
```
cowsay moo
cowsay -f tux hi am am tux
fortune|cowsay -f tux
cowthink moo >> cowthink.txt
pico cowthink.txt
ls|cowsay
```
here are a few examples ;)
cowsay is a must for learning CLI it's a safe command and a good way to use piping and create txt files

---

### Post by evstevemd on 2010-08-04
First thanks drenriza for your work.
I'm not that newbie but i'm learning :p

Then to the question

search software names (Having little clue)
**apt-cache search firef***

once you get list of package names and now you want to install
**sudo apt-get install package_1 package2 **

Installing from tar.gz
**tar -xzf mytar**
[B]cd mytarried_folder
./configure && make &&sudo make install
[/B]
if you are lazy like me to run each single command ):P

---

### Post by slooksterpsv on 2010-08-06
And for all the options for -f, besides tux, cow, daemon, here's a list:
```

apt
beavis.zen
bong
bud-frogs
bunny
calvin
cheese
cower
daemon
default
dragon-and-cow
dragon
duck
elephant
elephant-in-snake
eyes
flaming-sheep
ghostbusters
gnu
head-in
hellokitty
kiss
kitty
koala
kosh
luke-koala
mech-and-cow
meow
milk
moofasa
moose
mutilated
ren
satanic
sheep
skeleton
small
stegosaurus
stimpy
supermilker
surgery
suse
telebears
three-eyes
turkey
turtle
tux
udder
vader
vader-koala
www

```

Had to remove a couple as they weren't appropriate for the forums like... well... run ls /usr/share/cowsay/cows to see which ones I'm talking about

---

### Post by Drenriza on 2010-08-09
> First thanks drenriza for your work.
So was it useful in anyway, or do you believe it could be useful to others?

> Then to the question
> if you are lazy like me to run each single command
i don't really understand the question. You want to run it all as a single command?

---

