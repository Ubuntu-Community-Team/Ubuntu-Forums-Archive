---
title: "Samba, two dappers and an XP"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by tmtjjhnsn on 2006-09-25
I have three machines on a home LAN, two Dappers and one Windows XP.  Recently, I tried changing some settings in Firestarter, and now the Dapper machine on which I monkeyed with Firestarter, Ernie, is inaccessible from the other Dapper and my XP box, even when Firestarter is disabled!  When I type sudo smbtree on the affected machine, I get this:

MERLIN
        \\RACHAEL                       laptop
                \\RACHAEL\Printer               Lexmark 510 Series
                \\RACHAEL\My Pictures
                \\RACHAEL\print$                Printer Drivers
                \\RACHAEL\SharedDocs
                \\RACHAEL\IPC$                  Remote IPC
                \\RACHAEL\My Documents
        \\PENELOPE                      Samba 3.0.22
                \\PENELOPE\print$
                \\PENELOPE\IPC$                 IPC Service (Samba 3.0.22)
                \\PENELOPE\ADMIN$               IPC Service (Samba 3.0.22)
        \\ERNIE                         Samba 3.0.22
cli_start_connection: failed to connect to ERNIE<20> (0.0.0.0)

I have no idea what to do.  My Samba configuration file is exactly the same now as it has always been.  Any help would be much appreciated.

---

### Post by spd106 on 2006-09-25
I would recommend completely removing firestarter, then reboot to clear the kernel routing tables. If the problem persists could you post the smb.conf and the output of **sudo iptables -L -v**.

Might be a good idea to make a note of any settings you made in firestarter to aid re-installation later.

---

### Post by tmtjjhnsn on 2006-09-25
Okay, uninstalling Firestarter and restarting worked!  My machine is accessible on the network again.  

I am hesitant to reinstall Firestarter.  I have been trying to configure it to work with my network for a couple of months. The only way I was able to get it to coexist with my LAN was to click Edit>>Preferences>>Advanced settings and to uncheck the box for "Block broadcasts from external networks."  That sounded like defeating the purpose of a firewall, but I could be wrong.  Any thoughts?

---

