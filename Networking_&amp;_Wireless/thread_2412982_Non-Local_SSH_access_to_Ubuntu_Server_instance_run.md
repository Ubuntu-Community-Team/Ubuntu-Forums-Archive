---
title: "Non-Local SSH access to Ubuntu Server instance running in VirtualBox"
date: 2019-02-19
forum: Networking &amp; Wireless
---

### Post by ziegler911 on 2019-02-19
Hello all,

I successfully installed Ubuntu Server 18.04.2 LTS using a VM with VirtualBox. I am able to access my machine via ssh on the same network using <username@LocalIP>. However, I am unable to access my server outside of the local network (using a vpn on my laptop to test public access to server).

What I have done so far:
[LIST]
[*]I am using a bridged connection from the host-computer to my VM
[*]I configured my Belkin router to port-forward port 22 to my servers IP@192.168.2.10 obtained through ifconfig
[*]I tried to remote in via ssh <user@PublicIP> --this is where I get a timeout message...
[/LIST]

Is anyone able to assist me with this issue. I know more information is probably required but I'm not sure what. 

Thank you kindly in advance!

P.S I am attempting to do this to debug why I am unable to successfully access my nextcloud server via a subdomain pointed at my public address. And YES, I browsed hundreds of forums the last 3 days with no success -I am computer literate

---

### Post by TheFu on 2019-02-20
Many home routers will block return access through the WAN port for security reasons.  I'd check that.
I wouldn't use port 22/tcp on the internet.  You'll be constantly attacked.  Have your router do port translation from a really high port external to the static LAN IP for the Linux machine port 22/tcp.  Then use the ~/.ssh/config file so you never need to know that port or your static public IP again.  Also, setup denyhosts or fail2ban to do something about brute-force attacks and once you get things working perfectly, setup ssh-keys for all non-local access.

Some ssh articles:
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

As for nextcloud, I use it only with either an ssh-tunnel or over a full VPN.  HTTPS is just too hackable these days.  I see 10K HTTP/HTTPS attacks against my public servers every day - all looking for php hacks.  To me, it just isn't worth the risks to put a PHP-webapp directly on the internet.

The ssh-tunnel is setup this way:
```
$ more fireproxy-home.sh 
#!/bin/bash

# Only start SOCKS proxy if necessary
if  [ $(ps -eaf |grep ssh |grep -c 64000) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   ssh -f -C -D 64000 public.name.com -NT 
fi 
 
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:64000"; 
firejail --private chromium-browser \
         --proxy-server="socks5://localhost:64000" &
```

---

### Post by ziegler911 on 2019-02-21
Thank you for your response TheFu.

I reconfigured my router to forward a high port to my Local Servers Static IP -port 22/tcp.

I somewhat understand the ssh_config file. I made hosts and got them working on my internal network from my laptop to my desktop via ssh(as outlined in the articles you provided). However, I am still lost on how to configure the sshd_config or ssh_config to allow ssh connection from outside of my network... And mainly, what needs to be configured on the server-side versus the client-side (Ubuntu Server running in virtualbox vs LinuxMint OS running on laptop)

Do I need to add the Public IP from where I am connecting outside of network ? This will always change if I am moving location to location. Or, do I add the public IP that my router is using... I do not have a static IP but I do have a DNS from namecheap. I'm not sure if this changes anything.

When I type in user@publicIP and specify the high port, it times out. I have a feeling the server is not allowing these connections... I'm not sure what arguments to change in the config files without making my system vulnerable.
When I ping my public IP address with the specified port it works. When I ping my subdomain pointing at my public IP it works. When I try to ssh using my Public IP, timeout.

Lastly, I did not setup any keys yet because I am unable to get the other things working -I'll do that last because I see the importance!

---

