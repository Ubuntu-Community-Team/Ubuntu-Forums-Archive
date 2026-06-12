---
title: "Semi-Fancy mount icon?"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by minchina on 2007-01-01
As I drift away from complete noob status, I find that I quickly run into more problems as soon as I discover something new.  

I have figured out how to mount a samba share on another linux computer on my network by typing the following into konqueror:

sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX

it works like a charm.  Since this is a semi-regular mount, I wanted to find an easier way to do it than trying to remember everything and re-type it.  I made a new link to application on my desktop and typed the line above into the command box.
Unfortunately, since this is a sudo command it does not work.  Is there a way to make the icon prompt me for the password after I click it?

Thanks

---

### Post by blackmh on 2007-01-01
Did you consider automounting on boot? 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by minchina on 2007-01-01
I did think about it, but I do not always want the drive to be mounted.  I basically want a mount button on my desktop so I can just click it when I want it.  It would be very possible if it were not for the sudo/password requrement.

---

### Post by blackmh on 2007-01-01
I think it is still very possible with simple script. Unfortunately, I can't help you but I'm sure someone here can :s

---

### Post by Lord Illidan on 2007-01-01
```
 sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX
```

Replace the above with

```
 kdesu smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX
```

in KDE

or ```
 gksudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX
```

in Gnome

---

### Post by AgenT on 2007-01-01
Just add it as an alias in your bashrc file. Open ~/.bashrc and add this line to the bottom of the file:

**OPTION #1:**
```
alias mysmb="sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX"
```Save file, quit program. Either restart the terminal or do:
```
source ~/.bashrc
``` (if you open a new terminal, it will already source that file)
In the terminal, type:
```
mysmb
```

OPTION #2:
If you want a link on your desktop or panel, create the following file replacing sudo with gksudo if you use GNOME or ksudo if you use KDE:
```
#!/bin/bash
#
# my smb mount script
#

sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX
```
Save it as mysmb in some folder. Make the file mysmb executable (right-click -> properties -> permissions or just chmod it).

Now you can either execute this script (double click it) or create a Launcher for it. For example, on your desktop right-click -> "Create Launcher".  Select a name, icon and add the full path of your script in the "command" field. For example, if you saved the script as /home/agent/myscripts/mysmb put that in the "command" filed. That is all! Now click on the Launcher to start it.

---

### Post by Lord Illidan on 2007-01-01
> **AgenT said:**
> Just add it as an alias in your bashrc file. Open ~/.bashrc and add this line to the bottom of the file:

**OPTION #1:**
```
alias mysmb="sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX"
```Save file, quit program. Either restart the terminal or do:
```
source ~/.bashrc
``` (if you open a new terminal, it will already source that file)
In the terminal, type:
```
mysmb
```OPTION #2:
If you want a link on your desktop or panel, create the following file replacing sudo with gksudo if you use GNOME or ksudo if you use KDE:
```
#!/bin/bash
#
# my smb mount script
#

sudo smbmount //192.168.1.41/MyFiles /home/m/rmusic -o username=XXXXX,password=XXXX
```Save it as mysmb in some folder. Make the file mysmb executable (right-click -> properties -> permissions or just chmod it).

Now you can either execute this script (double click it) or create a Launcher for it. For example, on your desktop right-click -> "Create Launcher".  Select a name, icon and add the full path of your script in the "command" field. For example, if you saved the script as /home/agent/myscripts/mysmb put that in the "command" filed. That is all! Now click on the Launcher to start it.
Replace sudo with gksudo or kdesu or else that's not going to work when you click it.
EDIT : OOPS, forgot you already said it...

---

### Post by Lucas2005 on 2007-01-14
Great, just what i was looking for, 

I created a custom launcher in one of my panels and it's now way easier to mount a network hardrive. sweet

---

### Post by minchina on 2007-01-31
Thanks for all the ideas.  I actually ended up doing it slightly differently.  I just clicked the "run in terminal" box in the menu editor. Now when I click it I get a konsole window that just prompts me for my password.  I have another icon set up to sudo smbumount /dir so I can flip off the switch when I need it.  

Thanks again for all of the ideas.

---

