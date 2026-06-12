---
title: "TCP connet: No route to host"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by esolve on 2015-10-14
I started a tcp server on a host A and then start a tcp client on another host B.
both hosts are in the same LAN via the wireless router at home.
the tcp client tries to connect to tcp server on port 8000. but it failed due to " No route to host"
I can ping successfully the server host from the client host, and actually I'm ssh into the server from the client now


what is wrong with the server host?  are there any iptable rules which filter the packets? if so, how to restore to normal?


the result of ss -tlnp is as below (when the tcp server is running):


```



[root@god relay]# ss -tlnp
State       Recv-Q Send-Q                                       Local Address:Port                                         Peer Address:Port 
LISTEN      0      5                                                        *:8000                                                    *:*      users:(("server",6084,3))
LISTEN      0      128                                              127.0.0.1:17600                                                   *:*      users:(("dropbox",2348,32))
LISTEN      0      128                                                     :::513                                                    :::*      users:(("systemd",1,20))
LISTEN      0      128                                                     :::514                                                    :::*      users:(("systemd",1,19))
LISTEN      0      128                                              127.0.0.1:17603                                                   *:*      users:(("dropbox",2348,47))
LISTEN      0      50                                                       *:3306                                                    *:*      users:(("mysqld",1599,10))
LISTEN      0      128                                                      *:56813                                                   *:*      users:(("rpc.statd",1248,9))
LISTEN      0      128                                                     :::111                                                    :::*      users:(("rpcbind",1229,12))
LISTEN      0      128                                                      *:111                                                     *:*      users:(("rpcbind",1229,9))
LISTEN      0      128                                                     :::50099                                                  :::*      users:(("rpc.statd",1248,11))
LISTEN      0      128                                                     :::22                                                     :::*      users:(("sshd",1254,4))
LISTEN      0      128                                                      *:22                                                      *:*      users:(("sshd",1254,3))
LISTEN      0      100                                              127.0.0.1:25                                                      *:*      users:(("master",1737,12))
LISTEN      0      5                                                127.0.0.1:29754                                                   *:*      users:(("vpnagentd",1267,15))
LISTEN      0      128                                                      *:17500                                                   *:*     

```


