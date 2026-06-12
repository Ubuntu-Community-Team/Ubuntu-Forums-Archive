---
title: "how to play dota in ubuntu???"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by jaswind3r on 2010-11-08
hey guys,
i am new to ubuntu so please i want to know how to play Warcraft III - DOTA in ubuntu...
i have heard we can play it through winehq but seriously i'm nub in this thing.... please rpy as soon as possible...

thanks

---

### Post by bedihardeep on 2010-11-08
> **jaswind3r said:**
> hey guys,
i am new to ubuntu so please i want to know how to play Warcraft III - DOTA in ubuntu...
i have heard we can play it through winehq but seriously i'm nub in this thing.... please rpy as soon as possible...

thanks

Wine is a program that allow Linux users to run some Windows applications inside of Linux.If you are using ubuntu and want to play warcraft 3 in ubuntu,this tutorial may help you.
 First,make sure [COLOR=Red][graphics drivers installed]("http://www.tips5.com/to-install-graphics-drivers-on-ubuntu")[/COLOR] in your system,then install wine by executing following command in terminal:
```
sudo apt-get update
sudo apt-get install wine
```Locate to your warcraft folder and rename “Movies” to “_Movies” after wine installed.

[IMG]http://ubuntuguide.net/wp-content/uploads/2009/04/snapshot3-497x360.png[/IMG]

Start game by using command:

```
wine "/media/jmk/war3.1.20/WarcraftIII/War3".exe -opengl
```where “”/media/jmk/war3.1.20/WarcraftIII/War3&#8243;.exe” is the location of war3,it can be mounted from ntfs drive.
Tips:
There’s also a GUI tool called [COLOR=Red][PlayOnLinux]("http://ubuntuguide.net/install-windows-games-and-programs-in-ubuntu-with-playonlinux")[/COLOR] in Ubuntu Linux,that you can install and run WarCraft 3 in your Ubuntu.
ALt+right click combination key is often used,and a menu list pop up when you press the combination key in game.[COLOR=Red][Click here]("http://ubuntuguide.net/disable-alt-right-click-in-ubuntu")[/COLOR] to fix it.

---

### Post by jaswind3r on 2010-11-11
thank you bro.... soo much.. that was really helpfulll.....+karma

---

