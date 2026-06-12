---
title: "Can't open shared folders on a Lan"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by sequimbob on 2014-07-01
I have a HP Pavilion g7-2069wm Notebook PC running dual boot Win7 and Ubuntu 12.04 and a HP G71-340US Notebook running Ubuntu 12.04. I have set up a lan (wired) between both Ubuntu systems.  I can ping both sides so I know the LAN is connected and working.  I have set up sharing on folders in both computers but when I browse the Network on either computer a screen opens up "Password required for share downloads on (the other computer).  It lists my user name, the workgroup and the block for  the password.  I have entered my admin password but that doesn't work.  I don't know what other password would be correct.  When I set up the sharing, it did not ask me to set a password any where. When setting up the sharing, I open up the appropriate folders properties, set permissions for both owner  to create and delete files, group and others to access files, I also checked " Apply Permissions to Enclosed Files". Then I checked the "Share this Folder" Box. I have made sure that the folders in question have 775 permissions.  Can anyone tell me where I am going wrong.

---

### Post by sequimbob on 2014-07-05
I found the problem.  I had not set up a Samba userid and passwd.  Once I did that.  I had full access.

---

