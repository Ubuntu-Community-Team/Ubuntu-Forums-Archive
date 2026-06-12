---
title: "Setting up two monitors."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by ross.mitchell on 2009-01-16
Just finally made the move from vista.  (yes I'm ashamed of my past)

Have two monitors hooked up to the same graphics card, but I have no idea how make the secondary work....

A friend helped me get set up, and I'm starting to get the hang of things, but this is obviously beyond me.

Halp?

---

### Post by urk_nono on 2009-01-16
"Plug and play" won't work?

---

### Post by ross.mitchell on 2009-01-16
No.  I thought that was strange myself.

I assume you mean just hooking them up, not some program I've never heard of...

---

### Post by hessiess on 2009-01-16
What graphics card have you got? is the second screen detected by system -> prefs -> screen res.

---

### Post by urk_nono on 2009-01-16
> **ross.mitchell said:**
> 
I assume you mean just hooking them up, not some program I've never heard of...

Correct mr. Mitchell.

What's the name of your graphics card?
What's the name of your screens?
What version of ubuntu are you running?

Take a look at this guide: [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

Covers pretty much everything.

---

### Post by ross.mitchell on 2009-01-16
> **hessiess said:**
> What graphics card have you got?

> **urk_nono said:**
> Correct mr. Mitchell.

What's the name of your graphics card?
What's the name of your screens?
What version of ubuntu are you running?

EVGA GeForce 8800 GS
Main (working) Soyo something or other (can get more details if required)
Secondary (issue) Dell 15" junker  That I have no info on.
8.04 LTS.

---

### Post by ross.mitchell on 2009-01-16
> **urk_nono said:**
> 
Take a look at this guide: [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

Covers pretty much everything.


Which one should I use?  Sorry, really confused here, and I don't want to screw up my system.

---

### Post by urk_nono on 2009-01-16
try this one instead:

[http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/]("http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/")

---

### Post by hessiess on 2009-01-16
> **ross.mitchell said:**
> EVGA GeForce 8800 GS
Main (working) Soyo something or other (can get more details if required)
Secondary (issue) Dell 15" junker  That I have no info on.
8.04 LTS.

try configuring it using nvidia-settings
```
sudo nvidia-settings
```
(you may need to install the 'nvidia settings' package in add-remove)

---

### Post by Bölvaður on 2009-01-16
First of all, you need nvidia drivers if you dont already have them installed. Well.. do you?

If you do then find a program called nividia-settings-manager or was it just called nvidia-settings... any way you find there everything you need. To store the changes you make you have to log into that program with super user rights: alt+f2 and type nividia-settings-manager (or what ever that program is called) and do your thing.
Just make sure you back up your x configuration as in the thread you was pointed at.

---

### Post by ross.mitchell on 2009-01-16
> **urk_nono said:**
> try this one instead:

[http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/]("http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/")

tryed that one.  worked great until I clicked "Save to X Configuration file" and I got this

```
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
```

---

### Post by ross.mitchell on 2009-01-16
please help

---

### Post by hessiess on 2009-01-16
> **ross.mitchell said:**
> tryed that one.  worked great until I clicked "Save to X Configuration file" and I got this

```
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
```

Try putting 'sudo' in front of the command

---

