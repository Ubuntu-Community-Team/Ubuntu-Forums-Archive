---
title: "Username and password when accessing a Windows XP smb share from Ubuntu."
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by JackSchitt on 2007-04-26
I'm currently a windows user. My brother is currently running Ubuntu (not sure of the version, but it's under 6 months old).

He needs to access a shared folder on my windows xp computer but it's prompting him for a user name and password. While the windows computer is password protected, the share is specifically set up not to be (The share permissions include "Full Control" to the group "Everybody" and the "Security" tab has the user "NETWORK" with "Full Control". Why is this and can it be fixed easily (i.e. via gui)?

It might be noted that the prompt occurs when trying to view all of the shares on the computer, not when attempting to browse to a specific share (i.e. clicking on the computer's name).

---

### Post by spd106 on 2007-04-27
Has your brother added himself as an smbuser?

To do this open a terminal and run this command, then enter a password, which will be the password used for accessing the shares.
```
smbpasswd -a
```

---

