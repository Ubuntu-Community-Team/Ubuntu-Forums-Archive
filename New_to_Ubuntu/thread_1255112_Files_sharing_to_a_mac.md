---
title: "Files sharing to a mac???"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by powel212 on 2009-09-01
I have 2 Ubuntu machines one windows and one Mac running Leopard.

I have system-config-samba set up and I can share files back and forth between ubuntu and windows but I can not access the mac from the ubuntu boxes. I can grab files from ubuntu shares on the mac box but i can not access the shred folders on the mac from Ubuntu.

Anyone have this working.

I am sure I am just missing some configuration detail on the mac. I have already enabled folder sharing on the mac and have also turned on Samba on the Mac. If I look at my network shares from ubuntu I can see that the OSX box is registered in the router but i can not get access to it.

Any help is appreciated.

Powel

---

### Post by powel212 on 2009-09-10
In OSX settings - first enable file sharing under "sharing" - enable Samba and assign a password.

Then leave sharing settings and go to Settings "Accounts" 
Unlock it
click on guest account
click the check box "Allow guests to log into this computer"
and
"Allow guest to connect to share folder"

Should work now.

Mac OS is usually quite good at grouping settings together for ease of use, so I don't know why some of the share settings are under user accounts.

This works in Leopard but not in Snow. I still haven't figured out how to share files with Ubuntu in Snow Leopard. But I understand Snow is still full of bugs.

Powel

---

