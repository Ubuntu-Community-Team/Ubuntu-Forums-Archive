---
title: "adding multiverse and universe to sources"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-24
I am trying to install daz 3d, but to do that I need to get multiverse and universe onto my sources list so that I can get the proper fonts for Wine. I found a tutorial on installing the fonts that instructs one to use this line of code to first backup the source list


sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup


This makes me a bit nervous. When I used the line of code, nothing appears to have happened. Should I have seen some confirmation of the backup?

If someone can walk me through getting these sources or point me to the proper place for instructions, I would appreciate it.

thanks
mystmaiden

---

### Post by camper365 on 2009-04-24
When you copy in the terminal, there is absolutely no response. This is normal.
If you really want to check, you can open the file browser and check to make sure the file is there, but it did copy.

As to adding multiverse and universe, Go to 
System -> Administration -> Software Sources.
Once you are there, you can check the boxes to allow main, restricted, universe, and multiverse.
However, simply doing this will not allow you to have access to them.
When you click the close button in the bottom right corner, a dialog box will come up. Once there, click refresh, or if you missed your chance, in a terminal type
```
sudo apt-get update
```.
Doing either of these will download some files (about 42 (this is not a joke, the number really is 42)). These files are small and will not take up much space.
After you have done that, you can use sudo apt-get install (I prefer aptitude however, it handles dependencies better).

---

### Post by fooman on 2009-04-24
if you get nervous with the commands....try a gui

go to system > administration > software sources

on the ubuntu software tab...check off the first 4 choices (main, uninverse, restricted, multiverse)

hope that helps.

---

### Post by tjwoosta on 2009-04-24
[QUOTE=mystmaiden]This makes me a bit nervous. When I used the line of code, nothing appears to have happened. Should I have seen some confirmation of the backup?[/QUOTE]

no need to get nervous


all that command did was make a duplicate of your sources.list file called sources.list.backup

no you wont get a confirmation

to confirm that it worked you can simply ```
cd /etc/apt
``` to change directories and ```
ls
``` to list the files in that directory, then just look for sources.list.backup


to open a text file like sources.list you can use gedit (its just a text editor almost like notepad in windows)

so you can do 
```
sudo gedit /etc/apt/sources.list
``` (the sudo part is just to give yourself adiministrator privelages, so you can edit the file meaning it will ask for your password)

in your sources.list file you will see a bunch of lines that begin with a "#"

the # means that line is commented out (ignored)

so to enable repositories you can just find the correct line and remove the # to make it become active, then just save the file

its that simple!

if you decide you dont want it anymore you can just put the # back in place and everything is back to normal


if worse comes to worse and you screw up the file so bad that it wont work anymore you can simply restore the backup that you made earlier by renaming sources.list.backup to sources.list like this

```

sudo mv sources.list.backup sources.list
```


of course all of this stuff can easily be done without the command line,in a few different ways, but if you ask me its good practice

---

### Post by mystmaiden on 2009-04-25
Many thanks everyone! All set now :)

myst

---

