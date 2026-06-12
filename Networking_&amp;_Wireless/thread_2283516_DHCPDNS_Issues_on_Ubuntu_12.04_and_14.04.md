---
title: "DHCP/DNS Issues on Ubuntu 12.04 and 14.04"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by Joe_Miller on 2015-06-22
Hello All,

First let me start off by saying I am not a networking expert, I know enough to get me into trouble.  I will gladly provide any configs, logs, etc that more knowledgable networking gurus on this forum would want.  First, I will start by giving a bit of background on this long standing DHCP/DNS issue on server 12.04.

I deploy many Ubuntu servers from a template in VMWare vSphere (private cloud).  Intermittently after building a DHCP VM I am unable to access the machine by hostname.  On the machine I see that it has in fact populated a lease for the machine, my network engineer sees that a lease is created on our DNS server (Infoblox) but only certain machines have DNS registered.  Another interesting thing to note is that these machines will first grab a 1 hour lease, then in most cases grab 1 day shortly after.  This is completely against our DHCP lease policy on our Infoblox server, we assign leases across all subnets to 1 week TTL so the fact that it's not getting a week seems that something on the Ubuntu machine or DHCP client is requesting a particular kind of lease.  Throughout these issues I can always ping the machine by the IP it is assigned initially, so it does always get network just intermittently not getting its hostname registered.  Let me just repeat what I said earlier in that these machine are built from the same template in vSphere so they are identical.

I have tried rebuilding a clean template from an ISO, same deal.  I have also tried building a new template from an ISO on 14.04, same result.  

The configs always look ok to me no matter what result I am getting (at least as far as I know).  The files are configured for DHCP, pointing to our name servers, and with our domain.

I really don't know what to try at this point except potentially trying an alternate DHCP client.  I was really hoping going to 14.04 would fix the issue but it hasn't.  Any help would be greatly appreciated, thank you!

---

### Post by papibe on 2015-06-22
Hi Joe_Miller. Welcome to the forum ):P

There are several things in play here. Could you give us more detail about your problem?
[LIST]
[*]Are you using isc-dhcp-server/bind combo, or dnsmasq?
[*]Is the DHCP server updating the DNS server using a key?
[*]Who is running DNS? the same server? 
[*]Are you checking that the machines are getting different MACs after they are created?
[*]Have you test any other rouges DHCP servers (using dhcp-probe for example)?
[*]
[/LIST]
Regards.

---

### Post by Joe_Miller on 2015-06-22
Hey Papibe,

- We are using Infoblox providing both DHCP and DNS without any security.
- No
- Yes
- Yes, different MACs for every machine built from the template
- No other DHCP servers

Sorry for the yes/no answers.  If you would like any additional details on any of these let me know.  My networking knowledge is fairly slim so I'm not sure how to expand on the questions you asked. Thanks for your help!

---

### Post by Joe_Miller on 2015-06-23
Anyone have any other ideas?  I am stuck.  Thanks!

---

### Post by nlee2 on 2015-06-23
Try putting a sniffer on the wire for 67/udp and 68/udp. You are looking for DHCPOFFER, DHCPREQUEST,DHCPACK functions.

---

### Post by Joe_Miller on 2015-06-23
Thanks for the suggestion.  I used wireshark to inspect the DHCP requests.  They look totally fine, however I am getting lease times of an hour when I'm supposed to get 1 day, even after specifying an option for 1 day in the dhclient conf file.  I am going to back to my network engineer with this lease time info and see what he says.

---

