---
title: "TCP/IP Ports problem (I'm paranoid)"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by personjerry on 2008-09-17
OK how do I close my ports?
And how do I check which ports are being used by which programs?
What's scaring me is that some of my ports say "unknown", and some ports between 32000 or so and around 65000 or so keep randomly opening.
Help?

Edit: Also, port 15000 is open, saying unknown?

Edit: My netstat -l results:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:xmpp-client           *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:xmpp-server           *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:15000                 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
udp        0      0 192.168.2.10:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.2.1:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:41819                 *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     13056    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     13844    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     14900    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18163    /tmp/orbit-user/linc-18cc-0-155972204ee51
unix  2      [ ACC ]     STREAM     LISTENING     15110    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14857    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18177    /tmp/orbit-user/linc-18ca-0-4dc788d25bb38
unix  2      [ ACC ]     STREAM     LISTENING     18225    /tmp/keyring-iLjSns/socket
unix  2      [ ACC ]     STREAM     LISTENING     18230    /tmp/keyring-iLjSns/ssh
unix  2      [ ACC ]     STREAM     LISTENING     18232    /tmp/keyring-iLjSns/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18626    /tmp/orbit-user/linc-18cf-0-4cc9ef3557ab2
unix  2      [ ACC ]     STREAM     LISTENING     14095    /var/run/clamav/clamd.ctl
unix  2      [ ACC ]     STREAM     LISTENING     18673    /tmp/seahorse-fHtSdM/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18723    /tmp/orbit-user/linc-18cf-0-39b91b5fd67df
unix  2      [ ACC ]     STREAM     LISTENING     18729    /tmp/.ICE-unix/6351
unix  2      [ ACC ]     STREAM     LISTENING     18801    /tmp/orbit-user/linc-1927-0-7ad79e3514182
unix  2      [ ACC ]     STREAM     LISTENING     13846    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     21583    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     21588    /tmp/pulse-user/native
unix  2      [ ACC ]     STREAM     LISTENING     21634    /tmp/orbit-user/linc-1930-0-7ddd48ae35752
unix  2      [ ACC ]     STREAM     LISTENING     21944    /tmp/orbit-user/linc-1938-0-481976a5ed9b2
unix  2      [ ACC ]     STREAM     LISTENING     22134    /tmp/orbit-user/linc-193f-0-74109b1f5763d
unix  2      [ ACC ]     STREAM     LISTENING     22203    /tmp/orbit-user/linc-1941-0-74109b1f84ae1
unix  2      [ ACC ]     STREAM     LISTENING     22935    /tmp/orbit-user/linc-1998-0-ecb7d617755
unix  2      [ ACC ]     STREAM     LISTENING     23025    /tmp/orbit-user/linc-198c-0-22388b157b7e1
unix  2      [ ACC ]     STREAM     LISTENING     23032    /tmp/orbit-user/linc-1988-0-4345c0647cd30
unix  2      [ ACC ]     STREAM     LISTENING     23045    /tmp/orbit-user/linc-1994-0-ecb7d619141c
unix  2      [ ACC ]     STREAM     LISTENING     23186    /tmp/orbit-user/linc-194a-0-2f73ad35ae3eb
unix  2      [ ACC ]     STREAM     LISTENING     23315    /tmp/orbit-user/linc-1993-0-58d5bc356b0b8
unix  2      [ ACC ]     STREAM     LISTENING     23320    /tmp/orbit-user/linc-199d-0-355287a46e424
unix  2      [ ACC ]     STREAM     LISTENING     23505    /tmp/orbit-user/linc-199b-0-71c6f639ac6b8
unix  2      [ ACC ]     STREAM     LISTENING     23627    /tmp/orbit-user/linc-19af-0-3df4900a171be
unix  2      [ ACC ]     STREAM     LISTENING     24048    /tmp/orbit-user/linc-19c5-0-2b7dceea3c920
unix  2      [ ACC ]     STREAM     LISTENING     24223    /tmp/orbit-user/linc-19c8-0-525f262bca627
unix  2      [ ACC ]     STREAM     LISTENING     24246    /tmp/orbit-user/linc-19ce-0-525f262bdf64d
unix  2      [ ACC ]     STREAM     LISTENING     24267    /tmp/orbit-user/linc-19cb-0-525f262beec1c
unix  2      [ ACC ]     STREAM     LISTENING     1203726  /tmp/orbit-user/linc-286d-0-17eee16a29832
unix  2      [ ACC ]     STREAM     LISTENING     238106   /tmp/orbit-user/linc-22e8-0-3bb4470dd51b0
unix  2      [ ACC ]     STREAM     LISTENING     1270694  /tmp/orbit-user/linc-2ba6-0-6c11ec84c7d8a
unix  2      [ ACC ]     STREAM     LISTENING     13950    @/var/run/hald/dbus-UDcYG5vGB6
unix  2      [ ACC ]     STREAM     LISTENING     1346483  /tmp/orbit-user/linc-2c1d-0-189047f117907
unix  2      [ ACC ]     STREAM     LISTENING     1616637  /tmp/orbit-user/linc-2c7f-0-1e22bdb39c7e8
unix  2      [ ACC ]     STREAM     LISTENING     1346476  /tmp/gnome-system-monitor.user.3437553326
unix  2      [ ACC ]     STREAM     LISTENING     118862   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     13947    @/var/run/hald/dbus-kWH7F3CPmv
unix  2      [ ACC ]     STREAM     LISTENING     13191    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12956    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18754    @/tmp/dbus-ZzgQ7BB4P5


```

---

### Post by personjerry on 2008-09-18
bump

---

### Post by warchief_ryan on 2008-09-18
The method of closing your ports depends on if your using iptables directly or ufw.

With ufw you can 'sudo ufw default deny' to have a deny all policy, so only the ports you open(by adding ufw rules to allow them) are allowed.

With iptables you have you change the various chains default policy's also to have a deny all posture, but with 'sudo iptables -P INPUT DROP' and for outward packets just replace INPUT with OUTPUT, then you can add rules for ports you want allowed.

Lastly you don't have ports opening and closing themselves randomly its just netstat will show current connections and there states, so it was just you didn't have any earlier and now do when you checked netstat again. The ports were always open.

Hope that helped.

---

### Post by bab1 on 2008-09-19
The correct command to look at open TCP/UDP ports is:```
netstat -nltu
```

The results look like this:
```
bruce@malibu:~>netstat -nltu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*              LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          
udp        0      0 192.168.1.12:137        0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 192.168.1.12:138        0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*   
```

If you use:```
netstat -ltu
``` you will see the server names but not the port numbers.

Everything below: 
> Active UNIX domain sockets
in your original post is internal to the host.  They are UNIX sockets not TCP/UDP ports.

I don't see any problems with your ports.

---

### Post by gombadi on 2008-09-19
If you add a -p to the netstat command it will tell you the process that is listening on the port.

Note you need to be root to use -p so enter the command as root or use sudo.

```

sudo netstat -plntu

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5320/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      5263/sshd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           5853/dhclient   
udp        0      0 0.0.0.0:52190           0.0.0.0:*                           5287/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5287/avahi-daemon: 


```

---

