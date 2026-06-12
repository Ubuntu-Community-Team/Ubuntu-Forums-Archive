---
title: "auto enable wlan0"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by velovelo13 on 2009-10-20
Using Ubuntu for the first time and managed to install wireless lan using niswrapper.  After startup, I need to use terminal command to enable wlan0 (sudo iwconfig wlan0 ... "AP" Managed).  Where can I place this command so that it gets executived automatically?

---

### Post by martrn on 2009-10-20
If using gnome and need to run just one program you can add this at :
[https://help.ubuntu.com/community/AddingProgramToSessionStartup]("https://help.ubuntu.com/community/AddingProgramToSessionStartup")

   system > Preferences > Sessions
or System > Preferences > Startup Applications

Depending on which version of gnome you are running.

If you are running a series of commands you need to write a bash script [http://www.panix.com/~elflord/unix/bash-tute.html]("http://www.panix.com/~elflord/unix/bash-tute.html") and add these to Session Starup Applications or to your /etc/init.d  directory and make it executable.

---

### Post by kevdog on 2009-10-21
Did you ever get this question answered?  I can help you with it if you have any more questions or concerns.

---

### Post by velovelo13 on 2009-10-21
What I need is Linux equivalent of autoexec.bat.  I just need this command " sudo iwconfig wlan0 essid "AP" mode Managed" executed after bootup.

---

### Post by Warpnow on 2009-10-21
Doing what martrn suggested will make exactly that happen.

If all else fails, adding any command to the bottom of /etc/rc.local will run during bootup immediately as root.

---

### Post by martrn on 2009-10-21
> **velovelo13 said:**
> What I need is Linux equivalent of autoexec.bat.  I just need this command " sudo iwconfig wlan0 essid "AP" mode Managed" executed after bootup.

I am only commenting on what you wrote.

Ubuntu uses the /etc/init.d directory which is read by the linux kernel when ubuntu is booting up.  Ubuntu manages the startup sequences by a program know as upstart, which is ubuntus replacement for the sysvinit from the former unix or unix-linx systems.  See [http://upstart.ubuntu.com/]("http://upstart.ubuntu.com/") for more info.

You could write a shell scipt to be executed at the start of Ubuntu and if it is places in your /etc/rc0.d directory, which is where upstart will look for any scripts.

To execute a script at startup of Ubuntu:
========================================
Put your script in /etc/rc0.d
and make it executable (sudo chmod +x myscript)

Note that : The scripts in this directory are executed in alphabetical order, and the name of your script must begin with K99 to run at the right time. 

There are already some scripts there...
=======================================

There are already some written scripts in your /etc/rc0.d directory that Ubuntu will look at and execute every time you switch on your computer.  You might wish to look at the scripts in your /etc/rc0.d directory for more information on understanding the terminology of the shell scripts.

NOTE: I am only commenting on what you wrote ~~~ [COLOR="Silver"]*.."..I need is Linux equivalent of autoexec.bat.  I just need this command " sudo iwconfig wlan0 essid "AP" mode Managed" executed after bootup.."..*[/COLOR]

---

