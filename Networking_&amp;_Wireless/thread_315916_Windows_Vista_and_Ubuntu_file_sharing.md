---
title: "Windows Vista and Ubuntu file sharing"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by luckyaba on 2006-12-09
My file server/media center has windows vista installed on it and my box is ubuntu 6.10. 

Problem:
Whenever i try to connect to a vista machine it prompts for a username and pass. I enter it and it doesn't let me login. This is the same on 2 Vista machines in the house. Anyone know why and/or how to fix it?

SOLVED:
I manually mounted the share with the mount command

Example : mount //192.168.0.100/share /media/network -o username=username,password=password

---

### Post by Lord_Freelancer on 2006-12-09
what version/edition of vista is it?

---

### Post by luckyaba on 2006-12-09
Windows Vista RTM.

It seems like some issue with windows authentication but i can't figure out a way around it.

---

### Post by Lord_Freelancer on 2006-12-09
ok inable the master admin profile and issue it a password, use that for accessing the file share, also make sure usere have read nd write access in the folder your sharing.

---

### Post by luckyaba on 2006-12-09
You mean Enable the Actual Administrator account on the Vista machine and set a password for it. Then try and login?

---

### Post by Symok on 2007-01-31
> **luckyaba said:**
> 
SOLVED:
I manually mounted the share with the mount command

Example : mount //192.168.0.100/share /media/network -o username=username,password=password

I can't get it to work... I'm getting the error:

"Wrong fs type, bad option, bad superblock on //192.168.0.103/tv
missing codepage or other error"

Any thoughts?

---

### Post by dangerousdan07 on 2008-01-10
Hello!

I could not get this to work in terminal on my ubuntu 7.10 load

mount //192.168.0.100/share /media/network

I checked some other options myself. The following instructions worked for me. I had the password checking for filesharing in Vista turned off. I also turned off the windows firewall just in case that was a problem. It would most likely be better to just add an exception to the firewall though.

On my Ubuntu pc I did this.

   Open the "Places" menu and then click "Connect to Server..." 
   the "Connect to Server" dialog box opens.

   Select "Windows Share" as your service type.

   In the "Server" blank enter in the IP address of the computer with your shared 
   files. (The computer name did not work for me)

   Type in the share name in the "Share" blank and click "Connect".

Now there should be a new shortcut on your desktop. It should be the mounted share from the Vista pc. I hope this helps some! Good luck!

---