```

[root@god relay]# netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      6084/./server       
tcp        0      0 127.0.0.1:17600         0.0.0.0:*               LISTEN      2348/dropbox        
tcp        0      0 127.0.0.1:17603         0.0.0.0:*               LISTEN      2348/dropbox        
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      1599/mysqld         
tcp        0      0 0.0.0.0:56813           0.0.0.0:*               LISTEN      1248/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1229/rpcbind        
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1254/sshd           
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1737/master         
tcp        0      0 127.0.0.1:29754         0.0.0.0:*               LISTEN      1267/vpnagentd      
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      2348/dropbox        
tcp6       0      0 :::513                  :::*                    LISTEN      1/systemd           
tcp6       0      0 :::514                  :::*                    LISTEN      1/systemd           
tcp6       0      0 :::111                  :::*                    LISTEN      1229/rpcbind        
tcp6       0      0 :::50099                :::*                    LISTEN      1248/rpc.statd      
tcp6       0      0 :::22                   :::*                    LISTEN      1254/sshd           
udp        0      0 0.0.0.0:32962           0.0.0.0:*                           4912/dhclient       
udp        0      0 0.0.0.0:979             0.0.0.0:*                           1229/rpcbind        
udp        0      0 127.0.0.1:1001          0.0.0.0:*                           1248/rpc.statd      
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           2348/dropbox        
udp        0      0 0.0.0.0:48983           0.0.0.0:*                           1248/rpc.statd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4912/dhclient       
udp        0      0 0.0.0.0:111             0.0.0.0:*                           1229/rpcbind        
udp        0      0 192.168.0.107:123       0.0.0.0:*                           639/ntpd            
udp        0      0 127.0.0.1:123           0.0.0.0:*                           639/ntpd            
udp        0      0 0.0.0.0:123             0.0.0.0:*                           639/ntpd            
udp6       0      0 :::979                  :::*                                1229/rpcbind        
udp6       0      0 :::44330                :::*                                1248/rpc.statd      
udp6       0      0 :::34269                :::*                                4912/dhclient       
udp6       0      0 :::111                  :::*                                1229/rpcbind        
udp6       0      0 fe80::5e26:aff:fe2b:123 :::*                                639/ntpd            
udp6       0      0 ::1:123                 :::*                                639/ntpd            
udp6       0      0 :::123                  :::*                                639/ntpd            
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name     Path
unix  2      [ ACC ]     STREAM     LISTENING     30253    1899/gnome-session   @/tmp/.ICE-unix/1899
unix  2      [ ACC ]     STREAM     LISTENING     29511    2318/gvfsd-trash     @/dbus-vfs-daemon/socket-SVPQYvtM
unix  2      [ ACC ]     STREAM     LISTENING     29930    1599/mysqld          /var/lib/mysql/mysql.sock
unix  2      [ ACC ]     STREAM     LISTENING     26632    1737/master          public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     10255    1/systemd            /run/systemd/journal/stdout
unix  2      [ ACC ]     STREAM     LISTENING     30731    2318/gvfsd-trash     @/dbus-vfs-daemon/socket-XhGXwzm8
unix  2      [ ACC ]     STREAM     LISTENING     25529    1742/dbus-daemon     @/tmp/dbus-iAvdLGVeHX
unix  2      [ ACC ]     STREAM     LISTENING     24506    1735/dbus-daemon     @/tmp/dbus-aQRODrAQdd
unix  2      [ ACC ]     STREAM     LISTENING     30236    1979/ssh-agent       /tmp/ssh-LzmngdqhkKkz/agent.1899
unix  2      [ ACC ]     SEQPACKET  LISTENING     12319    1/systemd            /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     20969    605/abrtd            /var/run/abrt/abrt.socket
unix  2      [ ACC ]     STREAM     LISTENING     14888    1/systemd            /var/run/pcscd/pcscd.comm
unix  2      [ ACC ]     STREAM     LISTENING     30254    1899/gnome-session   /tmp/.ICE-unix/1899
unix  2      [ ACC ]     STREAM     LISTENING     25290    1219/libvirtd        /var/run/libvirt/libvirt-sock
unix  2      [ ACC ]     STREAM     LISTENING     23507    1219/libvirtd        /var/run/libvirt/libvirt-sock-ro
unix  2      [ ACC ]     STREAM     LISTENING     29243    2030/pulseaudio      /tmp/.esd-40078/socket
unix  2      [ ACC ]     STREAM     LISTENING     28841    1890/gnome-keyring-  /user/wgong/home/.cache/keyring-ccS70c/control
unix  2      [ ACC ]     STREAM     LISTENING     30292    1890/gnome-keyring-  /user/wgong/home/.cache/keyring-ccS70c/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     14887    1/systemd            /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     30321    2030/pulseaudio      /var/tmp/pulse-vDgqiPzvevUy/dbus-socket
unix  2      [ ACC ]     STREAM     LISTENING     30293    1890/gnome-keyring-  /user/wgong/home/.cache/keyring-ccS70c/gpg
unix  2      [ ACC ]     STREAM     LISTENING     30295    1890/gnome-keyring-  /user/wgong/home/.cache/keyring-ccS70c/ssh
unix  2      [ ACC ]     STREAM     LISTENING     18769    702/iscsiuio         @ISCSID_UIP_ABSTRACT_NAMESPACE
unix  2      [ ACC ]     STREAM     LISTENING     17861    1/systemd            /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     589      1/systemd            /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     21587    580/bluetoothd       @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     24032    1366/X               @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17862    1/systemd            /var/run/rpcbind.sock
unix  2      [ ACC ]     STREAM     LISTENING     26637    1737/master          private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     26640    1737/master          private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     28861    1909/dbus-daemon     @/tmp/dbus-qBzuTSJuRz
unix  2      [ ACC ]     STREAM     LISTENING     18542    593/gpm              /dev/gpmctl
unix  2      [ ACC ]     STREAM     LISTENING     26643    1737/master          private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     17863    1/systemd            /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18744    580/bluetoothd       /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     26646    1737/master          private/defer
unix  2      [ ACC ]     STREAM     LISTENING     26649    1737/master          private/trace
unix  2      [ ACC ]     STREAM     LISTENING     21529    645/mcelog           /var/run/mcelog-client
unix  2      [ ACC ]     STREAM     LISTENING     30585    2230/dbus-daemon     @/tmp/dbus-rnoXhAqtEp
unix  2      [ ACC ]     STREAM     LISTENING     29246    2030/pulseaudio      /var/tmp/pulse-vDgqiPzvevUy/native
unix  2      [ ACC ]     STREAM     LISTENING     18642    644/acpid            /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     26652    1737/master          private/verify
unix  2      [ ACC ]     STREAM     LISTENING     30739    2497/ibus-daemon     @/tmp/dbus-8H1V6Ko7
unix  2      [ ACC ]     STREAM     LISTENING     26655    1737/master          public/flush
unix  2      [ ACC ]     STREAM     LISTENING     26658    1737/master          private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     30887    2348/dropbox         /user/wgong/home/.dropbox/command_socket
unix  2      [ ACC ]     STREAM     LISTENING     30888    2348/dropbox         /user/wgong/home/.dropbox/iface_socket
unix  2      [ ACC ]     STREAM     LISTENING     26661    1737/master          private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     22756    1229/rpcbind         /var/run/rpcbind.sock
unix  2      [ ACC ]     STREAM     LISTENING     26664    1737/master          private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     26667    1737/master          private/relay
unix  2      [ ACC ]     STREAM     LISTENING     26670    1737/master          public/showq
unix  2      [ ACC ]     STREAM     LISTENING     26673    1737/master          private/error
unix  2      [ ACC ]     STREAM     LISTENING     26676    1737/master          private/retry
unix  2      [ ACC ]     STREAM     LISTENING     26679    1737/master          private/discard
unix  2      [ ACC ]     STREAM     LISTENING     26682    1737/master          private/local
unix  2      [ ACC ]     STREAM     LISTENING     26685    1737/master          private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     26688    1737/master          private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     26691    1737/master          private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     26694    1737/master          private/scache
unix  2      [ ACC ]     STREAM     LISTENING     24033    1366/X               /tmp/.X11-unix/X0



```




