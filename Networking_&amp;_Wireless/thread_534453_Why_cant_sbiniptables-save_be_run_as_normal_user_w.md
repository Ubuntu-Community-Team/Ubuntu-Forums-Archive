---
title: "Why cant /sbin/iptables-save be run as normal user with 777 permissions?"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-25
Im trying to mess with my iptables, and daemonize the process.  Ive found a thread that is helping me do this, however in the executable portions of the script it calls /sbin/iptables-save /sbin/iptables-restore.  These originally had 755 permissions, but after changing these to 777, I still cant run these commands as a normal user.  They will run as root.  Any ideas??

---

### Post by kidders on 2007-08-26
Hi there,

You'll have a great deal of difficulty manipulating your box into allowing an unprivileged user to play with a firewall. Don't forget ... iptables is just a front end, so being able to run it as a normal user gets you nowhere.

Three important notes:[LIST]
[*]If you ever find yourself typing something that starts "chmod 777...", 99.9% of the time, you are *definitely* doing something wrong (and possibly dangerous). Ordinarily, you should absolutely never do it.
[*]Firewalls are there to protect you. Defeating their security features very often opens exploitable holes, so great care is advisable.
[*]The difference between 0755 permissions and 0777 is the ability of the whole world to *modify* iptables-save and iptables-restore. You should reverse that change.[/LIST]What are you trying to do? Perhaps there is a way of making it work.

---

### Post by kevdog on 2007-08-26
I am aware of the 777 dangers, however I changed to this permission test in the testing phase of my script development but have hist a wall.  Original permissions where 755.  

I originally set all the firewall permissions (or iptables) using the guarddog interface.  This works, however Im finding that everytime I boot, I need to manually start guarddog, set the IPtables, and then exit the programs.  (Something similar needs to be done with Firestarter too). 

Since I have my firewall set the way I like it (I dont change the settings all that often), what I want to do is to export the current configuration to a file, and then load the file into the iptables at boot everytime the system boots.  Ive found a guide that helps me do almost everything I need - [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111). however the basis of saving, restoring the iptables script file are the iptables-restore and iptables-save command.  In trying to improve the script, I am unsuccessful in the testing phase, in running these commands at the command line as a normal user.  root can always run these commands.  I dont understand why?

---

### Post by kidders on 2007-08-26
> **kevdog said:**
> however the basis of saving, restoring the iptables script file are the iptables-restore and iptables-save command.  In trying to improve the script, I am unsuccessful in the testing phase, in running these commands at the command line as a normal user.  root can always run these commands.  I dont understand why?Sorry, I never actually said *why* that is. Iptables interacts with low-level kernel components responsible for routing control. Without root privileges, it can't access them.

Is there a reason you can't acquire root privileges on the box you're working with? (Perhaps you don't have administrative control of it?)

---

### Post by kevdog on 2007-08-26
I can, Im the only user on the box -- I just have never run into a situation where a file owned by root root, couldnt be executed by any user when 777 permissions were in place.

Standby, I might need help later.  Basically Im creating this script to load the iptables up at boot.  I assume I'll put these in a rc.d file -- where at what runlevel do I place this at??? Inside the rcS.d folder or some other run level (Isnt rcS imply all run levels)?

Also I need a separate script to run at shutdown of the system: Either logoff, shutdown or sudo shutdown -h now.  Is there a file that runs automatically at shutdown similar to rc at startup?

---

### Post by kidders on 2007-08-26
> **kevdog said:**
> I just have never run into a situation where a file owned by root root, couldnt be executed by any user when 777 permissions were in place.Any user can execute a file that is "chmod 755", regardless of who the owner is. Setting the additional write bits (ie "chmod 777") is unnecessary, and would make no difference. (After all, anything that needs write access to *itself* to run is almost certainly malicious!)

Perhaps the simplest way of explaining why "chmod 755" won't allow a script running as an unprivileged user to access privileged resources is as follows. Consider a script called /usr/local/bin/render_unbootable containing ...```
#!/bin/sh
rm -Rf /boot
```Imagine you run **sudo chmod 755 /usr/local/bin/render_unbootable** to give the whole world permission to run it. I may be misunderstanding, but it seems, from your posts so far, that you would now expect the script to function if executed by an unprivileged user. Naturally, it won't.

Similarly, merely having permission to execute things that manipulate iptables achieves very little.

> **kevdog said:**
> Basically Im creating this script to load the iptables up at boot. One of these should already be in place. If it's not adequate for your needs, creating your own, as you are doing, (rather than modifying the pre-existing one) is the right thing to do. Startup & shutdown scripts run with root privileges though, so you needn't worry about not having access to everything you could want.

> **kevdog said:**
> Also I need a separate script to run at shutdown of the systemNormally, people roll their startup & shutdown scripts together into one file. You could take a look at the contents of your /etc/init.d for some examples of the sorts of conventions used.

---

### Post by kevdog on 2007-08-26
Im not sure if what you are saying is totally accurate.  Everything for me at least in the /etc/init.d folder does not get started at startup.  The whole reason I am doing this exercise is because iptables are not set at startup without bringing up the guarddog GUI manually.  When I look in the /etc/init.d folder there is a guarddog file, and when perusing through it -- it calls a /etc/rc.firewall script -- which exists also.  However this script is not getting executed at boot --- hence the whole purpose of this exercise.  It works when booting into KDE but not Gnome, however when I look at the script files, I have no explanation for this since the scripts just call kernel commands.

---

### Post by kevdog on 2007-08-26
Maybe this exercise was all for not, since I found a solution that works for me here:
[http://www.mepis.org/node/12139](http://www.mepis.org/node/12139)

This is a known problem -- I dont know a lot about run level, but obviously the part of the solution was to remvove the script in the rcS run level and add it to rc0-6 runlevels.  Anyway it did the trick!

---

