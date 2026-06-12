---
title: "ssh connection timed out"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by highflie on 2011-02-09
Hi all,
 I want to remotely access a fedora desktop from my ubuntu computer via ssh. When I type the command this is what I got

lalit@lalit:~$ ssh -X b08lalit@10.25.32.5
ssh: connect to host 10.25.32.5 port 22: Connection timed out

When I ping the machine however, this is what I get

lalit@lalit:~$ ping 10.25.32.5
PING 10.25.32.5 (10.25.32.5) 56(84) bytes of data.
64 bytes from 10.25.32.5: icmp_seq=1 ttl=60 time=0.387 ms
64 bytes from 10.25.32.5: icmp_seq=2 ttl=60 time=0.414 ms

What should I do?

Thanks in Advance.

---

### Post by robsoles on 2011-02-09
Is it an absolute certainty that the fedora box is running openssh-server?

Is the firewall on the fedora box set appropriately, ie., port 22 is open on it's firewall?

Check the package manager in fedora for openssh-server, make sure it's installed - if it wasn't then try again after installing.

Still fails then confirm for sure that the firewall on the fedora box isn't blocking it.

---

### Post by highflie on 2011-02-09
The fedora's openssh is perfect. I can log on to that machine via a few PC's which are located in that same room (which all share a similar ip like 10.25.etc...). I just cant do that from my computer which has an ip 10.115.6.35. So, I think it's some problem with my firewall. But I don't know how to change those settings.

---

### Post by robsoles on 2011-02-10
The firewall on the 'ssh-client' (Ubuntu machine in this case) is not likely to be blocking an out-bound connection like that - it is possible to write rules for a system that 'lock you in' but I'm willing to doubt you've done so because most people who have know that they have and can even say when they did...

Your 'allow from' rule on the fedora box (ssh-server/host in this case) firewall may have '10.25.x.x' or similar in it, for a matter of 'allow local area network only' or something, if you can press into the fedora box's firewall and confirm that the rule is simply 'allow port 22' and not extra conditions - if it has 'allow from 10.25.x.x' then change that to 'allow from 10.x.x.x' and it should be fine.

Failing that:
Can you ping the server machine from the intended client machine?

Is there a switch/router "between" your computer and the ssh-server host? Can it's firewall be set inappropriately or does it in anyway isolate clients or entire networks?

There are more straws to clutch at, you could set up a virtual machine and give it 'bridged ethernet' connection and see that you can ssh to and from your virtual machine and your host system (when a VM uses bridged ethernet; requests to and from it with the host 'look' just like a normal connection between a pair of hosts.) - should reveal if your Ubuntu firewall has become rather badly configured...

---

### Post by robsoles on 2011-02-10
Just in case you are an absolute beginner, the following is much more helpful than my previous.

From the Ubuntu machine, that is failing to be a client, please post  back the terminal's response to```
sudo iptables -L
```I am hoping  for```
rob@rob-desktop:~$ sudo iptables -L
[sudo] password for rob: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```Assuming you  can access the fedora box the same command is likely to work and you can  check for rules to eliminate there as well.

A squiz at the openssh server's config would be handy too, hopefully it  is in the same place in Fedora as for Ubuntu.```
cat  /etc/ssh/sshd.config
```

---

### Post by P4man on 2011-02-10
actually, its probably a routing issue.  If port 22 isnt forwarded to the right machine, it wont work unless you are on the same node (behind the same router). If you have no control over the router, you may need to use a reverse ssh tunnel:
[http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/)

---

### Post by highflie on 2011-02-11
@robsoles: 

I typed out the command you asked me to.
This was the response I got from my computer(Ubuntu).


lalit@lalit:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  localdns.iitkgp.ernet.in  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  localdns.iitkgp.ernet.in  anywhere            
ACCEPT     tcp  --  10.128.2.2           anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  10.128.2.2           anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.115.6.255        
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.115.6.35          localdns.iitkgp.ernet.in tcp dpt:domain 
ACCEPT     udp  --  10.115.6.35          localdns.iitkgp.ernet.in udp dpt:domain 
ACCEPT     tcp  --  10.115.6.35          10.128.2.2          tcp dpt:domain 
ACCEPT     udp  --  10.115.6.35          10.128.2.2          udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
lalit@lalit:~$ 


On the Fedora Machine, what is the procedure to change the rules?

@P4man: Thanks for the link! But I dont think I have access to a middle machine.

---

### Post by robsoles on 2011-02-11
On the Ubuntu machine I want you to try ssh'ing the fedora box after:
```
sudo ufw allow out 22
```
(your response to iptables -L looks like you've got a GUI firewall manager installed, ufw changes may be discarded - I can't see your allow for outbound to port 22 rule, you may need to open it with whatever firewall manager is 'most active' in your Ubuntu system).

I haven't tried Fedora but if```
ufw -h
```doesn't report that ufw isn't installed then you can use that, otherwise if 'iptables -L' works on the Fedora box then have a look at ```
man iptables
```for how to change rules using that.

---

