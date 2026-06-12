---
title: "Add logic to nfs mounting process?"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by clarknova on 2017-02-11
Ubuntu 16.10 amd64

I have an nfs share that I mount automatically from fstab thus:

```
10.130.0.2:/mnt/RedMirror/  /mnt/2tb nfs defaults
```

My automatic backup directory is on this share, so I like having it mount automatically, otherwise the backup fails.

The down side to this is that if I try to boot the system when the nfs share isn't accessible (not home, network not connected, etc) then the boot process hangs indefinitely. I don't want to add the 'user' mount option, because as I mentioned, this would break the automatic backup to network.

Is there a way to add some logic to the mount process so that it won't attempt to mount the nfs share if I'm not on a certain network, such as 10.128.0.0/14? Or to add a timeout so that boot will continue even if the share isn't mounted? Or failing those options, is there a way to manually tell the boot process to continue even while the nfs is not mounted? I tried esc and ctrl-c, but neither was effective.

---

### Post by SeijiSensei on 2017-02-11
I'll suggest another option.  If your backup is run from a script, mount the device there before the backup runs.  You can include some logic to test whether you're on the correct network.  
```

#!/bin/bash
if [ "$(ping -c 5 10.130.0.2 | grep '100% packet loss')" != "" ]
then
    mount 10.130.0.2:/mnt/RedMirror/  /mnt/2tb
    [include the backup code here]
    echo "$(date) - Backup completed" >> /var/log/backup
    exit 0
else
    echo "$(date) - Cannot mount backup device" >> /var/log/backup
    exit 1
fi

```

---

