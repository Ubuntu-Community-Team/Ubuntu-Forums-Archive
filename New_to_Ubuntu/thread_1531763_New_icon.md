---
title: "New icon?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by XR171 on 2010-07-15
This is going to sound horribly noobish but this is bugging me.

So I woke up this morning and first I checked the status of my downloads and I saw a new icon in the notification area.  When I right or left click it does nothing and I didn't start any new programs.

I didn't see anything too out of the ordinary on my running tasks.  I'm hesitant to reboot because of  said downloads.  Any help will be greatly appreciated!

Its the icon on the left side, the blue one.



Running tasks:
> 
xr171@X2:~$ ps ux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
xr171     1175  0.1  0.1 169688  3536 ?        Ssl  Jul05  27:54 gnome-session
xr171     1271  0.0  0.0  11928    88 ?        Ss   Jul05   0:00 /usr/bin/ssh-agent /usr/bin/dbus
xr171     1275  0.0  0.0  26252   296 ?        S    Jul05   0:00 /usr/bin/dbus-launch --exit-with
xr171     1279  0.8  0.0  24352  1576 ?        Ss   Jul05 117:42 /bin/dbus-daemon --fork --print-
xr171     1282  0.0  0.2  46408  5216 ?        S    Jul05   0:16 /usr/lib/libgconf2-4/gconfd-2
xr171     1286  0.0  0.2 458172  7592 ?        Ssl  Jul05   3:53 /usr/lib/gnome-settings-daemon/g
xr171     1289  0.0  0.0  69600  1372 ?        Sl   Jul05  10:44 /usr/bin/gnome-keyring-daemon --
xr171     1293  0.0  0.0  48120  1476 ?        S    Jul05  10:33 /usr/lib/gvfs/gvfsd
xr171     1300  0.1  0.7 302176 19040 ?        S    Jul05  27:51 gnome-panel --sm-config-prefix /
xr171     1301  0.0  0.0  78024  1060 ?        Ssl  Jul05   0:00 /usr/lib/gvfs//gvfs-fuse-daemon
xr171     1316  0.0  1.3 636960 34420 ?        Sl   Jul05   2:22 nautilus --sm-client-id 101df2f3
xr171     1321  0.0  0.0 154000  2412 ?        S    Jul05   0:10 /usr/lib/gvfs/gvfs-gdu-volume-mo
xr171     1328  0.0  0.1 182536  2968 ?        S    Jul05  14:06 /usr/lib/vino/vino-server --sm-d
xr171     1331  0.0  0.1 432268  3640 ?        Sl   Jul05   0:00 /usr/lib/evolution/2.28/evolutio
xr171     1334  0.0  0.1 215208  4800 ?        Sl   Jul05   0:03 /usr/lib/policykit-1-gnome/polki
xr171     1335  0.1  0.1 178296  3224 ?        S    Jul05  19:54 gnome-power-manager
xr171     1336  0.1  0.2 266204  5944 ?        S    Jul05  14:30 nm-applet --sm-disable
xr171     1337  0.2  1.1 457368 28456 ?        Sl   Jul05  41:14 mono --debug /usr/lib/docky/Dock
xr171     1339  0.0  0.1 248816  2964 ?        S    Jul05   0:00 python /usr/share/screenlets-man
xr171     1346  0.0  0.0  55236  1376 ?        S    Jul05   0:00 /usr/lib/gvfs/gvfs-gphoto2-volum
xr171     1349  0.0  0.0  69208  1200 ?        Sl   Jul05   0:27 /usr/lib/gvfs/gvfs-afc-volume-mo
xr171     1409  0.0  0.0 153100  2448 ?        Ssl  Jul05   0:00 /usr/lib/bonobo-activation/bonob
xr171     1470  0.0  0.0  52480  1564 ?        S    Jul05   0:00 /usr/lib/gvfs/gvfsd-trash --spaw
xr171     1476  0.0  0.0 173768  1824 ?        Ss   Jul05  12:31 gnome-screensaver
xr171     1489  0.3  0.3 267008  8584 ?        S    Jul05  45:52 /usr/lib/gnome-panel/wnck-applet
xr171     1496  0.1  0.4 337264 11020 ?        Sl   Jul05  17:15 /usr/lib/indicator-applet/indica
xr171     1497  0.1  0.7 429648 19528 ?        Sl   Jul05  14:44 /usr/lib/gnome-panel/clock-apple
xr171     1500  0.0  0.4 246328 12212 ?        S    Jul05   0:00 /usr/lib/gnome-panel/notificatio
xr171     1501  0.1  0.3 327320  9408 ?        S    Jul05  16:28 /usr/lib/indicator-applet/indica
xr171     1520  0.0  0.1 355624  3368 ?        Sl   Jul05   0:00 /usr/lib/evolution/2.28/evolutio
xr171     1536  0.0  0.1 391228  3200 ?        Sl   Jul05   0:00 /usr/lib/evolution/evolution-dat
xr171     1541  0.0  0.0  41916  1412 ?        S    Jul05   0:00 /usr/lib/gvfs/gvfsd-metadata
xr171     1550  0.0  0.1 196364  4724 ?        S    Jul05   0:04 /usr/lib/gnome-disk-utility/gdu-
xr171     1578  0.0  0.0 219012  1880 ?        S    Jul05  10:31 /usr/lib/indicator-sound/indicat
xr171     1580  0.0  0.0  47856   976 ?        S    Jul05   0:00 /usr/lib/gvfs/gvfsd-burn --spawn
xr171     1582  0.0  0.0 146892  1952 ?        S    Jul05  12:53 /usr/lib/indicator-application/i
xr171     1593  0.1  0.0 143968  1972 ?        S    Jul05  25:20 /usr/lib/indicator-me/indicator-
xr171     1609  0.0  0.0 140900  2236 ?        S    Jul05  13:19 /usr/lib/indicator-session/indic
xr171     1617  0.0  0.0 138100  1788 ?        S    Jul05  12:39 /usr/lib/indicator-messages/indi
xr171     1639  0.1  0.2 210048  6888 ?        S    Jul05  16:30 /usr/lib/notify-osd/notify-osd
xr171     1725  0.2  0.1 231148  3700 ?        S    Jul05  28:57 python /usr/share/system-config-
xr171     1924  0.0  0.1 192964  4856 ?        S    Jul05   0:25 update-notifier
xr171     2355  0.5  0.3 332996  9908 ?        S    Jul05  75:55 compiz --replace
xr171     2374  0.0  0.0   4088   188 ?        Ss   Jul05   0:00 /bin/sh -c /usr/bin/compiz-decor
xr171     2375  0.3  0.2 180060  6244 ?        S    Jul05  55:03 /usr/bin/gtk-window-decorator
xr171     2548  1.6  0.0 282812  1812 ?        Sl   Jul05 233:55 conky
xr171     2641  6.8  2.6 713092 67532 ?        Sl   Jul05 994:57 /usr/bin/python /usr/bin/deluge-
xr171     8450  0.0  0.4 298592 11768 ?        Sl   Jul14   0:05 /usr/lib/gnome-user-share/gnome-
xr171     8458  0.1  0.0  81812  2548 ?        S    Jul14   1:56 /usr/bin/obex-data-server --no-d
xr171     9513  0.4  0.1 335724  3948 ?        S<sl Jul13  12:50 /usr/bin/pulseaudio --start --lo
xr171     9532  0.0  0.0  96648  1672 ?        S    Jul13   0:00 /usr/lib/pulseaudio/pulse/gconf-
xr171    17357  1.2  2.4 838408 61788 ?        Sl   Jul14  16:42 rhythmbox /home/xr171/Music/Batt
xr171    24298  2.3  0.5 217376 15100 ?        Sl   13:32   0:00 gnome-terminal
xr171    24299  0.1  0.0  14484   792 ?        S    13:32   0:00 gnome-pty-helper
xr171    24300  2.9  0.1  20992  3772 pts/1    Ss   13:32   0:00 bash
xr171    24379  0.0  0.0  15252  1180 pts/1    R+   13:32   0:00 ps ux
xr171    24405  0.1 11.0 1653768 283280 ?      Sl   Jul05  23:44 java -Xmx768M -Xss16M -Dfile.enc
xr171    25738  0.0  0.0      0     0 ?        Z    Jul12   0:00 [xdg-open] <defunct>
xr171    26327  0.0  0.0  94144  1980 ?        S    Jul09   0:00 /usr/lib/gvfs/gvfsd-http --spawn
xr171    26582  0.0  0.0   4092   292 ?        S    Jul12   0:00 /bin/sh /usr/lib/firefox-3.6.6/f
xr171    26593  0.0  0.0   4092   296 ?        S    Jul12   0:00 /bin/sh /usr/lib/firefox-3.6.6/r
xr171    26597  3.5  3.9 724732 101356 ?       Sl   Jul12 138:46 /usr/lib/firefox-3.6.6/firefox-b
xr171    26926  1.5  0.6  90528 15740 ?        Sl   Jul12  61:21 /usr/lib/nspluginwrapper/i386/li
xr171    28279  0.0  0.0  62652  1312 ?        S    Jul09   0:00 /usr/lib/gvfs/gvfsd-computer --s
xr171@X2:~$ 


---

### Post by nothingspecial on 2010-07-15
That is the bittorrent client deluge.

If it doesnt respond, try opening a terminal and typing ```
killall-deluge
```

Come to think of it, it might be```
 killall deluge-torrent
```

Try them both.

---

### Post by nothingspecial on 2010-07-15
Ah sorry, the one on the left.

The only thing I see in your current processes is the update-notifier.
 
I`ve never seen that icon though, have you installed a set of fancy ones?

That or bluetooth, sorry I don`t use panels.

---

### Post by XR171 on 2010-07-16
I've not installed anything new within the past week.  It was just there when I got up.  Normally when I have Bluetooth on it displays the normal Bluetooth symbol.  And it's still there.  I've installed updates today and a couple days ago but they didn't require a restart.

---

### Post by emoguitarist06 on 2010-07-16
It's Deluge

The deluge icon on the right is the application
On the left you have the a view of both of your workspaces and it's just showing you that you have deluge opened in the first workspace and nothing opened in your second workspace.

---

### Post by XR171 on 2010-07-28
Ok figured it out... finally.  Its because I transferred files via Bluetooth.  Thanks for the help everyone!

---

