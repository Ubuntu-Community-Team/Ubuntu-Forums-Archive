---
title: "[SOLVED] No Network Drives on Reboot!"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Redline21 on 2008-04-02
I have several network drives that I mount using cifs. They used to work fine, but now they are not mounted after a reboot. If I run "sudo /etc/init.d/networking restart" they are mounted after networking comes back up. Only things I have changed recently was removing evolution from the session startup and installing OpenSSH. Any ideas?

---

### Post by devurandom77 on 2008-04-15
Haven't personally used cifs, but if doing a networking restart solves the problem, then you probably have a chicken & egg problem in your startup.  It's possible that the cifs mounts are being attempted at boot, but some aspect of networking isn't quite ready at that time (e.g..: DNS, mDNS if you're using it, netbios, etc...)  Check your logs to look for failed attempts to mount your cifs volumes.  I assume that you've got these mounts in /etc/fstab.

What distro of ubuntu are you using and who's cifs packages?

In lieu of a networking restart, also try doing a "mount -a -t cifs" once the system is up and see if that mounts them.

---

### Post by Redline21 on 2008-04-16
Well I got it working before I read your reply which is good, but I didn't have a chance to try your suggestions. FYI, I am using Gutsy and I don't remember/know how to tell which cifs package. I am using fstab to mount the shares.

The solution (as far as I can tell) was something in my /etc/network/interfaces file. I edited it and the next time I rebooted my shares came up like they were supposed to! I'm not sure what I could have changed in it that would have fixed it. I added a couple routes and changed some routes to use a different interface and I removed some blank lines from the end of the file...maybe that was it. Anyway it is working like normal so I'm happy! :)

---

