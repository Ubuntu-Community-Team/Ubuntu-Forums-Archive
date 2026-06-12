---
title: "Can't access internal Apache server from external url."
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2015-01-14
I changed my gateway hardware to a buffalo dd-wrt, I set up port 80 forwarding to my linux box as it was with the old gateway. NOW I can't get the website if I go to [http://myurl.org](http://myurl.org)  

HOWEVER, if I go to my house and go to [http://myurl.org](http://myurl.org) it works. It also works internally if I got 10.10.10.2

Is this a gateway config issue or could there be an apache setting I should be looking at.

---

### Post by Lars Noodén on 2015-01-14
Did you set up your new modem with your dynamic DNS account information?

---

### Post by wlraider70 on 2015-01-14
My server actually handles the ddns, and it accessible from a toatly separate location. 
It seems to be the loop that is an issue.

---

### Post by Lars Noodén on 2015-01-14
Can you access the web server via the external ip at all from the internal network?  It might be that the new device does not support hairpinning without modification.  Searching for dd-wrt showed a few mentions of issues with recent versions.

---

### Post by wlraider70 on 2015-01-14
No, not at all. So is "hairpinning" the term I should be looking into?

---

### Post by Lars Noodén on 2015-01-14
It's one of them.  I can't remember the synonyms, but you should be able to find useful material under "nat hairpinning" and "dd-wrt"

---

### Post by wlraider70 on 2015-01-14
Thanks for the help!

For the record/posterity

The issue was a buffalo dd-wrt one.

I added the command in "administration" > "commands"
iptables -t nat -I POSTROUTING -o br0 -s 10.10.10.0/24 -d 10.10.10.0/24 -j MASQUERADE


as found on [http://superuser.com/questions/285699/dd-wrt-how-to-allow-port-forwarding-to-apply-to-requests-originating-from-insid](http://superuser.com/questions/285699/dd-wrt-how-to-allow-port-forwarding-to-apply-to-requests-originating-from-insid)

---

### Post by Lars Noodén on 2015-01-14
Great.  

Also, for the record the alternate terms are "NAT Loopback", "NAT Reflection" and "NAT Hairpinning".  It took a while to find them the last one seems to be the most popular term.

---

