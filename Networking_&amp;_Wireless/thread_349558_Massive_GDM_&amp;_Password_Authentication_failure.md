---
title: "Massive GDM &amp; Password Authentication failure"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by lfloyd on 2007-01-30
Have lost all login capabilities.  Recovery mode cannot even find password file.  This happened after I edited the samba. cong, pam.conf, etc to try to conncet to windows business server.  I repeat ubuntu now has no user records.  How can I fix this?  Ubuntu is unusable at this point no terminal functions, no shell functions, no gdm functions, no kdm functions.  I am absolutely locked out of my own system.  It says root user does not exist.  Appreciate any help.  Thanks

---

### Post by spd106 on 2007-01-30
Oops, it sounds like you should have made copies of those critical files. You could try booting a desktop cd and attempt to replace the files, though this will probably be a non-trivial task.

This is a little out of my league, so I suggest you try to extract any important data files you have left (with a live/desktop cd), then re-install. You might want to retain the /home directory and have a look through it for any saved settings.

---

### Post by lfloyd on 2007-01-30
Thanks for the quick reply.  I thought about that but everytime i boot with the live cd i can't access my server filesystem.  And for the record ubuntu should keep backups of these files to default back to.  Everytime I have a failure its some type of gdm failure it should automatically default to previously saved good configuration to prevent this.  Thanks again I'm going to try and see if I can unlock my server filesystem with live cd for the first time.  Once I do that I just have to comment the changes I made.  But gettting to those files is the problem.

---

