---
title: "Revert to Ubuntu from Kubuntu"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-09-27
I recently installed KDE-DESKTOP and decided to remove it. Used purge etc, but now I'm left with the KDE Login screen etc. I tried the code from [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome), and after it runs I get this in the terminal - 

0 upgraded, 0 newly installed, 250 to remove and 3 not upgraded.
After this operation, 687MB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.

ergh? help my brain is going to leak out of my ears just to escape from the torture of having to try to work this out!

---

### Post by candtalan on 2010-09-27
> **Hippytaff said:**
> I recently installed KDE-DESKTOP and decided to remove it. Used purge etc, but now I'm left with the KDE Login screen etc. I tried the code from [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome), and after it runs I get this in the terminal - 

0 upgraded, 0 newly installed, 250 to remove and 3 not upgraded.
After this operation, 687MB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.

ergh? help my brain is going to leak out of my ears just to escape from the torture of having to try to work this out!

What are you trying to work out here? I have not yet used the psychocats link information but it looks the sort of thing you will need to do if you want to get rid fully of kubuntu session and get back closer to a clean ubuntu (gnome) environment.

I have often tried kubuntu-desktop, then later removed only the kubuntu-desktop package. I never went as far as also removing the multitude of extra stuff needed when Kubuntu-desktop is installed, but is not also removed later!  Irritating? YES, however not so bad.

hth

---

### Post by andrewthomas on 2010-09-27
> **Hippytaff said:**
> I recently installed KDE-DESKTOP and decided to remove it. Used purge etc, but now I'm left with the KDE Login screen etc.
Make sure that your /etc/X11/default-display-manager file reads

```
/usr/sbin/gdm
```
i.e. ```
cat /etc/X11/default-display-manager
```

---

### Post by Hippytaff on 2010-09-27
The fact all that stuff is left behind isn't that bad, though I could do with the space, it's more the fact that when I'm asked - y/n in the terminal, I type y and enter and it aborts anyway. Thats a little odd!?

---

### Post by Hippytaff on 2010-09-27
I get this

** (gdm-binary:1934): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.48" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:1934): WARNING **: Could not acquire name; bailing out

which doesn't look good

---

### Post by andrewthomas on 2010-09-27
are you running 10.04 or 9.10?

If you are running 9.10 this is the right link

[http://www.psychocats.net/ubuntu/puregnomekarmic](http://www.psychocats.net/ubuntu/puregnomekarmic)

---

### Post by Hippytaff on 2010-09-27
After sudo su I get this from the code you posted Andrew - displays GNOME upsplash!? and this output -

cat /etc/X11/default-display-manager
/usr/bin/kdm

so it's still reading KDM at startup, so I'm guessing I need to change etc/x11/deafult display manager?

---

### Post by Hippytaff on 2010-09-27
using 10 LTS (I'm almost positive :-)

---

### Post by andrewthomas on 2010-09-27
```
gksu gedit /etc/X11/default-display-manager
```change kdm to gdm


BTW: why are you entering ```
sudo su
``` ???

---

### Post by andrewthomas on 2010-09-27
> **Hippytaff said:**
> using 10 LTS (I'm almost positive :-)
```
cat /etc/lsb-release
```

---

### Post by Hippytaff on 2010-09-27
```
(gksu:2210): Gtk-WARNING **: cannot open display: :0.0
```

---

### Post by Nero147 on 2010-09-27
Sudo apt-get install kubuntu-desktop

---

### Post by andrewthomas on 2010-09-27
try 

```
gksudo gedit /etc/X11/default-display-manager
```If that does not work then 

```
sudo apt-get install gnome-desktop
``` before trying the psychocats removal process.

---

### Post by Hippytaff on 2010-09-27
Just removed KDE-Desktop. I want to get rid of all the other crap to and get fresh ubuntu gnome...see above :-)

---

### Post by Hippytaff on 2010-09-27
[CODE]No protocol specified

(gksudo:2251): Gtk-WARNING **: cannot open display: :0.0[CODE]

---

### Post by Hippytaff on 2010-09-27
```
 gksudo gedit /etc/X11/default-display-manager

No protocol specified

(gksudo:2251): Gtk-WARNING **: cannot open display: :0.0

```

---

### Post by andrewthomas on 2010-09-27
[B]You do have ubuntu-desktop and all the rest of GNOME installed don't you?
Post the output of[/B]
```
aptitude search ubuntu-desktop
```



I use nano to edit files

```
sudo apt-get install nano
```then 

```
sudo nano /etc/X11/default-display-manager
```

---

### Post by Hippytaff on 2010-09-28
Lots of missing dependencies. tried getting them manually but Ubuntu is broken. Think I'm installing removing and autocleaning it to death. I think I'm going to do a fresh install.
 
Thanks for your help Andrew

---

### Post by Hippytaff on 2010-09-28
...or should I try to fix it and learn something?

---

### Post by andrewthomas on 2010-09-28
I would try and fix it before you reinstall.

Post  the output of 

```
sudo aptitude update && sudo aptitude install ubuntu-standard
```

---

### Post by Hippytaff on 2010-09-28
Worth taking it on :-)
 
I'm in work at the moment...have a crack when I get home and the kids are in bed...there are a few dependecies missing though (gedit, mozilla ones etc) and I cant get them manually. sudo apt-get doesn't work. will post the errors I get later.
 
Thanks again for you help

---

### Post by andrewthomas on 2010-09-28
It might be best to try 

```
sudo aptitude update && sudo aptitude install ubuntu-minimal
```first.

---

### Post by Hippytaff on 2010-09-28
After doing

sudo aptitude update && sudo aptitude install ubuntu-minimal
and the code from the link in the first post to remove all the KDE gubbins has gone...I'm Gnome pure.

Quite odd but KDE daemon and other KDE stuff was sharing running Ubuntu with Gnome it seems. Is this possible?

Cheers Andrew!

---

### Post by andrewthomas on 2010-09-28
You could now install ubuntu-standard or ubuntu-desktop if you would like more of the default packages.

---

