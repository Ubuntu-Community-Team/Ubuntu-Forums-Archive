---
title: "Help: Port 25 restricted"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by nedmas on 2007-02-03
Hi im currently at uni and as such am forced to resided behind a proxy server, nothing wrong with that except that they've blocked every port except 80 and 21. Which means i cant check my mail using port 25. Ive tried several solutions including proxychains but cant get anything to work. I know that its possible as ive done it in windows with proxifier.
So i was just wondering if anyone has any ideas for a solution.

---

### Post by Gerard Barberi on 2007-02-03
Maybe [this ]("http://www.no-ip.com/support/guides/email/blocked_port_25.html")might help, but I'm not sure.

---

### Post by tturrisi on 2007-02-03
> **nedmas said:**
> Hi im currently at uni and as such am forced to resided behind a proxy server, nothing wrong with that except that they've blocked every port except 80 and 21. Which means i cant check my mail using port 25. Ive tried several solutions including proxychains but cant get anything to work. I know that its possible as ive done it in windows with proxifier.
So i was just wondering if anyone has any ideas for a solution.
Check your mail where?  Port 25 is not needed for checking mail.  Port 25 is the default port used BY a smtp server (MTA - sending mail).  

The wording of your post is confusing.  One usually "checks mail" using a mail client, checking is done using the POP protocol, which uses server port 110 by default.  Pls clarify what you want to be able to do.

In the event you are running a mail server (MTA) and the isp blocks port 25, then you need to configure the server as a "smarthost", which is essence means that all mail sent by the MTA is forwarded via the isp's smtp server.

---

### Post by tagginannie on 2007-02-03
> **nedmas said:**
> Hi im currently at uni and as such am forced to resided behind a proxy server, nothing wrong with that except that they've blocked every port except 80 and 21. Which m[Ubuntu Forums - Reply to Topic]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=2100684")eans i cant check my mail using port 25. Ive tried several solutions including proxychains but cant get anything to work. I know that its possible as ive done it in windows with proxifier.
So i was just wondering if anyone has any ideas for a solution.

Set the smtp port to 587 non-SSL at first if you get error message turn it on  

Suzy:KS

---

### Post by nedmas on 2007-02-03
> **tturrisi said:**
> Check your mail where?  Port 25 is not needed for checking mail.  Port 25 is the default port used BY a smtp server (MTA - sending mail).  

The wording of your post is confusing.  One usually "checks mail" using a mail client, checking is done using the POP protocol, which uses server port 110 by default.  Pls clarify what you want to be able to do.

In the event you are running a mail server (MTA) and the isp blocks port 25, then you need to configure the server as a "smarthost", which is essence means that all mail sent by the MTA is forwarded via the isp's smtp server.

Sorry, what i meant was that i dont have any other ports except port 80 and 21 so i cant use a mail client. So i want to some how tunnel through my proxy or do something so that i get full port access.

Sorry again for my ill explained situation.

---

### Post by tturrisi on 2007-02-03
I take it that the school manages the proxy server.  It is very unusual that they would disallow the use of email clients.  Clients such as browsers and email do NOT use ports 80, 21, 25 or 110.  Servers use those ports.  Clients connect to the server's ports by sending a request on any available port above 1025 and they also receive on a free port.  If you cannot use an email client then it's not likely the proxy has anything at all to do with it, it's your client configs/settings.  

FYI, email clients should be configured to connect to port 110 for POP (receive) and 25 for SMTP (send).  The client does not actually use those ports at all.  Same w/ a browser, it does not use port 80.  If your school only allowed port 80 & 21 then you could not even browse the www.

---

