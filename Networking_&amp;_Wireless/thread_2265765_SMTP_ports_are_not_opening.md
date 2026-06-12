---
title: "SMTP ports are not opening"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by musicweb on 2015-02-17
Having a problem with SMTP ports on our server.
We have enabled ports 25, 465, and 587 in the router, but
they don't show up in our nmap report. Does this usually
mean the ISP is blocking them?

This is the report on our open ports:

```

Nmap scan report for wm-mw.org
Host is up (0.00066s latency).
Not shown: 988 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
23/tcp    open  telnet
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
993/tcp   open  imaps
995/tcp   open  pop3s
8080/tcp  open  http-proxy
8081/tcp  open  blackice-icecap
10000/tcp open  snet-sensor-mgmt
20000/tcp open  dnp

Nmap done: 1 IP address (1 host up) scanned in 68.05 seconds


```

---

### Post by TheFu on 2015-02-17
Yes that is likely for port 25 on non-business connections.  From here they appear CLOSED - ISPs generally block port 25, not the others. 

I'd be very nervous having all those ports open on a single server. If they are forwarded to different servers internally, great. I wouldn't (and don't) run any non-encrypted services if there was any choice.  Definitely no plain pop3 or imap services are needed these days. All clients can do pop3s and imaps.  Telnet on the internet is just crazy, but you know that already.

---

### Post by musicweb on 2015-02-18
Some of the ports are routed to another server, yes.
We wrote to our ISP, but no response yet.
Is there a suggested iptables configuration shown anywhere?

This is ufw report, if it means anything.

```
root@wmmw:/home/bruce# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
10000/tcp                  ALLOW       Anywhere
25/tcp                     ALLOW       Anywhere
587/tcp                    ALLOW       Anywhere
20000/tcp                  ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
23/tcp                     ALLOW       Anywhere
24/tcp                     ALLOW       Anywhere
110/tcp                    ALLOW       Anywhere
143/tcp                    ALLOW       Anywhere
465/tcp                    ALLOW       Anywhere
993/tcp                    ALLOW       Anywhere
995/tcp                    ALLOW       Anywhere
587                        ALLOW       Anywhere
25                         ALLOW       Anywhere
80/tcp (v6)                ALLOW       Anywhere (v6)
10000/tcp (v6)             ALLOW       Anywhere (v6)
25/tcp (v6)                ALLOW       Anywhere (v6)
587/tcp (v6)               ALLOW       Anywhere (v6)
20000/tcp (v6)             ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)
23/tcp (v6)                ALLOW       Anywhere (v6)
24/tcp (v6)                ALLOW       Anywhere (v6)
110/tcp (v6)               ALLOW       Anywhere (v6)
143/tcp (v6)               ALLOW       Anywhere (v6)
465/tcp (v6)               ALLOW       Anywhere (v6)
993/tcp (v6)               ALLOW       Anywhere (v6)
995/tcp (v6)               ALLOW       Anywhere (v6)
587 (v6)                   ALLOW       Anywhere (v6)
25 (v6)                    ALLOW       Anywhere (v6)

587                        ALLOW OUT   Anywhere
25                         ALLOW OUT   Anywhere
587/tcp                    ALLOW OUT   Anywhere
25/tcp                     ALLOW OUT   Anywhere
587 (v6)                   ALLOW OUT   Anywhere (v6)
25 (v6)                    ALLOW OUT   Anywhere (v6)
587/tcp (v6)               ALLOW OUT   Anywhere (v6)
25/tcp (v6)                ALLOW OUT   Anywhere (v6)

```

---

### Post by SeijiSensei on 2015-02-18
What does nmap show if it is run from another machine on the local network?  Are the appropriate ports visible from behind the router?

If your ISP is blocking these ports, it's probably because your Terms of Service agreement forbids servers.  Have you read the TOS?

---

### Post by musicweb on 2015-02-18
The other server is an Apple G4, and I'm remote, so not sure how to use that software.
I'll need to read up on that.... :)
Anyway, our old IBM server was working fine for email, until Gentoo go all messed up on it.
It was old, so we decided to get a new server and OS.
All the ports shown in my post are enabled and open in the router.

This is what shows under the mail queue in Postfix:

> D75B41B80D25     2015/02/17 10:12     [email]admin@wm-mw.org[/email]     [email]musicweb2@sbcglobal.net[/email]     741 bytes     all network protocols are disabled

---

### Post by TheFu on 2015-02-18
The ISP has routers upstream from you. Is this server in a hosted data center, a business or a private home? That will tell us much.
What was the IP address for the old gentoo box that worked? Was it on the same subnet as this new machine?
After 5 messages, we still haven't nailed done what is blocking the SMTP traffic. As SeijiSensei asked, we need to see where the block is happening
* on the server itself
* on the LAN router
* on the WAN router
* at the ISP.
So running a nmap against each of those levels would be how I did it from inside AND outside the network. I visited the ISP webpage to find more details - all French, so couldn't read it. ;( They appear to have both residential and business offers.

Once that is determined, if the ISP isn't blocking, then we can get email working in fairly short order (assuming DNS is properly setup already).

BTW, Apple "Servers" haven't been supported in many years. It is a security nightmare if it is directly on the internet.  Or it is a hacker's dream - depends on your viewpoint. Hopefully, it is off or well locked down to only support extremely specific connections.

---

### Post by musicweb on 2015-02-18
The server is in a private home.
And it is in Canada, I'm in USA.

Not sure how to try nmap against all levels. I'll have to read up on that.

The old server had the same IP as this one. It's a fixed IP and the router points to 
each server depending on the ports. Such as:

80: IBM
8080: Apple G4

---

### Post by TheFu on 2015-02-18
If the private home is using residential connectivity - then the ISP is blocking 95% likely.

To remotely connect, just use ssh and run the nmap on the box in the correct network zone. Then move to a different box and run nmap again and again, as you get to machines on different network subnets. Sounds like there is internal and external - so only 1 box inside and from your location.
**sudo nmap -sT ip-address**

hostnames cannot have spaces. Mixed case is a bad idea too because you never know when a script won't be written to handle that.  For that reason, ibm would be better as a name than IBM - however for DNS it shouldn't matter at all.  Just trying to get you to avoid stupid issues in 2 yrs when a script doesn't work over this stuff.

---

### Post by russellclaude on 2015-04-06
I am having the same kind of trouble. I have added rules to my iptables/UFW, but I cannot get port 465 to show open-- b/c I am trying to firewall a site that needs to send email via Worpress forms. 

 sudo ufw status numbered
Status: active


     To                         Action      From
     --                         ------      ----
[ 1] 465                        ALLOW IN    Anywhere
[ 2] 22                         ALLOW IN    Anywhere
[ 3] 80                         ALLOW IN    Anywhere
[ 4] 25/tcp                     ALLOW IN    Anywhere
[ 5] 587                        ALLOW IN    Anywhere
[ 6] 587                        ALLOW OUT   Anywhere (out)
[ 7] 465                        ALLOW OUT   Anywhere (out)


but netstat doesn't show anything on 465 as open. Wierd because if I turn my firewall off, I can send mail-- but port does not show open then, either???? Can anyone help, please?

---

