---
title: "White screen after installing Jaunty"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by mogsmar5 on 2009-05-04
Hi

As I have a fairly slow internet connection I left my mum's laptop on over the weekend installing Jaunty. When I checked on it instead of starting up normally it goes through the new loading bar and then displays a white/brown screen without reaching the login screen. I can access the terminal by pressing Ctrl+Alt+F1 and from there I can see that the files are still intact but I've been unable to fix the problem. I can only assume that Jaunty didn't install properly.

How can I fix this problem? Is there a Windows-esque System Restore function on Ubuntu that'll let me restore to Intrepid? Basically, can I fix this without having to reinstall Ubuntu? It took me *ages* to get the settings that way I want them!

Thanks in advance,
Chris

---

### Post by NESFreak on 2009-05-04
> **mogsmar5 said:**
> Hi

As I have a fairly slow internet connection I left my mum's laptop on over the weekend installing Jaunty. When I checked on it instead of starting up normally it goes through the new loading bar and then displays a white/brown screen without reaching the login screen. I can access the terminal by pressing Ctrl+Alt+F1 and from there I can see that the files are still intact but I've been unable to fix the problem. I can only assume that Jaunty didn't install properly.

How can I fix this problem? Is there a Windows-esque System Restore function on Ubuntu that'll let me restore to Hardy? Basically, can I fix this without having to reinstall Ubuntu? It took me *ages* to get the settings that way I want them!

Thanks in advance,
Chris

did you do an upgrade? Have you changed your xorg.conf file while using intrepid?

if yes try:
first of all backing up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bakupthingie
```
reconfigure the xserver:
```
sudo dpkg-reconfigure xserver-xorg
```

use the default options for the things you don't know what to set them to.

if it makes things worse you could revert using
```
sudo cp /etc/X11/xorg.conf.backupthingie /etc/X11/xorg.conf
```


-----edit----
did you upgrade from hardy? mm dont think you where supposed to upgrade directly from hardy to jaunty. See there was a release in between. Intrepid. Might be things are screwed up bigtime now.

---

### Post by mogsmar5 on 2009-05-04
I get a 'xorg server package in broken' (or something like that) error when trying the first step.

---

### Post by NESFreak on 2009-05-04
> **mogsmar5 said:**
> I get a 'xorg server package in broken' (or something like that) error when trying the first step.

mm sounds like a big screw up? did you indeed upgrade directly from hardy to jaunty?

maybe try
```
sudo apt-get check
```
if there are any dependency problems this should fix them

---

### Post by mogsmar5 on 2009-05-04
Ah yes it is working now, thankyou!

One thing that is a little strange is the graphics. 'Desktop Effects' says Compiz is not installed, but apt-get says it is. I opened fusion-icon to see if I was in Metacity and it sorted itself out, but Desktop Effects still says Compiz is not installed. And I don't want to have to start fusion-icon every time I log on! Is there a fix?

---

