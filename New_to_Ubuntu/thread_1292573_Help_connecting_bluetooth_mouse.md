---
title: "Help: connecting bluetooth mouse"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by davewillis on 2009-10-16
Hello, I have just installed ubuntu 9.04 using wubi (I think ... within windows not a separate partition).  I'm trying to get my bluetooth mouse to connect and no success.  I've tried the wizard, but no devices show up.  I read some forum messages and tried these commands, but you can see the results.  I did press the button on the back of the mouse so it would 'pair' during these commands.  My computer is a toshiba laptop Satellite with builtin bluetooth.

davewillis@ubuntu:~$ /etc/init.d/bluetooth status
 * bluetooth is running
davewillis@ubuntu:~$ hcitool scan
Device is not available: No such device
davewillis@ubuntu:~$ sudo hciconfig hci0 inqmode 0
[sudo] password for davewillis: 
Can't get device info: No such device
davewillis@ubuntu:~$ sudo hidd -- search
sudo: hidd: command not found
davewillis@ubuntu:~$ 

Any help is very much appreciated!  I am installing this for a class and need to get the program written this weekend.  You can imagine not having a mouse.

Dave

---

### Post by davewillis on 2009-10-16
More info:  I dug around a little bit more this morning and it seems the bluez-utils are not running.  The synaptic package manager says they are installed, but there are no configure files and and when I enter /etc/init-d/bluez-utils the command is not there.  This might be the source of mouse connection problem.  Any hints on how to get the bluez-utils to run?

---

### Post by pookiebear on 2009-10-28
similar here but I can get 1 mouse out of 3 bluetooth ones I have to work. The one that works really does work well. The other 2 show up in the list but never connect.
bluetooth file transfer works good. All 3 work under winxp and win7. the one I want to use worked under fedora but not ubuntu ( I have been loading all kinds of OS's today to decide which one to go with on my work laptop)

---

