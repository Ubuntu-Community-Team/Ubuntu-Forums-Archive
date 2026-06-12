---
title: "Places -&gt; Network never asks for a password, unless smbclient command is used"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by rainwalker on 2007-10-24
I'm copying stuff from my current computer to a Windows box via ethernet, and I've found something peculiar; The drive I'm copying the files to is protected by a password, and the only time I'm ever presented with the opportunity to enter one is when I use the command line to copy the files. If I don't, I can't browse to the drive by going Places -> Network and I can't ping it either. What I'm left doing is keeping a terminal open running smbclient, but using the GUI to copy the files over.

It's nice to have a GUI to handle this, but what's the use if the GUI never asks for a password?

---

### Post by eugo on 2007-10-24
It is possible that when you entered  the password the first time (using smbclient), it was stored in some temporary cache. I don't think this is some out-of-the-box windows share exploit.

---

### Post by rainwalker on 2007-10-24
Well, yeah, but I mean what's the point in having the GUI if I have to use the command line to gain access to the drive anyway?

---

### Post by eugo on 2007-10-24
After next reboot, try using Nautilus first (smb://computername). This way it should ask you the GUI way. Or even add a shortcut to the desktop.

---

### Post by rainwalker on 2007-10-24
I've used the GUI, and it never asks for a password. 
If I don't use the smbclient command before I use the GUI, then I can't access the drive because the only time it aska for a password is with the command.

---

