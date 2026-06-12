---
title: "Kernel update, wifi driver not working"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by itsjareds on 2009-08-04
I updated my kernel to 2.6.28-14-generic through the update manager, but now I can't seem to get my wireless interface to show up (ra0). I'm guessing this is because my wifi driver isn't being loaded, but it's listed in /etc/modules so that it starts up automatically. I still have my old kernel (2.6.28-13-generic), and wifi sitll works fine. Does anybody know why my driver might not be loading on a new kernel?

The driver is RT2870STA (Ralink), under Ubuntu Jaunty 9.04. Thanks.

---

### Post by itsjareds on 2009-08-06
Bump

I'm fine with my current kernel, but I like to keep up to date with my software. Anybody have ideas?

---

### Post by stderr on 2009-09-12
Did you have any success with this? I could be battling a similar issue with a new NIC with RT2870STA, whereby getting it to reliably automatically connect on startup is nigh on impossible. I haven't tried previous kernel versions yet though.

---

### Post by itsjareds on 2009-09-12
Nope, in fact I haven't visited on this subject for a few weeks until, ironically, 30 minutes ago in a new thread. It's #3 on my list.

[http://ubuntuforums.org/showthread.php?t=1264610]("http://ubuntuforums.org/showthread.php?t=1264610")

I thought my problem was that the driver would have to be installed on every single kernel version, but I know that this should not be a normal issue. Which kernel are you using? I have the driver working fine on 2.6.28-13-generic, if you want to try that one.

---

### Post by itsjareds on 2009-09-12
I was able to connect after installing the driver on my newer kernel. That'll start to get annoying :(

I wonder if I can uninstall the driver that was for my old kernel, and have my old kernel still connect.

---

