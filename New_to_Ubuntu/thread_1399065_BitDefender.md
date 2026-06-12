---
title: "BitDefender"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by iggy pop on 2010-02-05
I am running Ubuntu 9.10 (Karmic Koala), and i want to start using BitDefender. Only problem is when i visit the BitDefender site i can only find the version for small businesses?

---

### Post by abybaddi on 2010-02-05
No need for that. Presently you are no threat by virus under ubuntu.

---

### Post by warfacegod on 2010-02-05
Agreed. Anti-virus is almost totally pointless in Linux outside of servers. There have been two "viruses" found in the gnome-looks site recently but that's hardly cause for alarm. If you are concerned about potentially passing along Windows viruses to your friends that use Windows then ClamAV is your friend.

```
sudo apt-get install clamav
```

To update it you will need to open it as root:

```
gksudo clamav
```

I would use it to scan files you wish to email. If you want to scan your entire file system then feel free. Either way, just use it without root privileges.

---

### Post by iggy pop on 2010-02-05
Thanks for the info both.

---

