---
title: "problems with pivot root on nfs-mounted file system"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by lusth on 2008-02-28
Hi all,

I'm having a problem attempting to do a pivot_root on an nfs mounted file system.
This is a step twoards my ulitmate goal of a thin client wireless notebook.

I'm essentially running the commands listed in the pivot_root man page:

# portmap
# mount beastie.cs.ua.edu:/opt/ltsp/i386/ /mnt
# killall portmap
# cd /mnt
# pivot_root . old_root
# exec chroot . sh -c 'umount /old_root; exec /sbin/init' \
> < dev/console > dev/console 2>&1

I run these commands as root. All succeed until the last.

I get the following error from the exec chroot command:

bash: dev/console: Permission denied

On beastie, ls -l /opt/ltsp/i386/dev/console yields:

crw------- 1 root   tty    5,   1 2008-02-06 15:30 console

I suspect the problem is I'm not root anymore on the
new root system. Any ideas on how I should proceed?

john

---

