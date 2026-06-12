---
title: "listening ports are closed?"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by BeardedLinuxGeek on 2009-06-27
hostname: torrentfreak
local ip: 192.168.2.2

I run "netstat -l" and it tells me its listening on 27015 as well as on 565
```

colin@torrentfreak:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 torrentfreak:27015      *:*                     LISTEN
tcp        0      0 *:565                   *:*                     LISTEN

```I run a port scan on the computer of itself and  it tells me 27015 is closed and 565 is open
```

colin@torrentfreak:~$ nmap 127.0.0.1 -p 27015,565

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-27 19:20 EDT
Interesting ports on localhost (127.0.0.1):
PORT      STATE  SERVICE
565/tcp   open   unknown
27015/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds
colin@torrentfreak:~$

```What on earth is going on?
Btw the way:
565 is sshd and I can connect to it via LAN or internet
27015 is srcds (counter strike server) and I can connect to it from LAN but not internet. Interesting that I can connect from LAN even if the port claims its closed

Just incase it is relevent, here is the full output of netstat -l
```

colin@torrentfreak:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 torrentfreak:27015      *:*                     LISTEN
tcp        0      0 *:565                   *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN
tcp6       0      0 [::]:565                [::]:*                  LISTEN
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN
udp        0      0 *:27015                 *:*
udp        0      0 torrentfreak:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 torrentfrea:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
udp    11088      0 *:27020                 *:*
udp        0      0 *:26901                 *:*
udp        0      0 *:44760                 *:*
udp        0      0 *:mdns                  *:*
udp        0      0 *:27005                 *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     7832     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     6818     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     7831     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     5774     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     6816     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     7076     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     5569     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     7130     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     6886     /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     5996     @/var/run/hald/dbus-RhXMAYBV9K
unix  2      [ ACC ]     STREAM     LISTENING     5961     @/var/run/hald/dbus-1LJ5oa5bCW
colin@torrentfreak:~$

```What the heck am I doing wrong?

---

### Post by The Cog on 2009-06-28
**netatat -ln** will tell you more information. I can see that port 565 is listening on ip address * which means any IP address on the machine. Port 27015 on the other hand, is listening on one specific IP address only (torrentfreak) and I guess that's not the address you're trying to connect to.

---

