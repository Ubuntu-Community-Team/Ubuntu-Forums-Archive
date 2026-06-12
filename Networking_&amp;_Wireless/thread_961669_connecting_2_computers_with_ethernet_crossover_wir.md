---
title: "connecting 2 computers with ethernet crossover wire"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by kcode on 2008-10-28
i have have two computers running ubuntu 8.04. 
how can i configure the connection, so that i data can be transfered between the 2.

thanks

---

### Post by Fire_Chief on 2008-10-28
I am assuming you have a crossover ethernet cable connecting the two systems AND have a link light on both network cards.

Go to System -> Administration -> Network on both PCs.
Unlock the control panel (click Unlock button and enter password)
Click on Wired Connection and then click the Properties button
Uncheck Roaming Mode checkbox.
Set option to Static IP Address
Set the first PC's IP info to
   address 10.0.0.10
   netmask 255.255.255.0
   gateway (leave blank)

Set the second PC's IP info to
   address 10.0.0.11
   netmask 255.255.255.0
   gateway (leave blank)

Click Ok button and save the configurations. You should now be able to open a terminal window on PC #1 and test connection to PC #2
```
ping 10.0.0.11
```Press CTRL Z to stop the ping.
If you see replies from 10.0.0.11 then the connection is working.

Now open Nautilus and browse to the folder you want to share. (Places menu)

Right click on the folder you want to share and select Sharing Options.
Click the check box to share this folder. Select the other check boxes if you want to grant access for writing from the other PC and guest access if you do not want to require a username and password to view the share.

Ubuntu may prompt you to install packages for either NFS or Samba. NFS is preferred but you can use either one. After the packages install, the sharing should become active.

Cheers!

---

