---
title: "runlevel"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by cherishcc on 2009-07-22
I want to change the default runlevel in order to install NVIDIA Linux Driver but I can't find  the file /etc/inittab. I don't know why. Thanks~:)

---

### Post by Durden on 2009-07-22
Ubuntu (Debian) Linux uses /etc/init.d

It's a directory, each file in there is the startup script for the processes you are running. Each script can be started/shutdown/restarted by using the corresponding "start," "stop" and "restart" commandline arguments.

---

### Post by dk06 on 2009-07-22
If you just want to temporarily change  runlevels,

[SIZE=4][B]Try one of the following:
[/B][/SIZE]
[SIZE=2][B]sudo init 1

sudo init 2

sudo init 3

sudo init 4

sudo init 5

sudo init 6

EXPLANATION[/B][/SIZE]
> 
**1** Single-User Mode Does not: configure network interfaces, start daemons, or allow non-root logins.[[2]]("http://en.wikipedia.org/wiki/Runlevel#endnote_behavour_of_runlevel_1")   **2** Multi-User Mode Does not: configure network interfaces or start daemons.[[3]]("http://en.wikipedia.org/wiki/Runlevel#endnote_behavour_of_runlevel_23")   **3** Multi-User Mode with Networking Starts the system normally.[[4]]("http://en.wikipedia.org/wiki/Runlevel#endnote_behavior_of_runlevel_23")   **4** Unused/User defined for special purposes   **5** X11 As runlevel 3 + [display manager]("http://en.wikipedia.org/wiki/X_display_manager").[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

==========================================================
[COLOR=Red][B]
Why would you want to change the default runlevel just to install something?[/B][/COLOR]

---

### Post by cherishcc on 2009-07-23
> **Durden said:**
> Ubuntu (Debian) Linux uses /etc/init.d

It's a directory, each file in there is the startup script for the processes you are running. Each script can be started/shutdown/restarted by using the corresponding "start," "stop" and "restart" commandline arguments.

Thanks a lot. But how can I know my default runlevel? Because in /etc/inittab, I know that the sentence appears as  id:n:initdefault:  indicates the default runlevel, but how can I know it here? and how can I know which level is where the X window is not running?  
Thanks!
:P

---

### Post by cherishcc on 2009-07-23
> **dk06 said:**
> If you just want to temporarily change  runlevels,

[SIZE=4][B]Try one of the following:
[/B][/SIZE]
[SIZE=2][B]sudo init 1

sudo init 2

sudo init 3

sudo init 4

sudo init 5

sudo init 6

EXPLANATION[/B][/SIZE]
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

==========================================================
[COLOR=Red][B]
Why would you want to change the default runlevel just to install something?[/B][/COLOR]

Because my system typically boots to the X window system and if I want to install the NVIDIA Linux Driver, it should both exit X window and change the default runlevel.
Thanks for your help!

---

### Post by kpkeerthi on 2009-07-23
1. Press ctrl + alt + F1
2. stop gdm
```
sudo /etc/init.d/gdm stop
```
3. install the driver
----------
reboot (type **sudo reboot** at the prompt) or try
1. Start gdm
```
sudo /etc/init.d/gdm start
```
2. Press ctrl + alt + F7

---

### Post by louieb on 2009-07-23
One thing that Ubuntu and Debian differ from the list dk06 posted is run levels 2 - 5  are all the same. (run level 3 in his list).

Also Ubuntu replaced the traditional **init** service with **Upstart**. Upstart is compatible with the init system and can run the same scripts.    

Just use the method kpkeerthi posted and you should be fine.

---

### Post by Paddy Landau on 2009-07-23
> **louieb said:**
> Also Ubuntu replaced the traditional **init** service with **Upstart**. Upstart is compatible with the init system and can run the same scripts.
Not quite related to the OP... Do you know how I can get a script to automatically run whenever the computer wakes up from hibernate, suspend or screensaver? I've searched for this before and found no answer.

---

### Post by louieb on 2009-07-24
> **Paddy Landau said:**
> Not quite related to the OP... 

Have not done that. Probably best to start a thread for your question.

---

### Post by frunns on 2009-07-24
> **kpkeerthi said:**
> 1. Press ctrl + alt + F1
2. stop gdm
```
sudo /etc/init.d/gdm stop
```
3. install the driver
----------
reboot (type **sudo reboot** at the prompt) or try
1. Start gdm
```
sudo /etc/init.d/gdm start
```
2. Press ctrl + alt + F7

Yeah, this is the way to do it. Might have to kill X manually after stopping gdm.
```
sudo killall xorg
``` 
Think you need to sudo it at least.

---

