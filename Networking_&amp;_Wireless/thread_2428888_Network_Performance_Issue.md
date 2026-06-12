---
title: "Network Performance Issue"
date: 2019-10-10
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2019-10-10
I have a small network for my office. It contains two kinds of computers. 2 Ubuntu 18.024 servers and a number of windows 7 workstations. All are equipped with Gigabit Ethernet and connected through a dumb gigabit Ethernet switch.

We are experiencing problems with downloading messages from one of our servers whihc runs Exim4 as a mail server as well as Samba for file sharing.

When a local user download email via POP3 the downloads are extremely slow and Windows Task Manager indicates less than 1% network utilization.

However when I contact the same mail server over the Internet and download email it downloads much faster for the same accounts, whether to a Unix machine or a Windows 7 Machine essentially equal to the ones in the office..

There is obviously something wrong, but I'm at a loss trying to figure it out. Any suggestions?

---

### Post by TheFu on 2019-10-10
Exim has a few security issues. Is your system currently patched?
I wouldn't put a high-risk service like email on the same system that has Samba.  IMHO, all file sharing needs to be as far away from the internet as possible, even on a different LAN and all other internet-facing services.

What do the log files show on all the systems?  Slowness can be caused by all sorts of things, but hardware failures is where I always start.

---

### Post by rsteinmetz70112 on 2019-10-11
I thought I'd replied to this but I guess I forget to hit Submit :(
> **TheFu said:**
> Exim has a few security issues. Is your system currently patched?
It is regularly patched.
> 
I wouldn't put a high-risk service like email on the same system that has Samba.  IMHO, all file sharing needs to be as far away from the internet as possible, even on a different LAN and all other internet-facing services.
The email server is behind a router that does 1 to 1 NAT. 

[/QUOTE]
What do the log files show on all the systems?  Slowness can be caused by all sorts of things, but hardware failures is where I always start.[/QUOTE]

There is nothing I can find in my logs that indicate a problem. As far as Hardware both internal and external connections use the same hardware and switch. Some of the remote machines are effectively identical to the internal ones and perform much faster with regard to downloading mail. All of the internal machines show the same problem, I don't see a single piece of hardware whihc is implicated.
One thought I had is that since the email is on the same machines as the user honme directories that may be somehow causing the problem.

---

### Post by TheFu on 2019-10-11
I wouldn't mix email with any other service.  Actually, I split email into a gateway box and a separate "communications server", with the gateway on a different, more risky, subnet.

Anyways, how are DNS handled internally vs externally?  That can slow access drastically and 18.04 server DNS is foobar'd IME. Samba uses a different method to resolve names than DNS, doesn't it?  If you allow avahi to run for Samba needs, perhaps changing the email clients to use {hostname}.local would make them faster?  Have you tried using LAN IPs too? Is that faster or not?

---

### Post by rsteinmetz70112 on 2019-10-11
> **TheFu said:**
> I wouldn't mix email with any other service.  Actually, I split email into a gateway box and a separate "communications server", with the gateway on a different, more risky, subnet.

Anyways, how are DNS handled internally vs externally?  That can slow access drastically and 18.04 server DNS is foobar'd IME. Samba uses a different method to resolve names than DNS, doesn't it?  If you allow avahi to run for Samba needs, perhaps changing the email clients to use {hostname}.local would make them faster?  Have you tried using LAN IPs too? Is that faster or not?

DNS is handled by each server independently. The workstation typica;lly use th eISP's router but some have had the DNS servers hard coded to know good servers.The designated DNS servers are a mix of the Google and the Registrar's servers, mostly because the ISP's DNS has proven flaky.  I am not using Samba's internal DNS. 

Upon further investigation the problem seems to be mote closely related to POP3 email downloads.

---

### Post by TheFu on 2019-10-12
But google doesn't know the name -to- IP lookup for your internal servers/IPs.  What is the internal DNS solution?  If there isn't one, the systems have to try lots of methods.

Can you ping by hostname from the clients to the pop server?  I'm curious, why use pop and not IMAP?

---

### Post by rsteinmetz70112 on 2019-10-13
Actually Google does know because the Public IP addresses are listed in our registrars DNS records.

I can ping by FQDN ( when ping is enabled) using the DNS name or the WINS name (internal to the LAN) and also can use Private IP Addresses. None of that seems to affect the network speed.

I use POP3 because I access email from many different machines and I like to keep backups of the emails at the different locations.

---

### Post by TheFu on 2019-10-13
Way to bury the lead.  So, internal and external systems always use the public IP to access the systems?  Really?

WINS only works for SAMBA. It has ZERO to do with DNS.  WINS has ZERO to do with email protocols.  Yes?

---

### Post by SeijiSensei on 2019-10-13
> **rsteinmetz70112 said:**
> I use POP3 because I access email from many different machines and I like to keep backups of the emails at the different locations.
Have you tried using IMAP4 instead?

I'm much happier with a single email repository that I can backup regularly rather than distributing messages around on multiple client machines.  I dropped POP3 long ago and have never looked back.

Try using a telnet client and see how fast it is.

```

telnet mail.example com 110
USER username
PASS password
LIST <== returns a list of msgid numbers and sizes
RETR msgid
QUIT

```
For instance, RETR 1 will display the first message.

---

### Post by rsteinmetz70112 on 2019-10-14
> **TheFu said:**
> Way to bury the lead.  So, internal and external systems always use the public IP to access the systems?  Really?
No they can use either.

WINS only works for SAMBA. It has ZERO to do with DNS.  WINS has ZERO to do with email protocols.  Yes?

The email server may be contacted locally by it's Private IP address, NetBIOS name, DNS name(s) or Public IP address.
External machines may contact it by its Public IP address, DNS name or MX record. It all depends on the way the email client is configured except of course for mail received from outside the local network.
External machines are not allowed to send mail, but can get mail.

As far as I can tell the contact method used does not affect performance, (it may in fact have some marginal effect but it's not much). I can even set up a local hosts file on a workstation with an arbitrary alias and performance is the same.

What I can tell is that performance is worse within the local network than over the internet, which makes no sense to me.

---

### Post by SeijiSensei on 2019-10-14
And the result of that telnet test was ....?

---

