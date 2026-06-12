---
title: "Disappearing Gnome taskbars"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by 2spurs on 2009-05-24
My top & bottom taskbars have disappeared.  Doing a search of the Forums I’m not the first this has happened to.    I’ve tried the “help” that has been suggested and gotten nowhere!

This computer / install has worked fine for approx 1 month  before this.

Things tried
RT clicking lets me open / start a new folder etc,    but no help – no way to access a terminal session.

Alt F2 does nothing!   How can this work for some folks and not others?  I’m using a USB keyboard.  

I rebooted into “safe mode” Option #2  and got to the Grub command line.  From there I don’t see how to log into any accounts – like my admin acct.  or ROOT  typing HELP brings us the list of commands available,  but I don’t see anything that helps.  It does not recognize SU APT-GET INSTALL GNOME-PANEL

I have most things backed up,  so is the easiest thing simply to reinstall???
The computer – home brew – all components purchased new 2 month ago.
Motherboard       Asus M3A78-T  this has integrated ATI graphics 3300 series,
 Microsoft USB- KB,  Logitech wireless mouse.
 Ubuntu 9.04  64 bit

---

### Post by fooman on 2009-05-24
when you right-click on the desktop,  do you see an option to "create launcher"?

if yes,  click on it and when the window opens type:

```
gnome-terminal
```into *both* the "name" space *and *the "command" space...then click "ok".

that should place a launcher for the terminal onto the desktop....click on the new launcher and when the terminal opens,  type the following into it:

```
gnome-panel &
```see if that gets the panels back...if it does not,  try opening a terminal again and try this one:

```
sudo apt-get install gnome-panel
```then log-out and back in again,  or just reboot.  ...hope one of those helps.

---

### Post by 2spurs on 2009-05-25
Yes I have tried using RT click to help.  RT click brings up
create folder                this works
create launcher              nothing happens
create document              this works
clean up by name             works
keep aligned                 ???
change desktop background    works

apparently some basic features are not working! I haven't found a way yet to get a terminal session   SO    I'm going to do a reinstall and hope this cures things.

Thanks

---

### Post by fooman on 2009-05-25
another thing you could try to get to a terminal....

press the ctrl-alt-f1 keys.  that should get you to a console shell....log in with your name and password.

type this command:

```
sudo apt-get install nautilus-open-terminal
```after it installs....reboot:

```
sudo reboot
```

when you get back to the desktop,  you should be able to right click and have a new option for "open in terminal"

try that.  if it works,  try:

```
gnome-panel &
```to get the panels back.

good luck

---

### Post by melrokz on 2009-05-25
looks like a corrupt installation. Did you check the cd for defects? (or the hdd or optical drive?)

---

