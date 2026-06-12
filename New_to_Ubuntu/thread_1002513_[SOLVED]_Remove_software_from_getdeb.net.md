---
title: "[SOLVED] Remove software from getdeb.net?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by b0yd07 on 2008-12-05
After giving up on my install of Songbird 'the way they want me to' (.tar.gz), I found getdeb.net and installed it from there. All is well.

I'm starting to dislike it actually though. My touch buttons don't work and it just doesn't feel polished like some others. For the life of me though I can't figure out how to uninstall it. It's not under synaptic and it's not under add/remove programs... the only two ways I know of to do stuff at the moment (learning).

Two, three (i guess) questions for you:
1. How the heck do I get it off my system?
2. When installing anything in Windows, **** gets installed everywhere. Ubuntu just copies the program into a folder in the file system and that's the end of it?
3. I'm looking for a media player to use for my ipod. I don't like Songbird, so that leaves Banshee, Amorak, and Rhythmbox? Which of the three to you guys prefer?

---

### Post by nakama85 on 2008-12-05
> **b0yd07 said:**
> After giving up on my install of Songbird 'the way they want me to' (.tar.gz), I found getdeb.net and installed it from there. All is well.

I'm starting to dislike it actually though. My touch buttons don't work and it just doesn't feel polished like some others. For the life of me though I can't figure out how to uninstall it. It's not under synaptic and it's not under add/remove programs... the only two ways I know of to do stuff at the moment (learning).

Two, three (i guess) questions for you:
1. How the heck do I get it off my system?
2. When installing anything in Windows, **** gets installed everywhere. Ubuntu just copies the program into a folder in the file system and that's the end of it?
3. I'm looking for a media player to use for my ipod. I don't like Songbird, so that leaves Banshee, Amorak, and Rhythmbox? Which of the three to you guys prefer?
You can copy and paste if you would like.
in terminal (Applications--->Accessories--->Terminal) run the following code

1:to remove songbird ```
sudo apt-get remove songbird
```
2: not sure what your asking
3:```
sudo apt-get install amarok
```
Amarok is one of the more popular apps that should work with ipod you could also try Rythembox i here it does really well. Just try them and see what you like

---

### Post by yellowaeroplane on 2008-12-05
1)Not too sure, ha. I installed mine "the way they wanted me to"

2)Kind of, but it depends on the app. Most apps (like Firefox) get installed in your home directory as hidden(.) folders and then are launched from usr/bin. But it depends, some files are installed in /opt, some in /etc. It just depends on their function and how they're written.

3)What kind of iPod do you have? If you have new one like a touch (like me) or iPhone, you're out of luck. Nothing really supports them. In fact, this is really the only reason I ever use Windows.

Older iPods and new classic iPods are supported fairly well. I'd say the consensus best app for iPods is Amorak, but it depends on who you're talkin' to.

---

### Post by jespdj on 2008-12-05
> **b0yd07 said:**
> 1. How the heck do I get it off my system?
The good thing about .deb packages is that the packaging system knows about them, so you can uninstall them with apt-get or with Synaptic in the same way that you would uninstall any other program installed from the Ubuntu repository.

> **b0yd07 said:**
> 2. When installing anything in Windows, **** gets installed everywhere. Ubuntu just copies the program into a folder in the file system and that's the end of it?
No, but the packaging system is much better at keeping track of what gets installed where, so when you uninstall something, it's usually much cleaner than with Windows. Note that normally when you uninstall something with "apt-get remove" (or with Synaptic), configuration files might be left on your system. You can do a more thorough uninstall by using "apt-get purge" instead of "apt-get remove" - this will also remove configuration files.  (Note that you can also do this in Synaptic: right-click the package you want to remove and select "Mark for **Complete** Removal" instead of the usual "Mark for Removal").

> **b0yd07 said:**
> 3. I'm looking for a media player to use for my ipod. I don't like Songbird, so that leaves Banshee, Amorak, and Rhythmbox? Which of the three to you guys prefer?
Sorry, can't help you with this. I do have an iPod, but I use iTunes on Windows to manage it.

---

### Post by SunnyRabbiera on 2008-12-05
it all depends on how you installed it, for your original install of songbird what did you do to install it before discovering the .deb?

---

### Post by Michael.Godawski on 2008-12-05
> 1. How the heck do I get it off my system?
If you installed the package via a downloaded deb try
```
sudo dpkg --remove package.deb
```
> 2. When installing anything in Windows, **** gets installed everywhere. Ubuntu just copies the program into a folder in the file system and that's the end of it?
Yes Linux is not Windows. 

[LIST]
[*][https://help.ubuntu.com/community/InstallingSoftware#Packages%20and%20Package%20Management](https://help.ubuntu.com/community/InstallingSoftware#Packages%20and%20Package%20Management)
[/LIST]
> 3. I'm looking for a media player to use for my ipod. I don't like Songbird, so that leaves Banshee, Amorak, and Rhythmbox? Which of the three to you guys prefer?
have no ipod, have no idea, but the three are your right candidates...

---

### Post by ajgreeny on 2008-12-05
> If you installed the package via a downloaded deb try
 	Code:
 	sudo dpkg --remove package.deb 

Actually it's just ```
sudo dpkg --remove package
```Don't add the **.deb** at the end.

---

### Post by b0yd07 on 2008-12-05
> **ajgreeny said:**
> Actually it's just ```
sudo dpkg --remove package
```Don't add the **.deb** at the end.

That worked great. Thanks for the help everyone.

I guess the underlying question I had for #2 pertained to how windows got more and more cluttered with garbage after installing a program. Even after uninstalling a program your system never truly was the same again until you reformat the drive. My hunch was that Ubuntu/Linux in general *did* go back to its original state, and run just as fast as it did beforehand. Is my thought process getting me anywhere? Haha

As per the music players, I guess I could have tried all three out but didn't want to start ****ing my fresh install up by adding and removing software. But I guess that is just windows that self-destroys itself.
I might end up having to use iTunes though for the Nike+ integration. Boo

---

### Post by nhasian on 2008-12-05
From Getdeb's website:

> The following document will help you to uninstall all getdeb packages, this action is recommended if 
you are about to perform an Ubuntu distribution release upgrade.

System *> Administration *> Synaptic Package Manager
Click on the &#8220;Search&#8221; button
Type &#8220;getdeb&#8221; on the seach field, and change the &#8220;Look in&#8221; to version.

From the result list select all packages by pressing &#8220;CTRL*A&#8221;
Then mark the packages to be deleted with &#8220;DEL&#8221;
You may get a warning that additional packages will need to be removed:

Please note that &#8220;ubuntu*desktop&#8221; means you are removing some packages which are part of the 
Ubuntu standard desktop list, it will not remove all your desktop packages.
You should now use the &#8220;Apply&#8221; button to start the packages removal.



PS I had to press the Reload button in Synaptic Package Manager before the search worked for me

---

