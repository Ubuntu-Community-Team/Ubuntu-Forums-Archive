---
title: "Unable to SSH or HTTPS into server from outside of LAN"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by kodb on 2014-09-11
I am ready to pull my hair out!
I run a series of 12.04 servers for my office.  All are on a local subnet typical addressing 192.168.x.x.  I have a static IP setup and am using Tomato firmware on a Linksys router: this works well.  On one of the servers we run our email/groupware (SOGo- love it) and an Owncloud instance.  This past few weeks I have been playing around with LDAP/Kerberos and installed these and dnsmasq.  I am now having difficulties I simply do not understand->  I can connect to the server in question (green) from any machine in the LAN either via its 192.168.x.x address or via the static address and forwarded port.  I cannot connect to either SSH or SOGo or Owncloud from outside the lan where previously this was not a problem and I was able to access email and calendars from both my phone and laptop while at home or traveling.  I am still able to SSH and https to all the other servers from outside the LAN.  Using my phone I can access all resources while connected to local wifi, but if I disable wifi I again am unable to connect to green but can connect and ssh to all other servers.  When I check the logs on the router it shows accepting the connection and forwarding it to the appropriate ip address internally for green.  Likewise, I am unable to connect to this one server from home but can access and ssh/https to all the other servers in the office from home.
Figuring this must be some issue with the server's firewall, I completely disabled UFW and reset iptables completely using a couple of scripts I found with google.  I confirmed accepting all with iptables -L.  This still does not fix the issue.
Hopefully someone will see what I am obviously missing!
Thanks
Bob

---

### Post by TheFu on 2014-09-12
Can you draw a picture and verify each part with tools? I find this invaluable in troubleshooting what seem to be simple things. Usually I've missed something.

Also - **ssh -vvv** will provide extra information about the connection attempts.

---

### Post by papibe on 2014-09-12
Hi kodb.

A few thoughts:

In case you installed dnsmasq on a Ubuntu server, and you haven't disable the DHCP/DNS service on the router, you have the case of a 'rouge DHCP or DNS server'. In other words, two machines are fighting to both assign LAN IPs and resolve names.

If you were doing DHCP reservations on the router (instead of static IP on the servers itself) before you set up dnsmasq, it could be as simple as the servers got new IP addresses thus making the forwarding rules to point to the wrong places.

Hope it helps.
Regards.

---

### Post by kodb on 2014-09-12
Thanks Fu-> I will try to use -vvv when I try to ssh in from home tonite.  Appreciate your help; your blog already sits in my bookmarks under Sysadmin and has helped me learn a lot over the past year or so
Bob

---

### Post by kodb on 2014-09-12
Thanks papibe!
This also helps-> previously the DHCP was running on the router.  I just checked and it is indeed disabled on the router and I am using dnsmasq on the server for dishing out dhcp leases.  There is a checkbox in the Tomato firmware that "use internal DNS" I just disabled.  Will check that once I get home and see if I can make some headway.
Bob

---

### Post by kodb on 2014-09-13
OK so still stuck. I used ssh -vvv per TheFu's post-> this shows debug1 results of connecting to the router at our static IP via the correct (nonstandard) port Ihave forwarded to the greenserver.  The connection simply times out.  I went ahead and tried different permutations of using the "internal dns" on the router and neither disabling nor enabling this appears to change my ability to either ssh to the server or use a webbrowser to even hit the apache2 test page.  I am able to ssh in without difficulty to any of the other servers still and hit their apache2 instances. Perplexing and frustrating.  All help eagerly accepted! Thanks Bob

---

### Post by TheFu on 2014-09-13
Exactly what command are you typing?

Did you draw the picture and fill in all the port and IP address details for each connection point?
Then validate that is exactly what is truly configured?

Are you using port translation on the router?   ext 63022 -->int 22

---

### Post by kodb on 2014-09-13
I have tried doing ssh with both putty and via cli.
Command used from cli:     ssh -vvv -p 10022  user@ipaddressgreenserver
Using port forwarding on router   ext 10022->int 22

I have the ports forwarded for https ext 11443-> int 443.

