---
title: "network stopped working again"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-05-26
I am now using ubuntu 18.04  
I had this problem on 16.04 (one of the reasons I upgraded) and never really figured it out.  I tried to ping and it just looked at me until it timed out.  I then went to settings/network and it showed me that both the network and the vpn were up (they were not).  I think took another look at that little three dot thing that holds sound and network stuff and it was there - with a question mark!  I went back to the settings, turned off the network, and vpn, and then turned them back on again and I was in business.  

Below is a snippit of my syslog that was recorded around the time this happened.  Perhaps somebody will see the problem (I looked but.........):
May 26 11:09:43 movies gnome-shell[2802]: JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4
May 26 11:10:33 movies gnome-shell[2802]: message repeated 17 times: [ JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4]
May 26 11:10:37 movies dbus-daemon[2118]: [session uid=1000 pid=2118] Activating service name='org.gnome.Nautilus' requested by ':1.15' (uid=1000 pid=2802 comm="/usr/bin/gnome-shell " label="unconfined")
May 26 11:10:37 movies dbus-daemon[2118]: [session uid=1000 pid=2118] Successfully activated service 'org.gnome.Nautilus'
May 26 11:10:37 movies gnome-shell[2802]: clutter-actor.c:10049: Actor 'dashtodockDashScrollview' tried to allocate a size of -198.00 x 192.00
May 26 11:10:38 movies dbus-daemon[944]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.208' (uid=1000 pid=30008 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
May 26 11:10:38 movies systemd[1]: Starting Hostname Service...
May 26 11:10:38 movies dbus-daemon[944]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 26 11:10:38 movies systemd[1]: Started Hostname Service.
May 26 11:10:38 movies gnome-shell[2802]: clutter-actor.c:10049: Actor 'dashtodockDashScrollview' tried to allocate a size of -198.00 x 192.00
May 26 11:10:39 movies nautilus[30008]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
May 26 11:10:40 movies gnome-shell[2802]: JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4
May 26 11:10:43 movies gnome-shell[2802]: message repeated 3 times: [ JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4]
May 26 11:10:46 movies gvfsd-metadata[3283]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
May 26 11:10:46 movies gvfsd-metadata[3283]: message repeated 7 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
May 26 11:10:53 movies gnome-shell[2802]: JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4
May 26 11:10:58 movies gnome-shell[2802]: message repeated 2 times: [ JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4]
May 26 11:11:00 movies gnome-shell[2802]: clutter-actor.c:10049: Actor 'dashtodockDashScrollview' tried to allocate a size of -198.00 x 192.00
May 26 11:11:01 movies gnome-shell[2802]: JS WARNING: [/home/greg/.local/share/gnome-shell/extensions/transmission-daemon@patapon.info/extension.js 178]: Too many arguments to method Soup.Message.set_request: expected 3, got 4
May 26 11:11:01 movies gnome-shell[2802]: clutter-actor.c:10049: Actor 'dashtodockDashScrollview' tried to allocate a size of -198.00 x 192.00

---

### Post by jgw on 2018-05-29
My network stopped yet again.  I checked my syslog file and found which has been repeating (except for the first line when it started).   I found my network was no longer working, stopped the network, then restarted it (so I could send this)  apparently the network is still on but clogged so bad that the only way to fix it is to restart it.  The strange thing is that its still repeating this stuff even though its working and the fact that I stopped and restarted was not logged.  

I am curious, should I be looking at another logfile that might deal with the network?

Thank you..............
May 29 00:09:41 movies rsyslogd:  [origin software="rsyslogd" swVersion="8.32.0" x-pid="947" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Attempting to re-register :1.50/org/ayatana/NotificationItem/multiload; resetting instead
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Item :1.50/org/ayatana/NotificationItem/multiload is already registered
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Attempting to re-register :1.50/org/ayatana/NotificationItem/multiload; resetting instead
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Item :1.50/org/ayatana/NotificationItem/multiload is already registered
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Attempting to re-register :1.50/org/ayatana/NotificationItem/multiload; resetting instead
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Item :1.50/org/ayatana/NotificationItem/multiload is already registered
May 29 00:09:42 movies gnome-shell[3419]: [AppIndicatorSupport-WARN] Attempting to re-register :1.50/org/ayatana/NotificationItem/multiload; resetting instead

---

### Post by hans12345 on 2018-08-11
I am having this problem too, with 18.04.1 :
```

Aug 11 12:05:26 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered
Aug 11 12:05:26 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Attempting to re-register :1.62/org/ayatana/NotificationItem/multiload; resetting instead
Aug 11 12:05:26 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered
Aug 11 12:05:26 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Attempting to re-register :1.62/org/ayatana/NotificationItem/multiload; resetting instead
Aug 11 12:05:26 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Attempting to re-register :1.62/org/ayatana/NotificationItem/multiload; resetting instead
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Attempting to re-register :1.62/org/ayatana/NotificationItem/multiload; resetting instead
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Attempting to re-register :1.62/org/ayatana/NotificationItem/multiload; resetting instead
Aug 11 12:05:27 Ace gnome-shell[17410]: [AppIndicatorSupport-WARN] Item :1.62/org/ayatana/NotificationItem/multiload is already registered

```

Any ideas?

---

### Post by jgw on 2018-08-11
Its strange.  I just gave up and live with it.  Its currently not doing it.  I found that if the browser, or anything else that needed the net and took too long that it was down and I would just turn it on again.  If you are using 18.04 you might be able to find an extension that would popup if your network failed.  I know there is one of those for a vpn.  The truly strange thing is that the system thinks its actually working, even though its not.

This is one of those things that come under the heading of "mystery" and all I can do is wish you good luck.

Just happened to me again on 8/16/2018.................  Fixed it by disconnecting and then re-connecting.

---

