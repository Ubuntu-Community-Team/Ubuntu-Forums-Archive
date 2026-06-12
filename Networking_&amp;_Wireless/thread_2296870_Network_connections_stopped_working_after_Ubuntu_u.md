---
title: "Network connections stopped working after Ubuntu update"
date: 2015-09-29
forum: Networking &amp; Wireless
---

### Post by Neeeeeeeeeel.- on 2015-09-29
I've been using Ubuntu 14.04 since it's release without problems. I always install Ubuntu updates, I've never experienced any problems until today.

After the update, I rebooted my system (the update didn't ask me to do it, but I did it). After that, my screen resolution was changed to 800x600 and I couldn't see any wifi signal. Then, I tried to connect an ethernet wire directly, but it also didn't work.

I also can't change my screen resolution.

I tried running the wireless-info script but there I get this errors:
```
leo@leo:~/Documentos$ ./wireless-info./wireless-info: línea 1: $'\r': orden no encontrada
./wireless-info: línea 28: $'\r': orden no encontrada
./wireless-info: línea 33: $'\r': orden no encontrada
./wireless-info: línea 38: $'\r': orden no encontrada
./wireless-info: línea 43: $'\r': orden no encontrada
./wireless-info: línea 48: $'\r': orden no encontrada
./wireless-info: línea 52: $'\r': orden no encontrada
./wireless-info: línea 57: error sintáctico cerca del elemento inesperado `elif'
./wireless-info: línea 57: `elif [ -x /usr/bin/zenity ]; t'en

```

After the Ubuntu update, I upgraded my Wine from 1.6 to 1.7 (I don't know if it has something to do with my problem, but I prefer to mention it).

I managed to get the packets updated today from the dpkg log
```
2015-09-29 11:44:09 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu42015-09-29 11:44:09 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:09 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:10 status installed wine1.6-amd64:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:13 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:13 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:13 status installed wine1.6-i386:i386 1:1.6.2-0ubuntu4
2015-09-29 11:44:14 status installed wine1.6:amd64 1:1.6.2-0ubuntu4
2015-09-29 11:44:21 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-09-29 11:44:25 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-09-29 11:44:29 status installed mime-support:all 3.54ubuntu1.1
2015-09-29 11:44:30 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-09-29 11:44:30 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-09-29 11:44:31 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-09-29 11:44:42 status installed hicolor-icon-theme:all 0.13-1
2015-09-29 11:45:12 status installed hicolor-icon-theme:all 0.13-1
2015-09-29 11:45:14 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-09-29 11:45:15 status installed mime-support:all 3.54ubuntu1.1
2015-09-29 11:45:15 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-09-29 11:45:16 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-09-29 11:45:16 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-09-29 11:45:16 status installed libpcap0.8:i386 1.5.3-2
2015-09-29 11:45:17 status installed wine-gecko2.34:amd64 2.34-0ubuntu1~ppa1
2015-09-29 11:45:17 status installed wine-gecko2.34:i386 2.34-0ubuntu1~ppa1
2015-09-29 11:45:17 status installed wine-mono4.5.4:all 4.5.4-0ubuntu1~ppa1
2015-09-29 11:45:18 status installed wine1.7:amd64 1:1.7.50-0ubuntu1
2015-09-29 11:45:18 status installed wine1.7-amd64:amd64 1:1.7.50-0ubuntu1
2015-09-29 11:45:18 status installed wine:amd64 1:1.7.50-0ubuntu1
2015-09-29 11:45:19 status installed wine1.7-i386:i386 1:1.7.50-0ubuntu1
2015-09-29 11:45:19 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-09-29 12:01:20 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-09-29 12:01:26 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-09-29 12:01:26 status installed libpython3.4-minimal:amd64 3.4.3-1ubuntu1~14.04.1
2015-09-29 12:01:27 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-09-29 12:01:28 status installed python3.4-minimal:amd64 3.4.3-1ubuntu1~14.04.1
2015-09-29 12:01:28 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-09-29 12:01:28 status installed ureadahead:amd64 0.100.0-16
2015-09-29 12:01:28 status installed libpython3.4-stdlib:amd64 3.4.3-1ubuntu1~14.04.1
2015-09-29 12:01:29 status installed mime-support:all 3.54ubuntu1.1
2015-09-29 12:07:04 status installed libpython3.4:amd64 3.4.3-1ubuntu1~14.04.1
2015-09-29 12:07:07 status installed python3.4:amd64 3.4.3-1ubuntu1~14.04.1
2015-09-29 12:07:08 status installed libc-bin:amd64 2.19-0ubuntu6.6

```

Please let me know if you need any aditional information. Thanks in advance.

---

