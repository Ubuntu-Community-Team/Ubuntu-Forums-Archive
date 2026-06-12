---
title: "Login freeze beacuse of wireless problem"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by lupus664 on 2008-06-07
Hello!

I have a problem when logging into Ubuntu 8.04. The problem occurred when I upgraded from the older version. The thing is that the computer freezes when it starts loading Ubuntu - first for a minute before logging in and then for another 5 min.

Here's the log:

```
Jun  7 17:19:16 xxxxx avahi-daemon[5248]: Registering new address record for fe80::21a:4bff:fe61:3459 on eth0.*.
Jun  7 17:19:25 xxxxx kernel: [   55.999925] eth0: no IPv6 routers present
Jun  7 17:20:19 xxxxx gdm[5514]: WARNING: Login sound requested on non-local display or the play software cannot be run or the sound does not exist. 
Jun  7 17:24:00 xxxxx NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  7 17:24:00 xxxxx NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

As you can see, there seems to be a problem with the login sound (which I also don't know how to fix, I tried to disable it, but it still waits before the login page) and after that a problem with the wireless network. I also just want to disable wireless completely so I'm actually looking for the quickest and painless solution. :) If anyone can spare a few moments to help out I would appreciate it very much. If there is any additional info needed, please ask.

Thank you!

---

### Post by lupus664 on 2008-06-12
Seems like nobody noticed this post. Maybe I posted in the wrong category...

I'm sure there's a simple solution to my problem - I just want Ubuntu to not search for any wireless networks when doing startup. Is there any way to turn this off, maybe disable some hardware detection?

---

