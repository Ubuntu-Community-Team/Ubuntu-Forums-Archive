---
title: "Root user and change texxt to GUI mode"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by hpng on 2011-08-19
I have 10.04 LTS.

When I type this:    shutdown -h now
It said I have to be a root user.
well, I am the only user on the laptop. 
When I install software or updates, i use the same password.
So how do I set myself up as root user.
I installed Ubuntu on my Laptop, so I do not understand why the one and only user account is not
the root user... Perplex.....

Problem#2b:
When in text mode, how do I run Gnome from text screen to get GUI display?

Cheers and thanks.

---

### Post by dave01945 on 2011-08-19
to run a command as root you should use sudo

```
sudo shutdown -h now
```

then it will prompt for your password and let you run that command as root

can you explain abit more about text mode are you booting in text only mode or are you pressing ctrl-alt-F1-6 to get to the text mode

---

### Post by sisco311 on 2011-08-19
Use sudo: [uhelp]community/RootSudo[/uhelp]

To start the GUI, run:
```
startx
```

---

### Post by jfed on 2011-08-19
Instead of just typing
```
shutdown -h now
```

run this command
```
sudo shutdown -h now
```

that means you're DO-ing, as the SUper user, it'll ask you for your password, give it. there you go :D

---

### Post by coffeecat on 2011-08-19
> **hpng said:**
> 
I installed Ubuntu on my Laptop, so I do not understand why the one and only user account is not
the root user... Perplex.....

Be glad, not perplexed, that the only user account is not root. :) There have been one or two (thankfully now defunct) Linux distros that set up just a root account for the ordinary user. Such a setup represents a security hole about the size of the Grand Canyon.

Don't forget to read the link sisco311 posted. Yes, please read it.

---

### Post by hpng on 2011-08-19
> **dave01945 said:**
> to run a command as root you should use sudo

```
sudo shutdown -h now
```then it will prompt for your password and let you run that command as root

can you explain abit more about text mode are you booting in text only mode or are you pressing ctrl-alt-F1-6 to get to the text mode

When I restart it in "recovery" mode, it goes into text only screen display.
Someone mention using command "startx" to go from text to gnome GUI

---

