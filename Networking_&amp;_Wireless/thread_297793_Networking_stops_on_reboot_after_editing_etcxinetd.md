---
title: "Networking stops on reboot after editing /etc/xinetd.d/Xvnc"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by grahams on 2006-11-11
Hi

I'm running edgy and after editing /etc/xinetd.d/Xvnc to correctly locate the fonts (see [http://www.ubuntuforums.org/showpost.php?p=1729632&postcount=174](http://www.ubuntuforums.org/showpost.php?p=1729632&postcount=174)) I got vnc working again (was working before dapper -> edgy upgrade), all was well (for a couple of days) until I rebooted.

Now after a rebooting I lose my networking. After a lot of head scratching I copy my orginal /etc/xinetd.d/Xvnc back rebooted and had my networking back, but no vnc.

I did actually the same steps on another system I upgraded to Edgy and everything works fine.

Here is my /etc/xinetd.d/Xvnc that works with VNC but kills networking on reboot.

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

I've scanned /etc/services and nothing is using port 5901

Any clues as to what is happening ??

Many thanks

---

### Post by grahams on 2006-12-21
I tracked this problem and it wasn't related to  /etc/xinetd.d/Xvnc. On my system(HP omnibook 6100) the wireless LAN usually doesn't come up correctly after a restart. I need to power off the system and boot for the wireless lan to come up. The issue only started after upgrading to Edgy,

---

