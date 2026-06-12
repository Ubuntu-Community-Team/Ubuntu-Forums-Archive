---
title: "Credibility of Domain Information from a Linux Machine"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by rangaraj2 on 2014-09-18
Hi


In an attempt to Determine which Domain my Linux Machine belongs to, I stumbled on methods like using the commands :
-> "hostname -d"
-> "dnsdomainname"
-> "domainname"

And, am not sure whether to trust them. Due to the following Reason:
[INDENT]
I added my Ubuntu 12.04 PC to a Windows AD using the Likewise-Open tool.
I followed the GUI procedure of using the "domainjoin-gui", as well as the "domainjoin-cli join <domain> <username>" command

I verified that the machine was joined to the AD & the information was updated in the Local Files (/etc/hosts).
Thus, I was able to get the Domain Information using the commands "domainjoin-gui" & "domainjoin-cli leave".

But, when I Left the Domain using the Same Tool, these Information were Not Reset. And, was still being shown as part of the AD.[/INDENT]


Here are my questions :

1. Are any other Ways / Commands to Correctly Determine the Domain my Machine is a part of ? 

2. Is there a way to resolve the Domain Netbios Name at the Client (Linux Machine) itself ?

3. Can a LInux PC be joined to Domains other than AD ? If yes, How to achieve it ? And, which Commands can be used to determine the similar Details of those Connections ?



Thanks in Advance


PS : Ran all the commands as "root"

---

### Post by TheFu on 2014-09-18
"domain" is a generic term.  You are confusing IP Domain, DNS Domain, NIS Domains and AD Domain - they have little, if nothing to do with each other.  Those commands do not have anything to do with AD Domains.

AD Domains came about 20 yrs too late and that company selected a name that was similar to, but unrelated for some, unknown, reason. I don't know why they did this - it was definitely a terrible idea ... sorta like naming an OS after a piece of glass was.  TERRIBLE IDEA.

I don't use AD - so cannot help you.  I think you want to research Samba4 commands.

---

### Post by rangaraj2 on 2014-09-19
> **TheFu said:**
> "domain" is a generic term.  You are confusing IP Domain, DNS Domain, NIS Domains and AD Domain - they have little, if nothing to do with each other.  Those commands do not have anything to do with AD Domains.

Yeah, even I came across the different types of Domains. But, I thought there were only 2 : DNS & NIS/YP.. Can you please elaborate what the IP & AD Domains are ?
Also, if they have nothing to do with each other, How is it that the dnsdomainname command returned the AD, only after I joined my Machine to it ??


> **TheFu said:**
> I don't use AD - so cannot help you.  I think you want to research Samba4 commands.


I tried searching about Samba too. But, it is a little broad. It would be really helpful if you provided a few related links. Thanks.

---

### Post by bab1 on 2014-09-19
> **rangaraj2 said:**
> ... I thought there were only 2 : DNS & NIS/YP.. Can you please elaborate what the IP & AD Domains are ?

As @TheFu said the term "domain" is a generic term.  In this instance it really is a reference to "area of control" or "area of responsibility".  In that context an IP domain might be considered an IP network which has boundaries of the network ID (i.e. 192.168.1.0 /24) and the broadcast address (i.e. 192.168.1.255 /24).  An AD (Active Directory) domain is a centralized collection of responsibilities that include user accounts and DNS and Kerbros tickets.  All of this is maintained in a LDAP structure.
> 
... How is it that the dnsdomainname command returned the AD, only after I joined my Machine to it ??

Since AD maintains the domain's DNS tables you can have a return on your DNS query if the listing is included.  That is what "Joining a Domain" means in an AD context.  You are adding the listing for your computer to the various AD services.
> 
I tried searching about Samba too. But, it is a little broad. It would be really helpful if you provided a few related links. Thanks.
Samba has nothing to do with DNS any of the other AD services.  Samba v3.6 (Ubuntu 13.10 or <) has no provisions for AD membership.  Samba v4.1 (Ubuntu 14.04 and >) has all the infrastructure to function as a AD domain controller if you configure it so.

