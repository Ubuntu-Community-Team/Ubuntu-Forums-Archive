---
title: "Ubuntu just got slow"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by jasperyate on 2010-02-08
In the past few days ubuntu has gone slow on me. It occasionaly freezes completely in firefox. I was streaming some video online the other day from some site linked from project free tv, and thats probably when it started. I ran the ps aux command to see if i could identify any illicit processes, but i can't tell. point is i think i may have picked up something malicious somewhere along the way; does anyone know if any of these are bad?
```

root       815  0.3  0.0   2224   568 ?        S<s  09:54   0:00 /sbin/udevd --daemon
root      1289  0.0  0.0      0     0 ?        S<   09:54   0:00 [kpsmoused]
root      2118  0.0  0.0   1808   532 tty4     Ss+  09:54   0:00 /sbin/getty 38400 tty4
root      2119  0.0  0.0   1808   532 tty5     Ss+  09:54   0:00 /sbin/getty 38400 tty5
root      2122  0.0  0.0   1808   532 tty2     Ss+  09:54   0:00 /sbin/getty 38400 tty2
root      2123  0.0  0.0   1808   528 tty3     Ss+  09:54   0:00 /sbin/getty 38400 tty3
root      2124  0.0  0.0   1808   528 tty6     Ss+  09:54   0:00 /sbin/getty 38400 tty6
root      2193  0.0  0.1   2204  1128 ?        Ss   09:54   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2238  0.1  0.0   2040   676 ?        Ss   09:54   0:00 /sbin/syslogd -u syslog
root      2261  0.2  0.0   1968   540 ?        S    09:54   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2263  0.4  0.2   3732  2460 ?        Ss   09:54   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2286  1.0  0.1   3036  1324 ?        Ss   09:54   0:00 /bin/dbus-daemon --system
111       2426  1.3  0.4   6720  4712 ?        Ss   09:54   0:01 /usr/sbin/hald
root      2429  0.0  0.2  17448  2584 ?        Ssl  09:54   0:00 /usr/sbin/console-kit-daemon
root      2492  0.0  0.1   3328  1136 ?        S    09:54   0:00 hald-runner
root      2522  0.0  0.2   5176  2084 ?        S    09:54   0:00 /usr/lib/hal/hald-addon-dell-backlight
root      2525  0.0  0.1   5176  1792 ?        S    09:54   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/
root      2543  0.0  0.1   5172  1752 ?        S    09:54   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      2544  0.0  0.1   5172  1804 ?        S    09:54   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      2561  0.0  0.1   5188  1780 ?        S    09:54   0:00 /usr/lib/hal/hald-addon-cpufreq
111       2562  0.0  0.1   5032  1808 ?        S    09:54   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.so
root      2564  0.0  0.1   5180  1804 ?        S    09:54   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      2589  0.0  0.1   3556  1556 ?        Ss   09:54   0:00 /usr/sbin/bluetoothd
root      2626  0.0  0.1  15032  1780 ?        Ss   09:54   0:00 /usr/sbin/gdm
root      2628  0.3  0.3  15592  3332 ?        S    09:54   0:00 /usr/sbin/gdm
root      2634 19.2  3.4  61196 35436 tty7     Rsl+ 09:54   0:14 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth
root      2655  0.3  0.2  16432  2800 ?        Ssl  09:54   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/
root      2672  0.0  0.3   6932  3112 ?        S    09:54   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm
root      2677  0.1  0.1   4280  1920 ?        S    09:54   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
avahi     2682  0.0  0.1   2944  1480 ?        Ss   09:54   0:00 avahi-daemon: registering [jasper-laptop.local]
avahi     2683  0.0  0.0   2944   504 ?        Ss   09:54   0:00 avahi-daemon: chroot helper
root      2711  0.0  0.2   6108  2320 ?        Ss   09:54   0:00 /usr/sbin/cupsd
root      2739  0.0  0.1   4324  1160 ?        Ss   09:54   0:00 /usr/bin/system-tools-backends
daemon    2813  0.0  0.0   2096   448 ?        Ss   09:54   0:00 /usr/sbin/atd
root      2858  0.0  0.1   3480  1040 ?        Ss   09:54   0:00 /usr/sbin/cron
root      2984  0.0  0.0   1808   532 tty1     Ss+  09:54   0:00 /sbin/getty 38400 tty1
jasper    3029  0.4  0.2  25672  3016 ?        S    09:55   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
jasper    3042  1.0  0.7  26424  7200 ?        Ssl  09:55   0:00 x-session-manager
jasper    3097  0.0  0.0   4784   608 ?        Ss   09:55   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session
jasper    3100  0.0  0.0   3144   696 ?        S    09:55   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-sess
jasper    3101  0.5  0.1   3064  1188 ?        Ss   09:55   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --s
jasper    3106  0.8  0.5  94676  5240 ?        Ssl  09:55   0:00 /usr/bin/pulseaudio --start
jasper    3107  0.0  0.2   7844  2624 ?        S    09:55   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
jasper    3109  2.5  0.4   7700  4568 ?        S    09:55   0:01 /usr/lib/libgconf2-4/gconfd-2
jasper    3120  0.9  0.6  19140  6464 ?        Ss   09:55   0:00 /usr/bin/seahorse-agent --execute x-session-manager
jasper    3127  0.1  0.2   5616  2116 ?        S    09:55   0:00 /usr/lib/gvfs/gvfsd
jasper    3133  0.0  0.2  29584  2368 ?        Ssl  09:55   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/jasper/.gvfs
jasper    3142  2.3  1.2  32956 12904 ?        Ssl  09:55   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
jasper    3148  3.5  1.1  20584 11712 ?        S    09:55   0:01 metacity
jasper    3149  6.1  1.8  34916 18444 ?        S    09:55   0:02 gnome-panel
jasper    3150  0.5  0.8  22588  8200 ?        S    09:55   0:00 maximus
jasper    3151  5.4  1.5  53252 16004 ?        S    09:55   0:02 nautilus
jasper    3153  0.1  0.3   7844  3528 ?        S    09:55   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
jasper    3154  0.0  0.0   1872   504 ?        S    09:55   0:00 /bin/sh /usr/bin/awn-autostart
jasper    3157  1.2  1.1  68412 12084 ?        Sl   09:55   0:00 /usr/lib/evolution/2.26/evolution-alarm-notify
jasper    3161  0.1  0.3   8220  3072 ?        S    09:55   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
jasper    3162  3.9  1.1  23032 12060 ?        S    09:55   0:01 nm-applet --sm-disable
jasper    3163  0.9  0.9  24444  9308 ?        S    09:55   0:00 update-notifier --startup-delay=60
jasper    3166  0.5  0.7  16552  7232 ?        S    09:55   0:00 bluetooth-applet
jasper    3169  1.9  1.4  27872 14264 ?        S    09:55   0:00 python /usr/share/system-config-printer/applet.py
jasper    3171  1.7  1.1  27292 12108 ?        Ss   09:55   0:00 gnome-power-manager
jasper    3178 12.1  1.2  22860 12260 ?        S    09:55   0:04 /usr/lib/notify-osd/notify-osd
jasper    3180  1.1  0.3  33576  3508 ?        Ssl  09:55   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-act
jasper    3185  0.2  0.2   5940  2784 ?        S    09:55   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_
jasper    3253  2.3  1.5  44888 15500 ?        Sl   09:55   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFI
jasper    3259  2.0  1.3  26916 14056 ?        S    09:55   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --o
jasper    3317  0.0  0.0   1872   508 ?        S    09:55   0:00 /bin/sh /usr/bin/avant-window-navigator
jasper    3351  4.8  1.2  25520 13092 ?        S    09:55   0:01 awn
jasper    3353  3.5  1.1  24480 11736 ?        S    09:55   0:00 Awn System Monitor on -p /usr/share/avant-window-navigator/a
jasper    3357  3.6  1.8  36712 18900 ?        S    09:55   0:00 python /usr/share/avant-window-navigator/applets/weather/wea
jasper    3368  0.5  0.2  16548  2576 ?        Ss   09:55   0:00 gnome-screensaver
jasper    3370 13.1  1.5  33804 16136 ?        Rl   09:55   0:01 gnome-terminal
root      3375  0.1  0.0   2276   996 ?        S    09:55   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client
jasper    3383  3.1  0.8  70928  8996 ?        Sl   09:55   0:00 /usr/lib/evolution/evolution-data-server-2.26 --oaf-activate
root      3396  0.2  0.2   5640  2204 ?        S    09:55   0:00 /usr/lib/NetworkManager/nm-dispatcher.action
jasper    3420  0.0  0.0   2036   700 ?        S    09:55   0:00 gnome-pty-helper
jasper    3425  7.2  0.3   5916  3200 pts/0    Ss   09:55   0:00 bash
jasper    3481  0.0  0.1   2768  1032 pts/0    R+   09:56   0:00 ps aux
```

