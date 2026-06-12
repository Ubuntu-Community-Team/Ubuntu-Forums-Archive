---
title: "Active directory and groups"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by ivomans on 2007-08-02
I used to have a Ubuntu Edgy system working as a fileserver in combination with Active Directory to a Windows SBS 2003 server. After upgrade to Feisty I notice that the shares that are limited to certain usergroups are not accessible anymore.

I've got some shares working without any problem with: ```
valid users= @"Domain Users"
```I've got some other shares limited to custom-named groups that are defined in the SBS-server. These shares are now inaccessible: ```
valid users= @"engineering"
```When I list the groups with either 'wbinfo -g' or 'entget groups' I see the groups.

Any suggestion appreciated!

---

### Post by ivomans on 2007-08-02
I found a workaround, removing the "valid users" line, adding a line:
```
acl group control = yes
```Double-checked the group owners and did a "chmod" to all the files in the share.

I'm still curious why my old configuration stopped working, but this new approach got the advantage that all the access-limitations is now in the filesystem, for linux and samba users the same.

---

