---
title: "Downgrade to previous samba"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by pksings on 2008-05-27
Hello all;

I have spent all the time I can on attempting to get the new version of Samba to let my Windows 98 VM access shares or a printer. 

I need to get rid of this version of Samba and go back to a previous version.

How do I first get a previous version? And then prevent the updater from writing over it with this one again?

Thanks very very much in advance.

Paul Kelly

The solution is to add the following to your smb.conf in the "global" section.

client lanman auth = yes
lanman auth = yes

Then re-create the password for each of your users, it's using a different hash to do it, that's why the old one doesn't work anymore. 

smbpasswd username (enter) 
or smbpasswd -a username (to add a new username)

stop and restart samba, /etc/init.d/samba restart.

Whammo, it works!

The fix was found on the samba users mailing list.

---

