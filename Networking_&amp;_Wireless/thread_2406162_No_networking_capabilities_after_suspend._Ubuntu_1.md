---
title: "No networking capabilities after suspend. Ubuntu 18.04.1 LTS - HP Pavillion"
date: 2018-11-16
forum: Networking &amp; Wireless
---

### Post by mintyfresh2 on 2018-11-16
Hi every, I'm a new Linux users. I've actually installed Linux in preparation for a new work opportunity and I'm having some issue I'm not sure how to resolve. It seems to be a software issues based on the fact that if I fresh boot my device. Everything works great. Go to bed wake up to continue what I was doing and I can't user the internet. Can someone please advise me on how to resolve this issue?

Using the 'IP LINK SHOW' command. I'm able to see that the state of the wireless card is UP but the mode has been changed to DORMANT. 
Using the 'LSPCI -k' command. I see the following:

08:00.0 Network Controller: broadcom Limited BCM43142 802.11b/g/n (rev 01)
           Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n
           Kernel driver in user: wl
           Kernel modules: wl
Using the 'sudo service network-manager restart' command. I see that the service is restarted in the top right of my screen the network symbol goes from '?' to '...' but then ends up back at '?' which is no good. 

When I do a fresh restart, the process works fine but I have no idea what processes control the networking operations as I'm just beginning to learn about linux. 


Two things I'd really appreciate. 
1) Understanding where I can learn about the process from boot to networking capabilities so I can fix similar issues on my own in the future. 
2) The fix. 

Thanks,

---

### Post by praseodym on 2018-11-17
Try this script
```

sudo touch /lib/systemd/system-sleep/wakeon_suspend.sh
```
Add to this file
```

#!/bin/sh
case $1/$2 in
  pre/*)
    echo "aktivate $2..."

## Network-Manager stop, unload modules
     /bin/systemctl stop network-manager.service
      /sbin/modprobe -rf wl
#       /sbin/modprobe -rf [LAN/WLAN- or other modules]
    ;;
  post/*)
    echo "wakeup from $2..."
## load modules, Network-Manager start
     /sbin/modprobe wl
#     /sbin/modprobe [LAN/WLAN- or other modules]
       /bin/systemctl start network-manager.service
    ;;
esac
```
and set the exec flag

```
sudo chmod a+x /lib/systemd/system-sleep/wakeon_suspend.sh
```

---

