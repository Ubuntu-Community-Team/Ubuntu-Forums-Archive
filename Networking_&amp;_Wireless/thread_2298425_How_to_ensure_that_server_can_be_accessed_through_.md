---
title: "How to ensure that server can be accessed through SSH only?"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by somebody3 on 2015-10-10
I have a remote Ubuntu server that I access through SSH. I would like to make sure that this is the only possible way of accessing it. What would be the best way to find out?

---

### Post by TheFu on 2015-10-10
The best way happens on the edge router; only open the port for ssh and nothing else to this server in the port forwarding rules.

2nd, verify that the only service/daemon listing on a public IP is openssh-server.  use netstat, lsof,  chkconfig or whatever systemd requires now. 

3rd, run a network scan against the server from another machine on the same LAN and check all 65K ports.  use nmap.

Different releases of Ubuntu server have slightly different commands for some of these things.

IMHO, server security starts with a smart network security setup. Putting **any** server directly on the internet is crazy talk these days.

---

### Post by SeijiSensei on 2015-10-11
> **TheFu said:**
> IMHO, server security starts with a smart network security setup. Putting **any** server directly on the internet is crazy talk these days.
I guess I must be crazy then.  I have three VMs at Linode with public IPs.  They all have iptables firewalls, of course, and SSH is limited to connections over my OpenVPN tunnels.  Is that sufficient to constitute a "smart network security setup," or am I "crazy?"  None of them have ever been compromised in any way.

---

### Post by TheFu on 2015-10-11
Yes, I think you are crazy. ;)  

However, your Unix skills can mitigate most of the security issues, but not all. Security needs to be deployed in layers.  Edge routers are the first line of defense. Network-based firewalls are the 2nd. Hardened servers are 3rd, limiting the services that can be accessed by internet connected IPs are the 4th ... I didn't come up with these ideas - they are well-know "best practices" understood for decades.  

Some references:
* [Real World Linux Security]("http://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562/") by Bob Toxen
* [Practical Unix & Internet Security]("http://www.amazon.com/Practical-Unix-Internet-Security-3rd/dp/0596003234/") by Simson Garfinkel and Gene Spafford

Just 1 opinion after seeing many compromised systems over many years. I've helped companies under attack by foreign states redirect those attacks. These attacks where penetrating both BSD and Linux firewalls. We weren't able to figure out how. Ended up replicating all switch port traffic for analysis and moved to a new public subnet which wasn't tied to the company name. That was 2 yrs ago and we haven't seen any further attempts.

Regardless, I think the OP would appreciate your views on what to run to check for open ports and security.

Being compromised isn't always something we recognize. I haven't had any of my servers compromised since 2002 (as far as I know). Prior to that, had 2 compromises, which taught me a great deal. Turned over one of the HDDs to have it analyzed by experts at work. Never got it back.  About a year ago, I was playing at a CTF competition and one of the other teams decided to compromise my laptop. It was fully patched and not running any services except ssh - with only key-based authentication allowed. All inbound ports except 22 were firewalled.  Just sayin'.   Sure, I could have made a mistake, but how hard is a default DENY and 1 tcp port IN allowed?  This is why layers are so important.  I was prepared for the compromise with daily, automatic, system, backups,  before the travel.

Hope this begins a relevant discussion for the OP.

---

### Post by somebody3 on 2015-10-11
Thanks for the replies!

Security has become a great concern for me indeed, especially after seeing over 30000 bruteforce attempts just within a few days.

