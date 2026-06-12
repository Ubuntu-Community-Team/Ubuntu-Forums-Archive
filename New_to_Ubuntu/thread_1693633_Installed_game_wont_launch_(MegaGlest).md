---
title: "Installed game wont launch (MegaGlest)"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by StarZtorm on 2011-02-23
So i installed a game called MegaGlest. Seemed like something worth trying out. 

Anyway. When i installed the game it wouldnt show up in the applications>games menu, so i restarted the system, and now it shows up there. But when i click it, the game wont launch, and neither will the editor. Theres no error message or anything. Just seems like nothing happens when i try to start the game.

Any help would be much appreciated.

---

### Post by StarZtorm on 2011-02-23
sorry but i cant help it. Bump.

---

### Post by An Sanct on 2011-02-23
(to bump within 24h is not cool)

Have you tried to run it from a terminal? If you run it from a terminal, output text will be shown, review it or copy it to the forum.

---

### Post by StarZtorm on 2011-02-23
(ill keep that in mind, thanks.)

Well, im a newbie at this. I know how to get to the terminal window. The command im not familiar with. but by typing the name of the program i got this. 

starztorm@starztorm-MS-7220:~$ megaglest
megaglest: command not found
starztorm@starztorm-MS-7220:~$ glest
The program 'glest' is currently not installed.  You can install it by typing:
sudo apt-get install glest
starztorm@starztorm-MS-7220:~$

---

### Post by lykeion on 2011-02-23
How did you install megaglest? Was it via GetDeb/PlayDeb or did you download the installer from megaglest.org?

The default installation dir is /home/<username>/megaglest
In this dir there should be a start script called *glest*

With this info you can start game from a terminal:
1. Applications > Accessories > Terminal
2. Enter this command (notice I've changed <username> to your username starztorm).
```
/home/starztorm/megaglest/glest
```

If it starts okay you can edit the entry in the Applications > Games menu:
1. Right-click Applications menu > Edit menus
2. Select Games to the left, and Megaglest on the right, then click Properties button.
3. Make sure the Command field have the correct path to the glest start script: /home/starztorm/megaglest/glest

PS You don't have to reboot Ubuntu to update Applications menu, see [HERE]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_refresh_GNOME_panel")

---

### Post by Perfect Storm on 2011-02-23
There's an ubuntu repository/package of the game here: [http://www.playdeb.net/updates/ubuntu/10.10/?q=mega](http://www.playdeb.net/updates/ubuntu/10.10/?q=mega)

---

### Post by jefrodmat on 2011-03-03
the same for me.
solved:
user/megaglest/docs/readme   - line190


some libraries's dependences 
i do not know for sure, but i think the openal is what was missing.:confused:
i used synaptic to get:
                       [LIST]
[*]                        libwxbase2.8-0 (2.8.11.0-0ubuntu4)
[*]                        libopenal1 (1:1.12.854-2)
[*]                        libwxgtk2.8-0 (2.8.11.0-0ubuntu4)
[*]                        wxformbuilder (3.1.59-0ubuntu1)
[/LIST]

still did not work (typing glest on terminal):(

i tried ./glest end THE LIGHT!! :)

---

