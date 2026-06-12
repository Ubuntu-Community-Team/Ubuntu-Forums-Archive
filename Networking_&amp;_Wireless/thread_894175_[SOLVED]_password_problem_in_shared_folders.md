---
title: "[SOLVED] password problem in shared folders"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by wolfen69 on 2008-08-19
i am finally able to see shared folders between laptop and desktop. i made a shared folder on my laptop that can be gotten into from my desktop. however, when i try to access folders on my desktop from my laptop, it asks for a password. nothing i try will get me in. any ideas? 

i set samba passwords on both computers with ```
sudo smbpasswd -a username
```  thanks.

---

### Post by cariboo on 2008-08-19
This might be a stupid questions but are the computer passwords and the smb passwords the same?

Jim

---

### Post by wolfen69 on 2008-08-19
the computer passwords are different, but the smb passwords are the same.

---

### Post by wolfen69 on 2008-08-19
also, why does my linux only network show up in windows network? shouldnt 2 linux machines see each other outside of windows network?

---