I've ran ```
netstat -ntlp | grep LISTEN
```

and in the output I saw only 2 entries, both are for my ssh port, I suppose one is for ipv4 and another for ipv6. Is it enough to be sure that SSH is the only way to access my server?

---

### Post by TheFu on 2015-10-11
Securing ssh: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

There are other ways, but that article is probably sufficient. There is a trade-off between easy of use and security, after all.

Some people might want to block all external IPs for ssh, except the few subnets/IPs they KNOW will be used inbound. I can't do that, because we have people traveling all over the world who need remote ssh access. We are a tech company with Unix experts, so ssh is fine, rather than deploying a full VPN.

---

### Post by Doug S on 2015-10-11
> **SeijiSensei said:**
> I guess I must be crazy then.  I have three VMs at Linode with public IPs.  They all have iptables firewalls, of course, and SSH is limited to connections over my OpenVPN tunnels.  Is that sufficient to constitute a "smart network security setup," or am I "crazy?"  None of them have ever been compromised in any way.I guess I am crazy also. My main server is directly connected to internet.

TheFu: I get "403 forbidden" clicking on that link in your last post.

---

### Post by somebody3 on 2015-10-11
> **TheFu said:**
> Securing ssh: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

There are other ways, but that article is probably sufficient. There is a trade-off between easy of use and security, after all.

Some people might want to block all external IPs for ssh, except the few  subnets/IPs they KNOW will be used inbound. I can't do that, because we  have people traveling all over the world who need remote ssh access. We  are a tech company with Unix experts, so ssh is fine, rather than  deploying a full VPN.

Thanks, I'm actually thinking of  allowing access only from the ip range of my ISP and deny everything  else. How would I achieve that? All I really have at the moment is just ufw  enabled.

And what about my previous question:

> **somebody3 said:**
> 

I've ran ```
netstat -ntlp | grep LISTEN
```

and in the output I saw only 2 entries, both are for my ssh port, I suppose one is for ipv4 and another for ipv6. Is it enough to be sure that SSH is the only way to access my server?

---

### Post by TheFu on 2015-10-12
If you allow access only from a portion of your ISP, what good does that achieve? You are already at home. It is when you are away from home that ssh/sftp access is most useful.  Perhaps from a cafe or school or work or library?  Those won't be on your ISP.

The netstat command shows ports that have listeners.  No necessarily what will work.  Plus, I think netstat needs elevated access to see which processes are doing the listening.
```
$ sudo netstat -ntlp | grep LISTEN
tcp        0      0 0.0.0.0:82              0.0.0.0:*               LISTEN      927/nginx -g daemon
tcp        0      0 172.22.22.41:4949       0.0.0.0:*               LISTEN      951/munin-node  
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      869/sshd        
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1608/master     
tcp        0      0 0.0.0.0:9000            0.0.0.0:*               LISTEN      6749/thin server (0
tcp        0      0 0.0.0.0:9001            0.0.0.0:*               LISTEN      6760/thin server (0
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      927/nginx -g daemon

```
Here's the output on 1 of my reverse-proxies. The outside world can't get to most of those ports. A few are only for the local machine or 1 specific machine on the same subnet. Showing the daemon is helpful, right?

@Doug - I do block abusive subnets and some highly abusive programs. Sorry if this caught you. Try a different browser and/or OS.  Firefox/Chromium on Linux should work fine. Most of the subnet blocking (7K rules) happens with the firewall, so a 403 would not be seen.

---

### Post by Doug S on 2015-10-12
> **TheFu said:**
> @Doug - I do block abusive subnets and some highly abusive programs. Sorry if this caught you. Try a different browser and/or OS.  Firefox/Chromium on Linux should work fine. Most of the subnet blocking (7K rules) happens with the firewall, so a 403 would not be seen.I was using MS windows, with firefox. I am a server guy and rarely use desktop linux, but I tried it on a desktop VM and it worked.
This user agent did not work:```
Mozilla/5.0 (Windows NT 10.0; WOW64; rv:41.0) Gecko/20100101 Firefox/41.0
```This user agent worked:```
Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:41.0) Gecko/20100101 Firefox/41.0
```@somebody3: sorry for the slight tangent on your thread.

By the way I do not change my ssh port number. It is on purpose, because I study the hacking attempts. I also don't use fail2ban. I use (with great success) these iptables rules:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```Although I admit, over the last year I have had to direct DROP many many large subnets from China due to their incredible persistence.

---

