---
title: "I need a windows PC to relay files across the LAN?"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2014-03-17
For some reason, I can not see either ubuntu pc in network neighborhood, but I can connect to a windows 7 pc.
So If I want to copy file from one ubuntu PC to another, I have to copy from ubuntu to windows, then from windows to the other ubuntu PC.
I know that seems odd, but that is how it works. 
Any ideas?

---

### Post by gifford on 2014-03-17
Strange..
Have you tried using NitroShare?

---

### Post by sdowney717 on 2014-03-17
No, is it good?

How do you connect to another ubuntu PC?
I told one of them to share /home in file manager.
Then look for it in network, even tried connecting to server name.

---

### Post by rogergantner on 2014-03-17
Are you sure samba is installed on the ubuntu machines? Open the Software Centre and search for samba. It'll show up as 'SMB/CIFS file, print, and login server for Unix'. Make sure this is installed.
I had the same issue yesterday when I installed Ubuntu on my laptop. I had a horrible time with Ubuntu connecting to networked drives. Also it could not see itself on the network, only the other computers. Since installing samba network discovery now works properly.

---

### Post by Bashing-om on 2014-03-17
sdowney717; Hello ,

Per Morbius1, easiest way to cp files 'tween two 'ubuntus that share the same router/house :
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

[INDENT][INDENT]'buntu, more than
[INDENT][INDENT][INDENT]one path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sdowney717 on 2014-03-17
yes, installed.

but maybe samba has a bug, both ubuntu are Trusty 14.04

---

### Post by Dennis N on 2014-03-17
For the task you describe (copying files between two Ubuntu machines on the same local network) I would use SSH and forget Samba. 

To make transfers from Ubuntu A to/from Ubuntu B on same local area network:

1) Need openssh-server installed on B (the remote machine). Install it if necessary.
2) Using Nautilus on A: File > Connect to Server
3) Server: Enter IP of B; type: SSH; select folder on B to be opened (default is /), and the account information on B.
4) Click connect. If it's a first time connection, ignore warnings and allow to "connect anyway".
5) Nautilus opens a window on B.
6) Drag and Drop files, in either direction A to B or B to A.
7) (optional) Make a bookmark for the remote folder and nautilus will do a one-click connect in the future from the side pane.

Reference System: Ubuntu 12.04

---

### Post by sdowney717 on 2014-03-17
> **gifford said:**
> Strange..
Have you tried using NitroShare?

looks good, but has not been built for trusty yet.

I mean file sharing should just work right in the file manager. That is what I think.
Maybe someone could create a gui like windows has for home networking setup.

---

### Post by bab1 on 2014-03-17
> **sdowney717 said:**
> I mean file sharing should just work right in the file manager. That is what I think.

It does just work.  The routines are built right into Gnome's Nautilus File Manager.  That's what Samba usershares are.  Just right click and share any directory in your /home directory.
> 
Maybe someone could create a gui like windows has for home networking setup.
Do you mean TCP/IP networking setup?  Or file sharing setup?  What would you want the GUI to actually do.

If you are not using GNOME then you can install Gigolo.  That's the GNOME (gvfs) routines used to accommodate Samba sharing.

---

### Post by sdowney717 on 2014-03-17
> **bab1 said:**
> It does just work.  The routines are built right into Gnome's Nautilus File Manager.  That's what Samba usershares are.  Just right click and share any directory in your /home directory.

Do you mean TCP/IP networking setup?  Or file sharing setup?  What would you want the GUI to actually do.

If you are not using GNOME then you can install Gigolo.  That's the GNOME (gvfs) routines used to accommodate Samba sharing.

Yes, using gnome, and no it does not just work for everyone. That is saying something is an absolute.
[http://ubuntuforums.org/showthread.php?t=2209795](http://ubuntuforums.org/showthread.php?t=2209795)

I have also had trouble with samba in previous versions.

---

### Post by bab1 on 2014-03-17
> **sdowney717 said:**
> Yes, using gnome, and no it does not just work for everyone. That is saying something is an absolute.
[http://ubuntuforums.org/showthread.php?t=2209795](http://ubuntuforums.org/showthread.php?t=2209795)

I have also had trouble with samba in previous versions.
The samba usershares (via the GUI) are not setup in the smb.conf file.  Your reference is not what I am talking about.

If you rrght click on the directory you want to share, Samba is installed and the share is created at /var/lib/samba/usershares.  You are prompted to set the amount of access permissions you wish to allow and the share is created.

The only caveat is the LAN TCP/IP connectivity and hostname resolution should be working BEFORE you share anything.  In the link you provided I see the OP says " ...it cannot just browse the network".  My experience is 99.999% of the time this is a nameserver problem not a Samba share problem.

---

### Post by gifford on 2014-03-18
Yes, NitroShare works really well. And yes, not built for trusty yet...hopefully soon.

---

