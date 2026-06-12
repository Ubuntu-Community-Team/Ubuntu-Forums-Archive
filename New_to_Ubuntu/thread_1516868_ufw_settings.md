---
title: "ufw settings"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-24
New to ubuntu.

Using gufw I set Incoming to Deny and Outgoing to Deny
Log options: Enable gufw logging
                  Enable ufw logging

Set level: Low

I can't find anywhere the meaning of 'Low' (medium, high, full).

Will the deny outgoing cause any problem? I can use the web ok so thought,
deny outgoing would be a good thing.

---

### Post by Paqman on 2010-06-24
Is there a particular outcome you're trying to achieve? Normally the default settings in Ubuntu are perfectly secure, you only need to mess about configuring your firewall if you've installed something like a server package.

---

### Post by Primus1 on 2010-06-24
Thanks for the reply.
My aim is just to be safe online, surfing, email, downloads. The default setting was 'deny' for incoming I think, and 'allow' for outgoing, I thought it would be a good idea to deny the outgoing too, just in case :). It didn't seem to get in the way of surfing the web so just wondering if I should leave it or not.

---

### Post by Paqman on 2010-06-24
> **Primus1 said:**
> 
My aim is just to be safe online, surfing, email, downloads.

Good news then, you already are!

The default setting on Ubuntu is that there are no services listening on any ports. Effectively every port is shut to any attack, because there's nothing listening that an attack could connect to. This is a considerably more secure default than some other operating systems (points subtly in the direction of Windows).

But don't just take my word for it. Turn ufw off and go run one of those silly "shields up" type scanners on the internet. You'll be pleasantly surprised at the results.

If you do end up installing some kind of server software, then you should take appropriate precautions. But desktop apps aren't a problem.

---

### Post by Primus1 on 2010-06-24
Thanks, one last thing, how will I know it is running at startup, always on, is there a list of running processes anywhere?

---

### Post by sydbat on 2010-06-24
Not to hijack, but I would like to know what settings to have for a home network with ssh going through a router. Or is it even necessary because the router is firewalled enough?

And one way to find your running processes is System > Administration > System Monitor.

---

### Post by Primus1 on 2010-06-24
Great sydbat, just what I was looking for.
Not hijacking, these threads help everyone ):P

Can't see ufw or gufw listed as running hm.

---

### Post by Rubi1200 on 2010-06-24
Another great tool for monitoring processes is htop (available from the Ubuntu Software Center).

Check it out:

[http://htop.sourceforge.net/](http://htop.sourceforge.net/)

---

### Post by bodhi.zazen on 2010-06-24
> **Primus1 said:**
> New to ubuntu.

Using gufw I set Incoming to Deny and Outgoing to Deny
Log options: Enable gufw logging
                  Enable ufw logging

Set level: Low

I can't find anywhere the meaning of 'Low' (medium, high, full).

Will the deny outgoing cause any problem? I can use the web ok so thought,
deny outgoing would be a good thing.

see man ufw:

[http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html)

> 
**[B]LOGGING**[/B]

       **ufw** supports multiple logging levels. **ufw** defaults  to  a  loglevel  of
       &#8217;low&#8217;  when  a  loglevel is not specified. Users may specify a loglevel
       with:

         ufw logging LEVEL

       LEVEL may be &#8217;off&#8217;, &#8217;low&#8217;, &#8217;medium&#8217;, &#8217;high&#8217; and full.  Log  levels  are
       defined as:

       **off**    disables ufw managed logging

       **low**    logs  all  blocked packets not matching the default policy (with
              rate limiting), as well as packets matching logged rules

       **medium** log level low, plus all allowed packets not matching the default
              policy,  all  INVALID  packets,  and  all  new connections.  All
              logging is done with rate limiting.

       **high**   log level medium (without rate limiting), plus all packets  with
              rate limiting

       **full**   log level high without rate limiting

       Loglevels  above  medium  generate  a  lot  of  logging output, and may
       quickly fill up your disk.  Loglevel  medium  may  generate  a  lot  of
       logging output on a busy system.

       Specifying &#8217;on&#8217; simply enables logging at log level &#8217;low&#8217; if logging is
       currently not enabled. > **sydbat said:**
> Not to hijack, but I would like to know what settings to have for a home network with ssh going through a router. Or is it even necessary because the router is firewalled enough?

And one way to find your running processes is System > Administration > System Monitor.

It depends on what you wish to accomplish with a firewall.

By default , services (ssh, apache) are "public" meaning they will allow connections by default.

With http (Apache) this is most likely exactly what you want.

With ssh, however, you probably do not want that.

So ...

You can secure or limit connections to ssh via several methods.

The most popular methods are to use ssh keys and disable passwords. People then use services such as denyhosts or fail2ban.

You can write rules for iptables to allow connections from only a limited ip address range, or iptables rules to block connections after som any failed attempts.

You can also use many other features such as rules in sshd_config (Allow/Deny users), TCP wrappers (hosts.allow and hosts.deny), and kerberos.

The point is, if you run ssh, and forward ports, be sure to secure it. As I said above, ssh keys , disable passwords, and denyhosts or fail2ban are sufficient for 99.99 % of ssh users.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Primus1 on 2010-06-24
thanks bz, understand the different levels of report now, and some of the other info on the page :)

