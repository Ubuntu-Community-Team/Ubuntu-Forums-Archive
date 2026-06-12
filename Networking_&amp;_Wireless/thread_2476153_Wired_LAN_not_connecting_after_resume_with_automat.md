---
title: "Wired LAN not connecting after resume with automatic openVPN"
date: 2022-06-17
forum: Networking &amp; Wireless
---

### Post by marcel-i on 2022-06-17
Ubuntu 22.04.
When resuming from suspend, the Wired LAN connection is not activated. Manually activating it works, and the VPN connects to. 
I have added and OpenVPN configuration, that is selected in the "Automatically connect to VPN" setting on the General tab in de Wired network configuration in the Advanced Network Configuration tool.

When I remove the automatic connection to VPN, the Wired connection is activated on resume.
Anyone have an idea how to get this to work with the automatic VPN?

---

### Post by web-user on 2022-06-18
I think there should be an option in the NetworkManager in the GUI/CLI

---

### Post by marcel-i on 2022-06-20
Thanks, That option is already checked :)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290627&stc=1[/IMG]

---

### Post by marcel-i on 2022-06-22
So, after some tinkering with a script. I managed to get it to work.
Script:
```
#!/bin/bash

# Use this by making a symlink
# ln -s /home/username/scripts/99_resume-lan /lib/systemd/system-sleep/
#

case "$1" in
    pre)
        echo "Suspending!"
        ;;
    post)
        echo "Resuming from suspend!"
        sleep 4
        ifconfig enp0s31f6 down
        echo "Resuming from suspend! - Down with the lan"

        sleep 2
        ifconfig enp0s31f6 up
        echo "Resuming from suspend! - Up with the lan"
        ;;
esac

```

This script is symlinked in /lib/systemd/system-sleep.
Make sure to make it executable, and owned by root.

---

