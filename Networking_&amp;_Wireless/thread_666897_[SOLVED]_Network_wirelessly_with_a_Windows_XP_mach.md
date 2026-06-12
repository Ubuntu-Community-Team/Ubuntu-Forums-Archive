---
title: "[SOLVED] Network wirelessly with a Windows XP machine?"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by 449 on 2008-01-13
I have a bunch of mp3s on my Windows computer's hdd. I need to get them on my Ubuntu computer's hdd. The Windows pc is wired to a router, whole the Ubuntu pc currently gets wireless internet from the router. How would I go about sharing files with the two machines? Thank you for your time and patience.

449

---

### Post by sqrt2 on 2008-01-13
That depends on what exactly you are planning to do. I suppose you want to use the Windows file sharing functionality to exchange files (the protocol's called SMB/CIFS, and NMB for resolving computer names to IP addresses). Now if you only want to copy files from and to the Windows box from your Ubuntu machine, everything should be set up already. I don't know about GNOME, but in KDE you'd simply have to type "smb:/" in the address box of a Konqueror session. GNOME certainly has similar functionality, just look for something named "Remote Places" or the like in your graphical file manager.

However, if you also want to be able to access the Ubuntu box from Windows, you'll have to setup Samba, which can be a bit tricky sometimes. Try a HOWTO like [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605).

---

### Post by 449 on 2008-01-13
I'm not quite sure exactly I'm trying to do.

My goal is to transfer files from the Windows pc to the Ubuntu pc.

---

### Post by sqrt2 on 2008-01-13
I see two practical ways of doing that. The first one is, you install an the OpenSSH server and use SFTP, which is easier to set up and encrypts the traffic, but makes authentication mandatory and requires you to install additional software on the Windows box. The second way would be to set up Samba, which allows you to use Windows file sharing ("My Network Places") and can be done without requiring authentiation, but is harder to set up.

If you choose the first way, open a terminal and type
[indent]sudo apt-get install openssh-server[/indent]
then install an SFTP client on your Windows box (for example the one from [http://winscp.net/](http://winscp.net/)), connect to the IP address of your Ubuntu box and authenticate with your Ubuntu username and password.

If you choose the second way, try the HOWTO I linked above.

---

### Post by 449 on 2008-01-13
Thanks for the quick responses. I will give the first a shot, and if that fails try samba. I'll mark this thread as solved.

---

