---
title: "apache help please :)"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Elisei on 2007-01-15
Hi !

I am running dapper drake and on it have ssh and apache2 server; i am using Ethernet connection with static ip and it seems to be working  ... but only for or between the computers that are connected to my router; if i was to access for example my website from any other network it would not go through; it does this : ](*,)  instead of going to my computer that runs apache & ssh; all needed ports have been forwarded so it might not be the router causing the problem;

Is there something in /etc/hosts and /etc/network/interfaces files that needs to be modified to allow WAN access?

---

### Post by Lucardo Mamones on 2007-01-16
are you running iptables? could be the actual box blocking the conection from outside...

---

### Post by tturrisi on 2007-01-16
To access from the wan you need to use your isp assigned ip address.
Use router port forwarding to forward port 80 for www and 22 for ssh.
Some isps filter port 80 so may have to config apache to use an alternate port such as 8080 and config router port forwarding for that.
> Is there something in /etc/hosts and /etc/network/interfaces files that needs to be modified to allow WAN access?
no, unless your /etc/hosts does not look like this:
```
127.0.0.1 localhost your-server-name
192.168.x.x your-server-name.your-fully-qualified-domain-name.com your-server-name

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```

---

### Post by Tim Stephenson on 2007-02-01
I am having a similar problem. Were you able to get this working.

I have  a static address leading to my router which is being forwarded to the server using NAT. When connecting from the LAN, everything works fine.  If I go to a computer outside the LAN I get no response. No error message or anything. 

The ISP isn't blocking any ports. I am running several other servers at my office all with no problem. If I swap IP addresses to one of the other computers they work. 

The problem seems to be on the box.

I also tried connecting it directly to the internet bypassing the router.  Still no luck. Any advice would be appreciated. This is a new install of Fedora Core 6 running Apache and Subversion. Would I benefit from switching to Ubuntu?

---

### Post by phossal on 2007-02-01
An Apache install is a messy thing to diagnose. If you swap to Ubuntu, you'll have reinstalled everything in about 20 minutes. Downloading the *package* for Apache pretty much guarantees that your box responds on port 80, with *no* configuration. That's a pretty good feeling. 

Then you can rip it apart, delete the apache2.conf file (or whatever it's called ; ) and harden it as necessary.

---

