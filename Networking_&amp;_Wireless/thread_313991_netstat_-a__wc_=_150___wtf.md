---
title: "netstat -a | wc = 150  ?? wtf"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by emersony on 2006-12-06
ok, so there is a load of crap making connections on my dapper machine and I can't figure out why or what it is. This is not happening on my breezy or hoary machines, nor on my server. So I am hoping someone can help me figure out where all these connections are coming from on a machine that is not connected to the internet in anyway. 

First, here is the output of ps ax:

  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:03 init [2]         
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S      0:00 [watchdog/0]
    4 ?        S<     0:04 [events/0]
    5 ?        S<     0:00 [khelper]
    6 ?        S<     0:00 [kthread]
    8 ?        S<     0:01 [kblockd/0]
    9 ?        S<     0:00 [kacpid]
  104 ?        S      0:00 [pdflush]
  105 ?        S      0:09 [pdflush]
  107 ?        S<     0:00 [aio/0]
  106 ?        S      0:00 [kswapd0]
  694 ?        S<     0:00 [kseriod]
 1790 ?        S<     0:00 [khubd]
 1861 ?        S      1:11 [kjournald]
 2094 ?        S<s    0:01 /sbin/udevd --daemon
 2891 ?        S<     0:00 [kgameportd]
 2888 ?        S      0:00 [shpchpd_event]
 3943 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 3945 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 3964 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 3979 ?        Ss     0:04 /usr/sbin/hald
 3980 ?        S      0:00 hald-runner
 3985 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 3990 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 3994 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4043 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4050 ?        S      0:14 /usr/lib/hal/hald-addon-storage
 4051 ?        R      0:01 /usr/lib/hal/hald-addon-storage
 4138 ?        S      0:02 python /usr/sbin/hpssd
 4365 ?        Ss     0:00 /usr/lib/postfix/master
 4399 ?        Ss     0:13 /usr/sbin/nmbd -D
 4419 ?        Ss     0:00 /usr/sbin/sshd
 4475 ?        Ss     0:00 hcid: processing events
 4481 ?        Ss     0:00 /usr/sbin/sdpd
 4490 ?        S<     0:00 [krfcommd]
 4503 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4537 ?        Ss     0:00 /usr/sbin/atd
 4550 ?        Ss     0:00 /usr/sbin/cron
 4902 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5012 ?        S      0:00 qmgr -l -t fifo -u -c
 5053 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
 5888 ?        SNs    0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 5908 ?        SNs    0:00 /usr/sbin/apache2 -k start -DSSL
 5911 ?        SN     0:00 /usr/sbin/apache2 -k start -DSSL
 5912 ?        SN     0:00 /usr/sbin/apache2 -k start -DSSL
 5913 ?        SN     0:00 /usr/sbin/apache2 -k start -DSSL
 5915 ?        SN     0:00 /usr/sbin/apache2 -k start -DSSL
 5916 ?        SN     0:00 /usr/sbin/apache2 -k start -DSSL
 5938 ?        SNs    0:00 /usr/sbin/cupsd
 8561 ?        SNs    0:00 /sbin/syslogd -u syslog
 8730 tty3     Ss     0:00 /bin/login --    
 8740 tty4     Ss     0:00 /bin/login --    
 8982 tty5     Ss     0:00 /bin/login --       
 9002 tty2     Ss     0:00 /bin/login --    
 9117 tty1     Ss     0:00 /bin/login --    
 9124 tty1     S      0:00 -bash
 9147 tty1     S      0:00 bash
 9165 tty1     S      0:00 bash
 9305 ?        Ss     0:00 /usr/sbin/dhcpd3 -q eth1
 9501 ?        S      0:00 pickup -l -t fifo -u -c
 9503 tty3     S+     0:00 -bash
 9573 tty3     R+     0:00 ps ax

