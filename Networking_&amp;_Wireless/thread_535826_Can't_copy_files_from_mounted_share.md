---
title: "Can't copy files from mounted share"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by fineghal on 2007-08-27
I've successfully mounted a Samba share, but when I try to copy files from it with the cp command, I get an NT_Access_Denied error. ls -l shows that I have -rx as root, which is how it should be, and I've checked the windows machine, the user I'm logging in with should have read and execute rights.

The other odd thing is that another share from the same machine I have no issues with. 

Any ideas?

Edit: Actual error reads cp Cannot read file 'FILE', NT_ACCESS_DENIED

Using a graphical samba client also yields the error NT_STATUS_ACCESS_DENIED.

The admin account, the user account, and SYSTEM all have full rights on the windows machine.

---

