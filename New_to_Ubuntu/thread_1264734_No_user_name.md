---
title: "No user name"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by captgadget on 2009-09-12
Just installed Ubuntu 9.04 on winxp and I don't recall setting a user name, but I did set a password. Any suggestions on how I can log in to Ubunutu now?

---

### Post by khelben1979 on 2009-09-12
If you know your password for root you're saved. If not, reinstall. As root (or super user) you can create and delete users in your system as you wish.

---

### Post by NoaHall on 2009-09-12
ON windows xp? How? Using wubi? 

Recovery mode -> Root Shell -> useradd USERNAME

---

### Post by mcduck on 2009-09-12
> **captgadget said:**
> Just installed Ubuntu 9.04 on winxp and I don't recall setting a user name, but I did set a password. Any suggestions on how I can log in to Ubunutu now?

If you can boot into recovery mode (I'm not sure if Wubi-installs have that option, I've never tried Wubi), all you have to do is select the root shell option when asked what you want to do, and then tun "ls /home". This will list all user home directories, and since the home directory is the same as the user name, it will tell you the username.

After that just run "reboot" to restart Ubuntu, and use the user name you just found to log in.

---

### Post by lisati on 2009-09-12
I can't remember the exact details with Wubi-based installations (it has been a while since I used it) but the "standard" installer asks for your full name, and uses a lower-case version of your first name as a default user name.

---

### Post by captgadget on 2009-09-12
Thanks, I just formatted and reinstalled. Nice not having anything installed yet.

---

