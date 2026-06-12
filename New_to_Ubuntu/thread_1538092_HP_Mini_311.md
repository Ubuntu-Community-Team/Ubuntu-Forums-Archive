---
title: "HP Mini 311"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Feyerbrand on 2010-07-24
_**Original Post**_

[I]I have a HP Mini 311 series that came with windows 7 home premium installed.  I then proceeded to install a program called "Game Booster" which turns of main functions of windows to free up a ton of my CPU and RAM.  Therefore I could play games like World of Warcraft on medium graphics.

Well here is the issue.  I uninstalled windows because I love the way linux works.  Well when I installed wine I added to the HCKEY in wine the openGL with the direct3drenderer.  I then installed "Compiz-Switch" and yet the game even running on the lowest graphics is super choppy and doesn't run the way it is supposed to.  I have the NVidia ION hardware drivers installed.  Is there anything I Can do to speed up the performance for a game with a simple switch and then switch it back so I get all the cool features of linux again?   I would hate resulting on dual booting because I don't want to have to revert back to windows...[/I] [I]

System Specs[/I] [I]
Intel Atom 1.66 GHZ
3 GB Ram
NVidia ION
Ubuntu 10.04[/I]

_**Solution**_

Ok so we put together a bash script and also set up an xterm that is only scripted to run the game when you log in.  I will provide the codes below so you don't have to scour the Forum.

This is based on if you have for example World of Warcraft as the game that you are running.  You can change the game in the script just make sure you include the proper directories and names that apply. (as I said I will use this example for world of Warcraft.)  [I]This is for processors that aren't strong enough to run the full OS and a game at the same time.
[/I] 
first you have to create an option to switch between the Gnome session and the Game Session.

```
sudo cp /usr/share/xsessions/xterm.desktop /usr/share/xsessions/wow.desktop
```this will make an option to boot from in the log in screen.  You then need to edit it so it will have a command to run.  

