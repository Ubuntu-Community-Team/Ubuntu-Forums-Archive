---
title: "installing 270.xx drivers for geforce 560ti"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by defsam on 2011-02-17
i know the driver is for 570 cards but that driver is my only hope of coming back to 1080p and use compiz. so anyone please give me some step by step easy to understand guide on how to install this driver for my video card. :confused:


thanks in advance for your helpful feedbacks.

---

### Post by defsam on 2011-02-17
BUMP for help

---

### Post by lightningfox on 2011-02-17
Go to System>Administration>Additional Drivers (it is called Restricted Drivers in Ubuntu versions before 10.10)

It will help you install the right driver for your video card.

---

### Post by defsam on 2011-02-17
> **lightningfox said:**
> Go to System>Administration>Additional Drivers (it is called Restricted Drivers in Ubuntu versions before 10.10)

It will help you install the right driver for your video card.

we ll as of now i dont see any appropriate driver for my GTX 560 ti. by "proper" i mean that i cant even go for 1080p resolution and i have a 1080p monitor. the max res atm is 800 x 600 4:3. so please provide me with more answers.

---

### Post by defsam on 2011-02-17
bumping please anyone?

---

### Post by defsam on 2011-02-17
bump til i drop

---

### Post by defsam on 2011-02-18
bump

---

### Post by defsam on 2011-02-18
bump

---

### Post by pressko on 2011-02-18
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")


[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")


There are one ppa on each site ... just add em to software sources and go to Restricted Drivers and install current ( it's ver. 270.19 ) :) 

Cheers :popcorn:

---

### Post by defsam on 2011-02-18
> **pressko said:**
> [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")


[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")


There are one ppa on each site ... just add em to software sources and go to Restricted Drivers and install current ( it's ver. 270.19 ) :) 

Cheers :popcorn:

as a beginner ubuntu user this is tough to understand for me honestly. i dont have any idea how to add repositories and i tried adding the ppa but it only gave me errors. i need an easy to understand step by step sorry.

---

### Post by Frogs Hair on 2011-02-18
This is to be copied , pasted , and  run in the terminal. Make sure you chose the Maverick , Lucid , or Natty package from the list . Copy and paste the package name on the third line of PPA .[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by defsam on 2011-02-18
from this post: [http://newyork.ubuntuforums.org/showthread.php?p=10470390#post10470390]("http://newyork.ubuntuforums.org/showthread.php?p=10470390#post10470390")


qouting post on what steps i tried:
> **Alp82 said:**
> 1 .If you have nvidia-current installed, deinstall it completly.

2. As root open Synaptic. Go the Settings -> Package sources -> Other Software. Hit the Add Button and copy "ppa:ubuntu-x-swat/x-updates" in the text input field.

3. Now reload the sources and reinstall nvidia-current, which is now loaded from the new source and is the most current version. You should also install nvidia-settings.

4. Optional: Make a backup of your /etc/X11/xorg.conf and run "nvidia-xconfig" in a terminal to create your nvidia X config file.

Please give me feedback if it works, writing all that from my memory.



still no reply and this is my latest update on it:
> **defsam said:**
> here is what i got after i did your steps (1 to 3) i clicked on system > preferences > Monitors
it says :
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" 

i clicked yes

then a pop up appears saying:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

should i just run nvidia-xconfig? i tried backing up my /etc/x11/xorg.conf but the terminal says: "cp: cannot stat `/etc/X11/xorg.conf-backup': No such file or directory"


what should i do?

---

### Post by defsam on 2011-02-18
> **Frogs Hair said:**
> This is to be copied , pasted , and  run in the terminal. Make sure you chose the Maverick , Lucid , or Natty package from the list . Copy and paste the package name on the third line of PPA .[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

tried this typed the instructions in terminal:

defsam@Defsam-desktop:~$ sudo apt-get install nvidia-graphics-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers

did i follow it right?
i followed the quoted post below on the site it says:
To install this PPA:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get install <package name>
where <package name> is one of the packages below.

and the package name was as far as i understand "nvidia-graphics-drivers"

am i doing it wrong?

---

### Post by cascade9 on 2011-02-18
Not 'nvidia-graphics-drivers', 'nvidia-current'. ;)

---

### Post by defsam on 2011-02-18
oh ok let's see.

---

### Post by defsam on 2011-02-18
quoting cascade*

this is what i got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

---

### Post by cascade9 on 2011-02-18
Hmmm......

Try getting nvidia-settings as well then. That should give you the nvidia x server control panel, which lets you change resolution and will also tell you the installed nvidia-current version.

---

### Post by Frogs Hair on 2011-02-18
In place Nvidia drivers try.

For Natty ```
270.26-0ubuntu1~xup
```

For Maverick 270.18-0ubuntu1~maverick~xup1

For Lucid ```
270.18-0ubuntu1~lucid~xup1
``` 

Pick the one for the version of Ubuntu you are using. beyond this there may be a failure to connect to the source and could be temporary.

---

