---
title: "Where does ddclient store it's settings?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by richardq on 2007-07-10
I'm running Feisty. I've installed ddclient via the repositories. I've got a DSL modem into a router and during the install, it asked me for my dynamic dns info (I've got a dyndns.org account). But I'm having a problem.

It seems like ddclient isn't running properly, or is misconfigured. I modified the /etc/ddclient.conf file based on instructions at the dyndns.com site since the original conf file wasn't checking via the web (ipcheck) but rather through the hardware interface and I thought that might be the problem. BUT, I don't think the changes I made to the /etc/ddclient.conf file are being used by ddclient. For instance I set the timing to check at 300 and if I check using 'ps aux |grep ddclient', it shows it starting at 600. I've rebooted the system to make sure the ddclient restarted, but it just doesn't seem to  read that file. Maybe it's getting it's setting from somewhere else.

Also, I only saw a single mention of ddclient in the /var/log/syslog file this morning. I checked it first thing and then about an hour later, and it still only showed a single ddclient check. Almost as if ddclient wasn't running the checks or was logging them somewhere else.

I just bought the router last week and I'm pretty green when it comes to networking. I'm trying to get ssh up and running from work. I got it to work via a VMware session on my local machine but it seems my ISP is changing the address every day (or ddclient isn't working). So by the time I get to work, it can't resolve the address.

Any clues? It may be something else, but I find it strange that after setting the timing to 300 it still shows it sleeping for 600 and counting down. Also strange is that it's not logging repeated checks..

Here is my ddclient.conf file (with the login and site stuff asterisked out):

```
daemon=300                  # check every 300 seconds
syslog=yes                  # log update msgs to syslog
mail=root                   # mail all msgs to root
mail-failure=root           # mail failed update msgs to root
pid=/var/run/ddclient.pid   # record PID in file.


### Select one of these options to determine your IP address

## via hardware interface (if you don't have a router/firewall)
#use=if, if=eth0

## via our CheckIP server
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

## from the status page for a linksys router/firewall
#use=linksys, fw=linksys, fw-login=admin, fw-password=admin

## from a FW status page
#fw-login=admin, fw-password=XXXXXX
#use=fw, fw=192.168.1.254/status.htm, fw-skip='IP Address'


## Enter your DynDNS username and password here

login=*******           # your DynDNS username
password=*******     # your DynDNS password


## This section requires no changes unless you need to set a default proxy server
## or you need to bypass your proxy server (because it interferes with the updates)

protocol=dyndns2                    # default protocol
server=members.dyndns.org           # default server
#server=members.dyndns.org:8245     # default server (bypassing proxies)
#proxy=fasthttp.sympatico.ca:80     # default proxy


## Default options for Dynamic/Static DNS Hosts

#mx=             # default MX host (leave undefined by default)
#backupmx=NO     # MX host is primary MX? (leave undefined by default)
wildcard=YES     # add wildcard CNAME?

## Dynamic DNS hosts go here
*******.dyndns.org

## Static DNS hosts go here
#static=yes, your-static-host.dyndns.org,another-static-host.dyndns.org

## Custom DNS hosts go here
#custom=yes, your-domain.top-level,your-other-domain.top-level

 
```

---

### Post by le0buntu on 2007-07-10
Hi,

Just installed ddclient on one of my Dapper machines.
The daemon time is not being honored in /etc/ddclient.conf as it appears to be overridden by the value in the /etc/init.d/ddclient script.

Did you forward your SSH port from your router to your Fiesty machine?

If ssh <internal_ip> works from your internal network, then try ssh <external_ip> from your internal network.
If the  ssh <external_ip> works, ssh <external_dns_name> should also work.

If you forwarded a non standard port on your router (as I believe you should), you'll need specify this as well; ssh -p <port> <external_dns_name>.

You can check to see if the name is resolving by attempting to ping <external_dns_name>.

Hope this helps some,
Leo

---