```
gksudo gedit /usr/share/xsessions/wow.desktop
```this will pull up an editor.  You can copy and paste the code below or you can write a different one for the game that you are trying to make.  Remember spelling is very important.

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=Play World of Warcraft
Exec=wow.sh
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=GDM
```save the file.  we now need to make the bash script that will execute the **wow.sh**.  I will now include the steps below.

```
gksudo gedit /usr/local/bin/wow.sh
```you will now have a blank editor show up.  copy and paste the command in the window

```
#! /bin/bash
wine "C:\Program Files\World of Warcraft\WoW.exe"
```now save the file.  Here is the important part.  You need internet connection for World of Warcraft to pull up.  On your connection manager on the task bar, right click and select edit connections.  Now under you network manager it depends on whether you have Ethernet or WiFi, so select the corresponding tab.  highlight the connection name and select "Edit".  On the bottom of the window that shows up click **Available to all Users**.  This will make your internet available to all users on this computer, which will also include you xterm Wow session.

close out of your windows that you have open.  Log off the account that you are currently in.  When you arrive at the log in screen select the user where you have the game installed and where you wrote the bash script.  when the name is highlighted it will prompt you for the password.  Before entering the password at the bottom of the screen you will see a bar that has a few options.  next to the option **Sessions** there is a drop down arrow.  click the arrow and select **World of Warcraft**.  This will change your session from regular Gnome to only run World of Warcraft and nothing else.  Type in your password and select **Log In**.

And there you have it, you are running the game without running the full Ubuntu GUI.  Now when you close the game it will bring you back to the log in screen.  be sure to change your **Sessions** from **World of Warcraft **to **Gnome**.  Type in your password and you are booted back into your regular GUI.  I appreciate the help that Kerry_S gave me.  If you have questions post on the thread I will respond as soon as I am able : )

---

### Post by Feyerbrand on 2010-07-24
bump

---

### Post by Feyerbrand on 2010-07-24
bump

---

### Post by Mark Phelps on 2010-07-24
According to the logs, you bumped three time in less than three hours!

Show a little patience.  

The polite practice around here is to bump no more than once in 24 hours.

---

### Post by Feyerbrand on 2010-07-24
well I am sorry, as you can see I am completely new to this forum thanks.

---

### Post by d3v1150m471c on 2010-07-24
yeah I hate windows too but until our favorite game companies port games for linux we're prettymuch screwed. I'd suggest virtualbox

---

### Post by Feyerbrand on 2010-07-25
but can virtualbox run a full video game without glitching or running choppy?  I have windows 7 on my virtualbox is there any way I can get it set up to run just as quick?

---

### Post by d3v1150m471c on 2010-07-25
that depends on how good your hardware is.

---

### Post by kerry_s on 2010-07-25
i think the short answer is "no".

what you can try to do is log out, select the xterm session & run your game from there, thats about as barebone as you can get os wise, nothing else will be running.

tip: type "exit" in the terminal to get back to the log in screen after your finished.

---

### Post by ThomasHC on 2010-07-25
> **d3v1150m471c said:**
> yeah I hate windows too but until our favorite game companies port games for linux we're prettymuch screwed. I'd suggest virtualbox
As he has said, he's running a netbook. Virtualbox is not the best idea.
> **Feyerbrand said:**
> but can virtualbox run a full video game without glitching or running choppy?  I have windows 7 on my virtualbox is there any way I can get it set up to run just as quick?
Possibly...but to be honest, it won't run very well.
> **d3v1150m471c said:**
> that depends on how good your hardware is.

It's a netbook.


As kerry_s said, the best idea might be an xterm session. Basically this just starts graphical interface with only a terminal running. I doubt you will get very good results being it's a netbook and running it on wine, but it's certainly worth a shot, and I wish you the best of luck!

Thomas

---

### Post by Feyerbrand on 2010-07-26
I will let you know the results when I try tomorrow and see if there is any improvement.  Thanks guys I just know that when games are made more naturally for Linux it will be a lot better but for the time being I will see what we can do with small atom processors : )

---

### Post by Feyerbrand on 2010-07-26
I have one problem though, how do you switch you account to xterm and how do I run WOw through wine through XTerm?

---

### Post by kerry_s on 2010-07-26
> **Feyerbrand said:**
> I have one problem though, how do you switch you account to xterm and how do I run WOw through wine through XTerm?

at the log in screen, after you select your name, there is a session menu on the bottom.

how do you launch it in the normal desktop now?
if it's a launcher you just need to look at the command.

---

### Post by Feyerbrand on 2010-07-26
> **kerry_s said:**
> at the log in screen, after you select your name, there is a session menu on the bottom.

how do you launch it in the normal desktop now?
if it's a launcher you just need to look at the command.

so I get world of warcraft to launch but I have no internet.
I have wireless internet and it isn't enabled in xterm how do I go about enabling it?

---

### Post by kerry_s on 2010-07-26
> **Feyerbrand said:**
> so I get world of warcraft to launch but I have no internet.
I have wireless internet and it isn't enabled in xterm how do I go about enabling it?

type: **nm-applet &**

a little tip, when your in the desktop session, right click the wireless icon-> edit connections
in there select "wireless"
select your connection & edit
check "available to all users"

that should bring your wireless up during boot.

---

### Post by Feyerbrand on 2010-07-26
> **kerry_s said:**
> type: **nm-applet &**

a little tip, when your in the desktop session, right click the wireless icon-> edit connections
in there select "wireless"
select your connection & edit
check "available to all users"

that should bring your wireless up during boot.

So I ran the game through wine in Xterm and it ran like a beauty.  I think what would make this better having a program that you can run that automatically switches it to xterm and runs it through terminal and then switches back after closing the game.  But for the time this works well.

---

### Post by kerry_s on 2010-07-26
> **Feyerbrand said:**
> So I ran the game through wine in Xterm and it ran like a beauty.  I think what would make this better having a program that you can run that automatically switches it to xterm and runs it through terminal and then switches back after closing the game.  But for the time this works well.

i think we can get you pretty close to that.

use your **accessories-> terminal** for these commands:

**sudo cp /usr/share/xsessions/xterm.desktop /usr/share/xsessions/wow.desktop**
**gksudo gedit /usr/share/xsessions/wow.desktop**

in there change it to something like this:
```
[Desktop Entry]
Encoding=UTF-8
Name=**World of warcraft**
Comment=**Play wow**
Exec=**the wine command**
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm

