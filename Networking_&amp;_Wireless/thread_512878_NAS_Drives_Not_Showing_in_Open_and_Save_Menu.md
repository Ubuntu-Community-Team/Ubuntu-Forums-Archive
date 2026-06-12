---
title: "NAS Drives Not Showing in Open and Save Menu"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Ride007 on 2007-07-29
Hello,

I have a Maxtor Shared Storage Plus 300Gb wired to a LinkSys Wireless G with SpeedBooster.  I have connected to the public and personal drive; there are two folder icons on the desktop that stay when I restart and I enter my password to connect to them.  The problem is that while I see the drives in the Network section under the desktop's Places menu I can't see the drives through any applications File Open or Save menus.  For example, when downloading in FireFox I would like to be able to select the network drive to save the file to but it does not appear in the list.  

How can I make my network drives behave like regular drives as I did in Windows XP?  Is this a limitation of Ubuntu?  Can it treat network drives as regular drives?

Still dual booting,

Ride007

---

### Post by Ride007 on 2007-07-30
Hello,

I've done some internet searches and have found the following link.
[COLOR="Blue"] 
[Automatically Mounting SMB Share]("http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/")
[/COLOR]
 I'll have to wait until I get home to try it.  I have some questions though.  

[LIST=1]
[*]Do I have to be logged on as "root" to execute these commands?  
[*]How do I  log on as root as I did not create a "root" login durring setup?  
[*]If my network drives have paths with smb in the path (eg. sbm://starfish/public) then do I need to do the "install" command?
[/LIST]

Thanks,

Ride007

---

### Post by Ride007 on 2007-07-30
Hello,

It doesn't work.  I can't do the mount command.  I get the following error:
```
mount: wrong fs type, bad option, bad superblock on //starfish/Public,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Anyone have any ideas?  I don't even know what this error means.  Help.  Please?

Ride007

---

