---
title: "'sudo' and 'at'"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by aatyler on 2009-10-14
I have a question. I started using the 'at' command today to schedule downloads and backups to happen at night when I discovered that if do:
 
```
sudo at <whenever>
```
 
I'm never propmpted to enter my password and the command is run as root. I thought maybe it was because I had recently used sudo in the same shell so I did a reboot and found that it did the same thing. Is this normal for at? Isn't this a possible security hazzard?

---

### Post by falconindy on 2009-10-14
I just tried this and I was prompted for a password. Is it possible your last sudo access hadn't timed out yet?

---

### Post by mocoloco on 2009-10-14
I'm prompted for a password.  Maybe you tweaked something at one point. What's in your sudoers file? Run sudo visudo.

---

