---
title: "Command Help"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by gobrien on 2009-06-25
Need some help with a command.

I have a second drive

/mnt/disk

and need to recursively change the group to admin while keeping me as the owner and no access for others?

---

### Post by aeiah on 2009-06-25
i always get uncomfortable with folder permissions, even nowadays. can you not use the gui? if not, then the command is chmod. do 'man chmod' and see what it says

---

### Post by sisco311 on 2009-06-25
```
sudo chgrp -R admin /mnt/disk
sudo chmod -R o-rwx /mnt/disk
```

---

### Post by Ocxic on 2009-06-25
"sudo chown -R gobrien:admin /mnt/disk" -- replace gobrien with the username of your account on the conmputer.

---

### Post by philcamlin on 2009-06-25
meh i dont like permissions either :D :popcorn:

---

### Post by gobrien on 2009-06-25
Will try these, thanks folks.

---

