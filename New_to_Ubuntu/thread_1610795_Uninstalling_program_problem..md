---
title: "Uninstalling program problem."
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Omnomnom on 2010-11-01
I try and uninstall Eternal Lands data and everything else and it doesn't work. Could someone give me a command to remove it?

---

### Post by bioterror on 2010-11-01
> **Omnomnom said:**
> I try and uninstall Eternal Lands data and everything else and it doesn't work. Could someone give me a command to remove it?

```

sudo apt-get purge <insert your program here> with out <>
sudo apt-get autoremove

```

---

### Post by Omnomnom on 2010-11-01
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Then I did that and it's configuring it or something, I have no idea.

---

### Post by Hippytaff on 2010-11-01
Does purge and autoremove work after it configures?

---

