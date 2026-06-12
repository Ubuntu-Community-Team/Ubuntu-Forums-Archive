---
title: "No netroot available in recovery boot mode"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by japhyr on 2009-10-06
Hello,

I am trying to complete an installation of 8.04.3 on an old Dell Optiplex GX260.  The installation went fine, until I ran the updates after installation.  The updates did not complete properly, and now the monitor is blank after I boot.

I have booted into recovery mode from the grub menu, but there is no netroot option, so I have not been able to fix the updates.  Does this happen because it is not connecting to the internet?  Is there a way to get connected from the command line?  "sudo /etc/init.d/networking restart" does not work, and the computer is hooked up to a wired internet connection.

---

### Post by sisco311 on 2009-10-06
try:
```
dhclient eth0
```

---

### Post by japhyr on 2009-10-06
That is exactly what I needed.  Thank you!

---

