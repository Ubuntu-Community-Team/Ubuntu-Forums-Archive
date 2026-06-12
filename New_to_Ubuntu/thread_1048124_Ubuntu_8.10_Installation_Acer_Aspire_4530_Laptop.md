---
title: "Ubuntu 8.10 Installation: Acer Aspire 4530 Laptop"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Shippou on 2009-01-23
Hello...

I have tried installing Ubuntu 8.10 on this laptop (owned by my friend). But then there is one problem: all applications launched somewhat "flicker" (you know, the feeling when you're CPU is @ 100% or you're out of RAM).

Computer Specs:
3GB RAM
AMD Turion X2 (2 Cores)
NVIDIA GEForce 9100m

Btw, the computer behaves like this: when one core is running at 100%, the other is running at 0%, and vice versa. Also, they tend to switch places after 30 seconds or so, with one CPU always at 100% and the other at 0%.

Please help.

---

### Post by mikewhatever on 2009-01-23
Can you post the output of <ps -aux> here.

---

### Post by 3rdalbum on 2009-01-23
Probably an easier command would be:

```
top
```

That should tell us what is using 100% of one of your cores.

If you have a single-threaded program that is using as much processing power as it can, then it's normal to see the 100% shift from one core to another - it's a kind of level-wearing function. If you're running a multi-threaded program or a couple of single-threaded programs you should see different core useage.

---

### Post by Shippou on 2009-01-23
Sorry for the late reply. Here are the outputs:

