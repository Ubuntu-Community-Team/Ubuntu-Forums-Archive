---
title: "ntfs partition folder permissions"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2008-02-22
I have an ntfs disk partition that my thin client users (each on his own
account) can access. There is one folder that I want to password protect
but can't. I ran Nautilus under sudo and right-click on that folder to
see its permissions and everything is attributed to root. But when I
attempt to change the "others/folder access" setting to "none" (instead of
"create and delete files") it just pops right back to "create and delete
files".
I tried chmod 700 from terminal but it had no affect (though it didn't
return any error).
I have the opposite problem with the partition in general: my users
can't access the paritition until I use my password (the server is
turned off every night) because it belongs to root, but I'd like to
remove the password protection. When I try to switch the ownership to
something else, the setting just bounces back to root.
By the way, permissions work properly for folders on the Ubuntu
partition.
I appreciate the help.
David Clinton

---

