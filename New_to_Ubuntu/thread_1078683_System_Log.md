---
title: "System Log"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by furialis on 2009-02-23
Can I comment out everything in the syslog.conf file?

---

### Post by Cypher on 2009-02-23
I believe if you do that, any and all warnings and errors will be sent to the console. Since you're in the GUI you will not see them, but if you switch to ALT-F7 console port, you'll see them.

Unless you're running of space in your /var directory there's no real reason to clear out the syslog.conf file. You can always delete the old logs to make room..

---

### Post by Tek-E on 2009-02-23
Can I ask why you would want to?

---

### Post by furialis on 2009-02-23
I'm trying to get Ubuntu to write as little as possible to the disk. I'm running off a USB drive.

Edit: I have /tmp mounted to RAM at startup, looking for more things like that.

---

### Post by furialis on 2009-02-24
Shameless bump.

So is it OK to comment out everything in that file? I'd like to shut off all logging that isn't essential to normal operation. Also, if anyone has any tips on how to stop Ubuntu from writing to disk for any reason, I'd like to hear it.

---