thanks for any help.

---

### Post by skvn on 2010-02-08
Hi. That's quite a long list and I'm not sure what to look for. There was one process with quite high cpu usage, but i don't know if that's normal for you.
```
root      2634 19.2  3.4  61196 35436 tty7     Rsl+ 09:54   0:14 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth
```
I think gdm is GNOME Display Manager, not sure what it does exactly, i think it has something to do with graphical login.

Maybe you could list the processes with 'top' the next time it freezes, that would make the list a bit easier to read since it sorts the processes by cpu usage for example.
Hope this helps :)

---

### Post by lovinglinux on 2010-02-08
It could be the vino-server behaving badly. Go to "System >> Preferences >> Startup Applications (aka Session)" and disable "Remote Desktop" then reboot. 

For optimizing Firefox see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). I would [disable Firefox feature that blocks attack sites and web forgeries](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2). Also [optimize the database](http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1).

---

### Post by dan1son on 2010-02-08
I'm relatively happy to see a thread like this since I've started having the same problem within the last few days.  I did an upgrade on Karmic with aptitude on Friday and ever since it's been incomparably slower.  

My system is an Apple TV with 256meg of RAM (I use it with XBMC on an HDTV) and it's been running great for a month or two, until I upgraded the system.  Now the machine swaps like crazy after bootup.  The hard drive just thrashes and thrashes whenever X launches and XBMC starts up.  Even if I load XFce instead, it thrashes like crazy.  

