---
title: "Backing up files to USB drive over Network"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by e30drift on 2008-06-07
I am having a devil of a time with this...

I have 3 ubuntu server running as web, mysql and backup servers respectively.

I installed a USB hard drive to the backup server and shared it out through Samba.

I am trying to setup a simple Tar backup script to archive certain directories from the web and mysql servers and copy them to the USB hard drive.

i know this can be done via FTP, but coming from a Windows network, i figured it would simpler to share out the USB drive on one server and copy the Tar files to it from the other 2 servers.

Essentially what i want is to have the web and mysql servers create their own Tar archives locally and copy them to a shared folder on the backup server.  The backup server will then replicate those Tar files to the USB hard drive.  yes, i graduated top of my class from the Redundant School of Redundancy.  


I have no idea how to create or run a script to do this nor do i have a full grasp of Cron jobs.  Help with that would be priority, but the bigger issue is how the hell can i see the shared folder on the backup server from the other 2?

I went to "Connect to Server" but i do not have an option for Samba.

---

### Post by e30drift on 2008-06-08
Bump!

---

### Post by prshah on 2008-06-10
> **e30drift said:**
> but the bigger issue is how the hell can i see the shared folder on the backup server from the other 2?

I went to "Connect to Server" but i do not have an option for Samba.

We can work on the scripting, tar-ing and backup part later; now, why not take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=785517&highlight=samba"), starting with post #4, for a step by step way to connect to a samba share?

If you don't have the option for samba, you need to install samba first, before trying the above```
sudo apt-get install samba
``` will get you started off.

---

### Post by e30drift on 2008-06-11
> **prshah said:**
> We can work on the scripting, tar-ing and backup part later; now, why not take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=785517&highlight=samba"), starting with post #4, for a step by step way to connect to a samba share?

If you don't have the option for samba, you need to install samba first, before trying the above```
sudo apt-get install samba
``` will get you started off.

prshah,

I do have samba installed on each box and have even rebooted after the install.  I did share out the USB drive and the respective folders that I need shared.  
I can hit them from my Windows laptop with \\server-name\shared-folder.
But from Ubuntu to Ubuntu, I'm having the issue.  
I do not know the syntax to put into the bash script.
Help with that would be greatly appreciated.

---

### Post by prshah on 2008-06-11
> **e30drift said:**
> 
I can hit them from my Windows laptop with \\server-name\shared-folder.
I do not know the syntax to put into the bash script.


You will have to run the bash script with superuser privileges; eg. sudo ./scriptname

In that, you can access your samba share with the following command;```
mount -o rw -t cifs //server-name/sharedfolder /mnt 
``` this command will mount your shared folder on "/mnt" (make sure it exists)

---

