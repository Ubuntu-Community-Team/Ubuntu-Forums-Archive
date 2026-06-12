---
title: "Is there a GUI Mirroring Application?"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by held7over on 2011-08-30
Is there a GUI based version of rsync or some other application, that can be configured easily to mirror my primary computer's hard drive on a second computer's hard drive of the same size on my network, so that if I add/delete or update an application, or in /home I delete or create a file, etc., on my primary computer, my second computer looks exactly the same as the contents of the primary computer?  

And it would be nice if I could set the times of when this mirroring update is accomplished, rather than having to have both computers running all the time, kind of like a backup is set to run at a certain time each day or on certain days per week, etc....

Thanks! :P

---

### Post by haqking on 2011-08-30
> **held7over said:**
> Is there a GUI based version of rsync or some other application, that can be configured easily to mirror my primary computer's hard drive on a second computer's hard drive of the same size on my network, so that if I add/delete or update an application, or in /home I delete or create a file, etc., on my primary computer, my second computer looks exactly the same as the contents of the primary computer?  

And it would be nice if I could set the times of when this mirroring update is accomplished, rather than having to have both computers running all the time, kind of like a backup is set to run at a certain time each day or on certain days per week, etc....

Thanks! :P

[www.clonezilla.org](www.clonezilla.org)

---

### Post by papibe on 2011-08-31
Grsync is a GUI for rsync, however both are designed for mirror data. If I understand correctly, you need to create images of the partitions in your HD, including the bootable partition.

If that is the case, as haqking suggested it, you need clonezilla.

Regards.

---

