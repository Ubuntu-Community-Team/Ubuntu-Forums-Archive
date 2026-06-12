---
title: "Does s2ram use the /etc/acpi scripts?"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by ResumeMan on 2007-11-28
Hi, I'm a mostly-newbie at Linux. I will try to make this relatively brief but fairly complete.

A few months ago I posted [this thread]("http://ubuntuforums.org/showthread.php?t=541549"), in which my shares were broken upon resuming from suspend; to use them I had to un-mount and then remount them. I never was able to solve the problem.

Since then I have done a fresh install of Gutsy and installed the latest version of s2ram from the Debian repos per [this]("https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238") bug report. s2ram works almost flawlessly, except that the shared folders still become inaccessible.

After reading [this thread]("http://http://ubuntuforums.org/showthread.php?t=365138"), I created and made executable the following two scripts:

1. /etc/acpi/suspend.d/20-smbfs-umount.sh 

```
#!/bin/sh

umount -t smbfs -a -l
```

2. /etc/acpi/resume.d/30-smbfs-mount.sh 
```

#!/bin/sh

mount -t smbfs -a
```

But still no shares upon resume from suspend. When I run them manually under sudo, they work.

So I was wondering if maybe s2ram doesn't use these scripts, and what they DO use,or what other workarounds I could use.

Thanks

---

### Post by ResumeMan on 2007-11-29
Nobody familiar with this issue? I know it's come up before...

---

### Post by njparton on 2007-12-14
You need to find a way of running the scripts as root automatically. I'd like to know this too.  

I have some scripts that power my rsync backups and I have to run them as root as I need to mount/unmount CIFS shares.

I use ```
sudo crontab -e
``` to do this with cron, but I'd like to find out how to run a script as root at shutdown or resart as cron is time, not event based.

---

