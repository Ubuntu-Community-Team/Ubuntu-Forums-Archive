---
title: "launcher for Firefox 4"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by ub9876 on 2011-01-31
i have fox 4 extracted to a folder called fox4 on my desktop..
how do I launch the thing???   clicking the folder only brings up all the sub folders...

---

### Post by weedeater64 on 2011-01-31
You've got to find the executable, and click it. 

Once you know the path to it ie..

/home/yourname/Desktop/FFolder/executable

You can then create a launcher wherever you want, or add a menu entry.

---

### Post by ub9876 on 2011-01-31
ok   so what is the executable for fox 4 beta???  there are many files in there..

---

### Post by khamil8686 on 2011-01-31
you can goto a terminal and type
```
whereis firefox
```
and it will tell you what directory you have firefox in, i thought firefox was usually preinstalled or at least came with an installer so you shouldnt have to install it by downloading a file from the internet.
usually to install programs you want to goto System>Administration>Synaptic
and to install firefox type firefox in the text box and hit enter and it should bring up a listing of packages, search for firefox in that list and then choose to install it (double click, right click and select install, i cant remember the exact option) then select apply changes (Again dont remember exact one, just look around for an apply button :) and it should install firefox for you which should be located in the applications menu on the top left side of your screen
of course im assuming youre running gnome, if youre running kde just click the kicker in the bottom left side of your screen and type firefox and either firefox or the firefox installer should pop up in the menu :) hope this helps!

---

### Post by ub9876 on 2011-01-31
you misunderstand    this is fox 4 beta

---

### Post by peculiar penguin on 2011-01-31
The executable is named firefox (surprising, I know :P). You probably want to read [this]("http://www.webgapps.org/firefox/installing-other-versions") ("Manual download from Mozilla") to make sure everything works properly.

---

### Post by weedeater64 on 2011-01-31
> **ub9876 said:**
> ok   so what is the executable for fox 4 beta???  There are many files in there..


[attach]182406[/attach]

---

### Post by balaknair on 2011-01-31
The executable you're looking for should be 
~/Desktop/fox4/firefox/firefox

assuming you've extracted the archive(which should contain a folder named firefox with some folders and a bunch of files) to a folder named fox4 on your desktop as you mentioned in the first post.
It's just a small file named *firefox*, you can open the folder and double click on it. (see screenshot below)

To create a launcher, right click on the desktop--> Create Launcher --> and enter the name you want and in command type in ~/Desktop/fox4/firefox/firefox or wherever the folder is.

For example, I have the FF4 beta installed in /opt by simply copying the firefox folder into /opt. So the command is /opt/firefox/firefox in my case.

---

### Post by PPPilot on 2011-01-31
Here is a less intrusive method of trying Firefox 4 Beta. In your current version of Firefox go to Tools>Add-ons and download and install the FoxTester extension. This will allow you download and run any number of Beta Firefox versions without having to do an install and have those Beta issues. The instructions for use are easy. I've had good luck with it. I am currently using FF 4.0b11pre this way. Hope this helps...

---

### Post by ub9876 on 2011-01-31
i got it going but... the launcher says permission denied   ??
what to do??

---

### Post by weedeater64 on 2011-01-31
> **ub9876 said:**
> i got it going but... the launcher says permission denied   ??
what to do??

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by balaknair on 2011-01-31
try right clicking on the file> properties> permissions tab> make sure that the option 'allow executing file as a program' is enabled.

---

### Post by DaBurninator on 2011-03-30
Hi I'm pretty new to Linux/Ubuntu and I'm having a similar problem. I downloaded, extracted, found the exe and installed. The problem is my old firefox lauchers lauch the OLD firefox and this is like lubuntu or somthing and I can't right click to create a launcher. I tried like changing the command for the whole shebang to the orginal install exe because thats the only thing I have to open 4.0. It worked technically but it would open 4.0 as if the first time every time (Mozilla welcome screen and whatnot)  I'm a total noob at non-Windows and help would be appreciated. Thanks :D

---

