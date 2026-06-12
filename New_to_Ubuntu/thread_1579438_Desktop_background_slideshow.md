---
title: "Desktop background slideshow"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by McTwitch on 2010-09-21
In Windows 7, and most of the MAC OS, it is possible to have your desktop background be a slideshow of pictures of a certain folder. I was wondering if it was possible to set this up with Ubuntu, and how to do it. I have Ubuntu 10.04, and if it would be possible, I want this effect to start immediately on log-in.

---

### Post by clhsharky on 2010-09-21
McTwitch

wally
[http://www.webupd8.org/2009/09/wally-best-automatic-wallpaper-changer.html](http://www.webupd8.org/2009/09/wally-best-automatic-wallpaper-changer.html)

Desktop Drapes
```
sudo apt-get install drapes
```
[http://www.webupd8.org/2009/05/automatically-change-wallpaper-under.html](http://www.webupd8.org/2009/05/automatically-change-wallpaper-under.html)

Crebs
[http://www.omgubuntu.co.uk/2010/06/crebs-wallpaper-slideshow-generator-gets-a-ppa-new-features/](http://www.omgubuntu.co.uk/2010/06/crebs-wallpaper-slideshow-generator-gets-a-ppa-new-features/)

Wallpaper Slideshow
[http://www.omgubuntu.co.uk/2010/05/how-to-easily-create-slideshow-wallpapers-in-ubuntu/](http://www.omgubuntu.co.uk/2010/05/how-to-easily-create-slideshow-wallpapers-in-ubuntu/)


Sharky

---

### Post by JSeglem on 2010-09-21
Found this post from an earlier similar question:

There is a screensaver call "Pictures folder" , to use this screensaver you have to have a folder named "Pictures" in your home folder. The screensaver will slideshow all pictures in this folder. So just put all of the pictures for your screen saver slideshow here. 

If you want to create a separate folder for that purpose you can try these steps below.

To change the folder destination of this screensaver (Ex : /media/win_d/tux instead of your Pictures folder in your home folder) :
_ sudo gedit /usr/share/gnome-screensaver/themes/personal-slideshow.desktop
_ Go to line 95 (Exec=slideshow --location=Pictures)
_ Change the name of the destination folder (Pictures) with what ever you want like /usr/share/pixmaps or /media/win_d/blabla . If the destination folder is in your home folder you can just put the name of your folder (yourfolder) but not the whole name (/home/yourname/yourfolder)

---

### Post by McTwitch on 2010-09-22
I tried Drapes, and found no end of trouble, and no start of actual progress. Instead of fixing it, I decided to just look for another alternative. I'll look into Wally though, thanks.

---

### Post by migs73 on 2010-09-22
> **jseglem said:**
> found this post from an earlier similar question:

There is a screensaver call "pictures folder" , to use this screensaver you have to have a folder named "pictures" in your home folder. The screensaver will slideshow all pictures in this folder. So just put all of the pictures for your screen saver slideshow here. 

If you want to create a separate folder for that purpose you can try these steps below.

To change the folder destination of this screensaver (ex : /media/win_d/tux instead of your pictures folder in your home folder) :
_ sudo gedit /usr/share/gnome-screensaver/themes/personal-slideshow.desktop
_ go to line 95 (exec=slideshow --location=pictures)
_ change the name of the destination folder (pictures) with what ever you want like /usr/share/pixmaps or /media/win_d/blabla . If the destination folder is in your home folder you can just put the name of your folder (yourfolder) but not the whole name (/home/yourname/yourfolder)

+1

---

### Post by A_M_S on 2010-09-22
Try this script:


#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/ams/Pictures/wallpapers/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 1h
done

I've found it in the foruns

I'm currently using it.
You can put it in the startup applications  
Currently it changes the background image each hour but you can change this in the sleep command
don't forget to change the directories.

---

### Post by McTwitch on 2010-09-22
Actually, I think I might go with Wally. How do I make Wally start on start-up?

---

### Post by MSPdwalt on 2010-09-22
> **A_M_S said:**
> Try this script:


#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/ams/Pictures/wallpapers/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 1h
done

I've found it in the foruns

I'm currently using it.
You can put it in the startup applications  
Currently it changes the background image each hour but you can change this in the sleep command
don't forget to change the directories.

Simple, yet effective, great script

---

### Post by Jazzy_Jeff on 2010-09-22
Thank you for that script. Works great.

---

### Post by Jesus_Valdez on 2010-09-22
I use this Nautilus script

[http://gnome-look.org/content/show.php/XML+animated+background+creator?content=118074](http://gnome-look.org/content/show.php/XML+animated+background+creator?content=118074)

---

### Post by Baldrick_NZ on 2010-09-23
Or, you could do it with the helps of 'crebs', available thru the Ubuntu Software centre. This will do what you want without terminal, using a GUI instead.

Cheers.

---

### Post by McTwitch on 2010-09-23
> Or, you could do it with the helps of 'crebs', available thru the Ubuntu  Software centre. This will do what you want without terminal, using a  GUI instead.

I couldn't find it. Perhaps I don't have the right repository added?

---

### Post by Rod J on 2010-10-22
> **McTwitch said:**
> I couldn't find it. Perhaps I don't have the right repository added?

+1 for CreBS.

I had been creating the XML files manually to switch wallpapers but it is tedious and error prone. See here for the tutorial: [[COLOR="Blue"]HowTo: Create a background slideshow[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1478700")
The advantage with that method is that it is using already installed functions in Ubuntu (no extra running process required).

CreBS (a gui app) comes to the rescue creating the script automatically and makes it a piece of cake to change the order of the wallpapers and other options too. See here for details of CreBS: [[COLOR="blue"]http://www.obfuscatepenguin.net/crebs/[/COLOR]]("http://www.obfuscatepenguin.net/crebs/")

About half way down that page are terminal commands for adding the repository and installing the app:
```
sudo add-apt-repository ppa:crebs/ppa
sudo apt-get update
sudo apt-get install crebs
```

---