The general topic of Windows Sharing (SMB/CIFS) and Samba is really a collection of protocols.  I would suggest starting at [Samba's documentation site ]("http://www.samba.org/samba/docs/").  I'm sure you will have more questions after a little reading.  It is a steep learning curve.  Things change all the time.  Microsoft is the leader they don't have to ask when they make changes for their benefit.  They do however share the information with Samba developers eventually.

---

### Post by hbot on 2015-03-25
All - please take note (South African English).


Windows Server 3.5, Windows NT 4 Server (NT4 Domains), Active Directory Server 2000 (AD2000), Server 2003 (AD2003), Server 2008/Server 2012 is different domains.  Never try to administer AD2000 domains with AD2003 domains - the allowance to have multiple lines in Server 2003 policies breaks the AD2000 policies (ie user and computer policies to change the behaviour of the logon messages).

Therefore you have NT4 domains and AD domains ("Kerebos" v5 version 5)
AD / Active Directory is a concept of Novell Netware 6.5 that was refined to the Windows situation - Novell took Microsoft to court and after years and years it was not resolved. 
Novell implemented DS (Directory Services) as a central store to list all users, printers and network resources.  
Interesting enough  - NAS iscsi as well as software RAID was already inplemented in Novell Netware 6.5.   The problem is the requirement to boot in a small DOS partition to load the OS.   Partitions is limited at this stage (but was very big for that time 1998).
Novell was years ahead on various technologies that is now only being implemented with Server 2012 / Windows 8/8.1

refer later about security principal and DNS / WINS.

Coming to Linux / Ubuntu
~~~~~~~~~~~~~~~~~~
I have realised if you want simple sharing then use NAUTILUS's add on to allow sharing.  BUT to not combine it with other SAMBA Linux Technologies.  It is mutually exclusive and causes unpredictable sharing behaviour.

I rather install the system-config-samba tools that install the necessary "guaranteed" GUI tools that allow the NT4 domain versus AD domain "KEREBOS v5" behaviour.   IF YOU INSTALL EVERY SAMBA ADMINISTRATION TOOL WITH SYNAPTIC, YOU GET THE INCONSISTENT BEHAVIOUR THAT I REFERRED TO.

Rather stay away from specific server management tools gadmin-samba and other fancy remote web-based server management tools.

With Ubuntu linux, I also realised not to mix Network Manager and command line /etc/network/interfaces. configurations - especially when using IPtables on pre-up post-up.

Interesting now is that the latests Novell services is hosted on a Linux base as OpenServer.   Novell Linux is available as workstation.   However I saw efforts on Microsoft's side to draw in Linux workstations and even allow running specific software on a Server 2008 / Server 2012 servers.  In server 2003 there were allowance for NFS, but it is properly refined in Server 2008/12 (NFS services, UNIX Identity Management, sub-system for UNIX-based applications).   Even in NT4 there were a subsystem to run legacy software but was disabled for C2 security certification / not used.


Back to Domains
~~~~~~~~~~~~~~
It can now be distinctly determined domain refers to a group of computers or very specifically mapping of names

_NIS Domain_ - A UNIX / Linux based domain - NIS Network Information Server  - storing of linux log on details.

_LDAP / Kerberos_ - replacement for NT4 and NIS (where applicable) domains.

**DNS  **[www.example.com](www.example.com).  ,  [www.army.mil](www.army.mil).   , mail.ananzi.co.za.   ,    smtp.google.com.  pop3.google.com all are mapping of the DNS name  .mil, .com, .edu, ac.za, to a _**IP ADDRESS (IPv4 and now IPv6) on the internet**_.   The predecessor of that was WINS (windows internetworking name service) or NetBIOS broadcast with lmhosts. and hosts. files on Windows and Linux computers.

_WINS_ - is a name service to nodally store a company's computers names registered on the network to improve faster access.   Microsoft **NETBUIE** and NOVELL NODE numbers **(IPX/SPX)** was the protocol before TCP/IP.  TCP/IP is now on WINS since NT4.
the concept of a-node, b-node, h-node, m-node
point to point only, broadcast node, hybrid (broadcast and then point to point name resolution) and mixed node (point to point to WINS/NetBIOS/DNS server and then broadcast if the server is down).

_Novell Netware DS (Directory Services)_ - predecessor of Microsoft AD

_NT 3.5 / WFW windows for workgroups 3.11_ network "peer to peer" and "client to server" networking technologies.

_NT4 with win 95/98_ - The nodal password control system of windows PCs.   DOMAIN\User logon that allows setting up domain trusts as one way or two way.  best layout is zulu.sun.ac.za with trusting domains alpha.sun.ac.za, bravo, charlie,..., uniform.sun.ac.za - maximum 4000 users per domain. Separate administration of computers and users - simple policy management. 

_AD - Active directory_   log on either up as DOMAIN\User or the security principal [email]User@DOMAIN.co.za[/email]  (and this is NOT a e-mail address).
Use of data structures like SCHEMA.  All structures managed in one tree - computers, users, other objects.  Allow for drill down Security permissions.   Object oriented approach - an object is - an object has properties.

_AD2000 with Win 2000 Pro / Win ME_ - LDAP based KERBEROS v5 implementation of global catalogue.  NESTED SECURITY GROUPS - allow groups to be specified in groups -ie finance_group and shopfloor_group is listed in DailyOps_SuperGroup to allow sharing of documentation on a network share.  Implemented DFS (SIMPLE distributed file system).  IPsec protocol implemented on the IP layer per workstation (encrypting of network communications) and certifcate serves.


_AD2003 with Win XP _- first ever IPv6 support.  Improvements on IPsec.  DFS spoke and node implementation.  Improved Policy Management.

_AD2008 with Windows Vista / Windows 7_ - refined for IPv6 (Internet Protocol) dynamic - IPv6 DHCP. support of the GlobalNames structure in DNS to allow the replacement of WINS style flat naming standard - ie serverFA1001.mybranchofficeCounty.mystateTexas.MyCountryUSA.COMPANY.comis now simply everyone in the company can be referred on the DNS name **ServerFA1001.**

_AD2012 with Win 8 / 8.1 _- refined for IoT (Internet of Things like IP TVs televisions and wireless gadgets) - support for providing of iSCSI targets

This is a broad outline to help to distinguish why domains, security principals, DNS names, e-mail addresses, Twitter Addresses,  RSS hyperlink feeds,  etc etc etc etc.

---

### Post by TheFu on 2015-03-25
Nice write-up - mostly correct as far as I know. WINS came way after IP and DNS - think I misread that above. To me, the main reason for WINS was to get around the lack of name resolution across subnets for MSFT systems.  Broadcasting names is easier, but less scalable.  Compared to other options, it is a nice answer for small networks - mostly.

NDS was awesome. Think it was related to x.500 directories which were too heavy for most needs, so LDAP was created.  I was a CNA, but never had to do NDS.

NIS+ has replaced NIS for Solaris networks. NIS has well-know security issues. I ran an NIS network in the mid-1990s for a few years and it worked great, before we needed to be paranoid. I don't think anyone makes NIS+ servers except Oracle with Solaris, but there are clients.

NFS on Windows worked in the mid-1990s. Ran a 600+ node network with it back then after our initial Netware deployment kept locking up every few weeks. The root cause of the lockups was traced to a netware backup tool (not from Novell) that replaced libc.

Most of this stuff doesn't matter any more other than from historical perspectives.  Wikipedia goes into much more detail on the older protocols than most care to learn.

Didn't AD2008 drastically improve the security model?

I feel bad for people who didn't grow up with these protocols as each had a different issue and was corrected in the next release. Old timers may remember the changes and how it is better today. Better might be easier or more secure and sometimes it is both, but not always. There is much history in each of these protocols.

For running Linux servers, I try to stay away from GUI tools for a number of reasons.  Just accept that modifying a few text files and restarting a service is how that happens. Sometimes you can just signal with -HUP to the PID to force a re-read of the config files. The CLI interfaces tend to have many more options and capabilities than any GUI "helper" tool can. Using both may or may not cause conflicts. Hard to say.

I didn't see any ZA specific differences in English. Beautiful country, BTW. Spent a few weeks in Cape Town a few yrs ago and presented at the CT-LUG [https://www.clug.org.za/](https://www.clug.org.za/) Nice folks.

---

