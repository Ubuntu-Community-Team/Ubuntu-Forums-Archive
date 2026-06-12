---
title: "tftpd server"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by deebee19701 on 2011-05-23
problems copying from the tftp server to my cisco switch:

I can't seem to transfer the file from my ubuntu TFTPD server to my switch. the error message is 

--- ubuntu syslogs ---
/var/log/syslog:May 23 00:08:24 testbed tftpd[5557]: tftpd: serving file from /tftpboot
/var/log/syslog:May 23 00:08:24 testbed tftpd[5557]: tftpd: read: Connection refused
/var/log/syslog:May 23 00:08:24 testbed tftpd[5559]: tftpd: trying to get file: c3560-advipservicesk9-mz.122-46.SE.bin
/var/log/syslog:May 23 00:08:24 testbed tftpd[5559]: tftpd: serving file from /tftpboot
dimitrib@testbed:~$ 

---- cisco switch ----

SW-1#copy tftp flash:
Address or name of remote host [10.0.0.3]? 
Source filename [c3560-advipservicesk9-mz.122-46.SE.bin]? 
Destination filename [c3560-advipservicesk9-mz.122-46.SE.bin]? 
Accessing tftp://10.0.0.3/c3560-advipservicesk9-mz.122-46.SE.bin...
Loading c3560-advipservicesk9-mz.122-46.SE.bin from 192.168.100.2 (via Vlan1): !
%Error reading tftp://10.0.0.3/c3560-advipservicesk9-mz.122-46.SE.bin (Transfer)
SW-1#

---

### Post by jtarin on 2011-05-23
Does this installation setup look familiar to what you did?

---

### Post by deebee19701 on 2011-05-24
I justed the default configuration and setting the daemon to startup in the /etc/xinetd folder

the switch is rather simple and that it has a simple vlan 1 with an IP address on it.  now my netbook has two connections.

   1) connects to the access point on the 10.0.0.x network under the wlan0  interface

   2) eth0 is configured on the 192.168.100.x network switch runs to my router lab.

I need to be able to use both interfaces to  kind of bridge the two. as my ubuntu server is offering the ntpd  services to the router lab and to my internal network. Now there are two default routes in the netstat -nR command. would that be the cause of the conflict?  and for me not to be able to offer files to the routers and switches?

---

### Post by 5149.5 on 2011-05-24
Try using your ubuntu boxes 192.168.x.x adress instead of the 10.0.x.x address here:

```
SW-1#copy tftp flash:
Address or name of remote host [10.0.0.3]?
```

Also verify that the vlan 1 config on your switch has a good address and the default gateway should be the 192.168.x.x address of your ubuntu box.

---

### Post by deebee19701 on 2011-05-24
okay so the problem was me playing around with both tftpd and atftpd. it would appear that the process was locked by another program which didn't release the port when I needed it to. the second problem was that there was not enough room on the flash: drive on the 3560 switch to upload the file. 
I have no idea why the OS kept the port locked but clearing I had to clear the problem bya simple reboot (sounds too windowsish). all the switches were upgraded and I'm good to go :)

p.s. never had to touch my interface confiuration i kept them as is>

---

