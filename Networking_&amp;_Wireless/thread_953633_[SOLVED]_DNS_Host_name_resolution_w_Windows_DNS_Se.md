---
title: "[SOLVED] DNS Host name resolution w/ Windows DNS Server"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by lumberjackshaw on 2008-10-20
Hi all,

We have been testing Ubuntu on out network at work.  I have been having trouble getting the Ubuntu systems properly added to our windows DNS.  

I have configured the Ubuntu system for a dhcp network and have installed likewise and successfully joined my windows domain. Unfortuneatly, without a manual entry to the hosts record on both the DNS server and the Ubuntu system, name resolution fails.  

I have read hundreds of post on this forum with all kinds of good information but I don't want to edit the host records every time I add a new Linux machine. We have a samll network and I would rather not create a Linux server just to hanle DNS for the linux machines.  There has got to be a way to make this work with out manual entries on a windows network.?

Any help would be appreciated.

Thanks,

LumberJackShaw

---

### Post by Iowan on 2008-10-20
I don't know which of the hundreds of posts you've read - I presume you have seen the ones advising setting **/etc/dhcp3/dhclient.conf**to "send hostname"? I notice that several of those are still unsolved.

---

### Post by lumberjackshaw on 2008-10-20
Iowan,

I certainly do thank you for your input and quick reply.  I have checked the the dhclient.conf. The following was already enabled by default.  I am new to Ubuntu (a few months under my belt)so if this is not correct please let know.
```
send host-name "<hostname>" ;
``` 


Thanks,


LumberJackShaw

---

### Post by mxdoom on 2008-10-20
> **lumberjackshaw said:**
> Iowan,

I certainly do thank you for your input and quick reply.  I have checked the the dhclient.conf. The following was already enabled by default.  I am new to Ubuntu (a few months under my belt)so if this is not correct please let know.
```
send host-name "<hostname>" ;
``` 


Thanks,


LumberJackShaw

LimberHackShaw you do what you want you must set the DHCP scope option 015 with is DNS Domain Name. As an example my windows domain is a .local so I set the scope option to domain.local and when I requested a new IP for my Ubuntu machine it automatically got the needed information and I could resolve names. Normally this is done by windows machines by netbios and registering the domain suffix to the network card but linux doesn't do this. That is why this option was made on windows dns, so support not windows netbios systems.

---

### Post by lumberjackshaw on 2008-10-20
Iowan,

Thanks for the info.  That did fix the the dns.  I have only one more question.

From Ubuntu I can ping my windows machines only using the hostname.
When I ping windows systems from ubuntu, however, I have to use the full domain names as in hostname.domain.local to get a response.  Is this just something I have to deal with in a mixed network or can it be fixed?

Thanks,


LumberJackShaw

---

### Post by mxdoom on 2008-10-21
> **lumberjackshaw said:**
> Iowan,

Thanks for the info.  That did fix the the dns.  I have only one more question.

From Ubuntu I can ping my windows machines only using the hostname.
When I ping windows systems from ubuntu, however, I have to use the full domain names as in hostname.domain.local to get a response.  Is this just something I have to deal with in a mixed network or can it be fixed?

Thanks,


LumberJackShaw

LumberJacShaw, you will not see my repeat myself often. If you do as I told you in my previous post you can simply ping by the host name. You must go to the DHCP server and set the scope option 015 DNS Domain name so that it will supply whatever your domain.local is. When the computer gets a new IP it will pretty much be computer.domain.local so you will be able to ping computers by just the host name. This is the steps you must take to configure your dns to provide the needed information to be able to search by host name.

---

### Post by lumberjackshaw on 2008-10-21
You are right.  I thought I properly cleared the server of is leases and run the dhclient on Ubuntu.  Apparently, I had not.  The dhcp lease renewed overnight and it was working this morning when I came in.

Thanks again for the help.


LumberJackShaw

---

### Post by frozenjim on 2009-05-01
Just wanted to add my thanks here.

New Windows Server 2003 wouldn't allow any of my Ubuntu boxes to use tsclient - Error was "getaddrinfo: name or service not known"  

Added my full domain to [15] in the dhcp scope, deleted the records of my ubuntu machines, restarted networking on the ubuntu boxes and everything just works now.

Great answer.  This will also close a bunch of other open threads I think.

---

