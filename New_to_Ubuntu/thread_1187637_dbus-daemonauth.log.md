---
title: "dbus-daemon/auth.log"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-06-14
Hey all.  I was just checking auth.log and trying to familiarize myself more with linux.  I noticed that dbus-daemon is doing something that appears to be failing every second.  I'm sure this isn't a security issue, but I'm wondering what it means because it never happened in other versions of linux I have tried.  Heres a snippet of what it is doing, it basically does this all day long.

> 
Jun 14 19:02:24 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.62" (uid=111 pid=4091 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.63" (uid=111 pid=4100 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.64" (uid=111 pid=4102 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.65" (uid=111 pid=4104 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.66" (uid=111 pid=4106 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.67" (uid=111 pid=4108 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.68" (uid=111 pid=4110 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.69" (uid=111 pid=4112 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.70" (uid=111 pid=4114 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))
Jun 14 19:03:46 m-pc dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=3461 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.71" (uid=111 pid=4116 comm="/usr/lib/policykit/polkit-read-auth-helper 1000 "))

Thanks.

---

