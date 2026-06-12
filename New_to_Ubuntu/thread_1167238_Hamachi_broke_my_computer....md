---
title: "Hamachi broke my computer..."
date: 2009-05-22
forum: New to Ubuntu
---

### Post by xubermensch on 2009-05-22
Hey ya'll.

I was fiddling around with Hamachi, trying to get it set up on this computer, when I ran into a problem. Here is the note that the synaptic package manager gave me:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.Now, I tried doing "sudo dpkg --configure -a" in the terminal, and then hamachi started up. However, it stalls out either at the "logging in" section, or if it manages to make it past that point, it stalls out after the list of hamachi commands comes up. Please help me, for I am a newb. Thank you!

---

### Post by xubermensch on 2009-05-22
Bump.

---

### Post by superprash2003 on 2009-05-23
try reinstalling hamachi

---

### Post by xubermensch on 2009-05-23
Here's what happened when I tried to reinstall Hamachi:

> rowland@rowland-desktop:~$ sudo su
[sudo] password for rowland: 
root@rowland-desktop:/home/rowland# aptitude install build-essential
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@rowland-desktop:/home/rowland# wget -c [http://www.rafekz.one.pl/hamachi_0.9.9.9.20.deb](http://www.rafekz.one.pl/hamachi_0.9.9.9.20.deb)
--2009-05-23 14:08:14--  [http://www.rafekz.one.pl/hamachi_0.9.9.9.20.deb](http://www.rafekz.one.pl/hamachi_0.9.9.9.20.deb)
Resolving [www.rafekz.one.pl]("http://www.rafekz.one.pl")... 94.23.103.1
Connecting to [www.rafekz.one.pl|94.23.103.1|:80]("http://www.rafekz.one.pl%7C94.23.103.1%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 333222 (325K) [text/plain]
Saving to: `hamachi_0.9.9.9.20.deb'

100%[======================================>] 333,222      242K/s   in 1.3s    

2009-05-23 14:08:16 (242 KB/s) - `hamachi_0.9.9.9.20.deb' saved [333222/333222]

root@rowland-desktop:/home/rowland# dpkg -i hamachi_0.9.9.9.20.deb
(Reading database ... 123762 files and directories currently installed.)
Preparing to replace hamachi 0.9.9.9-20 (using hamachi_0.9.9.9.20.deb) ...
Stopping hamachi...
tuncfg: no process killed
invoke-rc.d: initscript hamachi, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping hamachi...
tuncfg: no process killed
invoke-rc.d: initscript hamachi, action "stop" failed.
dpkg: error processing hamachi_0.9.9.9.20.deb (--install):
 subprocess new pre-removal script returned error exit status 1
Starting Hamachi hamachi-lnx-0.9.9.9-20 .. ok
Logging in ......... ok

  
It just indefinitely lagged out after attempting to log in, and no cursor appears, so I can't place additional commands.

---

