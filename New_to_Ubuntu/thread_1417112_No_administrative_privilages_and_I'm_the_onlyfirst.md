---
title: "No administrative privilages and I'm the only/first user"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by sharpie27 on 2010-02-26
I'm new to this Linux/Ubuntu thing and trying to become a convert. I installed Ubuntu on my laptop and desktop over last weekend, and I have my laptop up and running well. However, my desktop won't allow me to do anything that involves adding packages, installing updates, installing Firefox extensions, etc, etc. I am the only user on the computer and the first user (and should thus have root privalages according to everything I've read). When I attempt to do any of these tasks, I enter my password and then I get the following message:


                                 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 E: _cache->open() failed, please report. 



I've tried to do the "sudo dpkg --config -a" command in the terminal, but I have no idea what to do after that point. Any help would be greatly appreciated.


Thanks.

---

### Post by spiderbatdad on 2010-02-26
try this command:
```
sudo rm /var/lock/*
```

---

### Post by captain_171 on 2010-02-26
What are you trying to install? and reply with the command line and the error please.
The issue sounds as you are not a Sudoer user to see if you are i would try to run gedit as root using the command sudo gedit it will ask you for your password and then open gedit if it gives you a error saying "is not in the sudoers file.  This incident will be reported" then your user is not a sudoer and that is why you are having issues.

To see if your user is a sudoer user type this command
groups
if you are a sudoer you will be in the admin group if not then you will have to switch users to one that is.

---

### Post by kerry_s on 2010-02-26
just means the package manager messed up at some point. since it's still a fresh install just install again.

---

### Post by spiderbatdad on 2010-02-26
> **kerry_s said:**
> just means the package manager messed up at some point. since it's still a fresh install just install again.

Completely lame advice coming from someone with over 7,000 posts and long time forum member. Telling new members to reinstall without first trying to solve minor problems is just bad forum etiquette.

---

### Post by pastalavista on 2010-02-26
> **sharpie27 said:**
> ...
I've tried to do the "sudo dpkg --config -a" command in the terminal, but I have no idea what to do after that point. Any help would be greatly appreciated.


Thanks.

If you didn't type the command exactly as the message states (sudo dpkg --configure -a) and enter the password you used when you installed Ubuntu, dpkg won't work. When you enter the password in terminal, the keystrokes don't show. Just type it as you made it, make sure the caps lock isn't on, and press enter.

---

### Post by sharpie27 on 2010-02-26
> **spiderbatdad said:**
> try this command:
```
sudo rm /var/lock/*
```


I tried and got the message '/var/lock/*': no such file or directory

---

### Post by spiderbatdad on 2010-02-26
ok so not the problem. Also try:
```
sudo apt-get install -f
sudo apt-get autoclean

```

Edited to remove running dpkg again.

---

### Post by sharpie27 on 2010-02-26
> **captain_171 said:**
> What are you trying to install? and reply with the command line and the error please.
The issue sounds as you are not a Sudoer user to see if you are i would try to run gedit as root using the command sudo gedit it will ask you for your password and then open gedit if it gives you a error saying "is not in the sudoers file.  This incident will be reported" then your user is not a sudoer and that is why you are having issues.

To see if your user is a sudoer user type this command
groups
if you are a sudoer you will be in the admin group if not then you will have to switch users to one that is.


I was trying to install flash player extensions to firefox when I received the message, but I get the same message as in my first post whenever I even try to open update manager or synaptic. I can use the sudo gedit to open  gedit using your instructions above. when I type "groups" I get a message with my user name followed by:

adm dialout cdrom plugdev lpadmin admin sambashare

Additionally, my user is listed with administrative privilages in Users and groups program.

---

### Post by sharpie27 on 2010-02-26
> **spiderbatdad said:**
> Completely lame advice coming from someone with over 7,000 posts and long time forum member. Telling new members to reinstall without first trying to solve minor problems is just bad forum etiquette.

I tried that too, but Ubuntu will not overwrite itself and only gives me the option of installing alongside the other install and windows or wiping the hard disk clean.

---

### Post by spiderbatdad on 2010-02-26
The problem is you tried to install something perhaps from a package not in the repository, and likely with missing dependencies...this has left you package manager in an unworkable state.

The sudo apt-get install -f command ask the package manager to attempt to fix the broken package. Autoclean attempts to remove useless packages from the archive.

---

### Post by sharpie27 on 2010-02-26
> **spiderbatdad said:**
> The problem is you tried to install something perhaps from a package not in the repository, and likely with missing dependencies...this has left you package manager in an unworkable state.

The sudo apt-get install -f command ask the package manager to attempt to fix the broken package. Autoclean attempts to remove useless packages from the archive.

You are a zen master. It works now. Thank you very much for your help.

---

### Post by theozzlives on 2010-02-26
Best thing for Flash is install the restricted extras:
```
sudo apt-get install ubuntu-restricted-extras
```
It will install Flash, Java, some MS Fonts, and some other codecs and stuff.

---