Not sure if I'm any help... but at least I'm experiencing the same problems.

---

### Post by lovinglinux on 2010-02-08
> **dan1son said:**
> I'm relatively happy to see a thread like this since I've started having the same problem within the last few days.  I did an upgrade on Karmic with aptitude on Friday and ever since it's been incomparably slower.  

My system is an Apple TV with 256meg of RAM (I use it with XBMC on an HDTV) and it's been running great for a month or two, until I upgraded the system.  Now the machine swaps like crazy after bootup.  The hard drive just thrashes and thrashes whenever X launches and XBMC starts up.  Even if I load XFce instead, it thrashes like crazy.  

Not sure if I'm any help... but at least I'm experiencing the same problems.

I had a similar problem when I upgraded from Jaunty to Karmic. In fact I did a clean install but kept my settings, because I have a separate home. So I decided to start from fresh and deleted ALL my personal settings from home. This was a viable solution for me, because I keep record of most important things I change in the system, so it wasn't hard to get my system up and running the way I like.

---

### Post by uygar.raf on 2010-02-08
Since I've upgraded my Ubuntu Server Edition 9.10 a couple of days ago, my server has been consuming extremely more memory.
It's a relatively small server with 1GB of RAM, and it used to consume 250-400 MB before the upgrade.

The thing is, I couldn't update it with *apt-get* which kept saying 3 packages were kept back. So I had to upgrade via *aptitude*... The kernel image, the modules etc. installed without a warning or a problem. And the system appears to run fine, but it just consumes about 650MB of RAM now... Without any stress on the server..

The difference doesn't seem right to me.
Also when I check the processes with htop, i see 83 instances of **/usr/sbin/console-kit-daemon** running.

Weird things are in motion, if you ask me..
Doesn't it indeed look so?

---

### Post by dan1son on 2010-02-08
Well I found the problem for me.  Apparently ureadahead has a couple of VERY nasty bugs, especially on low RAM systems like mine.  For the record, ureadahead is a fairly new package (within the last month) for Karmic.  

[https://bugs.launchpad.net/ureadahead/+bug/491943](https://bugs.launchpad.net/ureadahead/+bug/491943)
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

Both of those can cause the system to have minimal amounts of RAM left (or almost none in my case).  

I removed ureadahead and /etc/init/ureadahead*. These numbers are with gdm autostarting Xorg and XBMC.
```

With ureadahead
dan@atv-ubuntu910:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           241        233          8          0          1         21
-/+ buffers/cache:        210         31
Swap:         1054         71        982


Without ureadahead
dan@atv-ubuntu910:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           241        233          8          0          4         84
-/+ buffers/cache:        144         96
Swap:         1054          3       1051

```Hope that helps.

---

### Post by uygar.raf on 2010-02-09
Seems like after a couple of reboots, memory consumption's back to normal 250-450 MB range for me.
It was probably due to some sort of reconfiguration right after the upgrade.

But the excessive number of */usr/sbin/console-kit-daemon* processes running is still bugging my mind.

If anyone has an idea, please feel free to share with me.

---

### Post by dan1son on 2010-02-09
> **uygar.raf said:**
> Seems like after a couple of reboots, memory consumption's back to normal 250-450 MB range for me.
It was probably due to some sort of reconfiguration right after the upgrade.

But the excessive number of */usr/sbin/console-kit-daemon* processes running is still bugging my mind.

If anyone has an idea, please feel free to share with me.

Sounds like the second bug I posted.  [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

ureadahead has some serious memory problems.

---

### Post by iponeverything on 2010-02-09
For console-kit --

There is a long and entertaining thread on launchpad..

[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454)

---

