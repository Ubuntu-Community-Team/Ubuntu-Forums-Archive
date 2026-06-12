---
title: "johnexpgn"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by johnexpgn on 2009-08-16
I recently tried to install AVG anti virus and the files appear to be corrupted but are there in the /filesystem/opt folder.
I want to remove this folder (as I have now successfully installed the Avast program) but it won't delete and comes up access denied.
Any idea how I can get rid of it?

---

### Post by credobyte on 2009-08-16
In terminal:
```
gksudo nautilus

```

Or:
```
sudo <command>
```

---

### Post by 3rdalbum on 2009-08-16
> **johnexpgn said:**
> I recently tried to install AVG anti virus and the files appear to be corrupted but are there in the /filesystem/opt folder.
I want to remove this folder (as I have now successfully installed the Avast program) but it won't delete and comes up access denied.
Any idea how I can get rid of it?

Credobyte is right. Another solution is to download the "nautilus-gksu" package, and then (after logging out and logging in again) you will have an option in the right-click menu to "Open as Administrator".

Almost anything outside your home directory can only be modified by root (the administrator account), to stop users from damaging the system or encroaching on other users.

I'll also point out that anti-virus is not necessary on Linux unless you want to find Windows viruses. The chance of you getting a virus on Linux is somewhere between "infinitesimal" and "mathematically impossible".

---

### Post by johnexpgn on 2009-08-16
Thanks for your replies!
I typed in "gksudo nautilus" in terminal and dragged the offending folder into deleted items.
The folder has now disappeared.
Success!

---

