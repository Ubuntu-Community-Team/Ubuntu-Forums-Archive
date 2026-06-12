---
title: "need my x server running to install some software"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by bitdoger on 2009-01-05
i recently overwrote my fiesty fawn with heron(8.04lts)...and
see below my startx attempt to start my x server to run my _installer.sh program...
david@david-desktop:~$ sudo su -
[sudo] password for david: 
root@david-desktop:~# cd /
root@david-desktop:/# ls


root@david-desktop:/home/david/tos# startx
xauth:  creating new authority file /root/.Xauthority
xauth:  creating new authority file /root/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
root@david-desktop:/home/david/tos# 

...and...
then tried to run this java based program with this _installer.sh
(after i apt-get the JAVA)...
root@david-desktop:/home/david/tos# ./thinkorswim_installer.sh
testing JVM in /usr ...
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
If you have access there is probably an X library missing.
An error occurred:
java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
Error log: /tmp/install4jError23343.log
root@david-desktop:/home/david/tos#

...tia dave

---

### Post by bodhi.zazen on 2009-01-05
First , that error message states the X is already running. What happens if you simple

Ctrl-Alt-F7 or sometimes it is on F8 or F9 ?

Second, why are you running X as root ?

Third, does this script require X ? Can you not , as root, ./my _installer.sh (or simply /full_path_to/my _installer.sh) ?

---

