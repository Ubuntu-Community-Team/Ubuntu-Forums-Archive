---
title: "Loading games"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by Schat on 2010-10-09
How do I load a game on Ubuntu , like simcity

---

### Post by Trandok on 2010-10-09
Just type the name of the game into terminal. The command you need to enter may sometimes be a little different from the name(e.g. Wolfenstein: Enemy Terriotry is [FONT="Courier New"]wolfet[/FONT]) to make it shorter. 

You can always run a game(or whatever application for that matter) from it's executable as well of course.

---

### Post by themusicalduck on 2010-10-09
Are you trying to install it?

What kind of game is it? A Windows game, DOS game or native Linux Game, or something else? What do you have to install it from?

---

### Post by e79 on 2010-10-09
If its not a native Linux Game (search through Ubuntu Software Center or from Ubuntu-Tweak) or if you know this is a Windows game (containing some executable files - .exe), you will have to install WINE to try and run them.

Visit this site first
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

and add the PPA as shown in the picture and then

```
sudo apt-get install wine
```

Hope this helps

---

### Post by Schat on 2010-10-10
The name of this game is simcity 4 it is an EA game. It runs from a CD . this works on micgrosoft windows

---

### Post by themusicalduck on 2010-10-10
Generally you can't run Windows software in Ubuntu.

You could try using Wine though as e79 says. You could install Wine straight from the Software Centre, or you can add the PPA if you want the latest version. Using the PPA might not be necessary though.

Once you've installed Wine, it's a good idea to copy the contents of the CD to the harddrive and install it from there. You could copy it into a folder on the Desktop. Then right click on the Setup file, go to Properties, Permissions and check the Allow executing file as program box. Then go to the Open With tab and select Wine. Alternatively launch it straight off the CD with the terminal (wine /path/to/setup.exe)

Double click the file and try to run the installer. Hopefully it should work from there on and you can launch the game from the Wine menu under Applications once it's installed.

If you have problems it might be worth looking through these pages - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10515](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10515) [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1565](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1565)

Wine isn't perfect though, it might just not work, hopefully it will though.

---