**Actually it would be nice to trim all those Apache starts down since its not serving anything and I only have one cpu, but first, I'd like to know what is causing all this (netstat -a)** 

Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     9725     @/tmp/hald-runner/dbus-oPctzej4tC
unix  2      [ ACC ]     STREAM     LISTENING     14665    /var/run/acpid.socket
unix  2      [ ]         DGRAM                    4877     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10712    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     10719    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     10733    private/rewrite
unix  2      [ ]         DGRAM                    9733     @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     10737    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10741    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     10745    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     10749    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     10753    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     10757    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     10761    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     10765    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     10769    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     10773    private/error
unix  2      [ ACC ]     STREAM     LISTENING     10777    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     10781    private/local
unix  2      [ ACC ]     STREAM     LISTENING     10785    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     10789    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     10793    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     10797    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     10801    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     10805    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     10809    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     10813    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     10817    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     10821    private/mailman
unix  5      [ ]         DGRAM                    15830    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     9724     @/tmp/hald-local/dbus-fXtUh6DGAP
unix  2      [ ACC ]     STREAM     LISTENING     9701     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10992    /var/run/sdp
unix  2      [ ]         DGRAM                    16185    
unix  2      [ ]         DGRAM                    16178    
unix  2      [ ]         DGRAM                    16013    
unix  2      [ ]         DGRAM                    15516    
unix  3      [ ]         STREAM     CONNECTED     14747    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     14746    
unix  2      [ ]         DGRAM                    13937    
unix  2      [ ]         DGRAM                    13880    
unix  2      [ ]         DGRAM                    13059    
unix  2      [ ]         DGRAM                    12468    
unix  2      [ ]         DGRAM                    12389    
unix  3      [ ]         STREAM     CONNECTED     12387    
unix  3      [ ]         STREAM     CONNECTED     12386    
unix  3      [ ]         STREAM     CONNECTED     12385    
unix  3      [ ]         STREAM     CONNECTED     12384    
unix  3      [ ]         STREAM     CONNECTED     12383    
unix  3      [ ]         STREAM     CONNECTED     12382    
unix  3      [ ]         STREAM     CONNECTED     12381    
unix  3      [ ]         STREAM     CONNECTED     12380    
unix  3      [ ]         STREAM     CONNECTED     12379    
unix  3      [ ]         STREAM     CONNECTED     12378    
unix  3      [ ]         STREAM     CONNECTED     12377    
unix  3      [ ]         STREAM     CONNECTED     12376    
unix  3      [ ]         STREAM     CONNECTED     12375    
unix  3      [ ]         STREAM     CONNECTED     12374    
unix  3      [ ]         STREAM     CONNECTED     12373    
unix  3      [ ]         STREAM     CONNECTED     12372    
unix  3      [ ]         STREAM     CONNECTED     12371    
unix  3      [ ]         STREAM     CONNECTED     12370    
unix  3      [ ]         STREAM     CONNECTED     12369    
unix  3      [ ]         STREAM     CONNECTED     12368    
unix  3      [ ]         STREAM     CONNECTED     12367    
unix  3      [ ]         STREAM     CONNECTED     12366    
unix  3      [ ]         STREAM     CONNECTED     12365    
unix  3      [ ]         STREAM     CONNECTED     12364    
unix  3      [ ]         STREAM     CONNECTED     12363    
unix  3      [ ]         STREAM     CONNECTED     12362    
unix  3      [ ]         STREAM     CONNECTED     12361    
unix  3      [ ]         STREAM     CONNECTED     12360    
unix  3      [ ]         STREAM     CONNECTED     12359    
unix  3      [ ]         STREAM     CONNECTED     12358    
unix  3      [ ]         STREAM     CONNECTED     12357    
unix  3      [ ]         STREAM     CONNECTED     12356    
unix  3      [ ]         STREAM     CONNECTED     12355    
unix  3      [ ]         STREAM     CONNECTED     12354    
unix  3      [ ]         STREAM     CONNECTED     12353    
unix  3      [ ]         STREAM     CONNECTED     12352    
unix  3      [ ]         STREAM     CONNECTED     12351    
unix  3      [ ]         STREAM     CONNECTED     12350    
unix  3      [ ]         STREAM     CONNECTED     12349    
unix  3      [ ]         STREAM     CONNECTED     12348    
unix  3      [ ]         STREAM     CONNECTED     12347    
unix  3      [ ]         STREAM     CONNECTED     12346    
unix  3      [ ]         STREAM     CONNECTED     12345    
unix  3      [ ]         STREAM     CONNECTED     12344    
unix  3      [ ]         STREAM     CONNECTED     12343    
unix  3      [ ]         STREAM     CONNECTED     12342    
unix  3      [ ]         STREAM     CONNECTED     12341    
unix  3      [ ]         STREAM     CONNECTED     12340    
unix  3      [ ]         STREAM     CONNECTED     12339    
unix  3      [ ]         STREAM     CONNECTED     12338    
unix  3      [ ]         STREAM     CONNECTED     12337    
unix  3      [ ]         STREAM     CONNECTED     12336    
unix  3      [ ]         STREAM     CONNECTED     12335    
unix  3      [ ]         STREAM     CONNECTED     12334    
unix  3      [ ]         STREAM     CONNECTED     12333    
unix  3      [ ]         STREAM     CONNECTED     12332    
unix  2      [ ]         DGRAM                    12125    
unix  2      [ ]         DGRAM                    10984    
unix  3      [ ]         STREAM     CONNECTED     10983    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10982    
unix  2      [ ]         DGRAM                    10965    
unix  2      [ ]         DGRAM                    10697    
unix  2      [ ]         DGRAM                    10194    
unix  3      [ ]         STREAM     CONNECTED     10064    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10063    
unix  3      [ ]         STREAM     CONNECTED     10050    @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     10049    
unix  3      [ ]         STREAM     CONNECTED     10040    @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     10039    
unix  3      [ ]         STREAM     CONNECTED     10010    @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     10005    
unix  3      [ ]         STREAM     CONNECTED     9889     @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     9888     
unix  3      [ ]         STREAM     CONNECTED     9885     @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     9882     
unix  3      [ ]         STREAM     CONNECTED     9857     @/tmp/hald-local/dbus-fXtUh6DGAP
unix  3      [ ]         STREAM     CONNECTED     9848     
unix  3      [ ]         STREAM     CONNECTED     9728     @/tmp/hald-runner/dbus-oPctzej4tC
unix  3      [ ]         STREAM     CONNECTED     9727     
unix  3      [ ]         STREAM     CONNECTED     9704     
unix  3      [ ]         STREAM     CONNECTED     9703     