```

"Exec=" is the important 1 you need put the command that you used in the xterm session, what this should do is launch the game in stead of opening a xterm.

"TryExec=" is the fall back & will launch the xterm if the "Exec=" fails.

just log out & select it in the session menu.

quiting the game should kick you back out to the log in.

let me know how it go's. good luck!

---

### Post by Feyerbrand on 2010-07-28
whenever I try to type the command it gives me the error 

no such file or directory

I don't know what I am doing wrong

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> whenever I try to type the command it gives me the error 

no such file or directory

I don't know what I am doing wrong

what command?

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> what command?
**sudo cp /usr/share/xsessions/xterm.desktop /usr/share/xsessions/wow.desktop**
[B]gksudo gedit /usr/share/xsessions/wow.desktop

it says 
cp: target '/usr/share/xsessions/wow.desktop' is not a directory
[/B]

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> **sudo cp /usr/share/xsessions/xterm.desktop /usr/share/xsessions/wow.desktop**
[B]gksudo gedit /usr/share/xsessions/wow.desktop

it says 
cp: target '/usr/share/xsessions/wow.desktop' is not a directory
[/B]

copy & paste the commands in order.

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> copy & paste the commands in order.ok so I edit that, but the wine commands I put in don't launch the game they just put me back into the regular ubuntu Gui.  What would be a good example for a wine command?

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> ok so I edit that, but the wine commands I put in don't launch the game they just put me back into the regular ubuntu Gui.  What would be a good example for a wine command?

what did you use in the xterm session?

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> what did you use in the xterm session? I just used 

**cd /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/**

and then when I am in the directory I type 

**wine Launcher.exe **

and it runs it

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> I just used 

**cd /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/**

and then when I am in the directory I type 

**wine Launcher.exe **

and it runs it

try putting:
wine "C:\Program Files\World of Warcraft\Launcher.exe"
or
wine "C:\Program Files\World of Warcraft\WoW.exe"
or
wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe


according to "  [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) " 1 of those commands should work.

im thinking the " wine "C:\Program Files\World of Warcraft\WoW.exe" " will be the one.

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> try putting:
wine "C:\Program Files\World of Warcraft\Launcher.exe"
or
wine "C:\Program Files\World of Warcraft\WoW.exe"
or
wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe


according to "  [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) " 1 of those commands should work.

im thinking the " wine "C:\Program Files\World of Warcraft\WoW.exe" " will be the one.I tested the last one in terminal and it launched it perfectly, I gedited the wow.desktop and logged out and launched the command like I would xterm.  It still logs me into the regular gnome sessions and doesn't launch the game.  Any clues?

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> I tested the last one in terminal and it launched it perfectly, I gedited the wow.desktop and logged out and launched the command like I would xterm.  It still logs me into the regular gnome sessions and doesn't launch the game.  Any clues?

okay, that's try to put it in a script.

gksudo gedit /usr/local/bin/wow.sh

put:

#!/bin/bash
wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe

chmod +x /usr/local/bin/wow.sh

try "wow.sh" in the terminal see if it works.
if that go's okay

put "wow.sh" for the command in wow.desktop.

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> okay, that's try to put it in a script.

gksudo gedit /usr/local/bin/wow.sh

put:

#!/bin/bash
wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe

chmod +x /usr/local/bin/wow.sh

try "wow.sh" in the terminal see if it works.
if that go's okay

put "wow.sh" for the command in wow.desktop.ok it loads the world of warcraft just fine through terminal with the bash, when I put that in the wow.desktop and it pulls up the Splash image like its going to load the game, and then it flashes the screen like its logging out and puts me back to the log in screen to choose my user.

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> ok it loads the world of warcraft just fine through terminal with the bash, when I put that in the wow.desktop and it pulls up the Splash image like its going to load the game, and then it flashes the screen like its logging out and puts me back to the log in screen to choose my user.

okay, sounds like where getting closer.
lets try it with the terminal then.

gksudo gedit /usr/local/bin/wow.sh

add "xterm -e" to the front, should look like this now:

```
#!/bin/bash
xterm -e wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
```

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> okay, sounds like where getting closer.
lets try it with the terminal then.

gksudo gedit /usr/local/bin/wow.sh

add "xterm -e" to the front, should look like this now:

```
#!/bin/bash
xterm -e wine /home/tyson/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
```

It did the same thing, but this time it pulled up terminal like I was in Xterm and it had the splash logo of wow but still puts me back to the log in page

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> It did the same thing, but this time it pulled up terminal like I was in Xterm and it had the splash logo of wow but still puts me back to the log in page

okay, lets try cutting the game loose from the script.

gksudo gedit /usr/local/bin/wow.sh

```
#!/bin/bash
wine "C:\Program Files\World of Warcraft\WoW.exe" &