```

[root@god cap]# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
INPUT_direct  all  --  0.0.0.0/0            0.0.0.0/0           
INPUT_ZONES_SOURCE  all  --  0.0.0.0/0            0.0.0.0/0           
INPUT_ZONES  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
FORWARD_direct  all  --  0.0.0.0/0            0.0.0.0/0           
FORWARD_IN_ZONES_SOURCE  all  --  0.0.0.0/0            0.0.0.0/0           
FORWARD_IN_ZONES  all  --  0.0.0.0/0            0.0.0.0/0           
FORWARD_OUT_ZONES_SOURCE  all  --  0.0.0.0/0            0.0.0.0/0           
FORWARD_OUT_ZONES  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
OUTPUT_direct  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FORWARD_IN_ZONES (1 references)
target     prot opt source               destination         
FWDI_public  all  --  0.0.0.0/0            0.0.0.0/0           
FWDI_public  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FORWARD_IN_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_OUT_ZONES (1 references)
target     prot opt source               destination         
FWDO_public  all  --  0.0.0.0/0            0.0.0.0/0           
FWDO_public  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FORWARD_OUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_direct (1 references)
target     prot opt source               destination         


Chain FWDI_public (2 references)
target     prot opt source               destination         
FWDI_public_log  all  --  0.0.0.0/0            0.0.0.0/0           
FWDI_public_deny  all  --  0.0.0.0/0            0.0.0.0/0           
FWDI_public_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FWDI_public_allow (1 references)
target     prot opt source               destination         


Chain FWDI_public_deny (1 references)
target     prot opt source               destination         


Chain FWDI_public_log (1 references)
target     prot opt source               destination         


Chain FWDO_external (0 references)
target     prot opt source               destination         
FWDO_external_log  all  --  0.0.0.0/0            0.0.0.0/0           
FWDO_external_deny  all  --  0.0.0.0/0            0.0.0.0/0           
FWDO_external_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FWDO_external_allow (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           


Chain FWDO_external_deny (1 references)
target     prot opt source               destination         


Chain FWDO_external_log (1 references)
target     prot opt source               destination         


Chain FWDO_public (2 references)
target     prot opt source               destination         
FWDO_public_log  all  --  0.0.0.0/0            0.0.0.0/0           
FWDO_public_deny  all  --  0.0.0.0/0            0.0.0.0/0           
FWDO_public_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain FWDO_public_allow (1 references)
target     prot opt source               destination         


Chain FWDO_public_deny (1 references)
target     prot opt source               destination         


Chain FWDO_public_log (1 references)
target     prot opt source               destination         


Chain INPUT_ZONES (1 references)
target     prot opt source               destination         
IN_public  all  --  0.0.0.0/0            0.0.0.0/0           
IN_public  all  --  0.0.0.0/0            0.0.0.0/0           


Chain INPUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain INPUT_direct (1 references)
target     prot opt source               destination         


Chain IN_dmz (0 references)
target     prot opt source               destination         
IN_dmz_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_dmz_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_dmz_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_dmz_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW


Chain IN_dmz_deny (1 references)
target     prot opt source               destination         


Chain IN_dmz_log (1 references)
target     prot opt source               destination         


Chain IN_external (0 references)
target     prot opt source               destination         
IN_external_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_external_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_external_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_external_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW


Chain IN_external_deny (1 references)
target     prot opt source               destination         


Chain IN_external_log (1 references)
target     prot opt source               destination         


Chain IN_home (0 references)
target     prot opt source               destination         
IN_home_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_home_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_home_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_home_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:631 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138 ctstate NEW


Chain IN_home_deny (1 references)
target     prot opt source               destination         


Chain IN_home_log (1 references)
target     prot opt source               destination         


Chain IN_internal (0 references)
target     prot opt source               destination         
IN_internal_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_internal_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_internal_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_internal_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:631 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138 ctstate NEW


Chain IN_internal_deny (1 references)
target     prot opt source               destination         


Chain IN_internal_log (1 references)
target     prot opt source               destination         


Chain IN_public (2 references)
target     prot opt source               destination         
IN_public_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_public_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_public_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_public_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353 ctstate NEW


Chain IN_public_deny (1 references)
target     prot opt source               destination         


Chain IN_public_log (1 references)
target     prot opt source               destination         


Chain IN_work (0 references)
target     prot opt source               destination         
IN_work_log  all  --  0.0.0.0/0            0.0.0.0/0           
IN_work_deny  all  --  0.0.0.0/0            0.0.0.0/0           
IN_work_allow  all  --  0.0.0.0/0            0.0.0.0/0           


Chain IN_work_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353 ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:631 ctstate NEW


Chain IN_work_deny (1 references)
target     prot opt source               destination         


Chain IN_work_log (1 references)
target     prot opt source               destination         


Chain OUTPUT_direct (1 references)
target     prot opt source               destination



```




