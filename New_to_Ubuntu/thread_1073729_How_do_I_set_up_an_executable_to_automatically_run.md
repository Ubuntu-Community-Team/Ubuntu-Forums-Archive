---
title: "How do I set up an executable to automatically run a script?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-02-18
I need to run a script called "runner" before I launch wine executable files. "Runner" automatically disables compiz before launching wine, and then re-enables it after closing wine. I have tried making several scripts, but I'm not exactly sure I know what I'm doing. Here is a script I made called "Winamp.sh"

#!/bin/sh
if [ $(whoami) != "root" ]; then
	echo "You need to execute this script as root."
	exit 1
fi

rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
modprobe usbcore usbhid xpad ehci_hcd ohci_hcd

runner wine*</home/jake/.wine/dosdevices/c:/Program Files/Winamp/winamp.exe>

***The goal here is to just double-click on the script called "Winamp", and run the program without having to enter anything into the terminal. I guess you would call this a "batch file" of sorts, for ubuntu. 

Whenever I try to launch this, nothing happens. This is what I get in terminal: 

jake@deathstar:~$ sudo '/home/jake/winamp1.sh' 
[sudo] password for jake: 
sudo: /home/jake/winamp1.sh: command not found

Any Ideas?

---

### Post by JillSwift on 2009-02-18
You're on the right track - you just need to make the shell script executable, I suspect:
In a terminal:```
chmod u+x winamp1.sh
```
[COLOR=Silver]change mode user(owner) add executable permission to winamp1.sh[/COLOR]

---

### Post by BDNiner on 2009-02-18
After creating the script did you make the script file executable?

---

### Post by asuastrophysics on 2009-02-18
thanks guys, that worked. i had forgotten that last step. by "executable", you mean that whatever is inside the script will show up in terminal correct?

so for example, i wanna make an exectuable script that will run "sudo gedit" without having to type it into terminal:
(in gedit)

#!/bin/sh

sudo gedit

then make it executable

chmod u+x winamp1.sh
...so what i'm asking is, does this script take everything underneath #!/bin/sh and put it in the terminal?

---

### Post by stchman on 2009-02-18
You do not need to be an admin to enable or disable compiz.  Try this kind of a script.  This script assumes you are running Gnome and not KDE.

```

#!/bin/sh

# disable compiz
metacity --replace &

# run WINE app
wine <windows executable>

# enable compiz
compiz --replace &


```

Now that you have created the script you need to make it executable.

```

chmod +x <script name>

```

---

