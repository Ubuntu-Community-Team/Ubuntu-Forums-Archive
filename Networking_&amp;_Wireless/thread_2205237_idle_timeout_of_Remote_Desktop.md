---
title: "idle timeout of Remote Desktop"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by wbsimey on 2014-02-12
We are connecting to an Ubuntu 12 server from windows 7 via “Remote Desktop” to run GUI apps. However, “Remote Desktop” disconnects after 5 minutes of idle time killing any running jobs. I have tried to edit the /etc/xrdp/sesman.ini (on Ubuntu), but sesman.ini seems to have zero influence on the behavior of “Remote Desktop”. For example, I have set IdleTimeLimit=0 and other larger numbers, but “Remote Desktop” disconnects after 5 minutes no matter what the sesman.ini configuration. There seem to be few configuration options from the client side. Anybody else run into this issue? 

NOTE: I am also considering TeamViewer, VNC, etc, but our IT folks want us to use Remote Desktop if possible.

---

### Post by tomearp on 2014-02-13
From the [man page]("http://manpages.ubuntu.com/manpages/precise/en/man5/sesman.ini.5.html#contenttoc4") for 12.04 (xrdp 0.5.0-2_i386):
```
SESSIONS
       The following parameters can be used in the [Sessions] section:

       MaxSessions=<number>
              Sets  the  maximum  number  of  simultaneous session on terminal
              server.
              If unset or set to 0, unlimited session are allowed.

       KillDisconnected=[0|1]
              If set to 1, true or yes, every session will be killed when  the
              user disconnects.
             ** -this option is currently ignored!-**

       IdleTimeLimit=<number>
              Sets the the time limit before an idle session is disconnected.
              If set to 0, automatic disconnection is disabled.
              **-this option is currently ignored!-**

       DisconnectedTimeLimit=<number>
              Sets the the time limit before a disconnected session is killed.
              If set to 0, automatic killing is disabled.
              **-this option is currently ignored!-**
```

---

