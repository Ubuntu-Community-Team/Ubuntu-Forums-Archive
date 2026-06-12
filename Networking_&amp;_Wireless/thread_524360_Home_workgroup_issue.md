---
title: "Home workgroup issue"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by whistlerspa on 2007-08-13
I have a home workgroup of two Ubuntu boxes, a Mac ibook and a Windows XP laptop.

The problem that I have is with file and folder shares. The XP and i-book  can connect and share their shared folders with each other and the Ubuntu boxes can connect to all and access all shares.

The problem is that the XP and iMac can't connect to the Ubuntu boxes. With the Mac I keep getting a pop up box going on about 'can't find alias' and the XP laptop just keeps asking for the password endlessly when I try to connect to the Ubuntu shares. They do detect each other as part of the workgroup however.

Because they can all see each other I suspect that the problem is with the Ubuntu boxes but what?

Can anyone help please

---

### Post by whistlerspa on 2007-08-13
My thanks to islander_810 who posted to  'Windows asks for a password  -----"

 and his reference to the wiki.

The answer is  :

```
In a terminal enter command 

**sudo smbpasswd -a system_username  **         -    (eg **peter **[account name])
When  prompted   **password:    **        -                      (enter password for account)

Then **gksudo gedit /etc/samba/smbusers**

Insert the line    **system_username = "network username"**   [save and close]
```

But for the record I'm with garton  - why should we have to be doing things like this in 2007.
I think that Samba needs some serious updating to make it more user friendly for the masses that are about to migrate to Linux.

---

