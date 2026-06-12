---
title: "Ican't connect to yahoo messenger wuth any program"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by simion314 on 2008-11-27
i tried kopete and pidgin, mainly and some other small program but i can't connect, it takes more then 1 hour to connect

1 I am not behind a firewall or proxr, i connect directly to the internet with DNS dinamic IP
2 the accounts are set up correct and they worked until 1 or 2 weaks ago, maybe i made an upgrade(the katest kde 4,1,3?? could this be?)

i tried pidgin from ubuntu 8.04 live cd and kopete from 8.10 kubuntu live cd and it have the same problems, do not connect

3 same problem in arch linux with same kde version
4 the firewall is disabled
5 in windows yahoo messenger works and pidgin for windows works, this is a linux problem then not a connection, router problem no?
6 my gmail account works perfectly so the problem is only with yahoo

the error in pidgin is 
Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com:
Name or service not known


I found the problem , it seams that DNS is not working corectly ,i must specify the IP insted of the server name, so is not a linux problem,

For people with this problem first  try this:
host scs.msg.yahoo.com
if this command gives you an error modify your pidgin or kopete account and change the server name with a valid IP  ,i used
66.163.181.189

and strange after the program connects the command host scs.msg.yahoo.com
 works.

---

### Post by loell on 2008-11-27
it would seems some dns servers are having this name mapping problem. there are reports about this lately.

---

### Post by fifth on 2008-11-27
> **simion314 said:**
> 
For people with this problem first  try this:
host scs.msg.yahoo.com
if this command gives you an error modify your pidgin or kopete account and change the server name with a valid IP  ,i used
66.163.181.189

and strange after the program connects the command host scs.msg.yahoo.com
 works.

Been having this problem for a few days and tried your suggestion with the ip, unfortunately still doesnt seem to work for me :(

---

### Post by simion314 on 2008-11-28
> **fifth said:**
> Been having this problem for a few days and tried your suggestion with the ip, unfortunately still doesnt seem to work for me :(

I found that ip in my windows machine i ping that address (do not remember exatly ) and windows displayed me the IP.
If you have a windows machine try this command in the command promt(Start->Run type cmd and press enter) 
ping scs.msg.yahoo.com
after a wile some messages should appear and an IP should be there try that IP.

I gues that can be other ways to find the IP. DO YOU USE PIDGIN OR kOPETE?

---

### Post by Ayuthia on 2008-11-28
I switched my over to cn.scs.msg.yahoo.com.  I found this one through:
[http://service1.symantec.com/SUPPORT/ent-gate.nsf/docid/2007645475208898](http://service1.symantec.com/SUPPORT/ent-gate.nsf/docid/2007645475208898)

---

### Post by fifth on 2008-12-05
> **simion314 said:**
> I found that ip in my windows machine i ping that address (do not remember exatly ) and windows displayed me the IP.
If you have a windows machine try this command in the command promt(Start->Run type cmd and press enter) 
ping scs.msg.yahoo.com
after a wile some messages should appear and an IP should be there try that IP.

I gues that can be other ways to find the IP. DO YOU USE PIDGIN OR kOPETE?

I've tried Pidgin and Kopete. I can ping the yahoo servers fine from ubuntu, I just can't get either app to connect :( Also, the beta Yahoo Web Interface also gets stuck on connecting/logging. The java app just keeps spinning with a message that its connecting.

---

### Post by simion314 on 2008-12-09
> **fifth said:**
> I've tried Pidgin and Kopete. I can ping the yahoo servers fine from ubuntu, I just can't get either app to connect :( Also, the beta Yahoo Web Interface also gets stuck on connecting/logging. The java app just keeps spinning with a message that its connecting.

If you do not found a solution yet try to  connect to #pidgin IRC chanel on freende and ask there or maybe subscribe to a mailing list, you should paste there your configuration and the error message. Good luck.
P.S. Sorry for the late response but the notification email was sent to spam and i just find it there

---

