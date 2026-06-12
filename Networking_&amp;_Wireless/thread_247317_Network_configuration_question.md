---
title: "Network configuration question"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by Guimas on 2006-08-30
Due to some problems with VMWare, I have to run ethtool to turn off tso (TCP Segmentation Offload), so I can transfer files between my host and guest in VMWare at a normal speed.

My question is: how to set tso off permanentely? I have to run 'sudo ethtool eth0 -K tso off' every time I boot the computer, before I run my virtual machine in VMWare. Is there a config file to set this off?

Thanks in advance, 

Guimas

---

### Post by NeTo on 2006-09-26
I couldn't figure this out either, so I decided to add a init.d script to do the job.

The code for the script would be something like:```
#! /bin/sh
# /etc/init.d/tso-disable

# Disable TSO (TSP segmentation offloading) for eth0

. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Disabling TSO for eth0..."
    ethtool -K eth0 tso off >/dev/null 2>&1
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Enabling TSO for eth0..."
    ethtool -K eth0 tso on >/dev/null 2>&1
    log_end_msg $?
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/tso-disable {start|stop}"
    exit 1
    ;;
esac

exit 0

```

You can save that to a file (eg: /etc/init.d/tso-disable) and set it to run at startup with:```
sudo update-rc.d tso-disable defaults 25
```That would disable TSO soon after networking is started.

Btw, I dunno if those /lib/lsb/init-functions work for anything besides Ubuntu.

---

### Post by JaminBenny on 2006-09-27
I'm trying to get Solaris 10 x86 ](*,) as a VM on VMWare Server 1.0.1 running on Dapper.  The hardware is an older 4 CPU Compaq server.

The install seems to hang, and many posts indicate that the thing to do is disable TCP Segmentation.  
Howerver, I get this error:
"Cannot set device tcp segmentation offload settings: Operation not supported"

Are you using something other than auto for the eth0 configuration in /etc/network/internface file?

---

