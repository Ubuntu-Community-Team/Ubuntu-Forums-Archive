---
title: "ubuntu wont to start-up"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by ireallydontcare on 2009-02-08
i get this message when i try to start ubuntu

* starting Avahi m/DNS/DNS-SD Daemon avahi-daemon [fail]
Timeout reached while wating for return value
Could not recieve return value from daemon process

then next line is something about cuspd and then it just does nothing

---

### Post by houstonbofh on 2009-02-08
Have you tried the other options in Grub?  Specifically, have you booted into memtest to make sure you haven't lost a stick, and have you tried to boot into the recovery console?

---

### Post by ireallydontcare on 2009-02-08
yeh i tried in recovery mode and it stops on

 * Setting up console font and keymap...

---

### Post by HermanAB on 2009-02-08
Avahi Daemon is a POS that you should probably just disable.  If you have a proper DHCP server on your LAN, then you don't need Avahi (or resolvconf, another POS that is best disabled).  The primary use of Avahi (and resolvconf) is for hooking an iPod to your laptop in standalone mode.  All it does is start broadcasting arps to see what is on the network and then Resolvconf will assign addresses in an effort to make things work.   However, if you have a properly configured LAN, then these services can louse things up.

Cheers,

Herman

---

### Post by ireallydontcare on 2009-02-08
how do i disable it?

---

### Post by houstonbofh on 2009-02-08
> **houstonbofh said:**
> Have you tried the other options in Grub?  Specifically, **have you booted into memtest to make sure you haven't lost a stick,** and have you tried to boot into the recovery console?
Try memtest.  A bad stick of ram can cause problems like this.  As soon as the system fills the memory to the bad point, it dies.

Also try booting a LiveCD and see if it comes up.  If so we look for disk issues.  While the program is question is not strictly necessary, the reason it is fails should be found, or you just move the problem without fixing it.

---

### Post by ireallydontcare on 2009-02-08
did the memtest and it says nothings wrong,

and yeh cant boot from cd cos this is a acer aspire one and it doesnt have a cd drive haha

---

### Post by houstonbofh on 2009-02-08
Make a bootable thumb drive and boot from that.

---

