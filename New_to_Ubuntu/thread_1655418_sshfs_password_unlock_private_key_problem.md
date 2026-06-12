---
title: "sshfs password unlock private key problem"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-12-29
how do i turn off the pic. In my sshd_config I changed 
PermitRootLogin no
# similar for protocol version 2
HostbasedAuthentication no

only changes made

---

### Post by lance bermudez on 2010-12-29
the computer in the pic is the local host

---

### Post by lance bermudez on 2010-12-29
i have a file to run at starup

#!/bin/bash
sshfs user@server:/home/user/folder /home/user/folder -p 22

i even tried
echo "password" | sshfs user@server:/home/user/folder /home/user/folder -p 22

both give me the pic

---

