---
title: "Shared Folder is Password Protected"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by theyain on 2007-06-09
Hello!  I have set up a shared folder on my UbuBox, but when ever I try and click the link to open it on any other computer, it asks for a name and password.  Now I have never set up a password or user name for this file, nor do I need it.  Is there any way to remove the password protechtivness?

---

### Post by jamillikan on 2007-06-09
If you are using SAMBA, try this in a terminal window:

sudo smbpasswd  -e  yourusername
sudo smbpasswd  -a  yourusername

Follow the on-screen prompts for password.

When you attempt to access the share, type in the password you entered with the above commands.  The password should be the same password for both entries, IMO.

Hope that resolves your issue.

Joe

---

