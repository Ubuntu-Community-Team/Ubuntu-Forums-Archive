---
title: "home networking shared folder. ideas?"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2007-02-07
hello. I have a home network that consists of one computer running kubuntu/kde-core, another read OSX, and two computers running Windows XP. The wireless router in between is a Linksys WRT54G with Thibor 15c firmware. I would like to set up a shared folder that all computers have read/write access to. What would be the best way to set this up?

Thanks!

---

### Post by etienne.navarro on 2007-02-07
You could do this by either creating a SMB (samba) share, which is a Microsoft type share, on whichever machine you want. All OSes support SMB so its a matter of which machine has the hard drive space to share.

If you want to create the SMB share on Kubuntu, follow this:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+smb+kde](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+smb+kde)
or look for other solutions in the forums.

In OS X, go to System Preferences, then Sharing and configure it there.
In WinXP, make sure you have file sharing enabled (go to Network Wizard maybe), and then to share the folder you want, just right click on it and select sharing.

Another option would be to use iFolder ([www.ifolder.com)]("http://www.ifolder.com%29").

---

