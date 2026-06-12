---
title: "New User needs help"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by pmag56 on 2010-04-04
I have installed Ubuntu 9.04  and upgraded to 9.10 on a Toshiba Satellite laptop (Model A135-S2386). Everything seems to work OK so far, however, my sound is not working at all.

I discovered this information [http://ubuntuforums.org/showthread.php?t=452992](http://ubuntuforums.org/showthread.php?t=452992) - which defines a possible fix. However, I don't know how to access (what I am guessing as) read-only file in Ubuntu Linux. I can navigate to the directory,but when trying to open and modify the file with Joe, it says read only and thats where I am stumped. 
If someone can guide me to a procedure, I would really appreciate it. Just need to know how to modifying file rights and what to use to do this?


Thanks sooo much.
Pete

---

### Post by audiomick on 2010-04-04
Hi.
To change the content of files in directories like /etc, i.e system directories, you generally need root privileges. You do not want to change the ownership of the file. The mechanism for this is "sudo"
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

Using it is easy:
[https://help.ubuntu.com/8.04/administrative/C/terminal.html](https://help.ubuntu.com/8.04/administrative/C/terminal.html)

To do the sort of thing that you seem to be wanting to do, I use the editor "gedit", which needs to be started with "gksu", since it has a graphical interface.
```
gksu gedit /the/file/you/want/to/edit
```

I don't think joe is graphical, so you could start it, if you prefer to use it, in the same manner, but using "sudo"
```
sudo joe /file/name
```

Note: "gksu" (and "gksudo", which seems to be effectively the same) opens a window in which you must enter your password (login password). "sudo" just prompts for the password in the terminal. When you type in your password at this prompt, you wont see what you are typing. Just type in the password and then "enter".

---

### Post by stderr on 2010-04-04
Hi pmag56, welcome.

To modify a file owned by the superuser ("root"), you need to temporarily assume the role of that user. Your user, "Joe", will have permissions setup in the sudoers file to use the sudo ("superuser do") command to act as if you were root. All you need to do is enter your own password (for user Joe), and you'll be able to act as root.

e.g.

sudo vim /etc/modules.d/alsa-base

or, to launch the file with a graphical editor, you need to use "gksudo"

gksudo gedit /etc/modules.d/alsa-base

---

### Post by bertolo on 2010-04-04
thks for the info.

---

### Post by pmag56 on 2010-04-07
> **stderr said:**
> Hi pmag56, welcome.

To modify a file owned by the superuser ("root"), you need to temporarily assume the role of that user. Your user, "Joe", will have permissions setup in the sudoers file to use the sudo ("superuser do") command to act as if you were root. All you need to do is enter your own password (for user Joe), and you'll be able to act as root.

e.g.

sudo vim /etc/modules.d/alsa-base

or, to launch the file with a graphical editor, you need to use "gksudo"

gksudo gedit /etc/modules.d/alsa-base

----------------------------------------------------------------------------------------------------------------------------
It's working using the gksudo gedit /path below I added the line with a comment to the last line of my script, rebooted the laptop an Nickleback is playing!

The file (alsa-base.conf) I had to modify was located in **/etc/modprobe.d/alsa-base.conf** in case someone with a similar situation needs help.

Thanks so much :guitar:

---

