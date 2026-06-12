---
title: "Cannot delete folders, access denied"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by brockolicosmique on 2014-03-06
Hello,

I am in the process of making a Ubuntu home server, and ran into some problems.

I have set up my shared partition to be available with Samba and NFS, I have chmod 777 the mounted partition as well, but whenever I copy folders to it from Windows or Mac, I am later unable to delete them using the server machine over terminal as I keep getting permission denied. I am however able to delete them using Windows, or Mac, regardless of which computer the files were copied from.

I'm not sure if something is wrong in my configuration or if there is a workaround... I have backed up a few hundred gigs of data already, and having to manage that through windows explorer to avoid those limitations is slow...

JF

---

### Post by papibe on 2014-03-06
Hi brockolicosmique.

The default samba authentication method tries to map the guest to one of the Linux users. When that fails, the user is usually log as:
```
user: nobody
group: nogroup
```
A few ideas:
[LIST]
[*]A simple solution would be to remove/rename/move the files using sudo.
[*]You could set samba to use always your user when creating files from any guest (check the options "force user" and "force group").
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by brockolicosmique on 2014-03-06
Thanks papibe! I should have thought of using sudo...

I tried forcing the user and group, but now I can't edit that partition anymore using windows as guest...

Sudo will do just fine.

Thanks!

---

