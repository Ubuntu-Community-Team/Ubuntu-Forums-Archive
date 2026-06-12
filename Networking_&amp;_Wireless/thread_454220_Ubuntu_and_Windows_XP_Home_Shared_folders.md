---
title: "Ubuntu and Windows XP Home Shared folders"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by ldclan on 2007-05-25
I have a problem that I am hoping someone here can help with me.
I have a small home network that consists of a Ubuntu PC (7.04), and 2 XP PCs(Home).
The XP PCs can be seen on the network using the Ubuntu PC, I can print to the XP printers, and I can connect to their shares via the “Connect to Server” using each XP PCs IP address.
If I browse the network from the Ubuntu PC, I can see everything but I can not see the XP shares only the PC themselves.

It is odd that I can connect via “Connect to Server” using each computers IP address and not by browsing to it.
Right nowthe Ubuntu box is part of my workgroup (XP Homes default “mshome”), the samba config file has not been changed except for:

    ####### Authentication #######

    # "security = user" is always a good idea. This will require a Unix account
    # in this server for every user accessing the server. See
    # /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
    # in the samba-doc package for details.
    ;  security = user

Sercuity has been changed to:

security = user
username map = /etc/samba/smbusers

The strange part is when I go to create a samba user by: sudo smbpasswd -a <username> it fails every time even doing this in the root account.

Does anyone have a clue on what I am doing wrong?

---

### Post by dolphin_oracle on 2007-05-25
Your smb.conf file shouldn't matter for browsing other machines.  Do your XP boxes have firewalls?  I'm had certain firewall programs hide shared folders in the past.  In particular, some versions of Norton Firewall hide the shares, but they are accessible if you directly put in the IP address or the //servername address.

---

### Post by ldclan on 2007-05-25
Well I have tried it and it doesn't work I am back to square one, but thank you for the help.

---

