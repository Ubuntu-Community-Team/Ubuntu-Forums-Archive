---
title: "Starting desktop GUI on server"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by nuddernuby on 2010-07-23
If this has been solved elsewhere, I apologise.

The latest Ubuntu server has been installed on the hardware of my ISP - i.e. it is accessable remotely.

I have added the desktop to the server (for ease of use) by following the instructions in Ubuntuguide and using FTP and Putty.

Question now is: How do I start up the desktop remotely so that I can see the familiar layout when I sign on?

Your assistance is really appreciated.
Thank you

---

### Post by matrixblue on 2010-07-23
run **startx**

---

### Post by CharlesA on 2010-07-23
> **matrixblue said:**
> run **startx**
That doesn't work when you are tunneling X over SSH does it?

---

### Post by nuddernuby on 2010-07-23
I am doing this remotely.
Does this mean I should go [http://ipaddress/startx](http://ipaddress/startx) ?

If I do this via Putty, I get :
> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux xxxxx.hosting24.com.au 2.6.18-028stab068.9 #1 SMP Tue Mar 30 17:22:31 MSD 2010 x86_64
Kernel command line: quiet
Build Date: 07 May 2010  06:33:21AM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 24 12:43:03 2010

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


Going to look at wiki.x.org now.
Any ideas?

---

### Post by Chris1274 on 2010-07-23
.

---

### Post by CharlesA on 2010-07-23
If the OP is using Putty, under "SSH" there is an option that says X11. Check the box that says "Enable X11 forwarding."

I don't know if you can forward an entire desktop over SSH, since I usually just start certain applications, such as VirtualBox or gedit.

---

### Post by bodhi.zazen on 2010-07-24
> **nuddernuby said:**
> If this has been solved elsewhere, I apologise.

The latest Ubuntu server has been installed on the hardware of my ISP - i.e. it is accessable remotely.

I have added the desktop to the server (for ease of use) by following the instructions in Ubuntuguide and using FTP and Putty.

Question now is: How do I start up the desktop remotely so that I can see the familiar layout when I sign on?

Your assistance is really appreciated.
Thank you

Well, honestly you are going about this all wrong, sorry.

First, X does not help all that much on a server. Most of what you will be doing is entering commands or editing text files and you can do all that from putty.

Second, if you are on Windows you need a X server, take a look at Xming.

If you want a graphical interface for your server I highly suggest a web tool such as webmin or phpmyadmin.

ftp is, IMO, less then ideal and I would suggest you use ssh. You can transfer files with scp. If you want a graphical interface, windows uses winscp and on Linux you can use sshfs.

Hard to know the cause of the error you posted, could be anything from ssh needing to allow X forwarding (/etc/ssh/sshd_conf ) to not running a X server (if you are connecting from windows).

---

### Post by drdos2006 on 2010-07-24
Appears to me that you need to login via Webmin.
Webmin needs to be installed on the server.
regards

---

### Post by nuddernuby on 2010-07-24
Thank you for all the advice.
I'll look at webmin to solve this.
Rgds

---

### Post by n3hu on 2011-03-04
> **nuddernuby said:**
> If this has been solved elsewhere, I apologise.

The latest Ubuntu server has been installed on the hardware of my ISP - i.e. it is accessable remotely.

I have added the desktop to the server (for ease of use) by following the instructions in Ubuntuguide and using FTP and Putty.

Question now is: How do I start up the desktop remotely so that I can see the familiar layout when I sign on?

Your assistance is really appreciated.
Thank you

  Finally figured this out last night and got my xfce4 display to a windows PC working from my VPS server using Xming. I'm running Ubuntu 10.04 on the VPS, win7 64 on the PC.

  - installed latest version of Xming

  - installed xfce4 (actually I installed the whole Xubuntu-desktop)

  - I ran an Xming xlaunch session from my windows machine using
        - one window

        - start a program

        - Start Program: /usr/bin/xfce4-session
        - Run remote using Putty
        - Connect to the IP or FQDN of the VPS server
        - user (I'm running root right now)

        - no changes to the parameter settings

   hope this works for you

---

### Post by nuddernuby on 2011-03-05
Thanks. Will try this out.

---

