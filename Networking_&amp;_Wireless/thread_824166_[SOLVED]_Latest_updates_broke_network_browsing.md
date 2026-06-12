---
title: "[SOLVED] Latest updates broke network browsing"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by John Harrington on 2008-06-09
I'm hoping somebody can help me with a problem browsing workgroup computers which apparently resulted from standard ubuntu updates which became available today and which I have just installed.

Prior to today's package updates, I could browse workgroup computers (one running Windows XP and one running Xubuntu) on my home network through Nautilus. Nautilus is running on a third computer using regular Ubuntu.  Nautilus => Go => Network would show each computer as well as the mshome workgroup.  Clicking on the workgroup would again show each computer.  (The netbios names are resolved through /etc/hosts, and have fixed addresses assigned in the router.  I haven't been able to get any other netbios name resolution method to work.)  

Following today's package updates, Nautilus => Go => Network shows only an icon for the mshome workgroup.  Clicking on the icon produces a blank window and the message "0 items" in the bottom bar.  I can still browse the network shares by manually typing "smb://<computername>", but the computers themselves do not appear.

smbtree produces no output.

nmblookup mshome produces:

querying mshome on 192.168.1.255
192.168.1.2 mshome<00>  # this is the Ubuntu computer on which command is run
192.168.1.4 mshome<00>  #  this is the Xubuntu computer

Pyneighborhood on the Xubuntu computer still shows both the Ubuntu and the XP computers (although it won't show or let me mount the file shares on the Ubuntu computer--a different problem)

I have restarted the computer, but to no avail.  

The package updates today included libsmbclient, samba, samba-common, smbclient, and smbfs.

I'd appreciate any suggestions about how to fix this.

---

### Post by John Harrington on 2008-06-09
Well, this has started working again mysteriously.  I didn't do anything--didn't even reboot any of the computers.

I think my description of what was happening was wrong in one respect.  Nautilus => Go => Network produced an icon labelled "Windows Network", not "mshome."  Now that it's working again, "Windows Network" leads to "mshome" which leads to the three networked computers.

---

### Post by TRBD16Z6 on 2008-06-20
I'm having this same problem right now. When I first installed Ubuntu 8.04 a month ago MSHOME came up under 'Windows Network'. Now it doesn't. I can still connect to shared files though manually typing in 'smb://ipaddress/sharename' into either firefox or nautilus. smbtree in terminal displays nothing for me. And it seems as though netbios names don't work for me.

---

