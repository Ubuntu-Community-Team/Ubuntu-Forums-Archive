---
title: "Where's the Samba Users Folder?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by rjmusto on 2008-05-05
I have Feisty running as a small file and print server and am using Webdmin to administer the Users, Groups and Samba settings.

However, the Users and Groups handling is not working correctly. Although they are all set up and show via Webmin in both Ubuntu and Samba, any workstation user appears on the Ubuntu box as a Guest, which means that Read, Write, List only works ok if I set it up for full access to the guest account. Samba does not seem to recognise the users.

Looking at the etc/samba folders, I can see no sign of the smbusers or smbpasswd files. Should they be there and if not where are they?  I'd like to check that they are indeed listed correctly in the Samba files.

What else should I be checking to make sure the Users and Groups are set correctly? Am I missing a Samba module perhaps?

Many thanks,
Ralph

---

### Post by superprash2003 on 2008-05-05
well i think you have found your problem..There should be a smbusers file.. you might want to setup samba again by following this guide [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by rjmusto on 2008-05-05
Thanks for the tip.

Despite Webmin claiming to do all this, it seems I did need to manually create the /etc/samba/smbusers file then add the users and enable them on the network - as per the guide.

Think I've got things running ok now.

Webmin is a handy tool - but needs to be used with care!

R

---

