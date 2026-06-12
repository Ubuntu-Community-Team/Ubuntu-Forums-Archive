---
title: "X11VNC Systemd Service"
date: 2016-04-15
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2016-04-15
Hello,

I'm experiencing an issue with **/etc/systemd/service/x11vnc.service**:
```
[Unit]Description=Start x11vnc at startup.
Requires=gdm.service
After=gdm.service


[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth /run/user/1000/gdm/Xauthority -rfbauth /home/ubuntu/.vnc/passwd -rfbport 5900 -noxdamage -forever


[Install]
WantedBy=graphical.target
```

The username is "**ubuntu**".
The service has been **enabled** with:
```
systemctl enable x11vnc
```
However, at each startup, the service is not started:
```
systemctl -l status x11vnc\u25cf x11vnc.service - Start x11vnc at startup.
   Loaded: loaded (/etc/systemd/system/x11vnc.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2016-04-15 12:38:25 CEST; 55s ago
  Process: 2392 ExecStart=/usr/bin/x11vnc -auth /run/user/1000/gdm/Xauthority -rfbauth /home/ubuntu/.vnc/passwd -rfbport 5900 -noxdamage -forever (code=exited, status=1/FAILURE)
 Main PID: 2392 (code=exited, status=1/FAILURE)
```
In the **/var/log/syslog**:
```
x11vnc[2392]: 15/04/2016 12:38:21 *** 1 2 3 4
x11vnc[2392]: No protocol specified
x11vnc[2392]: 15/04/2016 12:38:25 XOpenDisplay(":0") failed.
```
However, if I run the exact same command from the CLI, it works perfectly: the daemon is launched correctly and I can connect through a VNC client from outside.

Does anyone knows what is going on? I really need to be able to launch the service when the system is unattended, i.e without being able to launch the daemon manually when the system boots up.

---

### Post by actionmystique on 2016-04-15
Yes, that's what I suspected: no one has tried this recently. The official [documentation]("https://help.ubuntu.com/community/VNC/Servers") is so old that it's not applicable anymore on the last Ubuntu release.
For example, it suggests that we should run **x11vnc as root**, but:
- there is no Xauthority for the root account on my system
- running the command in a terminal as a non root user works perfectly, why doesn't it work as a service?

---

### Post by aperomsik on 2016-08-03
Have you tried "-auth guess" instead?  That's working for me, although I am running lightdm instead of gdm.

---

### Post by actionmystique on 2016-08-05
> **aperomsik said:**
> Have you tried "-auth guess" instead?  That's working for me, although I am running lightdm instead of gdm.
No, I have replaced X11VNC by Real VNC.

---

### Post by Pro_D on 2016-09-12
If it helps, here is my systemd file (/etc/systemd/system/x11vnc.system).

```

[Unit]
Description=x11vnc remote session for login.
After=network.target

[Service]
Type=simple
ExecStart=/bin/sh -c '/usr/bin/x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -o /var/log/x11vnc.log -rfbauth <path to passfile> -rfbport 5900'
Restart=on-success
SuccessExitStatus=3

[Install]
WantedBy=multi-user.target

```

I've only been running 16.04, from 14.04, for a day now and x11vnc was top of the custom services heap from upstart->systemd to get running again.  Since 12.04 I haven't been able to figure out how to start sessions not connected to a real display (lack of lightdm knowledge I think), so that up there is meant to connect to a real display's session.  The only elements of the systemd .system file that I'm confident I had a clue about were Description, Type, ExecStart, Restart, and SuccessExitStatus.  Description is kind of hard to mess up - that is just what gets shown in logs when starting the service.  Technically Type is redundant but I'm somewhat fond of specifying defaults in stuff I'm new to.  I figured out the SuccessExitStatus from watching syslog when I remotely logged out but I suppose 'systemctl status x11vnc.service' would have worked as well.  Everything else got pulled from either random web sites or using 'grep -R' in '/etc/systemd' to get a lay of how things might look.  Could probably benefit from limiting restarts in a short period but this is a first pass to get things working.

I found the [Redhat docs on systemd](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/sect-Managing_Services_with_systemd-Unit_Files.html) to be rather wordy and slow for me though that might be fine for someone totally new or looking for a deeper understanding.  I got lucky and found something a bit more man page like [right here](https://www.freedesktop.org/software/systemd/man/systemd.service.html).


Aside: The upgrade really borked up mysql for me, but then I've got a very customized configuration.  I managed to keep my databases unlike what most suggestions would have had me do, delete everything mysql (including databases) and start over.  I kept my databases by TEMPORARILY putting usr.sbin.mysql into /etc/apparmor.d/disable and then mysql showed me the errors in my configuration (in the logs) on service start.  Prior to TEMPORARILY disabling apparmor for mysql all I'd get was audit errors that mysql was disallowed from reading a file or some such that according to the apparmor profile it should have been allowed.  After fixing the lingering mysql configuration errors and re-enabling the apparmor profile, mysql is starting just fine.  Based on reading and the fact that (outside of my custom configuration) I didn't mess with the apparmor profile for mysql I'm GUESSING mysql is forking something off for errors which is seen as foreign to apparmor and the attempt to collect error information is blocked by apparmor. <shrug>

---

