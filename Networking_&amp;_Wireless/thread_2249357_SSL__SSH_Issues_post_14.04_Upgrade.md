---
title: "SSL / SSH Issues post 14.04 Upgrade"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by Cuyler on 2014-10-21
[FONT=courier new]So I upgraded to 14.04 and in hindsight forgot that an Ubuntu upgrade and create a complete mess of manual configurations.  I already went and set up the static IP again (192.168.0.202) but I’m sure I’m missing something pretty dumb - any help would be appreciated.

I have a server that serves HTTP (80), HTTPS (443) and VPN externally (many other things internally).  It has a single eth0 connection with nothing horribly funky.

SSH/HTTP/HTTPS connection from Local -> Server Local IP or Hostname (with DNS lookup):
 = Works

SSH connection from Local -> Public:
Client = ssh_exchange_identification: read: Operation timed out
Server = Oct 21 13:28:07 hyperion sshd[26843]: Connection from 192.168.0.1 port 59146 on 192.168.0.202 port 22
         Oct 21 13:28:25 hyperion sshd[26843]: Did not receive identification string from 192.168.0.1

Checking that port is being forwarded properly through the router I checked via public nmap:
Starting Nmap 6.45 ( [http://nmap.org](http://nmap.org) ) at 2014-10-21 19:21 Central Europe Daylight Time 
Nmap scan report for xx-xx-xx-xx.cable.teksavvy.com (xx.xx.xx.xx) 
Host is up (0.13s latency). 
Not shown: 97 filtered ports 
PORT STATE SERVICE 
22/tcp open ssh
80/tcp open http
443/tcp open https 
1723/tcp open pptp 


Good old telnet to the ports (here is 443, but 22 is the same) locally works:
$ telnet hyperion 443
Trying 192.168.0.202...
Connected to hyperion.lab.
Escape character is '^]'.
^]


Even a telnet to the public ip on https gets a response:
$ telnet xx.xx.xx.xx 443
Trying xx.xx.xx.xx…
Connected to xx-xx-xx-xx.cable.teksavvy.com.
Escape character is '^]'.
^]

When trying to connect from a browser:
 https://<localip> = Good
 https://<publicip>  = Timeout (with nothing in apache2 logs)

Interestingly:
 http://<publicip> = Works, but very delayed response, like it’s waiting for a timeout.

I’m listening:
$ netstat -tupan | grep LIST | egrep ':80|:443'
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      4317/python     
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN      -   

ufw is disabled
Routing is as simple as possible:
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

I'm seeing nothing in the apache logs.  I redid the apache SSL configuration but as the problem exists with both SSL and SSH I suspect the issue is somewhere else.

Thank you.
[/FONT]

---

### Post by TheFu on 2014-10-21
The only shot-in-the-dark I have is that some home routers see attempts to the public IP as a hacking attempt and block it.

You can turn up verbosity with ssh by adding **-vvv** to the command. That on the client and the server sshd logs should pinpoint any issues with those connections quickly.  It has always worked for me.

Can't help at all with apache stuff, but that could be the router too.

---

### Post by Cuyler on 2014-10-21
The ssh with -vvv didn't show anything else - just the attempt to connect and then die - nothing else.

Ideally I would like this to work as it did before the upgrade but for now, I have a work around that works.  I created an override entry in my DNS on the internal network to resolve my FQDN to the internal IP.  When I'm outside the network, that DNS server is unavailable so it'll resolve to the public IP using other DNS servers.

Not a great solution but it works.

---

### Post by TheFu on 2014-10-21
I have the ~/.ssh/config file setup to use different aliases for internal vs external access.  Externally, the router forwards and translates a high port to port 22 internally. Internally, system all listen on port 22.  I find this better than using the same name - since it validated the public interface or internal interface through config settings.

BTW - on the 10 or so systems I've migrated to 14.04 here - NONE have had any ssh issues from the migration and only 1 had any issue at all (which I self-inflicted via Ansible).

The last shot in the dark is that ~/.ssh/ and the files inside don't have the correct owner/permissions. There are specific requirements - an upgrade shouldn't touch those in a /home - but if a backup-restore was performed, it is highly possible the permissions were lost if an appropriate backup tool that retains ugo/perms and ACLs isn't used.

---