```

jidelica@jidelica:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   3056  1884 ?        Ss   09:32   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   09:32   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   09:32   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   09:32   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   09:32   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   09:32   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   09:32   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   09:32   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   09:32   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   09:32   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   09:32   0:00 [khelper]
root        51  0.0  0.0      0     0 ?        S<   09:32   0:00 [kintegrityd/0]
root        52  0.0  0.0      0     0 ?        S<   09:32   0:00 [kintegrityd/1]
root        54  0.0  0.0      0     0 ?        S<   09:32   0:00 [kblockd/0]
root        55  0.0  0.0      0     0 ?        S<   09:32   0:00 [kblockd/1]
root        57  0.0  0.0      0     0 ?        S<   09:32   0:00 [kacpid]
root        58  0.0  0.0      0     0 ?        S<   09:32   0:00 [kacpi_notify]
root       184  0.0  0.0      0     0 ?        S<   09:32   0:00 [cqueue]
root       188  0.0  0.0      0     0 ?        S<   09:32   0:00 [kseriod]
root       233  0.0  0.0      0     0 ?        S    09:32   0:00 [pdflush]
root       234  0.0  0.0      0     0 ?        S    09:32   0:00 [pdflush]
root       235  0.0  0.0      0     0 ?        S<   09:32   0:00 [kswapd0]
root       277  0.0  0.0      0     0 ?        S<   09:32   0:00 [aio/0]
root       278  0.0  0.0      0     0 ?        S<   09:32   0:00 [aio/1]
root      1294  0.0  0.0      0     0 ?        S<   09:32   0:00 [ksuspend_usbd]
root      1297  0.0  0.0      0     0 ?        S<   09:32   0:00 [khubd]
root      1327  0.0  0.0      0     0 ?        S<   09:32   0:00 [ata/0]
root      1329  0.0  0.0      0     0 ?        S<   09:32   0:00 [ata/1]
root      1331  0.0  0.0      0     0 ?        S<   09:32   0:00 [ata_aux]
root      2074  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_0]
root      2075  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_1]
root      2076  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_2]
root      2077  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_3]
root      2078  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_4]
root      2079  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_5]
root      2159  0.0  0.0      0     0 ?        S<   09:32   0:00 [scsi_eh_6]
root      2160  0.0  0.0      0     0 ?        S<   09:32   0:00 [usb-storage]
root      2344  0.0  0.0      0     0 ?        S<   09:32   0:00 [kjournald]
root      2520  0.0  0.0   2452   972 ?        S<s  09:32   0:00 /sbin/udevd --d
root      3137  0.0  0.0      0     0 ?        S<   09:32   0:00 [kpsmoused]
root      3558  0.1  0.0      0     0 ?        S<   09:32   0:01 [ath9k]
root      4498  0.0  0.0      0     0 ?        S<   09:32   0:00 [kjournald]
root      4749  0.0  0.0   1780   536 tty4     Ss+  09:32   0:00 /sbin/getty 384
root      4750  0.0  0.0   1780   536 tty5     Ss+  09:32   0:00 /sbin/getty 384
root      4753  0.0  0.0   1780   540 tty2     Ss+  09:32   0:00 /sbin/getty 384
root      4754  0.0  0.0   1780   540 tty3     Ss+  09:32   0:00 /sbin/getty 384
root      4758  0.0  0.0   1780   532 tty6     Ss+  09:32   0:00 /sbin/getty 384
root      4945  0.0  0.0   2308  1252 ?        Ss   09:32   0:00 /usr/sbin/acpid
root      4976  0.0  0.0      0     0 ?        S<   09:32   0:00 [kondemand/0]
root      4978  0.0  0.0      0     0 ?        S<   09:32   0:00 [kondemand/1]
syslog    5065  0.0  0.0   2012   704 ?        Ss   09:32   0:00 /sbin/syslogd -
root      5116  0.0  0.0   1940   544 ?        S    09:32   0:00 /bin/dd bs 1 if
klog      5118  0.0  0.0   3504  2348 ?        Ss   09:32   0:00 /sbin/klogd -P
108       5141  0.0  0.0   3004  1280 ?        Ss   09:32   0:00 /bin/dbus-daemo
avahi     5163  0.0  0.0   2888  1484 ?        Ss   09:32   0:00 avahi-daemon: r
avahi     5164  0.0  0.0   2888   668 ?        Ss   09:32   0:00 avahi-daemon: c
root      5211  0.0  0.0   6428  2388 ?        Ss   09:32   0:00 /usr/sbin/cupsd
111       5275  0.0  0.1   6448  4492 ?        Ss   09:32   0:01 /usr/sbin/hald
root      5278  0.0  0.0  16388  2572 ?        Ssl  09:32   0:00 /usr/sbin/conso
root      5279  0.0  0.0   3364  1148 ?        S    09:32   0:00 hald-runner
root      5362  0.0  0.0   3436  1064 ?        S    09:32   0:00 hald-addon-inpu
root      5372  0.0  0.0   3448  1036 ?        S    09:32   0:00 /usr/lib/hal/ha
111       5373  0.0  0.0   2296   944 ?        S    09:32   0:00 hald-addon-acpi
root      5376  0.0  0.0   3440  1064 ?        S    09:32   0:00 hald-addon-stor
root      5398  0.0  0.0   3440  1064 ?        S    09:32   0:00 hald-addon-stor
root      5431  0.0  0.0   3488  1552 ?        Ss   09:32   0:00 /usr/sbin/bluet
root      5438  0.0  0.0      0     0 ?        S<   09:32   0:00 [btaddconn]
root      5439  0.0  0.0      0     0 ?        S<   09:32   0:00 [btdelconn]
root      5453  0.0  0.0      0     0 ?        S<   09:32   0:00 [krfcommd]
root      5493  0.0  0.0   6408  2412 ?        Ss   09:32   0:00 /usr/sbin/Netwo
root      5521  0.0  0.0   4240  1852 ?        S    09:32   0:00 /sbin/wpa_suppl
root      5523  0.0  0.1   6772  2976 ?        S    09:32   0:00 /usr/sbin/nm-sy
root      5531  0.0  0.0  14240  1784 ?        Ss   09:33   0:00 /usr/sbin/gdm
root      5534  0.0  0.1  14776  3228 ?        S    09:33   0:00 /usr/sbin/gdm
root      5539 20.6  0.6  28016 18808 tty7     Rs+  09:33   4:16 /usr/X11R6/bin/
root      5554  0.0  0.0   4336  1152 ?        Ss   09:33   0:00 /usr/bin/system
daemon    5589  0.0  0.0   2068   452 ?        Ss   09:33   0:00 /usr/sbin/atd
root      5617  0.0  0.0   3412  1020 ?        Ss   09:33   0:00 /usr/sbin/cron
root      5718  0.0  0.0   1780   532 tty1     Ss+  09:33   0:00 /sbin/getty 384
jidelica  5750  0.0  0.0  14700  2208 ?        S    09:33   0:00 /usr/bin/gnome-
jidelica  5761  0.0  0.2  24760  5752 ?        Ssl  09:33   0:00 x-session-manag
jidelica  5849  0.0  0.0   3124   672 ?        S    09:33   0:00 /usr/bin/dbus-l
jidelica  5850  0.0  0.0   3032  1184 ?        Ss   09:33   0:00 //bin/dbus-daem
jidelica  5853  0.0  0.1  28940  4504 ?        Ssl  09:33   0:00 /usr/bin/pulsea
jidelica  5856  0.0  0.0   7528  2552 ?        S    09:33   0:00 /usr/lib/pulsea
jidelica  5858  0.0  0.1   7728  4724 ?        S    09:33   0:00 /usr/lib/libgco
jidelica  5864  0.0  0.2  17704  6292 ?        Ss   09:33   0:00 /usr/bin/seahor
jidelica  5869  0.0  0.1  13916  3640 ?        S    09:33   0:00 /usr/lib/gnome-
jidelica  5871  0.2  0.4  42856 13744 ?        Ssl  09:33   0:02 /usr/lib/gnome-
jidelica  5872  0.2  0.4  21452 12788 ?        S    09:33   0:02 /usr/bin/metaci
jidelica  5895  0.0  0.0   5688  2192 ?        S    09:33   0:00 /usr/lib/gvfs/g
jidelica  5901  0.0  0.0  29196  2064 ?        Ssl  09:33   0:00 /usr/lib/gvfs//
jidelica  5905  0.6  0.7  36180 21032 ?        S    09:33   0:07 gnome-panel
jidelica  5906  0.3  1.0  65236 30564 ?        S    09:33   0:04 nautilus --no-d
jidelica  5909  0.0  0.1  41656  3536 ?        Ssl  09:33   0:00 /usr/lib/bonobo
jidelica  5922  0.0  0.1  14240  3012 ?        Sl   09:33   0:00 /usr/lib/gvfs/g
jidelica  5924  0.0  0.0   5536  2208 ?        S    09:33   0:00 /usr/lib/gvfs/g
jidelica  5930  0.0  0.3  23172 10444 ?        S    09:33   0:00 /usr/lib/gnome-
jidelica  5932  0.0  0.0  15020  2772 ?        S    09:33   0:00 /usr/lib/gvfs/g
jidelica  5935  0.0  0.0  13752  2364 ?        S    09:33   0:00 /usr/lib/gvfs/g
jidelica  5977  0.0  0.4  26568 14092 ?        S    09:33   0:00 /usr/lib/fast-u
jidelica  5980  0.0  0.5  44660 15724 ?        Sl   09:33   0:00 /usr/lib/gnome-
jidelica  5983  0.1  0.1  21212  3780 ?        Ss   09:33   0:01 gnome-screensav
jidelica  5992  0.0  0.5  26064 14376 ?        S    09:33   0:00 update-notifier
jidelica  5993  0.0  0.3  32380 10068 ?        Sl   09:33   0:00 /usr/lib/evolut
jidelica  5994  0.1  0.3  31556 10544 ?        SNl  09:33   0:02 trackerd
jidelica  5995  0.0  0.1  15556  5552 ?        S    09:33   0:00 tracker-applet
jidelica  5997  0.1  0.9  39648 27176 ?        S    09:33   0:02 /usr/bin/python
jidelica  5998  0.0  0.2  14752  5844 ?        S    09:33   0:00 bluetooth-apple
jidelica  5999  0.0  0.4  25476 12976 ?        S    09:33   0:00 python /usr/sha
jidelica  6003  0.0  0.5  24992 14932 ?        S    09:33   0:00 nm-applet --sm-
jidelica  6010  0.0  0.4  69388 13500 ?        Ssl  09:33   0:00 gnome-power-man
jidelica  6192  0.0  0.5  24488 14388 ?        S    09:34   0:00 /usr/lib/notifi
root      6289  0.0  0.0   1844   488 ?        S    09:38   0:00 /bin/sh -c nice
root      6290  0.0  0.0   1764   556 ?        SN   09:38   0:00 run-parts --rep
root      6301  0.0  0.0   1844   536 ?        SN   09:38   0:00 /bin/sh /etc/cr
root      6316  0.0  0.0   1776   420 ?        SN   09:38   0:00 sleep 1014
jidelica  6387  0.0  0.0  14044  2684 ?        S    09:51   0:00 /usr/lib/gvfs/g
jidelica  6514  5.7  0.8 100008 24632 ?        Rl   09:53   0:00 gnome-terminal
jidelica  6517  0.0  0.0   2912   760 ?        S    09:53   0:00 gnome-pty-helpe
jidelica  6518  2.0  0.1   5724  3096 pts/0    Ss   09:53   0:00 bash
jidelica  6538  0.0  0.0   2744  1020 pts/0    R+   09:53   0:00 ps -aux
jidelica@jidelica:~$ top
[H[2J[m(Btop - 09:57:08 up 24 min,  2 users,  load average: 0.59, 0.50, 0.36[m(B[39;49m[K
Tasks:[m(B[39;49m[m(B 126 [m(B[39;49mtotal,[m(B[39;49m[m(B   1 [m(B[39;49mrunning,[m(B[39;49m[m(B 125 [m(B[39;49msleeping,[m(B[39;49m[m(B   0 [m(B[39;49mstopped,[m(B[39;49m[m(B   0 [m(B[39;49mzombie[m(B[39;49m[K
Cpu(s):[m(B[39;49m[m(B 13.5%[m(B[39;49mus,[m(B[39;49m[m(B  1.1%[m(B[39;49msy,[m(B[39;49m[m(B  0.2%[m(B[39;49mni,[m(B[39;49m[m(B 83.1%[m(B[39;49mid,[m(B[39;49m[m(B  2.0%[m(B[39;49mwa,[m(B[39;49m[m(B  0.1%[m(B[39;49mhi,[m(B[39;49m[m(B  0.1%[m(B[39;49msi,[m(B[39;49m[m(B  0.0%[m(B[39;49mst[m(B[39;49m[K
Mem: [m(B[39;49m[m(B  2851224k [m(B[39;49mtotal,[m(B[39;49m[m(B   455484k [m(B[39;49mused,[m(B[39;49m[m(B  2395740k [m(B[39;49mfree,[m(B[39;49m[m(B    43668k [m(B[39;49mbuffers[m(B[39;49m[K
Swap:[m(B[39;49m[m(B   698816k [m(B[39;49mtotal,[m(B[39;49m[m(B        0k [m(B[39;49mused,[m(B[39;49m[m(B   698816k [m(B[39;49mfree,[m(B[39;49m[m(B   195668k [m(B[39;49mcached[m(B[39;49m[K
[6;1H
[7m  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            [m(B[39;49m[K
[m(B 5539 root      20   0 45540  20m 7692 S   77  0.7   5:36.94 Xorg               [m(B[39;49m
[m(B 6514 jidelica  20   0 98.4m  24m  12m S    4  0.9   0:01.74 gnome-terminal     [m(B[39;49m
[m(B[m(B 6637 jidelica  20   0  2412 1068  800 R    4  0.0   0:00.04 top                [m(B[39;49m
[m(B    1 root      20   0  3056 1884  564 S    0  0.1   0:01.42 init               [m(B[39;49m
[m(B    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           [m(B[39;49m
[m(B    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        [m(B[39;49m
[m(B    4 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        [m(B[39;49m
[m(B    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         [m(B[39;49m
[m(B    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        [m(B[39;49m
[m(B    7 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1        [m(B[39;49m
[m(B    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         [m(B[39;49m
[m(B    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           [m(B[39;49m
[m(B   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1           [m(B[39;49m
[m(B   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            [m(B[39;49m
[m(B   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      [m(B[39;49m
[m(B   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      [m(B[39;49m
[m(B   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          [m(B[39;49m[6;1H[K[25;1H[?12l[?25h
													

```

---

### Post by Shippou on 2009-01-23
bump!

---

### Post by 3rdalbum on 2009-01-23
Xorg is using a hellova lot of your CPU power - it should be 4% maximum, and yours appears to be using 80%! Have you installed the Nvidia proprietary driver with the Hardware Drivers program?

---

### Post by Shippou on 2009-01-23
> **3rdalbum said:**
> Xorg is using a hellova lot of your CPU power - it should be 4% maximum, and yours appears to be using 80%! Have you installed the Nvidia proprietary driver with the Hardware Drivers program?

I'll try to install it. I haven't installed it yet. 

I'll post after. :)

---

### Post by halovivek on 2009-01-23
> **Shippou said:**
> I'll try to install it. I haven't installed it yet. 

I'll post after. :)

I got the same problem of flicker in acer laptop. Just install the nividia Driver. It will solve.

---

