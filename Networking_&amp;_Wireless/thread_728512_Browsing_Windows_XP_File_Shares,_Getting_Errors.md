---
title: "Browsing Windows XP File Shares, Getting Errors"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by zachwlewis on 2008-03-18
I've tried connecting to a networked windows machine from 7.10 (it works fine if I reboot to windows), but the computer doesn't appear in the MSHOME network.

I tried running nautilus as a root user, and when I try to connect to MSHOME, I get the following message:

```
Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Any idea what I need to do to browse windows shares?

---

### Post by Eiríkr on 2008-03-19
There's no need to run Nautilus as root, and in fact doing so will often generate oddball errors like the one you note.  

When you open Nautilus as a regular user and click Go -> Network, you should see at least the Windows Network icon, and ideally also computer icons for each machine in your Windows / Samba network.  Double-clicking the Windows Network icon should now show you an icon for your workgroup, in your case [font=courier]mshome[/font].  Clicking this should then show you again the icons for individual computers, if all is working correctly.  Clicking one of these should show you the individual shares available on that machine, and clicking one of these should then prompt you for your login credentials (username and password), and finally get you access to the shared files.  

If this doesn't work, it's likely due to trouble with hostnames, which is apparently a tricky area in Samba configuration.  Go to the Nautilus location bar (hit Ctrl+L or click View -> Location Bar if it's not showing) and type [font=courier]smb://IP.ADD.RE.SS[/font], replacing the caps with the numerical IP address of your Windows share server.  If that also fails, let us know and we'll go from there.  

HTH,

Eiríkr

---

### Post by zachwlewis on 2008-03-19
> **Eiríkr said:**
> Go to the Nautilus location bar (hit Ctrl+L or click View -> Location Bar if it's not showing) and type [font=courier]smb://IP.ADD.RE.SS[/font], replacing the caps with the numerical IP address of your Windows share server.

Worked like a charm. Thank you. Problem solved.

---

### Post by Eiríkr on 2008-03-19
Glad that helped, Zach!  :)  And if that resolves your issue here, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :D

Cheers,

Eiríkr

---

