---
title: "Adobe Flash not being recognized"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by waderain on 2011-05-30
Can't get Flash to work with Firefox or Chrome. 

I installed the Adobe Flash plugin that is for Ubuntu and it does show that its installed but when I go to Firefox or Chrome it still says I need to install Adobe Flash. Tried restarting Ubuntu and reinstalling everything but no go.

Any ideas.

---

### Post by flick on 2011-05-30
Do you have the normal Flash plugin installed from the Ubuntu repos? Or did you install it some other way?

From my machine :

flick@lil-spooky:~$ dpkg -l | grep flash
ii  flashplugin-installer                   10.3.181.14ubuntu0.11.04.1                 Adobe Flash Player plugin installer

---

### Post by waderain on 2011-05-30
Not sure actually, I've tried it two ways, the first way doesn't seem to work. The first way I tried is when your in the web browser and your click on a video it says I need to install Adobe flash. If I click on that it takes me to the Adobe site, and you choose Ubuntu and click on download now it it opens up the Ubuntu software center. I click on 'use source' but nothing happens.
The second way I tried is through Ubuntu Software Center. This does install and even shows it had installed but still the browsers say I need to install Adobe Flash, is there a step I'm missing?

Keep in mind I'm super new to Linux in any way, Ubuntu is the first I've ever tried

---

### Post by lovinglinux on 2011-05-30
Install [Flash-Aid](http://www.webgapps.org/add-ons/flash-aid) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by gandaran on 2011-05-30
-----------------------------

---

### Post by waderain on 2011-05-30
I tried Flash-aid, still doesn't work. I know theres something I'm doing wrong. Is the a setting somewhere to tell it to use a certain plugin?

---

### Post by lovinglinux on 2011-05-30
> **waderain said:**
> I tried Flash-aid, still doesn't work. I know theres something I'm doing wrong. Is the a setting somewhere to tell it to use a certain plugin?

After you install Flash-Aid, you must start the Wizard from the extension toolbar button menu. The Wizard will allow to change the Flash between the version from the repositories and the latest beta version from Adobe Labs. The Advanced Mode has even more options.

After running the Wizard, a terminal will execute the necessary commands for you. After restarting Firefox, you can check if the plugin was properly installed by typing **about[noparse]:[/noparse]plugins** in the address bar.

You can enable/disable plugins from Firefox Add-on Manager.

---

