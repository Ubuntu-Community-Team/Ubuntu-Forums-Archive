---
title: "[SOLVED] vsftpd and file permissions"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by bsh on 2007-10-21
I have installed vsftpd on my own server, and set up a few thigs. i can log in with my own local username and get into my home directory, and i'm not jailed, so this is good.
i have also set up another "general" local user to access the ftp. the home directory is /home/ftp, but this is a smbolic link to an other directory which has more space (since the /home is very small). this user is chrooted into this directory. local_umask is 022.
i can login via this user and upload and download fine.
but there is a problem: regardless of what access permissions i give to files in this user's home, the user can do just about anything with the files. i gave read only permissions, changed the owner of existing (static) files to root etc., yet the user can delete these.
what i want to do is: to have a read-only folder (download things from here), to have a read+write folder (for uploads), and a static "welcome message", a simple text file, which should be read-only, and should not be modified or deleted by this user.
can anyone tell me how to do this, coz all my efforts were unsuccessful.
thanks

---

### Post by bsh on 2007-10-21
never mind, i solved it.
i was trying to apply permissins to the symlink and not to the actual files/folders.
seems to be working now.

---

