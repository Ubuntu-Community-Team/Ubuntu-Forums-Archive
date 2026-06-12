---
title: "Samba for dummies"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by williammanda on 2007-02-19
I trying to get my arms around learning samba for one event. I want to transfer some files from a windows computer to one of my linux computers, then I will be done with windows. So how can I learn enough about samba without spending several hours sorting through google? I would like to find something that would be along the lines of "samba for dummies"
Also I would like to better understand file / folder permissions. I would love to figure out how I can use the gui instead of the command line. I still to new to linux so using the gui would be a great asset.
Thanks

---

### Post by moephan on 2007-02-19
I'm  not 100% sure you need samba for this. If you have a USB drive lying around, you might be able to just load all the files on the drive and transfer them that way. 

If samba is really what you need, then you just need to figure out what the right smb.conf file is. Here's a thread that might help:
[http://ubuntuforums.org/showthread.php?t=119486](http://ubuntuforums.org/showthread.php?t=119486)

Cheers, Rick

---

### Post by Tichondrius on 2007-02-19
You can install samba, but for occasioanl use it's simpler to install SSH.

For SSH you need to install SSH server on your Ubuntu:

sudo apt-get install ssh

And then install WinSCP (SSH client) on your windows machine, and use it to connect to the Linux machine.

WinSCP Download link:   
[http://winscp.net/download/winscp382setup.exe](http://winscp.net/download/winscp382setup.exe)

If you stil want Samba, instructions are here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

### Post by williammanda on 2007-02-19
Thanks for the help! It is now finished!

---

