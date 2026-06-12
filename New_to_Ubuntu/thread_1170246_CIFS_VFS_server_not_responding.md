---
title: "CIFS VFS: server not responding"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by theozzlives on 2009-05-26
K, I had problems getting my credentials file working until I installed smbfs. I've always gotten the following:

CIFS VFS: server not responding
CIFS VFS: No responce for cmd ### mid ###

Which didn't bother me before because after a sec or so it would shut down, or restart. Now it just locks up at that screen and I gotta use the power button to shut down. 

Do y'all have any answers???

---

### Post by DBrocks on 2009-05-26
Ahh yes I know that feeling. I had exactly the same problem. I'm not 100% sure, but I believe that the problem you are recieving is due to the fact that CIFS partitions arent being unmounted. I used this guy's script, and it seems to work fine for me. Should work for you.
 
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

