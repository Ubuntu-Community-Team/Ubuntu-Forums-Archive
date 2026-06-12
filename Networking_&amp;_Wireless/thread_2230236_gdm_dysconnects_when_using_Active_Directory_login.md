---
title: "gdm dysconnects when using Active Directory login"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by edubidu on 2014-06-18
Hi forum,

Not sure if I post at the right place.
The following problem seems to be in relation with gnome:

- Installed ubuntu 14.04 LTS amd desktop
- I'd like to connect the machine to Active Directory. 
- Installed this: 
```
http://www.sinap.si/wp-content/uploads/2011/08/LikewiseOpen-6.0.0.8388-linux-amd64-deb.sh
```

- Added the computer successfully. **Login works in terminal**, but gdm disconnects immediately.

cat /var/log/auth.log
```

...
Jun 17 12:13:18 mycomp polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.36 [gnome-shell --mode=gdm], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jun 17 12:13:35 mycomp gdm-password][2199]: pam_succeed_if(gdm-password:auth): requirement "user ingroup nopasswdlogin" not met by user "DOMAIN\adusername"
Jun 17 12:13:45 mycomp gdm-password][2199]: pam_unix(gdm-password:session): session opened for user adusername by (unknown)(uid=0)
Jun 17 12:13:45 mycomp gdm-launch-environment][1685]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Jun 17 12:13:45 mycomp polkitd(authority=local): Unregistered Authentication Agent for unix-session:c1 (system bus name :1.36, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Jun 17 12:13:46 mycomp gdm-password][2199]: pam_unix(gdm-password:session): session closed for user adusername
Jun 17 12:13:46 mycomp dbus[735]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.11" (uid=0 pid=996 comm="gdm ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.43" (uid=0 pid=2357 comm="/usr/lib/gdm/gdm-simple-slave --display-id /org/gn")
...

```

Some ideas? I googled around but cannot find anything for ubuntu...

---

### Post by edubidu on 2014-07-01
SOLVED:
[http://ubuntuforums.org/showthread.php?t=2230602](http://ubuntuforums.org/showthread.php?t=2230602)

---

