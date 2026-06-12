---
title: "Making MULTICAST Survive Reboots on wlan0"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by fejarama on 2007-02-03
Hello,

After troubleshooting Avahi for a while, I finally got it working when I discovered that multicast was not enabled for my wireless adapter (wlan0). Once I enabled it with:

```
$ sudo ifconfig wlan0 multicast
```

Avahi and zeroconf works fine.

However, the multicast flag does not survive reboots, and I'd like it to.

Any ideas?

The driver for my USB wireless adapter (a linksys wusb11 ver 2.6) is at76c503.

Thanks!

---

### Post by mrgrapefruit on 2007-02-04
i'm not sure of any direct way (don't know that much about ifconfig) but you could try ```
suco pico /etc/init.d/ifmulticast
```
Then in pico
```
#!/bin/sh
ifconfig wlan0 multicast
```

Then press:
ctrl+o
ctrl+x

Then type:
```
update-rc.d /etc/init.d/ifmulticast
```

good luck!

---

### Post by fejarama on 2007-02-04
Thanks for your reply. That seems like a fine solution, so I'll try it.

I was wondering: would putting the command into **/etc/rc.local** be appropriate? If so, where exactly would the command go? My never before modified /etc/rc.local looks like this:

```

#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
        if [ -x /etc/rc.local ]; then
                log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                log_end_msg $?
        fi
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

---

### Post by fejarama on 2007-02-04
I finally settled on a solution using cron. I added the following line to **/etc/crontab**:

```
@reboot root /sbin/ifconfig wlan0 multicast
```

Cron is awesome.

---

