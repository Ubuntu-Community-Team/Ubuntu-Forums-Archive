---
title: "Problem on running scp"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-09-30
Hi folks,


Ubuntu 7.04 server amd64
router IP : 192.168.0.10

Ubuntu 7.04 desktop
router IP :192.168.0.11


On server
$ scp file satimis@192.168.0.11:/path/to/dir

It works fine with file transferred.


On desktop
$ scp file satimis@192.168.0.10:/path/to/dir```

ssh_exchange_identification: Connection closed by remote host
lost connection

```


Tried with iptables on server stopped but w/o a solution.  Both ssh_conf and sshd_conf on server and desktop look the same.  

Please advise how to fix the problem?  Which file I have to edit and how.  

TIA


satimis

---

### Post by conjur3r on 2007-09-30
Is SSH working ok on both computers?  Can you SSH to both?

---

### Post by satimis on 2007-09-30
> **conjur3r said:**
> Is SSH working ok on both computers?  Can you SSH to both?
No also one way.

Server can ssh desktop.  But desktop can't ssh server with the same warning;```

ssh_exchange_identification: Connection closed by remote host

```

---

### Post by satimis on 2007-09-30
Hi folks,


I have my problem partially solved according to;

Connection closed by remote host Error Message
[http://www.wlug.org.nz/SSHErrors](http://www.wlug.org.nz/SSHErrors)

I have "denyhosts" installed on server, but not installed on desktop

Add following line on /etc/hosts.allow```

sshd sshd1 sshd2 : ALL : ALLOW

```

$ cat /etc/hosts.allow```

sshd: 127.0.0.1

# Domain
sshd: .satimis.com

# ISP from home
sshd: *.myISP.com

sshd sshd1 sshd2 : ALL : ALLOW

```
Would the adding of this line affecting above "Domain" and "ISP from home"???

What is "... removing the PARANOID line in /etc/hosts.deny, or ...." on the document?

$ cat /etc/hosts.deny```

sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log

ALL:ALL

```
???  Thanks.

Now I can;
$ scp file satimis@192.168.0.10:/path/to/dir

it works both way.


On desktop
$ ssh -Y satimis@192.168.0.10 rox
password:```

....
(rox:5168): Gtk-warning ** Locale not supported by C library
Using the fallback 'C' locale

```

Server Rox does not display on desktop.

Held here.  Any advice?  TIA


satimis

---

### Post by satimis on 2007-10-05
Hi folks,


I found the cause of problem.  It is the firewall "iptables" which stops X forwarding.

On server after running;
$ sudo iptables -F


On desktop;
$ ssh -X satimis@192.168.0.10 rox```

satimis@192.168.0.10's password: 

(process:5282): Gdk-WARNING **: locale not supported by C library

(rox:5282): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(rox:5285): Gtk-WARNING **: Could not find the icon 'mime-text:plain'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
        http://icon-theme.freedesktop.org/releases

(leafpad:5286): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(leafpad:5287): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```

remote rox displayed locally.  Files can be evoked.  I don't know why it displays a misleading warning there fooling around us.


Before the server crashed I ran another firewall script.  I'm now running following scripts;
$ cat /etc/rc.local```

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management
interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d MGMT_NIC_IP --reject-with
icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s MGMT_NIC_IP -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with
icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s MGMT_NIC_IP --reject-with
icmp-port-unreachable

```

MGMT_NIC_IP = server_IP


On server;

Restart iptables
$ sudo /etc/rc.local restart
No complaint

On desktop running
$ ssh -X satimis@server_IP rox```

ssh: connect to host server_IP port 22: Connection refused

```

$ ssh -X server_IP ```

ssh: connect to host server_IP port 22: Connection refused

```

It did not work


Again on server
$ sudo nano /etc/ssh/sshd_config
adding "ListenAddress 192.168.0.11" (router IP)

$ cat /etc/ssh/sshd_config```

....
Port 22
ListenAddress 192.168.0.10
ListenAddress 192.168.0.11
....

```

$ sudo /etc/init.d/ssh restart


Again on desktop
$ ssh -X satimis@server_IP rox```

ssh: connect to host server_IP port 22: Connection refused

```

$ ssh -X server_IP```

ssh: connect to host server_IP port 22: Connection refused

```

Problem still there.  Any advice?

TIA


satimis

---

