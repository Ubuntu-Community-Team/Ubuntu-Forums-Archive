---
title: "Scripting: edit one file via sed using variables"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Johnneylee on 2009-05-03
What I am attempting here is to create a series of commands for conky.
I places these inside the nautilus script folder. I've written all of them myself.

Problem? Only one;
This code you see let's you save the current conky config to a file in the nautilus scripts folder. It also creates a shell script that copies the contents of the saved conky config back into the .conkyrc file and restarts conky.

This is the template file that the main script calls to copy the contents into the new shell script.
```
#!/bin/sh
cd /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Configs/ && cp $filename /$HOME/.conkyrc;
cd /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Controls/ && ./conkyrestart.sh;
```

The problem withe the two scripts is that I want it to be automated; I want the variable $filename to be replaced with the value of the variable $currentconfig. Makes sense?
```
#!/bin/sh
currentconfig=`zenity --entry --text="Save Current Conky Config As:"`
cp /$HOME/.conkyrc /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Configs/$currentconfig ;
cd /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Configs/ && touch $currentconfig.sh;
cd /$HOME/;
cp template.sh /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Configs/$currentconfig.sh;
cd /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Configs/;
[COLOR="DarkOrange"]# sed -n 'w/ $currentconfig $filename/$currentconfig /&/w even' [/COLOR]<$currentconfig.sh;
chmod +x 777 $currentconfig.sh;
cd /$HOME/.gnome2/nautilus-scripts/Conky/Conky\ Controls/ && ./conkyrestart.sh;
```

Thank you for your help.

---

