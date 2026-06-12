---
title: "Tasks?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-26
Before I start, I'm a total NOOB to Ubuntu, I've been with XP Since 2003 and I'm good with that, but I don't know anything (Well MUCH) About Ubuntu... Anyway, the question, and I know your thinking I think Ubuntu is a free version of Windows but I don't... I want to know if there is some Force Quit / CTRL + ALT + DEL Similarity?

---

### Post by VCoolio on 2009-04-26
control+alt+backspace = kill x and go to login screen
alt+printscreen+REISUB = force reboot (type reisub while holding alt+prntscrn, with about 1 sec between each letter)

there is a tool you can add to panel (right click on a panel) named force-quit; you can click on the icon, then on the window you want to kill.

In terminal: 
killall appname : will kill all instances of an application
sudo reboot now : will reboot

---

### Post by Spiritous on 2009-04-26
> **VCoolio said:**
> control+alt+backspace = kill x and go to login screen
alt+printscreen+REISUB = force reboot (type reisub while holding alt+prntscrn, with about 1 sec between each letter)

there is a tool you can add to panel (right click on a panel) named force-quit; you can click on the icon, then on the window you want to kill.

In terminal: 
killall appname : will kill all instances of an application
sudo reboot now : will reboot

Massive thanks :)!

---

### Post by ad_267 on 2009-04-26
Also, often you can't get to this one if an application is preventing you from accessing your menu but System - Administration - System Monitor - Processes let's you monitor how much CPU and RAM processes are using and kill anything causing problems.

---

### Post by fballem on 2009-04-26
> **Spiritous said:**
> Before I start, I'm a total NOOB to Ubuntu, I've been with XP Since 2003 and I'm good with that, but I don't know anything (Well MUCH) About Ubuntu... Anyway, the question, and I know your thinking I think Ubuntu is a free version of Windows but I don't... I want to know if there is some Force Quit / CTRL + ALT + DEL Similarity?

There are a couple of ways to set this up. I'm assuming that you would like to use something like the 'End Task' function from Task Manager.

Probably one of the easiest is to add Force Quit to a panel. To do this, right click on the top (or bottom) panel, depending on which one you want. This will bring up a menu, with a number of options, including Add to Panel.

Select Add to Panel from the menu. This will bring up a long list. Scroll down until you see Force Quit in the list (see screenshot attached).

Click on Force Quit and you will notice that the +Add button is enabled. Click the +Add button and you will see a new icon for Force Quit on the panel. By habit, I also add the Keyboard Indicator and the Lock Screen (scroll down, click, +Add). When you are done, selectthe Close button.

If you don't like where they are located on your panel, right-click on the icon, select Move, then drag the icon to where you want it on your panel and click again. Once you are happy with the location, then you can right-click and select lock to panel.

To use this, click on the icon for Force Quit. You will get a message to select the window that you want to close. Click on the Window for the application, and it will close (often with confirmation). If you pressed the Force Quit in error, press the Esc key to cancel.

Hope this helps,

---

### Post by Spiritous on 2009-04-26
> **fballem said:**
> There are a couple of ways to set this up. I'm assuming that you would like to use something like the 'End Task' function from Task Manager.

Probably one of the easiest is to add Force Quit to a panel. To do this, right click on the top (or bottom) panel, depending on which one you want. This will bring up a menu, with a number of options, including Add to Panel.

Select Add to Panel from the menu. This will bring up a long list. Scroll down until you see Force Quit in the list (see screenshot attached).

Click on Force Quit and you will notice that the +Add button is enabled. Click the +Add button and you will see a new icon for Force Quit on the panel. By habit, I also add the Keyboard Indicator and the Lock Screen (scroll down, click, +Add). When you are done, selectthe Close button.

If you don't like where they are located on your panel, right-click on the icon, select Move, then drag the icon to where you want it on your panel and click again. Once you are happy with the location, then you can right-click and select lock to panel.

To use this, click on the icon for Force Quit. You will get a message to select the window that you want to close. Click on the Window for the application, and it will close (often with confirmation). If you pressed the Force Quit in error, press the Esc key to cancel.

Hope this helps,

Exactly what I wanted... :)

---

