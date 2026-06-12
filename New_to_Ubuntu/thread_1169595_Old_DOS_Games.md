---
title: "Old DOS Games"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-05-25
Is it possible to run my old DOS games ("gamename.exe") in Linux? I have Ubuntu 8.04. Any advice how to do it would be appreciated. Thanks

---

### Post by madmaxou on 2009-05-25
Try wine

---

### Post by RD1 on 2009-05-25
It sure is! Look into DOSBOX. I actually used it to install and run Windows 3.1 Talk about a blast from the past!

---

### Post by Mornedhel on 2009-05-25
Try dosbox (sudo apt-get install dosbox)

Then run dosbox path/to/game/directory.

---

### Post by Paqman on 2009-05-25
> **madmaxou said:**
> Try wine

Won't work. Wine is designed for software that runs on the Windows NT kernel, not DOS.

As mentioned above, DOSBox is where it's at.

---

### Post by jwaclawsky on 2009-05-25
Thanks DOSBOX works great! ...once you figure out how to use the mount command. :-)   Many Thanks!

---

### Post by Slash621 on 2009-05-31
I cant seem to get this thing to mount my drive..  my directory is in /home/slash/dosgames but the mount command dosent work.

I'm trying this in DOSBOX

mount c /home/slash/dosbox
or
mount c /home/dosbox

---

### Post by jerome1232 on 2009-05-31
Easier to just to do it like this, (I'm running this from my home directory and the file is at ~/License to Kill/BONDE.EXE

```
dosbox License\to\Kill/BONDE.EXE
```

Auto mounts the directory and runs the game.

---

### Post by andrew.46 on 2009-05-31
Hi,

Wooooo hoooooo! I just saw Descent on the list of games supported! I have so many memories of playing descent 1 and 2 modem to modem as well as with my Kali license. Any other Descent players here?

Andrew

---

### Post by Rytron on 2009-05-31
Hi.
Here is a guide to setting up DosBox in Linux:

[COLOR="DarkGreen"]**Automount drive in DosBox**

Open a terminal, and it should take you to your home directory. If not, type cd /home/yourname/

Create directory to store your DOS programs in. I called mine dosgames, so I typed mkdir dosgames The full pathname to this file is home/yourname/dosgames

Open dosbox by typing dosbox

You are now in the dosbox shell. Note that it automatically puts you at the Z:\ drive We want to change that. Try typing in the dos command C: Note that it says the drive doesn&#8217;t exist. We could mount the C drive everytime we open dosbox by typing mount c /home/yourname/dosgames everytime, but why do that when dosbox can create a configuration file to take care of that for you! But first we need to create the file.

At the dosbox Z:\ prompt, type in config -writeconf /home/yourname/dosbox.conf You now have the configuration file.

Type exit. This puts you back in your terminal session

Type sudo gedit dosbox.conf This will open the dosbox configuration file.

Scroll down the dosbox.conf file to this section

[autoexec]
# Lines in this section will be run at startup.Type the following in on a new line:

mount c /home/yourname/dosgames

This will automatically mount the C: drive to your dosgames directory.

If you want dosbox to automatically start on the C: drive, enter C: on a new line after your mount line.

Save and quit gedit.

Now at the terminal prompt, type in dosbox It should auto mount the C: drive.[/COLOR]

---

### Post by deece803 on 2009-05-31
Thanks guys! Thats awesome...playing captain comic as i type :) so many memories!

---

