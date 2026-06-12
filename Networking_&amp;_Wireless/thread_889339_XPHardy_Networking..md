---
title: "XP/Hardy Networking."
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Grumblebum on 2008-08-14
Have a dual boot Vista/Hardy machine, both up to date and a XP, SP2 machine, up to date.  The XP and Vista machine work well together and can see all shares.

Have set up samba on the Hardy machine and all necessary shares on both boxes (XP/Hardy).  The XP machine can see all files in all shared folders on Hardy.  However, whilst the Hardy machine can see the Windows network and the Workgroup (by name, as well), it can't see the shares on the XP machine.  I have been working on this on and off for weeks now and it's driving me bonkers.  Have searched FAQs and forums and tutorials and infinitum.

Any information afforded would be much appreciated.  I really need to get this network working.

---

### Post by cariboo on 2008-08-14
Have you tries in the location bar of Nautilus:

```
smb://<windowscomputer>/<windowsshare> 
```

Where <windowscomputer> is the name of the windows computer (you do name your computers don't you> and <windowsshare> is the share name you have given your windows  directory.

Jim

---

### Post by Grumblebum on 2008-08-16
Tried that, thanks Jim.  All I got was a blank page.  Yes, the computers and shares are appropriately named.  I'm using Firefox rather than Nautilus as a browser, but that shouldn't make a difference.

I'd like to be able to see the shared directories in Windows explorer fashion, rather than one share at a time, as I assume using the browser with specific targets would provide.

Any help much appreciated.

---

