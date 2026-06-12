---
title: "External drive not recogised on start up."
date: 2011-05-06
forum: New to Ubuntu
---

### Post by aaron76 on 2011-05-06
I have noticed recently that whenever I restart or boot my laptop, my Seagate FreeAgent drive is not showing up in my system.
Now, it does work and show up after I turn the drive off and on again (which I don't like doing by the mains supply) so it's not a compatibility issue.
Is there a start up setting I am missing? The drive worked fine on start up in 10.10. This only started after I installed 11.04.
Thanks

---

### Post by Mr Stoozer on 2011-05-06
Check your fstab file. You can auto-mount the drive on boot.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

For a GUI, try installing **ntfs-config** (available in the ubu repos)

---

### Post by aaron76 on 2011-05-07
Thanks for that. It will take me a while to understand the help document, but I'll give it a go.

---

