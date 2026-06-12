---
title: "ssh connection problem"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by markkus80 on 2007-03-13
Hi,

I've recently installed ssh server in one of my computers and I want to access to it through ssh either from my LAN network or from outside the LAN.

I have a wireless router and I have the 22 port redirected to my machine wich has the ssh server.

I can acces to the ssh server from within the LAN but not from outside. When I try to access from outside with the public ip of my router I have the next error:

...
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to markkus.homelinux.net [83.60.65.210] port 22.
debug1: Connection established.
debug1: identity file /home/markkus/.ssh/identity type -1
debug1: identity file /home/markkus/.ssh/id_rsa type -1
debug1: identity file /home/markkus/.ssh/id_dsa type -1
debug1: ssh_exchange_identification: \377\373\003\377\373\001

ssh_exchange_identification: Connection closed by remote host


I've looked for it in google here in forums but I havent been able to find a solution. I've checked the files hosts.allow, hosts.deny and sshd_config but I dont know how to find the problem. I'm not an expert on linux.

Thanks for any help

markkus80

---

### Post by Mr. C. on 2007-03-13
I know you said you checked, but please post your hosts.deny and hosts.allow files.  Also, please show output from:

```
netstat -a | grep ssh
```

MrC

---

### Post by markkus80 on 2007-03-13
yes of course, here it is:

hosts.allow content

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
ALL : 192.168.1.0/255.255.254.0
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#


hosts.deny content

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID


Output of 'netstat -a | grep ssh'

tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 192.168.1.34:ssh        192.168.1.33:52863      ESTABLISHED
unix  2      [ ACC ]     STREAM     LISTENING     17031    /tmp/ssh-ZVmfAK5780/agent.5780

---

### Post by Mr. C. on 2007-03-13
That's what I thought.  You have a hosts.allow entry for internal, but nothing for external.

The default for /etc/hosts.deny is to deny all requests.

Your entry in /etc/hosts.allow allows the 192 network. but no others.

Deny is performed after allow.

```
man hosts.allow
```

MrC

---

### Post by markkus80 on 2007-03-13
Thanks MrC

But how can I allow ips from outside my LAN. I was checking man hosts.allow and I typed this in the hosts.allow file:

...
ALL: 0.0.0.0
...

It is still not working from outside the LAN

I dont need to modify hosts.deny, dont I?

markkus80

---

### Post by Mr. C. on 2007-03-13
I've been waiting for that question! :-)

Let's clarify what your goals are ?

Are they to allow only certain IPs to connect to SSH ?  If so, do you have a list of those IPs?  If yes, add those to /etc/hosts.allow.

If not, and you are not sure from where you will connect, then you an empty hosts.allow file allows all IPs to attempt to connect. If you wont to block only a certain IP (or range), then an empty hosts.allow, and a hosts.deny with the denied IPs does what you'd want.

So, help me understand what you are trying to accomplish.

MrC

---

### Post by markkus80 on 2007-03-13
ok

let me clarify you what I want

So far Im connecting to the ssh server from my LAN but later I want to be able to connect to it from outside the LAN so I should live the hosts.allow empty without any line ALL .... is it correct?

The question is that I think I had this configuration before and it was not working.
I checked it 5 min ago and yes, its not working. So I dont know what to do maybe the problem comes from other side.

thanks

---

### Post by Mr. C. on 2007-03-13
Right, hosts.allow should be empty if you want to allow access to all IPs.

PM me your IP address, and I'll test.

MrC

---

### Post by markkus80 on 2007-03-14
ok

here you have my ip adress: 83.60.65.210

thanks

---

### Post by Mr. C. on 2007-03-14
Nothing at all.  This indicates a firewall is in stealth mode, silently dropping the packet.

MrC

---

### Post by markkus80 on 2007-03-14
I see, well and do you have an idea about what could I do?

I'll be trying to find out what to do.

Thanks MrC

markkus

---

### Post by Mr. C. on 2007-03-14
It depends on what hardware and settings are between me and you.

If you have a router/firewall connected, it may have a log mechanism.  If so, use it to see if any packets are even arriving to your site.  If not, your ISP is blocking them.

If you see the packets arriving, but your server does not, then your firewall is blocking them.

If your server sees the packets, but SSH is not allowing the connection, then your SSH is misconfigured.

You have to go through the layers.  I know my packets went out to your IP address.  What your systems or your ISPs systems did with them only you can determine.

First, start with your router/firewall.  If you have no logging capabilities, connect your server directly to the internet temporarily and use native packet capture tools (tcpdump, wireshark) to see what's coming in.

MrC

---

### Post by markkus80 on 2007-03-14
ok MrC

thanks for your explanation. I'll do what you say and I'll find out the problem.

I'll let you know

thanks again

markkus

---

### Post by togenshi on 2007-03-22
try port fowarding port 22. If accessed internally, no client firewall issues, therefore port fowarding issue.

---

