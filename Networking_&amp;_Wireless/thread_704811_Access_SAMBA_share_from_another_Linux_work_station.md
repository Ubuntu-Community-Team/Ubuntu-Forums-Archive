---
title: "Access SAMBA share from another Linux work station"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by vitiate34 on 2008-02-22
Hey guys, another Samba question,  but hold it there! it's a strange one!

I have a gutsy server running samba, set up for user shares and a print server which is working for all purposes fantastically. I can gain access to user shares from Windows (XP + 2000) but the curious thing is I cannot do the same from my gutsy workstation. From my work station I can see the "public" folder I have created for guest access, but not the user accounts.

My workstation user name and password matches that of my server's smbpasswd so I'm not sure what is going on. From what I can make of it, my workstation authenticates its self as "guest" but never tries to authenticate itself as a listed samba user.

Any thoughts? Thank you.

---

### Post by Iowan on 2008-02-22
My Ubuntu box seems to do the same thing with Samba. (Don't remember if it used to do that).  If I click my way to the server, then pull down the File>Connect to Server option, I can enter the name of the share I want - this puts an icon on my desktop.  I must already know the name of the share - since my smb.conf lacks a **browseable=yes** parameter.  Since I usually delete the "shortcut", I dunno if it comes back on reboot - it used to (a couple of versions ago).

---

### Post by vitiate34 on 2008-02-23
Any thoughts guys?

---

