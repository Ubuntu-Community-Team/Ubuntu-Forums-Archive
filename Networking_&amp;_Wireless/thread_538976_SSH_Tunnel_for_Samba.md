---
title: "SSH Tunnel for Samba"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by nachtkrab on 2007-08-30
Hello guys,

I was working through [this]("http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm") tutorial (see linux section) to get connected to a smb over ssh tunnel to a server on the internet.
I got it working with Fedora Core 6 but not on Ubuntu :(

ssh -l myUsername internetServerIP -L 139:127.0.0.1:139 works fine when I do a telnet 127.0.0.1 139 on FC but on Ubuntu I get the following error each time in the tunnels window: 
channel 3: open failed: connect failed: Connection refused

Hope you have any ideas :)

Regards,
nachtkrab

---

