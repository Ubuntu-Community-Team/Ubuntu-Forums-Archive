---
title: "Help With Samba"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Tim3049 on 2008-02-18
This is my first attempt at installing / configuring / using any Linux OS, so I'll say thanks in advance for everyone's patience in answering my questions.

I've installed 7.10 desktop and I'm trying to configure a shared folder on the Ubuntu system that can be accessed by my other Windows XP systems. I understand that I need to install Samba, but I've had these problems:

1. If I right click on the folder I want to share and select 'Share Folder,' a box pops up that says sharing services are not installed. I uncheck NFS and leave SMB checked and click Install Services. The box just disappears for a couple seconds and comes back up.

2. I tried to install Samba through the Synaptic manager and it says the package 'Samba-common' is already installed (ver 3.0.26a-1ubuntu2)

What am I missing?

---

### Post by jacrider on 2008-02-18
You will need to configure Samba.  Unfortunately, there is no easy GUI to do this.  It is done through editing the /etc/smb.conf file.

Start here:  [https://help.ubuntu.com/7.10/server/C/windows-networking.html](https://help.ubuntu.com/7.10/server/C/windows-networking.html)

This will get you on your way.  Post more questions if you need.

---

### Post by Tim3049 on 2008-02-19
Thanks again for you help.

I made the changes to /etc/samba/smb.conf that I thought were necessary. However, when I tried to restart the Samba daemons using 'sudo /etc/init.d/samba restart' I get the error 'sudo: /etc/init.d/samba: command not found'. Does this mean that Samba isn't installed correctly?

I also tried to install samba from the command line using 'sudo apt-get install samba' but I get an error that the package Samba is not available.

Sorry for all the basic questions; I know this should probably be a simple process.

Tim

---

