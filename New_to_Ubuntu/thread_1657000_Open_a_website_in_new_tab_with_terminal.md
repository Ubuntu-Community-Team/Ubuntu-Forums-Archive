---
title: "Open a website in new tab with terminal"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by turtlecloud on 2010-12-31
How can I map a keystroke to open a specific website in a new tab if google chrome is already open or opens a new window if chrome is not already running?

---

### Post by turtlecloud on 2010-12-31
Bump? I figured out that I should use the keyboard shortcuts in the preferences,  but I am not sure how to write in the command? Basically I need to know how to run a program through keyboard shortcuts, in this case google chrome.

---

### Post by turtlecloud on 2011-01-01
bump!

---

### Post by Idefix82 on 2011-01-01
The generally accepted norm on this forum is to not bump more often than once in 24 hours. Thanks.

---

### Post by PatchesTheCaveman on 2011-01-01
Hi turtlecloud!  Happy New Year!

Install the CompizConfig Settings Manager from the Ubuntu Software Center, or synaptic, or by running this command from a terminal:
```
sudo apt-get install compizconfig-settings-manager
```

After you installed that, open it by going to System > Preferences > CompizConfig Settings Manager.  At the top, there is a *Commands* option.  Check the box to the left of it if it is not already checked.  Then, click on *Commands*.

Next to the *Command line 0*, type the following in the box:
```
gnome-open http://www.google.com/
```
Replace [http://www.google.com/](http://www.google.com/) with the web site you want to open.

Then, switch to the *Key Bindings* tab.  Next to *Run command 0*, click the button that says *Disabled*.  Check the *Enabled* box.  Then press *Grab key combination*.  Now, press the key sequence you would like to program to open this website.  Then, click OK.

Now you can press the key sequence you selected and it should open the web site you selected.  You can repeat this in the other Run command boxes for as many web sites (or any program you like for that matter) up to 12 times.

Please note that Google Chrome will always open the site in a new tab of the most recent browser window you used.  If a window is not open, it will open a new window for it.  It is not possible to change this behavior.  (Mozilla Firefox supports opening new tabs and windows in a number of configurations.)

---

