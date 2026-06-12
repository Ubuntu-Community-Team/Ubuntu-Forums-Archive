---
title: "Samba permissions"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by kook44 on 2007-12-06
Hi-
I have set up a samba server for the purposes of setting up a shared file server.  All of the connectivity seems to be working, but I am having trouble with accessing the share.
What I would like is to be able to administer the security through system users and groups, so i set 'security=user' in smb.conf.  I want the directory /var/share/public to have the permissions 774 u/g:root/publicshare.
I have set up a user 'mike' who is in group publicshare.  When I first tried to map the drive from WinXP, I was unable to log in.  I then ran 'smbpasswd mike' and was able to connect to the share, but was unable to access anything in it.  Only after I enabled rwx for others was i able to drop a file there, and it appeared u/g: mike/mike.

Strangely, if i log in as mike and run 'groups', publicshare does not appear in the list, however, if i execute 'groups mike' i do see publicshare there.

is this a samba problem, or a groups/permissions problem?

---

### Post by jonandrews on 2007-12-07
I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

It might help with your permissions problem....

---

### Post by DSK on 2007-12-07
> **jonandrews said:**
> I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

It might help with your permissions problem....

Nice quick guide but I have an ubuntu server and this does not help.  I have simular problem as mentioned in first post.  I can see the ubuntu share but get an error about permissions.

---

