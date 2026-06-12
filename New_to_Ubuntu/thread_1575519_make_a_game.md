---
title: "make a game"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by zachary white on 2010-09-15
I want to make a game but I have no idea how to program in lynix!!!!!!!!!!!!!!!:-(
somebody help!!!!!!!!!

---

### Post by lkjoel on 2010-09-15
> **zachary white said:**
> I want to make a game but I have no idea how to program in lynix!!!!!!!!!!!!!!!:-(
somebody help!!!!!!!!!
Welcome to Ubuntu Forums!
What programming language do you want to use?

---

### Post by anewguy on 2010-09-16
More power to you for wanting to do this.  If you are younger, you may suspect that this easily done.  Text-based games aren't bad at all, however if you want to make a more main-stream action game with lots of moving graphics, you'll have to learn quite a bit first.

The first thing would be to decide exactly what you want to do, as some programming languages are better suited for some tasks than others.  After you have that defined, post here with a general idea (obviously we don't want to give away your game idea!) - graphics intensive, etc., types of things.  From there we can hopefully recommend a language that might suit your task - in fact I'm sure several will be recommended.  It will be up to you to be sure you understand the language you choose extremely well.  From there, there are some tutorials on the net for doing some game development - you may want to check those and see if you are up to the task.

Dave ;)

---

### Post by zachary white on 2010-09-16
would it be possible to use XNA Studios to make the game and then convert it to Linux?

---

### Post by 3rdalbum on 2010-09-16
> **zachary white said:**
> would it be possible to use XNA Studios to make the game and then convert it to Linux?

XNA Game Studio only outputs to Microsoft platforms, as you'd kinda expect considering it's a Microsoft product.

---

### Post by Paul820 on 2010-09-16
What about this: [http://game-editor.com/Main_Page]("http://game-editor.com/Main_Page")

---

### Post by anewguy on 2010-09-16
Never saw it before.  At a glance, I can't tell if it runs in Linux, or only has the ability to export games to Linux.  The source code is available for download, so I suppose you could always download the source code and try to compile it and see what happens.  I'd try it myself to let try to get it working but I honestly am not feeling that ambitious today.

Dave ;)

---

### Post by Paul820 on 2010-09-16
It runs on Linux ;) Here it is on Ubuntu 10.10 on my machine. Just chmod +x the executable and run it. There is an exe in there for windows and MacOS X.

---

### Post by lkjoel on 2010-09-16
> **zachary white said:**
> would it be possible to use XNA Studios to make the game and then convert it to Linux?
You could use WINE to run it.

---

### Post by anewguy on 2010-09-16
> **Paul820 said:**
> It runs on Linux ;) Here it is on Ubuntu 10.10 on my machine. Just chmod +x the executable and run it. There is an exe in there for windows and MacOS X.

For Linux, does it include the config and make files or some process to compile from the source?

Interesting.......

Dave ;)

---

### Post by Paul820 on 2010-09-16
I didn't compile from source i just downloaded the prebuilt package and ran the program. You can get the source code, which i have just done to have a look (it's a 66Mb download for the source) and there are instructions on how to build it along with the dependencies required and a makefile.
An excerpt from the build instructions
> Linux: (tested on Kubuntu 9.10 64bits)

1) Open a terminal window

2) Install the libx11-dev (if not installed on your system) 
	sudo apt-get update
	sudo apt-get install libx11-dev libxpm-dev x11proto-xext-dev libxext-dev

3) Make sure you have the gcc and g++ installed. If not, install it:	
	sudo apt-get install g++

4) Install the 32bit library if you are using a 64bit linux (Game Editor was not ported to 64bit yet)
	sudo apt-get install libc6-dev-i386
	sudo apt-get install lib32stdc++6	
	sudo apt-get install g++-multilib
	sudo apt-get install ia32-libs

5) Go to the Game Editor directory

6) type: make

7) Copy the contents of the directory gameEditor/res to output (or in the place you have put gameEditorLinux file)

Seems simple enough, but it's already prebuilt and works so i don't suppose there is any need to build it yourself. Unless you want to of course. :D

