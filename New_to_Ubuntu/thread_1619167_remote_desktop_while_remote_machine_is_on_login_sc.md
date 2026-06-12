---
title: "remote desktop while remote machine is on login screen?"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by bprins on 2010-11-11
Hi,

Apparently I want something impossible again..

I have a desktop machine which runs ubuntu10.04.
I have a laptop which runs ubuntu10.10.

When I try to connect from my laptop to my desktop via remote-desktop, while I have logged in on my desktop => no problems.

When I try to connect from my laptop to my desktop via remote-desktop, while I have NOT logged in on my desktop => access denied (connection closed).

I;ve tried to google the solution, but I am no expert on X.conf files or ssh.conf files so I am not really sure of what I am changing (I'll probably do more harm then good).

Who can give me some pointers?

Thanks in advance.

Regards,

Bas

---

### Post by CharlesA on 2010-11-11
If you are using the default remote desktop service, it doesn't start unless you are logged in.

Check out FreeNX or use a different VNC server.

---

### Post by bprins on 2010-11-11
Aha! thanks!

freenx does the trick.

---

