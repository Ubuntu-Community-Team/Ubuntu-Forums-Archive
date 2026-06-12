---
title: "Access to Windows shared resources"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by caribconsult on 2008-11-27
My problem seems to be the opposite of what many people are experiencing.  

I have a LAN with 3 XPPro units and one Ubuntu 8.10 unit.  Firewalls are all down, all XP machines can see the Ubuntu and its shared resources, the Ubuntu can use the printer attached to one of the XP machines, but unless I login to the Ubuntu as 'root' I cannot see the windows shared resources on any XP machine from the Ubuntu Net Mgr.  I see the networked computers, can ping them, but the shared resources don't appear on the Ubuntu Net Mgr unless I'm logged in as 'root'  I've created other users with the same names as  those on the XP machines, opened the guest account on the XP units, given the Ubuntu users full rights, executed the sudo smbpasswd -a command for two users, but still no go.  Can someone tell me what I'm doing wrong here?  I'm a total newbie to UNIX and Ubuntu, but I have tons of experience with Windows, Novell, and other networking systems.

Thanks to any who respond.

---

