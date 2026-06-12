---
title: "Problems with SMB share permissions"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by plainzwalker on 2015-05-14
I have an ubuntu server set up as a media server for XBMC. I find myself having to go in, what seems like every day or every other day, using webmin and resetting the folder permissions for the share folder so that users can see/add/delete files from the share folder. Is there something that I can change so I do not need to keep doing this?

Thank you

---

### Post by SeijiSensei on 2015-05-14
Do you need to keep track of which users created which files?  If not, then I recommend reading up on the "[force user]("https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEUSER")" and "[force group]("https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEGROUP")" directives in smb.conf.

---

