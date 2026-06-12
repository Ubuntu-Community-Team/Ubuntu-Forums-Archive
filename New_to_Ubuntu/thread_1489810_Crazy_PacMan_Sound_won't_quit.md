---
title: "Crazy PacMan Sound won't quit"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Ol'manScratch on 2010-05-21
This is an add on to the issue I just posted
Here is the log file (I think)
Does this answer the problem
Thanks


ay 21 00:17:01 jess-desktop CRON[1629]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 00:17:01 jess-desktop CRON[1629]: pam_unix(cron:session): session closed for user root
May 21 01:17:01 jess-desktop CRON[1633]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 01:17:01 jess-desktop CRON[1633]: pam_unix(cron:session): session closed for user root
May 21 02:07:56 jess-desktop gdm-session-worker[1575]: pam_unix(gdm:session): session opened for user jess by (uid=0)
May 21 02:07:56 jess-desktop gdm-session-worker[1575]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 21 02:08:00 jess-desktop seahorse-daemon[1736]: init gpgme version 1.1.8
May 21 02:08:06 jess-desktop dbus-daemon: Rejected send message, 3 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=1879 comm="/usr/lib/indicator-messages/indicator-messages-ser") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.8" (uid=0 pid=996 comm="/sbin/wpa_supplicant))
May 21 02:17:01 jess-desktop CRON[2040]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 02:17:01 jess-desktop CRON[2040]: pam_unix(cron:session): session closed for user root
May 21 03:17:01 jess-desktop CRON[2353]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 03:17:01 jess-desktop CRON[2353]: pam_unix(cron:session): session closed for user root
May 21 09:56:43 jess-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=jess ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May 21 09:56:43 jess-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=jess ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May 21 09:56:43 jess-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=jess ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May 21 10:08:46 jess-desktop gdm-session-worker[1503]: pam_unix(gdm:session): session opened for user jess by (uid=0)
May 21 10:08:46 jess-desktop gdm-session-worker[1503]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 21 10:08:50 jess-desktop seahorse-daemon[1709]: init gpgme version 1.1.8
May 21 10:08:55 jess-desktop dbus-daemon: Rejected send message, 3 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=1849 comm="/usr/lib/indicator-messages/indicator-messages-ser") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.8" (uid=0 pid=975 comm="/sbin/wpa_supplicant))
May 21 10:17:01 jess-desktop CRON[2074]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 10:17:01 jess-desktop CRON[2074]: pam_unix(cron:session): session closed for user root
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:25:53 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:25:53 jess-desktop sudo:     jess : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/jess ; USER=root ; COMMAND=/bin/kill -s 19 5
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): conversation failed
May 21 10:36:51 jess-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jess]
May 21 10:36:51 jess-desktop sudo:     jess : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/jess ; USER=root ; COMMAND=/usr/bin/computer-janitor-gtk

---

### Post by Chesamo on 2010-05-21
Please don't post more than one thread about a single topic.

[http://ubuntuforums.org/showthread.php?t=1489807](http://ubuntuforums.org/showthread.php?t=1489807)

---

