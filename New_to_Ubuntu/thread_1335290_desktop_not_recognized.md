---
title: "desktop not recognized"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-23
I'm trying to install this cpu applet I found on gnome look ([http://www.gnome-look.org/content/show.php/CPU+Frequency+Scaling+Monitor+Mac+Style?content=96714).But](http://www.gnome-look.org/content/show.php/CPU+Frequency+Scaling+Monitor+Mac+Style?content=96714).But) when trying to install it through terminal,cd Bureaublad isn't recognized (bureaublad is desktop in my language).
What's the correct input in the terminal?I've downloaded the tar to my desktop (bureaublad)

---

### Post by fooman on 2009-11-23
try:

```
cd /home/<user name>/Desktop 
```

*replace <user name> with your user name.

or just type:

```
cd ~/Desktop
```

*the "~" represents "/home/<user name>".



hope that helps.

---

### Post by dzon65 on 2009-11-23
Tried it,doesn't work>>>>not recognized

---

### Post by dzon65 on 2009-11-23
After several tryouts I'm getting this:john@ubuntu:~$ cd ~/Bureaublad
john@ubuntu:~/Bureaublad$ sudo tar -zxvf 96714-cpufreq.tar.gz /usr/share/pixmaps/cpufreq-applet
tar: /usr/share/pixmaps/cpufreq-applet: Komt niet voor in archief (doesn't exist in archive)
tar: Stopt met foutstatus vanwege eerdere fouten
 Translated (roughly)Stopping error-status due to previous mistakes.

---

