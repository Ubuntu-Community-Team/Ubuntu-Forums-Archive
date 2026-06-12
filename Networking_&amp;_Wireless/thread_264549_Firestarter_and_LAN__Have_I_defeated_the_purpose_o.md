---
title: "Firestarter and LAN:  Have I defeated the purpose of a firewall?"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by tmtjjhnsn on 2006-09-24
I have three machines on a home LAN, behind a NAT router, two running Dapper, and one Windows XP.  I am running Samba and Firestarter.  The only way I have found to share files among the three machines is to configure Firestarter by clicking Edit>Preferences>Advanced Options and unchecking the box for Block broadcasts from external networks.  I have allowed 192.168.1.0/24, and allowed Samba in Firestarter, but, still, I can only access the other machines on the network from the Dapper machines if I uncheck the aforementioned box or disable Firestarter altogether.

My question is, am I defeating the purpose of Firestarter by allowing broadcasts from external networks? What am I doing wrong in configuring Firestarter?  I know, I probably don't need Firestarter, especially since I am behind a NAT router, which is, in turn, behind a Web proxy, but I'm weird.  :-&

---

### Post by wieman01 on 2006-09-25
I have the exact same setup. But I had to allow Samba for "inbound" and "outbound" traffic. So I am enclosing screenshots of the rules for both... For your reference. This ought to work.

Try with one client first... One step at a time. :-) And let us know how it goes.

---

### Post by tmtjjhnsn on 2006-09-25
Oh, what have I done, Wieman01?  I tried that on the machine that I call Ernie, and it didn't work for me.  I couldn't access my network with those settings.  I then put Firestarter back the way I had it, and the other two machines could not access Ernie, even with Firestarter disabled altogether!  Typing sudo smbtree in a terminal gives me this:

MERLIN
\\RACHAEL laptop
\\RACHAEL\Printer Lexmark 510 Series
\\RACHAEL\My Pictures
\\RACHAEL\print$ Printer Drivers
\\RACHAEL\SharedDocs
\\RACHAEL\IPC$ Remote IPC
\\RACHAEL\My Documents
\\PENELOPE Samba 3.0.22
\\PENELOPE\print$
\\PENELOPE\IPC$ IPC Service (Samba 3.0.22)
\\PENELOPE\ADMIN$ IPC Service (Samba 3.0.22)
\\ERNIE Samba 3.0.22
cli_start_connection: failed to connect to ERNIE<20> (0.0.0.0)

I have no idea what to do. My Samba configuration file is exactly the same now as it has always been. Any help would be much appreciated.

---

### Post by wieman01 on 2006-09-25
Does the same happen if you shut down Firestarter? Try that.

If you still have the same problem then bear in mind that this problem may related to the folder's access rights. When Samba clients access a folder that is shared on the network, you need to ensure that it has proper access rights. Find out about the settings using this command:
> ls -l
Changing access rights is done using these:
> sudo chmod
sudo chown
sudo chgrp
But try without Firestarter first.

---

### Post by tmtjjhnsn on 2006-09-25
The problem persisted, even with Firestarter disabled.  I uninstalled Firestarter and restarted the machine, and then all was well.  Firestarter and I have not been friends.  I have been trying to configure it to run with my LAN for almost two months, now.

---

### Post by wieman01 on 2006-09-25
If Firestarter is not the issue, then it's the folder's access rights. You need to change the settings & rights in such a way that users other than your own have access to the FTP folders.

Firestart is fairly reliable, but I agree that it takes a while to figure it out.

---

