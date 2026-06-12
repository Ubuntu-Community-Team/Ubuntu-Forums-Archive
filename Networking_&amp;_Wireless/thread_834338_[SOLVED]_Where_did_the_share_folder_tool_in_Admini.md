---
title: "[SOLVED] Where did the share folder tool in Administration go?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by pyjimbo on 2008-06-19
I set up two shared folders across two 7.10 Gutsy Gibbon installations with the shared folders tool in administration. I upgraded those two and added another two computers with fresh installs of 8.04 Hardy Heron. I could not find where to input the network name for Samba on the new installs of 8.04, thus they were WORKGROUP and buried in the Network hierarchy by default. I just wanted to click Network and see all my shares up front. I have that now but I had to edit the smb.conf file on the two new installs with the custom domain name.

Is the GUI solution still around or was it removed? It used to be System > Administration > Shared Folders.

It says so here for 7.10 Gutsy Gibbon.
[https://help.ubuntu.com/community/SettingUpSamba#head-8e150e1996272f3eb37363c960274baed221513e](https://help.ubuntu.com/community/SettingUpSamba#head-8e150e1996272f3eb37363c960274baed221513e)

---

### Post by jetsam on 2008-06-19
It was taken out because Samba sharing has been integrated with Nautilus for Hardy.  

The old tool is still available (for most people-- a few people have had trouble running it) if you open a terminal and type:
```
shares-admin
```

The Hardy way of sharing isn't the same as the Gutsy way of sharing, though.  You can use shares-admin to set your workgroup name and wins settings, but it won't see or list shares that you've set up through Nautilus.  I think the possible confusion this could cause is the reason why the tool was removed from the menus.  

There isn't really a supported gui way to set your workgroup name in Hardy.  It's a problem; hopefully a solution will be on its way.  Until then, editing the smb.conf works fine, but isn't exactly easy for new users.

---