Yes I sketched out my connections and boxes and looked at each ip and then checked via /etc/network/interfaces or the router settings that they are correct.  I am running a static ip, one router, and then the server in question.  All the other servers (which are configured the same but with their own static ips) are reacheable via ssh and/or https.
I am bewildered.
Bob

---

### Post by elico on 2014-09-13
Have you tried to see tcpdump output while you try to connect from the outside network?
In networking this will be the first step ever to see if anything comes in from the router.
Kind of binary search troubleshooting.
If you get a syn packet it will be one thing and if not you know it's something on the tomato device probably.

---

### Post by TheFu on 2014-09-13
> **kodb said:**
> I have tried doing ssh with both putty and via cli.
Command used from cli:     ssh -vvv -p 10022  user@ipaddressgreenserver
Using port forwarding on router   ext 10022->int 22

I have the ports forwarded for https ext 11443-> int 443.

Yes I sketched out my connections and boxes and looked at each ip and then checked via /etc/network/interfaces or the router settings that they are correct.  I am running a static ip, one router, and then the server in question.  All the other servers (which are configured the same but with their own static ips) are reacheable via ssh and/or https.
I am bewildered.
Bob

Just to summarize:
* ssh to other systems both internal AND externally works as expected
* ssh to this system works internally, but not externally
* tried using IP addresses only - not DNS
* all internal systems are on the same subnet
* iptables doesn't have any rules preventing port 22 access
* routing table looks normal - single ethernet connection, no more.
* fail2ban hasn't locked out anything
* denyhosts isn't used
* the connections worked both internal and external before the updates
* tomato does NOT have any extra firewall rules

All of this is a stretch. Perhaps turning up the ssh-server AND iptables connection logging on the trouble box will help?

---

### Post by kodb on 2014-09-13
> **TheFu said:**
> Just to summarize:
* ssh to other systems both internal AND externally works as expected
Yes
* ssh to this system works internally, but not externally
Yes
* tried using IP addresses only - not DNS
Yes, use only numerical ip addresses not DNS
* all internal systems are on the same subnet
Yes
* iptables doesn't have any rules preventing port 22 access
Yes completely reset and checked with iptables -L.  UFW installed on system but disabled and iptables rewiped again so allow all
* routing table looks normal - single ethernet connection, no more.
there is a second nic with a separate ip address on each server.  Cannot hit that ip either
* fail2ban hasn't locked out anything
I removed fail2ban and purged as part of this troubleshooting; no change in behavior
* denyhosts isn't used
No
* the connections worked both internal and external before the updates
Yes.  The only changes I can see was me messing with LDAP and Kerberos with the thought of central auth and home dirs
* tomato does NOT have any extra firewall rules
Not that I am able to see.  As you prob know it runs a stripped version of dnsmasq but looking at the configs via ssh into the router is entirely unrevealing

*All of this is a stretch. Perhaps turning up the ssh-server AND iptables connection logging on the trouble box will help?
I will have to google how to turn up logging.  I did check all the tomato logs and it shows my outside connections being accepted and destination internal ip and port22 on the internal box as it should.  It's like the request is passed on and then hits a brick wall and times out the connection.  There is no activity when ssh -vvv is used other than the attempt to connect and then the timing out.  On all other ssh connections to the servers not being a PITA you get the usual gamish of ssh entries/negotiations/protocol and debut info.

I really appreciate your efforts to help-> this is really a bugger and I simply don't get why this won't work.
Bob

---

### Post by kodb on 2014-09-13
elico,
No have not tried tcpdump-not familiar with using that tool/command.  Will google and take a look.
Appreciate the suggestion/input as I am quite frankly stumped by this one.
Bob

---

### Post by TheFu on 2014-09-13
If the internal connections weren't working, I'd say to check the permissions on the ~/.ssh/ files and directory.

BTW - I use ~/.ssh/config to handle userid and port changes. Also, use different aliases for internal connections vs external connections so it is clear which I'm using.  I did it the hard way for 15 yrs - wish I would have known about this file earlier.  Any tool that uses ssh will honor this - rdfiff-backup, rsync, sftp, to name a few.

---

### Post by kodb on 2014-09-29
29SEP update:  Still not working.  Will post more once I have time to further mess with the dns servers as I suspect this or the ssh config is the culprit
Appreciate all the inputs thus far
Bob

---