---

### Post by Primus1 on 2010-06-25
ufw is not running at startup of computer, I looked at gufw at startup and it is grayed and the 'enable' box was empty, checked the status in terminal and it said ufw not running, don't understand why its not running after I ticked 'enable' any help please?

---

### Post by M1ke on 2010-06-25
> **Primus1 said:**
> ufw is not running at startup of computer, I looked at gufw at startup and it is grayed and the 'enable' box was empty, checked the status in terminal and it said ufw not running, don't understand why its not running after I ticked 'enable' any help please?
 
That's because it doesn't need to be! It was a question I had not long after installing Ubuntu too, but the short version as I understand it is this:
 
UFW doesn't run like a conventional windows firewall, so there isn't an associtated app or process permanently running in the background, or something you can command to "run at startup". UFW is simply a means to configure something called "iptables" which is what is actually protecting you. iptables is part of the operating system itself. Once you've used g/ufw once to tell Ubuntu what settings you want that's it; everything is configured and will stay that way. Nothing has to "run" permanently in the background to keep you protected.
 
As someone's already mentioned previously, the default settings in Ubuntu are perfectly secure for general internet use. Go ahead and test it on those "shields up"-style sites mentioned earlier :)

---

### Post by Primus1 on 2010-06-25
That's great, thanks Mike.

---

### Post by bodhi.zazen on 2010-06-25
> **Primus1 said:**
> ufw is not running at startup of computer, I looked at gufw at startup and it is grayed and the 'enable' box was empty, checked the status in terminal and it said ufw not running, don't understand why its not running after I ticked 'enable' any help please?

The graphical interface does not run at start up, but you should be able to start UFW and click the enable button.

Did you install any other firewall tools such as firestarter ?

Open a terminal and enter :

```
sudo ufw status
sudo iptables -L -v -n
```

Post the output here if you do not understand it.

See also :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

Once you configure your firewall with a graphical tool, ie enable UFW, you then close the graphical tool and your firewall settings remain active. 

To check your firewall settings, use the above commands.

To test your firewall use a tool such an nmap (zenmap is a graphical front end).

---

### Post by Primus1 on 2010-06-25
yes I have been using Firestarter in the past. Result of inputing your code, don't know if this is in the right format, not got a box round it:

dave@dave-desktop:~$ sudo ufw status
[sudo] password for dave: 
Status: active
dave@dave-desktop:~$ sudo iptables -L -v -n
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
 2257  253K ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
    6   252 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    8   320 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
19979   23M INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
    0     0 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.3          192.168.1.1         tcp dpt:53 
 2303  147K ACCEPT     udp  --  *      *       192.168.1.3          192.168.1.1         udp dpt:53 
    6   252 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    4   800 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
17362 2617K OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 
    0     0 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
19975   23M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    4   304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
16555 2581K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    3   228 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  804 35408 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
    0     0 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
    0     0 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
dave@dave-desktop:~$

---

### Post by bodhi.zazen on 2010-06-25
ufw is working.

firestarter conflicts with ufw/gufw

so to fix your gufw problem you need to purge (not remove) firestarter.

```
sudo apt-get install firestarter
sudo apt-get purge firestarter
```

If you simply remove firestarter , therevare config files left behind that conflict with ufw.

This is an old bug , I filed a bug report over a year ago, and the problem has not been fixed, likely because firestarter is no longer maintained.

---

### Post by Primus1 on 2010-06-25
dave@dave-desktop:~$ sudo apt-get install firestarter
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
dave@dave-desktop:~$ sudo apt-get purge firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firestarter*
0 upgraded, 0 newly installed, 1 to remove and 53 not upgraded.
After this operation, 2,015kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157628 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
dave@dave-desktop:~$ 

I guess I should reboot now? is my setting in gufw to deny 'outgoing' helping or hindering security?

---

### Post by bodhi.zazen on 2010-06-25
> **Primus1 said:**
> dave@dave-desktop:~$ sudo apt-get install firestarter
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
dave@dave-desktop:~$ sudo apt-get purge firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firestarter*
0 upgraded, 0 newly installed, 1 to remove and 53 not upgraded.
After this operation, 2,015kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157628 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
dave@dave-desktop:~$ 

I guess I should reboot now? is my setting in gufw to deny 'outgoing' helping or hindering security?

No need to reboot, gufw should now be working.

setting outgoing to deny probably will not help you much.

---

### Post by Primus1 on 2010-06-26
Thank you, must be quite a few newish people experiencing this bug issue.

---

### Post by Primus1 on 2010-06-26
This is strange. My computer could not connect to the internet this morning. I opened gufw and set the 'outgoing' to allow ( after prieviously changing it to 'deny' ), opened Firefox again and the internet connection now works! Odd.

---

### Post by bodhi.zazen on 2010-06-26
> **Primus1 said:**
> This is strange. My computer could not connect to the internet this morning. I opened gufw and set the 'outgoing' to allow ( after prieviously changing it to 'deny' ), opened Firefox again and the internet connection now works! Odd.

Yes, that is how it works.  You need to allow outbound connections if you wish to connect to the internet.

---

