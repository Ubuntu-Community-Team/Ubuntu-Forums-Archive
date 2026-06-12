---
title: "Automatically Changing Background"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by perito on 2010-10-23
In Ubuntu 10.10 there are 2 backgrounds (Cosmos and Contest) that automatically change when u activate them .. like a slide show..
is there more backgrounds like this ?

---

### Post by NESFreak on 2010-10-23
You might want to have a look at this:
[http://royvandewater.com/blog/2009/12/ubuntu-wallpaper-slideshow/](http://royvandewater.com/blog/2009/12/ubuntu-wallpaper-slideshow/)

---

### Post by bokgeneraal on 2010-10-23
[SIZE=5]Create you own
[SIZE=4]Without knowing anything about how XML works with changing the background.

If you go to /usr/share/backgrounds/comos you will find an XML file.
Open it with gedit or a text editor and copy all the text to a new file. Next change the picture file directory path to your own pictures' directory path and save. Know go back to where you change the background and add the xml file. Save the xml file where the pictures are located for convenience.
Just tinker with the xml.:popcorn:
[/SIZE][/SIZE]

---

### Post by mhgsys on 2010-10-23
Various way's
[http://art.ubuntuforums.org/showthread.php?t=1329147](http://art.ubuntuforums.org/showthread.php?t=1329147)

the way I did it;

> **mhgsys said:**
> 
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/mhgsys/Desktop/bcground/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 8s
done


---

### Post by A_M_S on 2010-10-23
try this

[http://ubuntuforums.org/showthread.php?t=1579438](http://ubuntuforums.org/showthread.php?t=1579438)

---

### Post by perito on 2010-10-23
> **mhgsys said:**
> the way I did it;

#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/mhgsys/Desktop/bcground/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 8s
done

this works fine .. but how to make it run on start up ?

---

### Post by mhgsys on 2010-10-23
You can load the sh script in System> Preferences> Startup Applications

f.e

I named the script bla.sh and stored it in /home/mhg

after the sudo chmod a+x you can run the script with ./bla.sh

You can make a Application launcher like; /home/mhg/bla.sh
or put that line in Startup applications.

---

### Post by mhgsys on 2011-09-15
updated script to work on 11.10

```
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/mhg/Desktop/temp/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gsettings set org.gnome.desktop.background picture-uri file:///$PIC

sleep 2s
done
```

---

