---
title: "Cannot ping on localhost"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by Manasss on 2014-04-17
Hello

I'm having this issue for a while about connection to localhost on Ubuntu 12.04.
I don't know why/how the problem began, but I realize it when I was trying to debug some java application on eclipse and it was refused.
When trying to connect to a local database, poiting to **localhost** it was refusing too, but after changing my url connection to **127.0.0.1** instead of localhost, it was successful.

Using ping, packages are retrieved when **127.0.0.1**, but don't with **localhost **(the terminal stays stuck)
> manasses@CIT009990:~$ ping localhost
PING localhost.cit (172.16.34.12) 56(84) bytes of data.



The strange thing is that this happens only when I'm connected to my company network. When I'm connected to my home network, the problem does not occur.

I tried some tests, like reducing my /etc/hosts file to only:
> # Do not remove the following line, or various programs
      # that require network functionality will fail.
      ::1     localhost.localdomain   localhost
      127.0.0.1   localhost
It was initially like this:
> # Do not remove the following line, or various programs
# that require network functionality will fail.
::1     localhost.localdomain  localhost
127.0.0.1    localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes

ff02::2 ip6-allrouters
And even tried to add my internal IP on the company network domain, like this:
> # Do not remove the following line, or various programs
# that require network functionality will fail.
::1     localhost.localdomain  localhost
127.0.0.1    localhost

172.16.34.12    localhost localhost.localdomain

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes

ff02::2 ip6-allrouters
But have no success at all.
I need to solve this for development purposes. I would appreciate any suggestion/help

Thanks in advance

---

### Post by SeijiSensei on 2014-04-17
It's possible that your company's DNS server has a non-standard address for localhost:
> 
manasses@CIT009990:~$ ping localhost
PING localhost.cit (172.16.34.12) 56(84) bytes of data.

That's pretty likely a misconfiguration on the admin's part.  All my DNS zone files have localhost pointing to 127.0.0.1.  Any other address should not be named "localhost."

An additional complication comes from the use of a "domain search" parameter that is probably passed to your computer by the company's DHCP server.  That tells the client's DNS resolver to add the .cit domain to any "unqualified" hostnames like "localhost."  The easiest way for you to fix the problem is to add localhost.cit as an alias for localhost in /etc/hosts:

```

127.0.0.1     localhost     localhost.cit

```

Re-reading your post leaves me confused though.  Is 172.16.34.12 the IP address of your machine? Then that ping result I posted above is likely caused by your adding your IP to /etc/hosts.  It may be that the company's servers are correctly configured, but you overrode that in /etc/hosts.  So I'd like to suggest a little test.  First, determine the IP address of the company's DNS server and run the command:
```
host localhost ip.of.dns.server
```
What does that return?

---

### Post by Manasss on 2014-04-17
Hello Seiji, thanks for your answer.
Do you have an idea about anything I can do locally to bypass this configuration? (the problem is that the IT department on the company does no support for Linux)
Thanks

---

### Post by SeijiSensei on 2014-04-17
Did you make the change I suggested to /etc/hosts?  That should fix the problem.

---

### Post by Manasss on 2014-04-17
Sorry for my misunderstanding

 The suggestion of /etc/hosts does not solved. It became like this after your suggestion: 
> # Do not remove the following line, or various programs
 # that require network functionality will fail.
 ::1         localhost.localdomain localhost
 127.0.0.1     localhost
 127.0.0.1         localhost     localhost.cit

And **ping localhost** continues answering the same as I posted.

Your analysis made me this about my host network configuration, and I guess **172.16.34.12** is not my IP address, as **ifconfig**:
> eth1      Link encap:Ethernet  HWaddr 74:86:7a:f5:e7:b4  
          inet addr:172.16.44.28  Bcast:172.16.44.255  Mask:255.255.255.0
          inet6 addr: fe80::7686:7aff:fef5:e7b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78800355 (78.8 MB)  TX bytes:25348030 (25.3 MB)


I found the DNS servers by running:
> nmcli dev list iface eth1 | grep IP4


And the DNS list:
> IP4.DNS[1]:                             172.16.22.6
IP4.DNS[2]:                             172.16.22.40
IP4.DNS[3]:                             172.16.22.69
IP4.DOMAIN[1]:                          cit


Using the command you suggested on one of the IPs of DNS, I got:
> manasses@CIT009990:~$ host localhost 172.16.22.6
Using domain server:
Name: 172.16.22.6
Address: 172.16.22.6#53
Aliases: 


Did this help you to help me?

---

### Post by steeldriver on 2014-04-17
what's the order of the 'hosts' line in your /etc/nsswitch.conf file?

---

### Post by Manasss on 2014-04-17
About nsswitch.conf file:
> hosts:          file mdns4_minimal [NOTFOUND=return] wins dns mdns4

---

### Post by steeldriver on 2014-04-17
Did you paste that exactly, or type it? the keyword should be files not file I think e.g.

```

hosts:          file[COLOR=#ff0000]**s**[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4

```

---

### Post by Manasss on 2014-04-17
Pasted it.....the keyword files is on networks line:
> hosts:          file mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files


---

### Post by SeijiSensei on 2014-04-17
According to "man nsswitch.conf" the correct keyword is "files" in all cases.

---

### Post by Manasss on 2014-04-22
Hello guys, thanks for the help

Seems everything is ok now. Maybe because I restarted the machine on the past days after following your instructions.

PS: I didn't change the **/etc/nsswitch.conf** file and **ping** now returns this:
> manasses@CIT009990:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.041 ms

---

