---
title: "Slow file transfer - needs to be &quot;waked&quot; up"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by chtse53 on 2007-04-23
I have setup Ubuntu 7.04 as a file server to be accessed by Windows XP PCs. My LAN is a gigabit ethernet network.  I noticed that the "normal" transfer rate is at about 20-25% of the 1000 Mb capacity.  However, the Ubuntu server appears to go into stand-by mode after 10 minutes or so and the transfer rate during this time is less than 1% of the gigabit capacity (checked by Windows XP's network performance in the Task Manager).  I have to "wake" up the Ubuntu server remotely by connecting to it with VNC or directly by mouse/keyboard activity.  After "waking up", the file transfer rate resumes to 20-25%.  I have checked the power management and ensure that the server should never go into sleep mode.  The same is set for the display.  Anybody has the same problem?  Any suggestions?

---

### Post by chtse53 on 2007-04-23
After further testing, I have got a clearer picture of my problem.  The slow transfer  only affects writing files to the Ubuntu samba server.  Reading files from the server always reach 20-25% of the gigabit network capacity.  By making a VNC connection to the Ubuntu server from one of my XP PCs, the speed of writing files to the server will immediately increased to the 20-25% capacity. If I minimize the VNC window, the writing speed will immediately drop to less than 1% of the network capacity.  Anybody has any idea what is causing my problem?

---

