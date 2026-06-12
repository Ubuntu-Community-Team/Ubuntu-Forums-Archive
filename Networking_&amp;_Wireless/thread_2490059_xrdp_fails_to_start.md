---
title: "xrdp fails to start"
date: 2023-08-21
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2023-08-21
xrdp service fails to start:
 john@Demonstrator:~$ systemctl status xrdp.service
 × xrdp.service - xrdp daemon Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: > Active: failed (Result: exit-code) since Tue 2023-08-15 08:44:54 BST; 28s > Docs: man:xrdp(8) man:xrdp.ini(5) Process: 186632 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited> Process: 186640 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status> CPU: 15ms
 Aug 15 08:44:54 Demonstrator systemd[1]: Starting xrdp daemon... Aug 15 08:44:54 Demonstrator xrdp[186640]: [INFO ] address [0.0.0.0] port [3389> Aug 15 08:44:54 Demonstrator xrdp[186640]: [INFO ] listening to port 3389 on 0.> Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] g_tcp_bind(7, 3389) failed b> Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] trans_listen_address failed Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] Failed to start xrdp daemon,> Aug 15 08:44:54 Demonstrator systemd[1]: xrdp.service: Control process exited, > Aug 15 08:44:54 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit> Aug 15 08:44:54 Demonstrator systemd[1]: Failed to start xrdp daemon. ...skipping... × xrdp.service - xrdp daemon Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: > Active: failed (Result: exit-code) since Tue 2023-08-15 08:44:54 BST; 28s > Docs: man:xrdp(8) man:xrdp.ini(5) Process: 186632 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited> Process: 186640 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status> CPU: 15ms
 Aug 15 08:44:54 Demonstrator systemd[1]: Starting xrdp daemon... Aug 15 08:44:54 Demonstrator xrdp[186640]: [INFO ] address [0.0.0.0] port [3389> Aug 15 08:44:54 Demonstrator xrdp[186640]: [INFO ] listening to port 3389 on 0.> Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] g_tcp_bind(7, 3389) failed b> Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] trans_listen_address failed Aug 15 08:44:54 Demonstrator xrdp[186640]: [ERROR] Failed to start xrdp daemon,> Aug 15 08:44:54 Demonstrator systemd[1]: xrdp.service: Control process exited, > Aug 15 08:44:54 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit> Aug 15 08:44:54 Demonstrator systemd[1]: Failed to start xrdp daemon.


     Could this page [https://community.spiceworks.com/how_to/195154-how-to-set-up-and-use-remote-desktop-connection-in-ubuntu-linux](https://community.spiceworks.com/how_to/195154-how-to-set-up-and-use-remote-desktop-connection-in-ubuntu-linux)  give a solution (shown below) to this bug even though it applies to  Ubuntu 18.04 and the bug gives a slightly different problem?
Solution is:
he problem is related to the xorgxrdp package and the particular changes  in Ubuntu 18.04 that caused xrdp capability breakage. In this guide, we  use Ubuntu 18.04.2 to configure xrdp. To solve the empty blue screen  problem, install the relevant xorgxrdp-hwe by executing the following  command:
 sudo apt-get install xorgxrdp-hwe-18.04
 To check the current version of Ubuntu, use this command:
 lsb_release -a
 Restart the xrdp service (daemon):
 sudo /etc/init.d/xrdp restart
 After the required package is installed, open the RDP client. Then, try using RDP to connect to your Ubuntu again.

---

### Post by johnaaronrose on 2023-08-23
Used the webpage at [https://orcacore.com/install-configure-xrdp-ubuntu-22-04/](https://orcacore.com/install-configure-xrdp-ubuntu-22-04/). xrdp got further but it fails with:
john@Demonstrator:~$ sudo systemctl restart xrdp
Job for xrdp.service failed because the control process exited with error code.
See "systemctl status xrdp.service" and "journalctl -xeu xrdp.service" for details.
john@Demonstrator:~$ sudo systemctl status xrdp
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Wed 2023-08-23 12:25:56 BST; 7s ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 1334827 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 1334835 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=1/FAILURE)
        CPU: 17ms

 Aug 23 12:25:56 Demonstrator systemd[1]: Starting xrdp daemon...
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (err>
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] trans_listen_address failed
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit-code'.
Aug 23 12:25:56 Demonstrator systemd[1]: Failed to start xrdp daemon.
lines 1-18/18 (END

---

### Post by johnaaronrose on 2023-08-23
I forgot to show the changes from the web page referred to in my last message:
From the installation, XRDP added a user named &#8220;**xrdp**&#8221;. The xrdp session uses a certificate key file &#8220;/etc/ssl/private/ssl-cert-snakeoil.key&#8221;.
You need to add the **xrdp user** to the &#8220;ssl-cert&#8221; group with the following command:

sudo usermod -a -G ssl-cert xrdp Now you need to edit the /etc/xrdp/startwm.sh file. Open the XRDP file on Ubuntu 22.04 with your favorite text editor, here we use vi:
sudo vi /etc/xrdp/startwm.sh Add the following commands before the commands that test & execute Xsession:
Unset DBUS_SESSION_ADDRESS
Unset XDG_RUNTIME_DIR...
if test -r /etc/profile; then
. /etc/profile
fi

[COLOR=#ff0000]Unset DBUS_SESSION_ADDRESS[/COLOR]
[COLOR=#ff0000]Unset XDG_RUNTIME_DIRUnset[/COLOR]

test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec /bin/sh /etc/X11/XsessionWhen you are done, save and close the file.
To apply these changes restart XRDP on Ubuntu 22.04 with the following command:
sudo systemctl restart xrdp

---

### Post by johnaaronrose on 2023-08-23
Used the webpage at [https://orcacore.com/install-configure-xrdp-ubuntu-22-04/](https://orcacore.com/install-configure-xrdp-ubuntu-22-04/). xrdp got further but it fails with:
john@Demonstrator:~$ sudo systemctl restart xrdp
Job for xrdp.service failed because the control process exited with error code.
See "systemctl status xrdp.service" and "journalctl -xeu xrdp.service" for details.
john@Demonstrator:~$ sudo systemctl status xrdp
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Wed 2023-08-23 12:25:56 BST; 7s ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 1334827 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 1334835 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=1/FAILURE)
        CPU: 17ms

 Aug 23 12:25:56 Demonstrator systemd[1]: Starting xrdp daemon...
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (err>
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] trans_listen_address failed
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit-code'.
Aug 23 12:25:56 Demonstrator systemd[1]: Failed to start xrdp daemon.
lines 1-18/18 (END

---

### Post by johnaaronrose on 2023-08-23
> **johnaaronrose said:**
> Used the webpage at [https://orcacore.com/install-configure-xrdp-ubuntu-22-04/](https://orcacore.com/install-configure-xrdp-ubuntu-22-04/). xrdp got further but it fails with:
john@Demonstrator:~$ sudo systemctl restart xrdp
Job for xrdp.service failed because the control process exited with error code.
See "systemctl status xrdp.service" and "journalctl -xeu xrdp.service" for details.
john@Demonstrator:~$ sudo systemctl status xrdp
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Wed 2023-08-23 12:25:56 BST; 7s ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 1334827 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 1334835 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=1/FAILURE)
        CPU: 17ms

 Aug 23 12:25:56 Demonstrator systemd[1]: Starting xrdp daemon...
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (err>
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] trans_listen_address failed
Aug 23 12:25:56 Demonstrator xrdp[1334835]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE
Aug 23 12:25:56 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit-code'.
Aug 23 12:25:56 Demonstrator systemd[1]: Failed to start xrdp daemon.
lines 1-18/18 (END

Here is startwm.sh:
[ATTACH]292641[/ATTACH]

---

### Post by johnaaronrose on 2023-08-25
I've just tried the changes outlined at [https://pimylifeup.com/ubuntu-xrdp/](https://pimylifeup.com/ubuntu-xrdp/)

After stopping the xrdp service & starting the service again it failed to start properly, its status is:
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2023-08-25 11:43:52 BST; 16s ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 1601088 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 1601096 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=1/FAILURE)
        CPU: 17ms

Aug 25 11:43:52 Demonstrator systemd[1]: Starting xrdp daemon...
Aug 25 11:43:52 Demonstrator xrdp[1601096]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 25 11:43:52 Demonstrator xrdp[1601096]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 25 11:43:52 Demonstrator xrdp[1601096]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) an>
Aug 25 11:43:52 Demonstrator xrdp[1601096]: [ERROR] trans_listen_address failed
Aug 25 11:43:52 Demonstrator xrdp[1601096]: [ERROR] Failed to start xrdp daemon, possibly address alre>
Aug 25 11:43:52 Demonstrator systemd[1]: xrdp.service: Control process exited, code=exited, status=1/F>
Aug 25 11:43:52 Demonstrator systemd[1]: xrdp.service: Failed with result 'exit-code'.
Aug 25 11:43:52 Demonstrator systemd[1]: Failed to start xrdp daemon.

---

### Post by johnaaronrose on 2023-09-25
xrdp now seems to start OK but Errors in Status:
root@Demonstrator:/home/john# service xrdp start
root@Demonstrator:/home/john# service xrdp status
&#9679; xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: >
     Active: active (running) since Sun 2023-09-24 09:00:24 BST; 1 day 4h ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
   Main PID: 956 (xrdp)
      Tasks: 1 (limit: 18961)
     Memory: 2.3M
        CPU: 1.499s
     CGroup: /system.slice/xrdp.service
             &#9492;&#9472;956 /usr/sbin/xrdp

Sep 25 13:18:27 Demonstrator xrdp[609603]: [ERROR] xrdp_iso_send: trans_write_c>
Sep 25 13:18:27 Demonstrator xrdp[609603]: [ERROR] Sending [ITU T.125] Disconne>
Sep 25 13:26:14 Demonstrator xrdp[956]: [INFO ] Socket 12: AF_INET6 connection >
Sep 25 13:26:14 Demonstrator xrdp[612419]: [INFO ] Using default X.509 certific>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [INFO ] Using default X.509 key file>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [ERROR] libxrdp_force_read: bad head>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [ERROR] [ITU-T X.224] Connection Seq>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [ERROR] xrdp_sec_incoming: xrdp_iso_>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [ERROR] xrdp_rdp_incoming: xrdp_sec_>
Sep 25 13:26:14 Demonstrator xrdp[612419]: [ERROR] xrdp_process_main_loop: libx>
lines 1-22/22 (END)

Remmina still cannot connect.

---

### Post by johnaaronrose on 2023-10-03
I'm wondering if anyone has managed to make xrdp (on Ubuntu 22.04) run correctly!

---

### Post by vincentertainment on 2023-11-30
I'm getting the same errors. This started about a week ago. I believe I had just rebooted after installing updates. I have tried purging xrdp and reinstalling and configuring. Still getting the same errors.

```

Nov 30 14:22:27 hq-lt-01 xrdp[15981]: [INFO ] address [0.0.0.0] port [3389] mode 1
Nov 30 14:22:27 hq-lt-01 xrdp[15981]: [INFO ] listening to port 3389 on 0.0.0.0
Nov 30 14:22:27 hq-lt-01 xrdp[15981]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (errno=22).
Nov 30 14:22:27 hq-lt-01 xrdp[15981]: [ERROR] trans_listen_address failed
Nov 30 14:22:27 hq-lt-01 xrdp[15981]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Nov 30 14:22:27 hq-lt-01 systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE

```

---

