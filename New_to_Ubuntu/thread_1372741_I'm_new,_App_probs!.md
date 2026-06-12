---
title: "I'm new, App probs!"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by :)Animal on 2010-01-04
I cannot find a application i have intalled using package manager D: 
I am new to ubuntu (and happy)
Ubuntu 9.10 
The applications i installed (via package manager) are googleearth-package and Cakephp

Can you help me find this? i know they are there..i just do not know how to find them :P..In process of learning :D

---

### Post by drs305 on 2010-01-04
Google Earth is most likely in Applications, Internet. 

For Cakephp, here is a link about it's location. It's old but the file structure probalby hasn't changed:
[http://ubuntuforums.org/showthread.php?t=668836]("http://ubuntuforums.org/showthread.php?t=668836")

---

### Post by Joe325 on 2010-01-04
To put it in the menu, type this into the terminal:

sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications/

---

### Post by :)Animal on 2010-01-04
Hmm, Google earth isn't under internet :/ and only thing under system tools is Unetbootin.
Is there a way to find them in the file system? or open using terminal?
(this is my 1st weak of ubuntu :P)

ps(thanks for replying!)

---

### Post by :)Animal on 2010-01-04
@joe

"cp: cannot stat `/usr/local/google-earth/googleearth.desktop': No such file or directory
"
:/

---

### Post by Joe325 on 2010-01-04
Try searching for the location of the google earth folder
find -name 'goog*'
Then move this folder to /usr/share/applications for it to be listed in the menu

---

### Post by drs305 on 2010-01-04
You can look in Synaptic to learn about file locations. Highlight the package, then Properties, File locations. The "run" command is often in the /usr/bin folder.

You can also type "which <appname>" in a terminal, using the exact name, such as "which firefox-3.5".  Type "whereis *appname*" for the file locations.

If you are in the terminal and aren't sure of the exact name, type some of the name and quickly tab twice. It will show you all the available commands starting with the letter combination you typed.

You can also enter "apt-cache show *appname*" for more info on an app,

---

### Post by :)Animal on 2010-01-04
> **drs305 said:**
> Google Earth is most likely in Applications, Internet. 

For Cakephp, here is a link about it's location. It's old but the file structure probalby hasn't changed:
[http://ubuntuforums.org/showthread.php?t=668836]("http://ubuntuforums.org/showthread.php?t=668836")


Ahh thank you greatly, it was there! :)! Helped a lot for cake!

---

### Post by :)Animal on 2010-01-04
Ahh i just found this :o (under location thank you hehe)

/usr/share/doc/googleearth-package/README.Debian



Says
"To use this package, run the 'make-googleearth-package' command. This will
download Google Earth, and create a Debian package (.deb file) of its contents.

The Debian package can be installed with the command 'dpkg --install'."

---

