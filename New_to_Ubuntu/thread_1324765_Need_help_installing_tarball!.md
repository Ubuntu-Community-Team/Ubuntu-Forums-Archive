---
title: "Need help installing tarball!"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by kana_dragongirl on 2009-11-12
(Warning: I'm a total noob when it comes to command line stuff. I know the very, very basic things and thats about it. So, if you want to me to do something in command line, please thoroughly explain.) Sorry I'm such a n00b! D:

:confused:

I'm trying to install a program called Alchemy. Here's where I downloaded the program: [http://al.chemy.org/download/](http://al.chemy.org/download/)

It comes in a tar.gz I looked at the read me and it tells me that I have to extract it. (Did that fine.) Then, take the folder and put it where I put all of my other applications. So, I have no clue where to put this thing. DX

Here's a link to the readme that they include: [http://en.flossmanuals.net/Alchemy/InstallingLinux](http://en.flossmanuals.net/Alchemy/InstallingLinux) 

It tells me that once I move it to the proper directory, I should run the .jar file in the java runtime environment. Well, since I didn't know where to put it, I just decided to try running it. It says that one or more modules need to be there for it to run. Theres a folder within the main Alchemy folder called modules so, I don't know whats up and I have no clue what I'm doing. If someone could please help my dumb self make sense of this that would be awesome. :P I'm used to downloading everything through synaptic package manager.

Also: I'm using Ubuntu 8.04

---

### Post by camaron1 on 2009-11-12
> **kana_dragongirl said:**
> (Warning: I'm a total noob when it comes to command line stuff. I know the very, very basic things and thats about it. So, if you want to me to do something in command line, please thoroughly explain.) Sorry I'm such a n00b! D:

:confused:

I'm trying to install a program called Alchemy. Here's where I downloaded the program: [http://al.chemy.org/download/](http://al.chemy.org/download/)

It comes in a tar.gz I looked at the read me and it tells me that I have to extract it. (Did that fine.) Then, take the folder and put it where I put all of my other applications. So, I have no clue where to put this thing. DX

Here's a link to the readme that they include: [http://en.flossmanuals.net/Alchemy/InstallingLinux](http://en.flossmanuals.net/Alchemy/InstallingLinux) 

It tells me that once I move it to the proper directory, I should run the .jar file in the java runtime environment. Well, since I didn't know where to put it, I just decided to try running it. It says that one or more modules need to be there for it to run. Theres a folder within the main Alchemy folder called modules so, I don't know whats up and I have no clue what I'm doing. If someone could please help my dumb self make sense of this that would be awesome. :P I'm used to downloading everything through synaptic package manager.

Also: I'm using Ubuntu 8.04

I think you probably need to install sun-java 6 
Once you've done that just put the program folder anywhere you like (it doesn't matter where) and either click on the file call ALCHEMY every time you want to run the program or right-click on the menu (applications-places-system) and click on EDIT MENUS  to create a shortcut anywhere you like in the applications menu. To do this click on Science (for example), click on ADD ITEM. Write the name of the application (Alchemy), chose a logo, and for command browse to the application folder and click again ALCHEMY. 

This should do.

---

### Post by kana_dragongirl on 2009-11-13
I have java installed on my computer. When I run it in java it says it needs one or more modules.

---

### Post by camaron1 on 2009-11-13
> **kana_dragongirl said:**
> I have java installed on my computer. When I run it in java it says it needs one or more modules.

Does it tell you what modules?

---

### Post by camaron1 on 2009-11-13
Thinking about it: install a java program from synaptic like VUZE (torrent client). This will install all modules and dependencies you need to run a java program in Ubuntu and then try running yours.

---

### Post by SwatKat on 2009-11-14
Hey, 
Most application files are in /usr/bin. So try copying your alchemy folder there. If you extract the jar download, you must get a folder called Alchemy. Then open the terminal and type

```
sudo cp -R ~/Downloads/Alchemy /usr/bin/Alchemy
```I am assuming that you have your folder stored in Downloads. If it is on the desktop, replace Downloads by Desktop.
That should copy your folder to /usr/bin. The readme says
**To open Alchemy simply double-click on the 'Alchemy' file inside the Alchemy folder to launch the .jar file. **
So click on Alchemy file (the one with the blue rhombus thingy). According to the instructions given in the readme, this should work. Good luck!!

---

### Post by Rtech on 2010-07-23
OK! I got it to work on my 64 bit 10.04 :D
Create a plain document in the Alchemy folder(same folder location as the 'modules'), open it up with gedit, enter in the text: 
[I]
cd '/home/blah blah/wherever/Alchemy'
sudo sh Alchemy[/I] 

Then save it as a .sh So it should look like this [I]Alchemy.sh
[/I]Right click that document and select "Permissions" from the tabs, then make sure you check "Allow _e_xecuting file as program"
Only one thing left to do is to make a shortcut, like on the panel or wherever is convenient for you. Make sure you make a "custom application launcher". Set the "Type" as a Application, Name it Alchemy of course ;), browse for that file you just made (Alchemy.sh), close it, and you should be good! Hope that works for you.

[CENTER][I][COLOR=Blue]This proves the power of Ubuntu or Linux in general!
I am not a programmer, I have very little known commands, 
I had a hunch...and it worked! That describes most of how I'm learning 
Ubuntu. Trial and error...with very little error ;) 
[/COLOR][/I][/CENTER]

---

### Post by mkvnmtr on 2010-07-23
Have you downloaded the manual from the site? That might help. Without the manual I can not seem to figure out where to get the modules.

---

