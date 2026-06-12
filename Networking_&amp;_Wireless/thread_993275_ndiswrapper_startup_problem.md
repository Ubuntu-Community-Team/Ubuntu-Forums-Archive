---
title: "ndiswrapper startup problem"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by sanjuro_dave on 2008-11-25
I have installed ubuntu 8.10 and used ndiswrapper to get my wireless internet working. (Marvell chipset w8300 using the driver off original cd mrv8k51)

When this is loaded with modprobe after the system is started there is no problem however in adding ndiswrapper to /etc/modules the system starts fine until I log in to gnome when it hangs.

Reading through other posts have suggested this is due to a driver conflict but I am unsure how to investigate further.

Many thanks

Dave

---

### Post by jnorthr on 2008-11-25
You may find some answers in the system logs.
goto System>Admin>System Logs
which should show the kernel messages written into /var/log/syslog
and then review the messages near the bottom of the scroll pane as these should be the most recent messages.

Could this be a permissions issue ?

---

### Post by Rick_ hen on 2009-01-02
I also have problems when i restart my pc. 
I am using an asus WL138g with a marvell chipset. 
I used the "windows wireless drivers" program to load the driver, and it works fine, but when i restart the computer is really slow, wireless does not work and programs keep crashing. then i have to go to the ndiswrapper folder and remove the driver by hand to get the pc working again. When i remove the driver before shutdown i dont have that problem. Does anyone know a way to fix this, or maybe write a script that will automatically move the file back to the ndiswrapper folder at startup and move it away at shutdown. 
By the way, i am using Linux Mint 6 on a dell gx270.
I am looking forward to your reply,
Rick

---

### Post by Rick_ hen on 2009-01-03
I found a solution!:D

It is not a great solution, but it works...
open a gedit window, and insert this text:
```

sudo ndiswrapper -r mrv8k51
sudo shutdown -P 0
```

then open a command line and use ```
chmod 755 shutdownscriptfilename
```
then right click on the desktop and click "create launcher". Click browse and select your script. Now when you want to shut down your computer ALWAYS use THIS link! That way you will be able to start your pc again normally. 
You do however have to use ndis-gtk every time you restart your computer to have wireless internet. This is a temporary solution, so it is not perfect but it works for me.:)

---

