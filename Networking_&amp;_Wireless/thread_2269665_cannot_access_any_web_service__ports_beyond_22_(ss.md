---
title: "cannot access any web service / ports beyond 22 (ssh)"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by alex351 on 2015-03-17
Hi guys,

somehow my network got messed up...though I cant remember changing anything.

I can still access my ubuntu 14.04 server (3.13 kernel) via SSH but my services are not reachable anymore beyond that. I am running CUPS and LXC web panel. If I patch the port through SSH to my local machine it works but directly connecting via server-ip:5000 or server-ip:631 does not work anymore. i already checked and reset my router and had a look at the network interfaces but could not find anything unusual. I also reset iptables (iptables -F) but no luck here either. I running a LXC container with all my services which also not able to connect and I am not able to connect either. UFW is disabled.

I really hope you can help - I have no idea what has happened...

Cheers

p.s.: I've setup a network bridge br0 through which the LXC container is connected...
Alex

---

### Post by TheFu on 2015-03-17
Are the daemons running?
**sudo lsof |grep 631**

---

### Post by alex351 on 2015-03-17
Output looks like this:

firewalld 1692            root  mem       REG                8,1   163128     140490 /usr/lib/python2.7/dist-packages/_dbus_bindings.so
gmain     1692 2391       root  mem       REG                8,1   163128     140490 /usr/lib/python2.7/dist-packages/_dbus_bindings.so

---

### Post by TheFu on 2015-03-17
So CUPS isn't even running.
[B]
sudo service cups start[/B]
see if that doesn't fix that part.

---

### Post by alex351 on 2015-03-17
I checked that (but something seems) wrong. Starting the service again gives (same result for lxp web panel):

```

$ sudo service cups start
start: Job is already running: cups
$ sudo service lwp start
start: Job is already running: lwp
```

Edit: I just checked the same for LWP - at least that is running & listening but I still cant access it inside my network - only local

```
lwp       1588            root    3u     IPv4              11638      0t0        TCP *:5000 (LISTEN)

```

---

### Post by TheFu on 2015-03-17
Did the cups config change to only allow connections from localhost?  To allow from anywhere, it should be the LAN IP for the machine in the /etc/cups/cupsd.conf file. Here's mine:

**Listen 172.22.22.4:631**

That's the only thing I remember having to fix last summer on a new 14.04 install.  Know it works - printed something from a netbook this morning ... the first time  in months. Plus both machines are currently patched and Ubuntu systems.

Don't know what lwp has to do with this - that is a perl module in my mind. ;)

For LXC stuff, I use virt-manager and libvirt - er ... after the bridge and container are created.

---

### Post by alex351 on 2015-03-17
checked my  /etc/cups/cupsd.conf again. Not bound to localhost. I was mentioning LXC Web panel (LWP) because that's the second service running on the main server that is not accessible. As shown earlier it is listening on the port 5000 but I am not able to access it...same as port 631 for CUPS...

so this seems to be more of general problem that is not service specific...

---

### Post by TheFu on 2015-03-17
Where are you trying to access these from?
LAN?
Same PC?
WAN?

Is cups running inside a container?

---

### Post by alex351 on 2015-03-17
my Home Network (LAN) but different PC - Cups is running on the host only.

---

### Post by TheFu on 2015-03-17
Thanks.

So ... the only way for this NOT to work, assuming cups is actually running (though lsof isn't showing that - try a restart) - is if either of the coputers is running a firewall.  Check both of them -don't just flush it - turn it off.

I'd also check /etc/hosts.deny and hosts.allow on the cups machine.

If the cups server is really running, then I'd try to telnet to that port from both the same machine and from the different machine. Any difference?  Here telnet makes a connection.

Cups doesn't seem to grab port 631 - sorry about that mistake earlier.  lsof isn't seeing it here either.```

$ service cups status
cups start/running, process 11886
$ psg 11886
root     11886     1  0 06:46 ?        00:00:00 /usr/sbin/cupsd -f
```

I have to head out for a few hours. Sorry.

---

### Post by alex351 on 2015-03-17
Hi again,

it is definitely the host system (ubuntu server) as I tried accessing from multiple devices. I did the following:

- checked hosts.deny / hosts.allow: both are empty
- restarted the system
- ufw is not enabled, I did not install any other firewalls on the system
- telnet from local host works but not from remote (port 631 (cups) and 5000 (lwp))

```
$ telnet localhost 631Trying 127.0.0.1...
Connected to localhost.
```


```
$ telnet 192.168.178.103 631
Trying 192.168.178.103...
telnet: connect to address 192.168.178.103: Connection refused
telnet: Unable to connect to remote host
```

netstat shows the following
```
$ sudo netstat -tulpe
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      root       10686       1640/sshd       
tcp        0      0 *:ipp                   *:*                     LISTEN      root       13198       2622/cupsd      
tcp        0      0 *:smtp                  *:*                     LISTEN      root       12912       2356/master     
tcp        0      0 *:5000                  *:*                     LISTEN      root       11638       1588/python     
tcp        0      0 *:41516                 *:*                     LISTEN      statd      9112        826/rpc.statd   
tcp        0      0 *:sunrpc                *:*                     LISTEN      root       9085        796/rpcbind     
tcp        0      0 *:8083                  *:*                     LISTEN      xbmc       12243       2102/python     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      root       10688       1640/sshd       
tcp6       0      0 [::]:ipp                [::]:*                  LISTEN      root       13199       2622/cupsd      
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      root       12913       2356/master     
tcp6       0      0 [::]:sunrpc             [::]:*                  LISTEN      root       9088        796/rpcbind     
tcp6       0      0 [::]:44597              [::]:*                  LISTEN      statd      10094       826/rpc.statd   
udp        0      0 *:44827                 *:*                                 root       10280       1206/dhclient   
udp        0      0 *:bootpc                *:*                                 root       10223       1206/dhclient   
udp        0      0 *:sunrpc                *:*                                 root       9081        796/rpcbind     
udp        0      0 *:49270                 *:*                                 avahi      9236        534/avahi-daemon: r
udp        0      0 cerebrum.fritz.box:ntp  *:*                                 root       13232       2661/ntpd       
udp        0      0 localhost:ntp           *:*                                 root       13231       2661/ntpd       
udp        0      0 *:ntp                   *:*                                 root       13224       2661/ntpd       
udp        0      0 *:41129                 *:*                                 statd      9110        826/rpc.statd   
udp        0      0 *:ipp                   *:*                                 root       13893       1699/cups-browsed
udp        0      0 *:962                   *:*                                 root       9084        796/rpcbind     
udp        0      0 localhost:1002          *:*                                 root       10087       826/rpc.statd   
udp        0      0 *:mdns                  *:*                                 avahi      9234        534/avahi-daemon: r
udp6       0      0 [::]:52970              [::]:*                              statd      9114        826/rpc.statd   
udp6       0      0 [::]:32530              [::]:*                              root       10281       1206/dhclient   
udp6       0      0 [::]:40905              [::]:*                              avahi      9237        534/avahi-daemon: r
udp6       0      0 [::]:sunrpc             [::]:*                              root       9086        796/rpcbind     
udp6       0      0 fe80::201:2eff:fe3c:ntp [::]:*                              root       13234       2661/ntpd       
udp6       0      0 ip6-localhost:ntp       [::]:*                              root       13233       2661/ntpd       
udp6       0      0 [::]:ntp                [::]:*                              root       13225       2661/ntpd       
udp6       0      0 [::]:962                [::]:*                              root       9087        796/rpcbind     
udp6       0      0 [::]:mdns               [::]:*                              avahi      9235        534/avahi-daemon: r
```

and my iptables -L looks like this:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
INPUT_direct  all  --  anywhere             anywhere            
INPUT_ZONES_SOURCE  all  --  anywhere             anywhere            
INPUT_ZONES  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
FORWARD_direct  all  --  anywhere             anywhere            
FORWARD_IN_ZONES_SOURCE  all  --  anywhere             anywhere            
FORWARD_IN_ZONES  all  --  anywhere             anywhere            
FORWARD_OUT_ZONES_SOURCE  all  --  anywhere             anywhere            
FORWARD_OUT_ZONES  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
OUTPUT_direct  all  --  anywhere             anywhere            


Chain FORWARD_IN_ZONES (1 references)
target     prot opt source               destination         
FWDI_public  all  --  anywhere             anywhere            


Chain FORWARD_IN_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_OUT_ZONES (1 references)
target     prot opt source               destination         
FWDO_public  all  --  anywhere             anywhere            


Chain FORWARD_OUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_direct (1 references)
target     prot opt source               destination         


Chain FWDI_public (1 references)
target     prot opt source               destination         
FWDI_public_log  all  --  anywhere             anywhere            
FWDI_public_deny  all  --  anywhere             anywhere            
FWDI_public_allow  all  --  anywhere             anywhere            


Chain FWDI_public_allow (1 references)
target     prot opt source               destination         


Chain FWDI_public_deny (1 references)
target     prot opt source               destination         


Chain FWDI_public_log (1 references)
target     prot opt source               destination         


Chain FWDO_external (0 references)
target     prot opt source               destination         
FWDO_external_log  all  --  anywhere             anywhere            
FWDO_external_deny  all  --  anywhere             anywhere            
FWDO_external_allow  all  --  anywhere             anywhere            


Chain FWDO_external_allow (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain FWDO_external_deny (1 references)
target     prot opt source               destination         


Chain FWDO_external_log (1 references)
target     prot opt source               destination         


Chain FWDO_public (1 references)
target     prot opt source               destination         
FWDO_public_log  all  --  anywhere             anywhere            
FWDO_public_deny  all  --  anywhere             anywhere            
FWDO_public_allow  all  --  anywhere             anywhere            


Chain FWDO_public_allow (1 references)
target     prot opt source               destination         


Chain FWDO_public_deny (1 references)
target     prot opt source               destination         


Chain FWDO_public_log (1 references)
target     prot opt source               destination         


Chain INPUT_ZONES (1 references)
target     prot opt source               destination         
IN_public  all  --  anywhere             anywhere            


Chain INPUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain INPUT_direct (1 references)
target     prot opt source               destination         


Chain IN_dmz (0 references)
target     prot opt source               destination         
IN_dmz_log  all  --  anywhere             anywhere            
IN_dmz_deny  all  --  anywhere             anywhere            
IN_dmz_allow  all  --  anywhere             anywhere            


Chain IN_dmz_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW


Chain IN_dmz_deny (1 references)
target     prot opt source               destination         


Chain IN_dmz_log (1 references)
target     prot opt source               destination         


Chain IN_external (0 references)
target     prot opt source               destination         
IN_external_log  all  --  anywhere             anywhere            
IN_external_deny  all  --  anywhere             anywhere            
IN_external_allow  all  --  anywhere             anywhere            


Chain IN_external_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW


Chain IN_external_deny (1 references)
target     prot opt source               destination         


Chain IN_external_log (1 references)
target     prot opt source               destination         


Chain IN_home (0 references)
target     prot opt source               destination         
IN_home_log  all  --  anywhere             anywhere            
IN_home_deny  all  --  anywhere             anywhere            
IN_home_allow  all  --  anywhere             anywhere            


Chain IN_home_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ipp ctstate NEW
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-ns ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-dgm ctstate NEW


Chain IN_home_deny (1 references)
target     prot opt source               destination         


Chain IN_home_log (1 references)
target     prot opt source               destination         


Chain IN_internal (0 references)
target     prot opt source               destination         
IN_internal_log  all  --  anywhere             anywhere            
IN_internal_deny  all  --  anywhere             anywhere            
IN_internal_allow  all  --  anywhere             anywhere            


Chain IN_internal_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ipp ctstate NEW
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-ns ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-dgm ctstate NEW


Chain IN_internal_deny (1 references)
target     prot opt source               destination         


Chain IN_internal_log (1 references)
target     prot opt source               destination         


Chain IN_public (1 references)
target     prot opt source               destination         
IN_public_log  all  --  anywhere             anywhere            
IN_public_deny  all  --  anywhere             anywhere            
IN_public_allow  all  --  anywhere             anywhere            


Chain IN_public_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW


Chain IN_public_deny (1 references)
target     prot opt source               destination         


Chain IN_public_log (1 references)
target     prot opt source               destination         


Chain IN_work (0 references)
target     prot opt source               destination         
IN_work_log  all  --  anywhere             anywhere            
IN_work_deny  all  --  anywhere             anywhere            
IN_work_allow  all  --  anywhere             anywhere            


Chain IN_work_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ipp ctstate NEW


Chain IN_work_deny (1 references)
target     prot opt source               destination         


Chain IN_work_log (1 references)
target     prot opt source               destination         


Chain OUTPUT_direct (1 references)
target     prot opt source               destination         
```

---

### Post by alex351 on 2015-03-17
Nevermind...I just went ahead and reinstalled the system...hope it works now ;-)

But thank you for the help! I just love this community.

---

### Post by TheFu on 2015-03-17
After reading everything ... I had nothing to offer besides turning up iptables logging and checking some system log files.  

Reinstalling cups might help.
Last Sunday, I had to reinstall a server here that stopped working - it was x2goserver. The reinstall of x2goserver solved it. Not related to your issue, but maybe the technique will help? Good luck!

---

### Post by alex351 on 2015-03-17
thank - I just did a fresh reinstall ubuntu minimal + lxc + cups and it is working again ;-)

---

### Post by TheFu on 2015-03-17
I suspect you didn't need to reinstall ubuntu minimal, but whatever works .... anyways - please mark the thread as solved so others can reference that and gurus don't read it trying to help.

---