```

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> okay, lets try cutting the game loose from the script.

gksudo gedit /usr/local/bin/wow.sh

```
#!/bin/bash
wine "C:\Program Files\World of Warcraft\WoW.exe" &

```that got rid of the splash screen and it had the same result as the first attempt

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> that got rid of the splash screen and it had the same result as the first attempt

thats try & get some logs

gksudo gedit /usr/local/bin/wow.sh

```
#!/bin/bash
wine "C:\Program Files\World of Warcraft\WoW.exe" > /home/tyson/Desktop/wow.log
```

---

### Post by Feyerbrand on 2010-07-28
> **kerry_s said:**
> thats try & get some logs

gksudo gedit /usr/local/bin/wow.sh

```
#!/bin/bash
wine "C:\Program Files\World of Warcraft\WoW.exe" > /home/tyson/Desktop/wow.log
```it gives the error

"/home/tyson/Desktop/wow.log: no such file exists"

---

### Post by kerry_s on 2010-07-28
> **Feyerbrand said:**
> it gives the error

"/home/tyson/Desktop/wow.log: no such file exists"

alright, take a break. i got about 45min more on my movie, then i'll take a closer look at it.

---

### Post by kerry_s on 2010-07-28
so weird i just tried it with the movie player & it works as expected.

lets go back to the session.

gksudo gedit /usr/share/xsessions/wow.desktop

for the command put:
wine "C:\Program Files\World of Warcraft\WoW.exe"

do both the "Exec=" & "TryExec="

can you post your wow.desktop so i can see how you have it in there, just to double check.

---

### Post by Feyerbrand on 2010-07-29
> **kerry_s said:**
> so weird i just tried it with the movie player & it works as expected.

lets go back to the session.

gksudo gedit /usr/share/xsessions/wow.desktop

for the command put:
wine "C:\Program Files\World of Warcraft\WoW.exe"

do both the "Exec=" & "TryExec="

can you post your wow.desktop so i can see how you have it in there, just to double check.no go with the command in both exec= and tryexec

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=Play World of Warcraft
Exec=wine "C:\Program Files\World of Warcraft\WoW.exe
TryExec=wine "C:\Program Files\World of Warcraft\Wow.exe
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```

---

### Post by kerry_s on 2010-07-29
your missing **"** on the end of.

Exec=wine "C:\Program Files\World of Warcraft\WoW.exe
TryExec=wine "C:\Program Files\World of Warcraft\Wow.exe

got to be careful little things like that will make it fail right away.

---

### Post by Feyerbrand on 2010-07-29
> **Feyerbrand said:**
> no go with the command in both exec= and tryexec

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=Play World of Warcraft
Exec=wine "C:\Program Files\World of Warcraft\WoW.exe
TryExec=wine "C:\Program Files\World of Warcraft\Wow.exe
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```

so as crazy as this sounds it works!  I changed it around a bit and put it back to the bash that you made.  The wow.sh was in the exec=wow.sh

so the code now looks like 

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=Play World of Warcraft
Exec=wow.sh
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```

---

### Post by Feyerbrand on 2010-07-29
now the next even cooler step would be to make an icon on the desktop that would log me out and run the xterm that we just scripted : )

---

### Post by kerry_s on 2010-07-29
> **Feyerbrand said:**
> so as crazy as this sounds it works!  I changed it around a bit and put it back to the bash that you made.  The wow.sh was in the exec=wow.sh

so the code now looks like 

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=Play World of Warcraft
Exec=wow.sh
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```


finally! you must of had a typo some where.
man i was running out of ideas.

---

### Post by kerry_s on 2010-07-29
> **Feyerbrand said:**
> now the next even cooler step would be to make an icon on the desktop that would log me out and run the xterm that we just scripted : )

beyond my skills, sorry.

---

### Post by Feyerbrand on 2010-07-29
> **kerry_s said:**
> beyond my skills, sorry.its ok I will mark this as solved and add a post on the front that shows people how to do it thank you for all your help you are a Genius : )

---

### Post by ATLien3 on 2010-07-29
> **thomashc said:**
> as he has said, he's running a netbook. Virtualbox is not the best idea.

Possibly...but to be honest, it won't run very well.


It's a netbook.


As kerry_s said, the best idea might be an xterm session. Basically this just starts graphical interface with only a terminal running. I doubt you will get very good results being it's a netbook and running it on wine, but it's certainly worth a shot, and i wish you the best of luck!

Thomas

its a netbook

---