**I don't know why all that mail stuff would be running, since I'm not using any MTA, and the HAL stuff isn't opening all those connections on my other machines. Finally that whole run of open unix sockets is just sick, what's up with that?**

Any knowledge of this would be greatly appreciated. 

-Emerson

---

### Post by zgornel on 2006-12-07
Netstat lists also the sockets opened for interprocess communication like client-server applications and are related to the OS. The *unix* in front of every connection specifies that they are unix domain sockets.

---

### Post by tturrisi on 2006-12-07
Try netstat -s
and netstat -h for all switches available.

---

### Post by emersony on 2006-12-11
[FONT="Lucida Console"]The question I was asking is why this is only happening on ONE of my Ubuntu machines, and I also mentioned that I have an Ubuntu server running MTA, vpop, Apache, the works where netstat -a | wc is only 49. 

So how do I find out why out of all my Ubuntu machines, 1 of them has an extra 100 listening sockets ?? Again, the machine is not connected in anyway to the internet. 

Emerson[/FONT]

---

### Post by zgornel on 2006-12-11
> **emersony said:**
> [FONT="Lucida Console"]The question I was asking is why this is only happening on ONE of my Ubuntu machines, and I also mentioned that I have an Ubuntu server running MTA, vpop, Apache, the works where netstat -a | wc is only 49. 

So how do I find out why out of all my Ubuntu machines, 1 of them has an extra 100 listening sockets ?? Again, the machine is not connected in anyway to the internet. 

Emerson[/FONT]
Problem solved :D.
Whenever you do a netstat, for the unix domain sockets, watch for the I-NODE (the number). To get the process that is associated with that socket, do: ```
lsof -U|grep <the INODE number>
```. To view all opened unix sockets and associated processes, ```
lsof -U
```

PS. Connections might be left from killed or closed processes so some connections might have associated processes that do not exist anymore.

---

