---
title: "Using Grsync to clone a partition"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-13
I had a drive with multiple 10gb partitions on it and I tried to clone an install of 8.10 to another partition to see what would happen.  The cloning seemed to work okay, but I wasn't able to login to the newly cloned installation, so it seems like the password data was corrupted.  Does anyone have an idea of what might have gone wrong?  Is something wrong with my drive or is rsync simply not the right tool for the job?

---

### Post by DGortze380 on 2009-06-13
> **learningcurb said:**
> I had a drive with multiple 10gb partitions on it and I tried to clone an install of 8.10 to another partition to see what would happen.  The cloning seemed to work okay, but I wasn't able to login to the newly cloned installation, so it seems like the password data was corrupted.  Does anyone have an idea of what might have gone wrong?  Is something wrong with my drive or is rsync simply not the right tool for the job?

use dd for bitwise copies, not rsync.

example:

```

dd /dev/sda1 /dev/sda3

```

---

### Post by jbrown96 on 2009-06-13
> **learningcurb said:**
> I had a drive with multiple 10gb partitions on it and I tried to clone an install of 8.10 to another partition to see what would happen.  The cloning seemed to work okay, but I wasn't able to login to the newly cloned installation, so it seems like the password data was corrupted.  Does anyone have an idea of what might have gone wrong?  Is something wrong with my drive or is rsync simply not the right tool for the job?

You will probably need to run Grsync/rsync as root. Passwords are stored in /etc/shadow, to which only root has access.
I've used rsync to copy installations and never had problems, so hopefully it's just a root problem.

---

