---
title: "Other Ubuntu machine disappeared"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by chicagonpg on 2008-01-16
I need help my network to my other machines are gone from my places - network folder. Same thing has happen to my laptop. The one that has ubuntu-media still reads all on the network.
I didn't change anything it just stopped for some reason. I reinstalled all the samba files but it still is a no go. Thank you for any help. Oh the desktop you see is reading in the terminal but also is not showing up in my network folder.


chicagonpg@chicagonpg-desktop:~$ smbtree
Password: 
WORKGROUP
        \\MACINTOCH-LOCAL               macintoch.local
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to MACINTOCH-LOCAL<20> (63.251.179.13). Error NT_STATUS_CONNECTION_REFUSED
MSHOME
        \\UBUNTU-MEDIA                  ubuntu-media server (Samba, Ubuntu)
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to UBUNTU-MEDIA<20> (8.15.7.117). Error NT_STATUS_CONNECTION_REFUSED
        \\CHICAGONPG-DESK               chicagonpg-desktop server (Samba, Ubuntu)
                \\CHICAGONPG-DESK\IPC$                  IPC Service (chicagonpg-desktop server (Samba, Ubuntu))
                \\CHICAGONPG-DESK\Music          
                \\CHICAGONPG-DESK\Videos         
                \\CHICAGONPG-DESK\print$                Printer Drivers
chicagonpg@chicagonpg-desktop:~$

---

### Post by mimada on 2008-01-16
There is an issue with samba and the iptables firewall. Install Firestarter on both Ubuntu machines and disable the firewall. Then see if you can access your shares.

---

