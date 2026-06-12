---
title: "SSH Timeout over wireless"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by jgallen23 on 2008-06-10
I'm having issues connecting to my computers over ssh.  I can connect to my desktop over ssh when I'm connected over the wire, but not when I'm conected over wireless.  I can, although, connect to smb and ping over wireless
Here is my debug log:
```

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug1: channel 0: free: client-session, nchannels 1
Read from remote host jga1: Connection timed out
Connection to jga1 closed.
debug1: Transferred: stdin 0, stdout 0, stderr 78 bytes in 932.8 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.1
debug1: Exit status -1

```

anybody have any ideas?
I'm running ubuntu 8.04

---

### Post by jgallen23 on 2008-06-14
bump....nobody has any ideas?

---

### Post by jgallen23 on 2008-06-25
still no ideas ?

---

### Post by bellani on 2008-07-08
Have the same situation with a ubuntu 8.04 64 bit in a Hp pavillion dv2000, and a bitchy Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by jgallen23 on 2008-07-08
I got it finally working by disabling the restricted wireless driver.

---

