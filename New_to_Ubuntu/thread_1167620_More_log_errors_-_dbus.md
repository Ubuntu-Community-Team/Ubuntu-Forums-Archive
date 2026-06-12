---
title: "More log errors - dbus"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-23
My log file is full of this...any idea what is going on.


May 23 19:20:01 pj-indulgence dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=4160 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1234" (uid=0 pid=27054 comm="/USR/SBIN/CRON "))
May 23 19:20:02 pj-indulgence CRON[27054]: pam_unix(cron:session): session closed for user root
May 23 19:30:01 pj-indulgence CRON[27653]: pam_unix(cron:session): session opened for user root by (uid=0)
May 23 19:30:01 pj-indulgence dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=4160 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1235" (uid=0 pid=27653 comm="/USR/SBIN/CRON "))
May 23 19:30:01 pj-indulgence CRON[27653]: pam_unix(cron:session): session closed for user root
May 23 19:40:01 pj-indulgence CRON[28253]: pam_unix(cron:session): session opened for user root by (uid=0)
May 23 19:40:01 pj-indulgence dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=4160 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1236" (uid=0 pid=28253 comm="/USR/SBIN/CRON "))
May 23 19:40:01 pj-indulgence CRON[28253]: pam_unix(cron:session): session closed for user root
May 23 19:42:47 pj-indulgence dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=4160 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1237" (uid=0 pid=28612 comm="/usr/lib/NetworkManager/nm-dhcp-client.action "))
May 23 19:50:01 pj-indulgence CRON[28876]: pam_unix(cron:session): session opened for user root by (uid=0)
May 23 19:50:01 pj-indulgence dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=4160 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1238" (uid=0 pid=28876 comm="/USR/SBIN/CRON "))
May 23 19:50:02 pj-indulgence CRON[28876]: pam_unix(cron:session): session closed for user root

---

### Post by Harag on 2009-05-24
[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513) seems to be about the same DBUS issue...

The cron issue is spoken about here [https://bugs.launchpad.net/ubuntu/+bug/216990](https://bugs.launchpad.net/ubuntu/+bug/216990) but I have had no luck with fixes or work around on this issue.

---