---

### Post by zachary white on 2010-09-16
i tried game editor but couldent get it to run even with the chmod terminal command.

---

### Post by Paul820 on 2010-09-16
> **zachary white said:**
> i tried game editor but couldent get it to run even with the chmod terminal command.
Did you > **sudo** chmod +x gameEditor

---

### Post by lkjoel on 2010-09-16
After "make", try:
```
sudo make install
```

---

### Post by zachary white on 2010-09-16
it says that there is no such file in directory, how do I copy the files to the directory???????????????

---

### Post by Paul820 on 2010-09-16
Ok, make sure you are in the right place. You should see all these files:
> bin            functions.xml     Game Editor Professional.url  readme.txt
b_xy.png
gameEditor.exe
GPL.txt
Tutorials
changelog.url
GameEditor.ini
grid.JPG
Docs
gameEditorLinux
license.txt
editor.dat
gameEditorMacOSX
logo.png
Open a terminal and cd to the directory with those files in it if you are not already there. So you enter
> cd /to/the/folder/
Type ls (that's a lowercase L)to make sure you see those files above. Now in the terminal enter
> sudo chmod +x gameEditorLinux
Enter your password. Now either double click the 'gameEditorLinux' file or run it from the terminal by entering
> ./gameEditorLinux

Let us know how you get on. :D

---

### Post by fslezak on 2010-09-16
You should practice with SIMPLE applications before you get into big stuff like games.

Use Python. VERY SIMPLE and STRONG!!!

Documentation: [http://python.org/doc/](http://python.org/doc/)

---

### Post by zachary white on 2010-09-17
I cant figure out the path.
what would the path be if the game editor folder is on my desk top?
oh and I'm not running kubuntu. I'm running ubuntu 10.42 desk top edition and am on a gnome sesion

---

### Post by Paqman on 2010-09-17
> **zachary white said:**
> 
what would the path be if the game editor folder is on my desk top?


~/Desktop/foldername

(which is exactly the same as /home/username/Desktop/foldername)

---

### Post by Paul820 on 2010-09-17
> oh and I'm not running kubuntu. I'm running ubuntu 10.42 desk top edition and am on a gnome sesion

I don't think it really matters if you are not using Kubuntu. I'm using the Ubuntu 10.10 development version with Gnome and it works fine on mine.

---

### Post by limestone on 2010-09-17
python and pygames

---

### Post by zachary white on 2010-09-17
ummmmmmmmm......................

Im not sure but I dont think it worked.
I enterd the "sudo chmod +x Desktop/GameEditor" command and hit enter and nothing happend exept for the curser moving down to the next line.
and when I double clicked on the program, as crazy and imposible as it may sound, all it did was reopen the exact same folder I was in (GameEditor-File Browser)

now I,m realy confused. what just happend?
and how do I fix it?

---

### Post by Paul820 on 2010-09-17
Right, lets start this again.

Open a terminal and enter this:
> sudo apt-get install nautilus-open-terminal
When that has downloaded, log out and then back in again.

Make sure you can see the file gameEditorLinux, it's a 3.1Mb file. If you can then you are in the right place. If not, browse to the place where that file is. When you are in the right place the continue below.

Right click anywhere and select
> Open In Terminal
Now enter this in the terminal
> sudo chmod +x gameEditorLinux
Nothing else but that, copy and paste it if you have to. When you have done that, double click the gameEditorLinux file to run it or run it from the terminal by typing
> ./gameEditorLinux
Do not close the terminal if you run it from there as it will close the program as well.

---

### Post by zachary white on 2010-09-17
[size=7]thats it!!!!!!!!!!!
It finally worked!!!!
Thanks for your help!!!!!!!!!!!!!!!!!!!!!!!!!!
[/size]

---

### Post by anewguy on 2010-09-17
WOW, and I was just getting my sight back again since the old above-ground nuclear test days!

---

### Post by baddnady23 on 2010-09-17
> **anewguy said:**
> WOW, and I was just getting my sight back again since the old above-ground nuclear test days!


I think he got it to work.  :lolflag:

---

