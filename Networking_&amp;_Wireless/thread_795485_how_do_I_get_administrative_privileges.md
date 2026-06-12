---
title: "how do I get administrative privileges?"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by user-unit on 2008-05-15
when I try to share a folder I get

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

its not asking me for my password so how do I get the administrative privileges to share my files?

---

### Post by ivze on 2008-05-15
Just installed samba? If so, reboot, and that will be fixed. Had the same bug. =)

---

### Post by uidb4056 on 2008-05-15
You should prefix your commands with 'sudo' whitout the quotes, it will ask you then your password and execute the commnads with admin privilileges.

---

### Post by ivze on 2008-05-15
> **uidb4056 said:**
> You should prefix your commands with 'sudo' whitout the quotes, it will ask you then your password and execute the commnads with admin privilileges.
As for me,
drwxrwx--T 2 root sambashare  4096 2008-04-22 16:03 usershares
.
A normal desktop user shall be in this group. NO sudo is needed. After samba sharing installation the user appears in this group after reboot - experimental result.

---

### Post by user-unit on 2008-05-15
> **ivze said:**
> Just installed samba? If so, reboot, and that will be fixed. Had the same bug. =)

the reboot fixed it.

---

