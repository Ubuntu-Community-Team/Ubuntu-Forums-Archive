---
title: "Share a partition"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by TheStealthDj on 2011-02-05
hi, i need help setting up sharing on my network, i have a desktop and laptop, ubuntu on the desktop and dual boot ubuntu/vista on laptop. my thoughts where ubuntu to vista was going to be hardest to set up, that is not the case. i can easily share files on the desktop partition in vista with samba but ubuntu to ubuntu wouldn't work together. I installed ssh 2 days ago and it worked for a short while, i created bookmarks to folders but now when i try to access them folders over ssh i get error: host key verification failed.  can someone please help?

---

### Post by eriktheblu on 2011-02-05
In what way do you identify the machine that contains the share?

I find it much more reliable to connect using IP rather than computer name. This of course makes it necessary to set a static IP on the machine.

---

### Post by TheStealthDj on 2011-02-05
yes i use ip 192.168.0.2 to connect

---

### Post by Morbius1 on 2011-02-05
If you are using Samba on both machines did you create any shares?

If you did then what happens when you run the following command:
```
nautilus smb://192.168.0.2
```

---

### Post by TheStealthDj on 2011-02-05
when i use nautilus smb://192.168.0.2 it opens up and i can see the partitions but gives error "Failed to mount windows shares" however i can access the print$ folder any suggestions?

---

### Post by TheStealthDj on 2011-02-05
anybody?

---

### Post by TheStealthDj on 2011-02-05
i have gotten the error message to change
"dbus error org.freedesktop.dbus.error.noreply"
this was done by deleting the known_hosts file, not quite sure what im doin

---

### Post by TheStealthDj on 2011-02-05
i have managed to solve the problem after deleting known_hosts i noticed there was two entries in passwords and encryption keys "192.168.0.2@thestealthdj" so i deleted them and now i can connect without problem.
thank you for trying to help!

---

