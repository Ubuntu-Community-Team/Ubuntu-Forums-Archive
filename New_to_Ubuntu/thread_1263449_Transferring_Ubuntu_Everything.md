---
title: "Transferring Ubuntu Everything"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Doman on 2009-09-11
I just installed Ubuntu to a 16gb Flash drive and want to move everything from my current install on Ubuntu to that one.  Profile settings n' all - I don't need lessons for copy and paste =P.   How do I do it?

---

### Post by MelDJ on 2009-09-11
you could make a live cd of it using rmastersys or reconstructor and installing it on the pendrive

---

### Post by quinnten83 on 2009-09-11
> **Doman said:**
> I just installed Ubuntu to a 16gb Flash drive and want to move everything from my current install on Ubuntu to that one.  Profile settings n' all - I don't need lessons for copy and paste =P.   How do I do it?
Without lessons for copy & paste it's going to be difficult, since you need to copy your homedrive from the computer to the pendrive.
You can use synchronisity or unison to synchronize between copies, but a simple gksudo nautilus and then copy homefolder should do it.

---

### Post by talsemgeest on 2009-09-11
Something like ```
dd if=/dev/sda of=/dev/sdb
```

Where /dev/sda is the hard drive you want to copy from, and /dev/sdb is the one you want to copy to. 

However, the easiest, safest and best option would be to install Ubuntu onto the flash drive, then simply copy over the /home directory.

---

### Post by Doman on 2009-09-11
I mean I understand how to copy and paste.  I installed them both with separate partitions for /home, so does that mean I can just copy that over and everything'll transfer?

---

### Post by earthpigg on 2009-09-11
hi,

uummmmm....

create users with the same usernames. 

copy your /home folder over.

install all the same stuff from synaptic - the programs will use the settings and configurations that you just copied from your /home instead of their defaults.

done.

---

### Post by talsemgeest on 2009-09-11
> **Doman said:**
> I mean I understand how to copy and paste.  I installed them both with separate partitions for /home, so does that mean I can just copy that over and everything'll transfer?
Copy over the /home directory and you should keep your settings. You will still have to reinstall your apps, but their settings will remain intact.

---