if I swap the two hosts, namely  I started the tcp server on the host B and then start the tcp client on the host A.  then the TCP connection is successful



The related tcp client and server are:
[http://www.cs.cmu.edu/afs/cs/academic/class/15213-f99/www/class26/tcpserver.c](http://www.cs.cmu.edu/afs/cs/academic/class/15213-f99/www/class26/tcpserver.c)


[http://www.cs.cmu.edu/afs/cs/academic/class/15213-f99/www/class26/tcpclient.c](http://www.cs.cmu.edu/afs/cs/academic/class/15213-f99/www/class26/tcpclient.c)

---

### Post by Doug S on 2015-10-15
> **esolve said:**
> the tcp client tries to connect to tcp server on port 8000. but it failed due to " No route to host"
I can ping successfully the server host from the client host, and actually I'm ssh into the server from the client now
what is wrong with the server host?  are there any iptable rules which filter the packets? if so, how to restore to normal?
All that you have said makes sense in the context of the iptables rule set you listed.

To add the ability to access port 8000 via tcp, just copy every tcp port 22 line in your rule set and change port 22 to port 8000.

---

### Post by esolve on 2015-10-15
> **Doug S said:**
> All that you have said makes sense in the context of the iptables rule set you listed.

To add the ability to access port 8000 via tcp, just copy every tcp port 22 line in your rule set and change port 22 to port 8000.

what are the steps? I'm not familiar with iptables, thank you!

---

### Post by Doug S on 2015-10-15
> **esolve said:**
> what are the steps? I'm not familiar with iptables, thank you!Well, that's a good question. The answer depends on how the master rule set was done on your system. There are several methods. For example, and because I do some directly related things, I use a script and launch it via a "pre-up" command within my /etc/network/interfaces file. Some, and I used to also, use a directive within the /etc/rc2.d directory. Some, and I used to also, use direct iptables-save and iptables-restore commands, somehow autorun during startup, similar to previously mentioned methods. Some, and I never have and know nothing about it, use a package called "iptables-persistent" to help manage things. Sometimes the iptables rule set is generated by some higher level program such as ufw, but that doesn't appear to be the case for yours, at least I don't recognize it as such. There are probably other methods also.

You will have to figure out which method your system is using, so that you can be sure to make the changes in such a way as to to be applied to the "master" file.

---

