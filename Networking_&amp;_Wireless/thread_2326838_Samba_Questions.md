---
title: "Samba Questions"
date: 2016-06-05
forum: Networking &amp; Wireless
---

### Post by LVCNSOL on 2016-06-05
Hi all,

I have set up a headless Ubuntu server to use for media and have been struggling to get Samba shares working on Windows.

What I want to know is why can I not use my user details that I use to login to the server as my Samba user? I created a new user and added them to a group called "smbgrp" and Windows can access the share no problem. However if I add my login user to the same group Windows does not allow access to the share?

Any reason for this? I don't want to use different credentials for my shares.

Secondly, how important is it to have a user login for my shares on my home network? Can I not just have an unsecured share instead?

Thirdly, if I mount an entire HDD and share it why can I not write to it? Seems I can write to folders but not mounts? Is there a way around this?

Thanks!

---

### Post by bab1 on 2016-06-05
> **PseudZ said:**
> Hi all,

I have set up a headless Ubuntu server to use for media and have been struggling to get Samba shares working on Windows.

What I want to know is why can I not use my user details that I use to login to the server as my Samba user? I created a new user and added them to a group called "smbgrp" and Windows can access the share no problem. However if I add my login user to the same group Windows does not allow access to the share? 

Any reason for this? I don't want to use different credentials for my shares.

If you have a Ubuntu user that you want to be able to access the Samba shares you need to add that user to the Samba database using ```
sudo smbpasswd -a <user>
```...where <user> is the name of your user. 
> 

Secondly, how important is it to have a user login for my shares on my home network? Can I not just have an unsecured share instead?

You can have anonymous (guest access) shares.  The default user becomes *nobody* and the group is *nogroup*. 
> 

Thirdly, if I mount an entire HDD and share it why can I not write to it? Seems I can write to folders but not mounts? Is there a way around this?

Thanks!
You always share a directory, even if it is the root directory of a partition that spans the entire HDD space.

---

