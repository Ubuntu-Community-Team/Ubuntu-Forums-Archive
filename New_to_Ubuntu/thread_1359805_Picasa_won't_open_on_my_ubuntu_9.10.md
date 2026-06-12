---
title: "Picasa won't open on my ubuntu 9.10"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by bungz on 2009-12-20
Hi 

I installed Picasa 3 for linux on my system. But when i click on the application icon nothing happens. 

I am trying to reinstall it and try again. (That's pretty much what i know as i am just migrating from windows.)

Any other suggestions?

---

### Post by diablo75 on 2009-12-20
What method did you use to install it?  What did you do?

---

### Post by bungz on 2009-12-20
Downloaded the 'Picasa 3 for Linux (Beta)' package from google website, and double clicked the package and installed through package installer.

---

### Post by diablo75 on 2009-12-20
> **bungz said:**
> Downloaded the 'Picasa 3 for Linux (Beta)' package from google website, and double clicked the package and installed through package installer.

Well you might try to remove the program using Synaptic Package Manager (System>Administration menu) and then install it again with the deb package installer like you did before.  But this time while it's installing, expand out the window with that little triangle flip tab thing on the left which will display a terminal window with all the details about what's going on.  You should be able to copy and paste the contents of that window back into here for us to examine and look for errors or problems...

---

### Post by bungz on 2009-12-20
Alright. I did three things. 

1. Uninstalled Picasa through Synaptic Package Manager and reloaded. The first image is the message i got. 

2. Installed through the .dep package. The second image is what i got when i tried it.

3. I cancelled that and went ahead and installed it anyways. And the third image is the terminal that you had asked for.

Did another thing just now. Tried following the instruction on google-picasa FAQ and pasted this in the terminal
[PHP]wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
apt-get update  [/PHP]

And the 4th image is what i got in the terminal.

---

### Post by Soul-Sing on 2009-12-20
You add a software source with picasa in it, you didn't sigh that source though with the pgp key
So: remove the old picasa (via synpatic?)
then: ```
sudo apt-get install picasa
```
(with all the depend.)

---

### Post by xorand on 2009-12-21
I've linked to the google repo and installed wine on Karmic too.  Picasa will simply not start.
I installed with sudo apt-get install picasa

This is in sources.list:
# Google repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

I have used sudo apt-get update

Is there a way to diagnose picasa on startup?  Looking at my kernel messages, there may be video issues?
output:
Dec 21 23:50:55 hobbes kernel: [ 8379.705544] [drm] TV-14: set mode NTSC 480i 0
Dec 21 23:50:55 hobbes kernel: [ 8379.847032] [drm] TV-14: set mode NTSC 480i 0
Dec 21 23:50:55 hobbes kernel: [ 8380.203611] [drm] TV-14: set mode NTSC 480i 0
Dec 21 23:50:55 hobbes kernel: [ 8380.344116] [drm] TV-14: set mode NTSC 480i 0

---

### Post by swiftsam on 2009-12-21
I'm having this problem too.  Just updated a machine from 9.04.  Picasa wouldn't run so I removed and installed it again. Still nothing.

```

apt-cache policy picasa
picasa:
  Installed: 2.7.3736-15
  Candidate: 2.7.3736-15
  Version table:
 *** 2.7.3736-15 0
        500 http://dl.google.com stable/non-free Packages
        100 /var/lib/dpkg/status


```

any ideas?

---

### Post by Aliik on 2010-01-12
I have the same problem with Picasa 2.7
But I can open it with gksudo picasa in the terminal. Then it works.

Some programs also work via Wine only when it is run with root privileges.

Anyone know why and what to do?

(And I apologize for my bad English;))

---

### Post by oldfred on 2010-01-12
i am running 3.6 in Karmic wine.
                                       [http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
   
  I did have to look in google to find that the downloaded file had to be moved into wine programs to install, but otherwise this worked. I have not been able to use the shop. It comes up but will not open and let me upload to other sites.

---

### Post by jtholb on 2010-01-14
Unfortunately I have the same issue after sudo apt-get install picasa...just to add to the fire.

---

### Post by cimness on 2010-02-25
I'm pretty sure we're all having this problem: 

[http://ubuntuforums.org/showthread.php?t=945257&highlight=picasa+won%27t+open](http://ubuntuforums.org/showthread.php?t=945257&highlight=picasa+won%27t+open)

In that thread they diagnosed the problem as Regedit, but nobody has offered a fix.

---

### Post by roach_chris on 2010-11-03
Try creating a launcher using the "gksu picasa" command in a terminal. 

I had a similar problem in 10.04 and this worked. 

Try it, who knows...

---

