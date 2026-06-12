---
title: "Disable Mouse Taps Perminantly"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by Chrissd on 2011-08-27
Hi all,

I've recently reinstalled Ubuntu and got problems with mouse taps. Every time I start up the computer I have to type the following series of commands into the terminal:
```
synclient TapButton1=0
synclient TapButton2=0
synclient TapButton3=0
synclient VertTwoFingerScroll=0
synclient VertEdgeScroll=off
```

How can I set it so these changes are perminant? Google suggests changing xorg.conf, but I have no xorg.conf and remember from days of old that file breaking my computer. :lol:

Thanks for any help!

---

### Post by Chrissd on 2011-08-29
No one got any ideas? :(

---

### Post by jwbrase on 2011-08-29
I don't think it would work to add that to Xorg.conf.

My first instinct would be to try putting those commands in a shell script and adding the script to your startup programs.

There may be a better way but I'm a diehard handheld-mouse user and don't know much about configuring touchpads.

---

### Post by Chrissd on 2011-08-29
> **jwbrase said:**
> There may be a better way but I'm a diehard handheld-mouse user and don't know much about configuring touchpads.

So am I really, which is why I like a button to press and find it annoying to close windows, resize them etc with just my palms. I like my touchpad to just move the mouse.

A quick Google suggests I create a file somewhere (where?) 'chmod +x' and put the following in it:
```
#!/bin/bash
synclient TapButton1=0
synclient TapButton2=0
synclient TapButton3=0
synclient VertTwoFingerScroll=0
synclient VertEdgeScroll=off
```

I then put it in the startup programs to be run?

---

### Post by HarrisonNapper on 2011-08-29
Yes, you can add it to startup programs in gnome if you only want it to launch with gnome. I believe that's System>Preferences (maybe Administration, don't use Gnome)>Startup Applications. Just add the script there. 

You can also edit rc.local and add each command above "exit 0" which will run those commands every time the runtime changes (so at boot, resume, reboot, etc). Note that it's a core system file, so I would recommend creating a backup just in case, and only modify it if you're comfortable replacing the file with the backup from the command line. Given the commands, I don't think it's too risky, but better safe than sorry :)

---

### Post by Frogs Hair on 2011-08-29
Use Gedit to make and save the script , create a folder where you wish and move the document to the folder . Make the script executable by right clicking the document  > Properties > Permissions and mark Execute .

Add the script to startup applications by entering a name . In the command section use the browse option and locate your script and select open  . Finally , use the add option , comments are optional .

---

