---
title: "What does this output from terminal mean pls?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by listerdl on 2010-02-03
Hi I did this

```
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

```

and this happened...

```
cp: cannot stat `/home/henry/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory
```

Not too sure what to do....My understanding is that all i had to do was copy and paste the code minus the $ and all done? But no....

I am following a tutorial to fix my sound issue with 9.10

Thanks!

---

### Post by J V on 2010-02-03
Well you missed something, something to do with "asound" is missing (both the home config files and the system config files)

If you needed to install something before, do it now...

---

### Post by listerdl on 2010-02-03
Do you reckon if I install this then it will install what might be missing?

```
sudo apt-get remove sl-modem-daemon
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Seriosuly. The sound issue in Ubuntu 910 seems to be an absolute headache.

---

### Post by nhasian on 2010-02-03
in the future it would be helpful to link to the tutorial you were following but I think its the pulseaudio fix tutorial for 8.04 and 8.10.  It is no longer necessary with Ubuntu 9.10

> **listerdl said:**
> I am following a tutorial to fix my sound issue with 9.10 Thanks!

---

### Post by listerdl on 2010-02-03
sorry! [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by J V on 2010-02-03
**N**[COLOR=Blue]**ote:** Don't worry if some of these files did not exist on your system.[/COLOR]

Imagine thats a quote, I'm getting errors from the forum...

---

### Post by nhasian on 2010-02-03
I knew i recognized that terminal command.  that was the exact thread i was thinking of.  hehe yeah those error messages are nothing to worry about, move along.

> **listerdl said:**
> sorry! [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

