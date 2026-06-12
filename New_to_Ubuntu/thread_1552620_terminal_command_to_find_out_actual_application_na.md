---
title: "terminal command to find out actual application name"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by midcommander on 2010-08-13
something happen, and i can only login to ubuntu in text mode/terminal (sort of like the server thing).

i need to uninstall several application/package to do reparation, perhaps using this command :

```
sudo apt-get remove package_name
```can i also remove the application using this command?:

```
sudo apt-get remove actual_application_name
```now the real question is: how do I find out the actual name of  application or the actual name of the package installed in my system?  I'm only use terminal now, so no synaptic method. also I try : 

```
ps aux
```[http://unixhelp.ed.ac.uk/CGI/man-cgi?ps](http://unixhelp.ed.ac.uk/CGI/man-cgi?ps)

But is it only for the current running process?

Thanks.

---

### Post by Finalfantasykid on 2010-08-13
While this doesn't do exactly what you want, it should give you the answer anyways.

```

sudo apt-cache search "Application Name"

```

This should give you a list of the packages relevant to the text in the quotes, and will most likley contain the one you are wanting to know.

---

### Post by midcommander on 2010-08-14
thanx, i'll try that. in the mean time, i'll try and i'll report if i can find the app or pack that i want to remove.

FYI, i enable XDMCP (sort of, I'm not sure what else that I enable) by editing this file ```
/etc/gdm/custom.conf
```
from this thread [http://ubuntuforums.org/showthread.php?t=1471703](http://ubuntuforums.org/showthread.php?t=1471703) 

At the same session I installed nxserver (with all the requirement, nxclient and nxnode also), then I reboot. The result is the desktop (gdm, gnome) fail to run. I press esc during booting, see what the causes and find out that nxserver fail to load, perhaps i forgot set the node, then it's also follow by sentence
```
starting X display manager xdm
```
then nothing happen, ubuntu just stuck in that line (blinking cursor after the xdm)

i uninstall nxserver, now thinking to  undo the XDMCP (still do not know how).

on top of that, in recovery mode, i can not select any option in recovery menu, because arrow button does not work (to move the selection up and down), perhaps i have to create another thread to this problem. if i press the arrow button , it goes to the splash screen (ubuntu loading) same thing when i press "esc" or F12, and worse it also start immediately the first option in recovery menu (resume normal boot, which is xdm fail).

only by luck that i can enter "drop to root shell prompt with networking". sure i want to test the option "repair broken package" but so far, i'm in no luck.

TMI and out of thread topic, will post link new thread soon.

---

### Post by oldos2er on 2010-08-14
Just FYI, there's no need to use sudo with apt-cache search.

---

