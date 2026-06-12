---
title: "New Document Samba User Permission Issue"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-24
We have setup a Samba server and at first every thing was working great, all user are able to connect and use all the file in the /share folder.

The issue is with new files & folder that are being create. These files have the "UserName":users -rw-r--r--. We want all new files to have root:user -rwxrwx---

Share section of Samba.conf
[share]
      writeable = yes
      path = /share
      write list = alex,becky,lisa,attorney,vince,sadmin,lori,@users
      force directory mode = 770
      force group = users
      force create mode = 770
      force user = root
      comment = Share File
      valid users = alex,attorney,becky,lisa,sadmin,vince,@users
      create mode = 770
      directory mode = 770

---

### Post by Eiríkr on 2008-03-24
Samba setups with multiple users and shared file access get a little messy.  You're actually better off configuring the underlying filesystem to handle how permissions are inherited, not least as this ensures consistency of permissions even when files and directories are created / accessed by users logged directly into the Ubuntu machine.  I'd recommend you read over [post=4496702]this post[/post], particularly the "Multi-user" section about setting up groups, group memberships, and filesystem permissions, and then make changes (using the [font=courier]chown[/font], [font=courier]chgrp[/font], and [font=courier]chmod[/font] commands as needed) to your [font=courier]/share[/font] directory permissions.

HTH,

Eiríkr

---

