---
title: "Grant service restricted port"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Dudsmacka2 on 2008-03-23
How could I go about granting permission to a service/user to a restricted (< 1024) port ?

---

### Post by nixscripter on 2008-03-23
As far as I know, the only way to do that is to run the process as root, bind the socket, and then setuid().

However, as a somewhat creative hack, you could do something creative with port forwarding within the local machine over ssh. Please read the ssh manual page first, but something like this might work (**don't just copy and paste this**): ```
 sudo ssh -NL 1234:localhost:**restricted-port** you@localhost
``` Then connect to port 1234 on the local machine, and ta da. You would need to have sshd running, though.

That's the best I can come up with.

---

