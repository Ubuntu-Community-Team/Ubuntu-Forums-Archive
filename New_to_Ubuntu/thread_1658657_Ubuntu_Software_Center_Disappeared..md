---
title: "Ubuntu Software Center Disappeared."
date: 2011-01-02
forum: New to Ubuntu
---

### Post by OnboardMIKE101 on 2011-01-02
How do I install Ubuntu software center it doesn't show up on applications. Neither does my update manager or cleaner in system administration. :mad:

---

### Post by zeroseven0183 on 2011-01-02
Have you tried reinstalling it?

```

sudo apt-get update
sudo apt-get remove software-center
sudo apt-get install software-center
```

---

### Post by Rubi1200 on 2011-01-03
Hi and welcome to the forums :-)

Before you try reinstalling, please explain how they disappeared.

Did you change the menus?

What version are you using?

If you are using Gnome, right-click on the top panel at the left hand side and Edit Menus. Look if the options are still there because maybe you accidentally removed them from the menu.

Also, open Synaptic Package Manager and search to see if they are installed.

---

### Post by OnboardMIKE101 on 2011-01-03
I got E: Package software-center has no installation candidate,Errors were encountered while processing:
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1) and it didn't install ubuntu software center with the codes.
(I also get E:apport:subprocess installed post-installation script returned error exit status 1 when i installed update manager on synaptic package manager.)

HELP

---

### Post by OnboardMIKE101 on 2011-01-03
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Before you try reinstalling, please explain how they disappeared.

Did you change the menus?

What version are you using?

If you are using Gnome, right-click on the top panel at the left hand side and Edit Menus. Look if the options are still there because maybe you accidentally removed them from the menu.

Also, open Synaptic Package Manager and search to see if they are installed.
"There are no edit options and i have gnome with Ubuntu 10.04.1 LTS and i might have changed it or deleted -(edit options). when i was figuring out how to download programs on Ubuntu software center none worked it said dependencies could not be resolved.

---

### Post by OnboardMIKE101 on 2011-01-04
> **zeroseven0183 said:**
> Have you tried reinstalling it?

```

sudo apt-get update
sudo apt-get remove software-center
sudo apt-get install software-center
```
 
Yes and it didnt work.:confused:

---

### Post by zeroseven0183 on 2011-01-06
What happens when you type in the Terminal?
```
software-center
```
```
sudo software-center
```

Can you see and post what's in the Terminal?

---

### Post by OnboardMIKE101 on 2011-01-06
> **zeroseven0183 said:**
> What happens when you type in the Terminal?
```
software-center
``````
sudo software-center
```Can you see and post what's in the Terminal?

_this is what I got>>>_
name$ software-center
The program 'software-center' is currently not installed.  You can install it by typing:
sudo apt-get install software-center
name$ sudo apt-get install software-center
[sudo] password for name: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package software-center is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package software-center has no installation candidate

---

### Post by OnboardMIKE101 on 2011-01-10
I can't even open my edit menu to or should i reinstall ubuntu but i cant lol i don't have startup disc creator. but i got a usb device with more than enough room to download and install ubuntu. HELP

---

