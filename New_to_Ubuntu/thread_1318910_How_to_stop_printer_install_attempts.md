---
title: "How to stop printer install attempts?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Irker on 2009-11-08
I'm running Ubuntu 9.04 "Jaunty Jackalope" - Release i386# from a Live CD (downloaded, hash checked, etc. per all instructions) while I try various things to see if I can make ubuntu my primary OS.
 
The problem is that during some sessions, it tries to install one of my local printers. That overlays and interupts what I'm trying to work on, and it can't be made to go away for upwards of 2 minutes while it searches all the disks for a driver that doesn't exist. 
 
It doesn't do it in every session, but when it does it once, it repeats every few minutes, not letting me get anything done.
 
I've checked all the documentation, but I couldn't find anything about turning off this 'feature'.
 
All printers work under XP(SP2) -- so it's not a cable or other hardware problem.
 
Is there an easy fix for this? Maybe a command line I can type in at the start of every session to turn off the autodetect? (Installing the printer is not an option.)
 
Any help appreciated!

---

### Post by sliketymo on 2009-11-08
You can keep cups from starting using the start-up applications settings found in the control panel.,System >Preferences > Start-up Applications.

---

### Post by Miljet on 2009-11-08
What about just unplugging the printer?

---

### Post by Irker on 2009-11-08
> **sliketymo said:**
> You can keep cups from starting using the start-up applications settings found in the control panel.,System >Preferences > Start-up Applications.

The list does not include 'cups' -- the only thing that seems to relate at all to printing is "Print Queue Applet." 

Also, wouldn't anything there have already started by the time I reach that? (I'm running this from Live CD -- can't justify a permanent install until I know I'll actually be able to use ubuntu for my primary computer use.)

---

### Post by Irker on 2009-11-08
> **Miljet said:**
> What about just unplugging the printer?

Pulling the desk away from the wall (for access to the cables) each time I boot ubuntu isn't what I call a good option.

---

### Post by nothingspecial on 2009-11-09
The old way used to be

```
sudo /etc/init.d/cups stop
```

That turns off printing services. If you do want to print jujt change stop to start

```
sudo /etc/init.d/cups start
```

However they`ve made changes in the new ubuntu so it might be

```
sudo service cups stop
```

I`m not using it so I`m not sure.

---

### Post by Irker on 2009-11-09
> **nothingspecial said:**
> I`m not using it so I`m not sure.
 
Many, many thanks! As long as I know it involves 'sudo' and 'cups' on a command line, I can figure it out.
 
Can't thank you enough!

---

