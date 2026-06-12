---
title: "Setting up a Mail server"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by timboellis on 2008-01-18
Can anyone advise on how to setup a proper mail server.

I have the domain mydomain.com with 123reg however how do I tell that to connect to my IP/PC 

And what to install to manage it

---

### Post by HermanAB on 2008-01-19
OK, first you may have to upgrade your ISP account to a 'server' account.  Your ISP will then remove any port blocks they may have in place and give you more bandwidth in exchange for about $10 more per month.  

They will also allocate you two or more IP addresses.  Use these addresses at your registrar and ensure that you have A, PTR and MX records pointing to these addresses.  Configure your server with your fully qualified name.

TEST it.  Use nslookup and ensure that your A, PTR and MX records all resolve properly.

Now go here: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

and about 20 minutes later you should have a fully functional mail system.  

Note that most mail problems are caused by DNS trouble.  So, ensure that your DNS is configured right and that the hostname of the machine is defined properly and resolves.

Hope that helps!

Herman

---

### Post by timboellis on 2008-01-19
Well what can I say the best to the point answer I have ever had thanks a lot but.........

My ISP will not provide me with a static IP address unfortunatly.

Or can it be done this way I have my shared server somwhere in cyberspace with SMTP, IMAP and POP3 could I configure a server to collect the mail from that then store it on a server until the local machines decided to get it?

Unless there is a way o do it dynamicly

---

### Post by HermanAB on 2008-01-19
Hmm, I don't like shared servers, since you cannot install what you want and that ruins the Ubuntu Geek experience.

You could rent a dedicated server somewhere on a server farm and install everything yourself.  CiHost frequently has 'Crazy Deals' - old dedicated servers available for $50 a month or less.  I ran one old Celeron server with their Dallas centre for more than 5 years:
[http://www.cihost.com/products/crazy-deals/index.php](http://www.cihost.com/products/crazy-deals/index.php)

Other server farms may have similar things going.

Otherwise, change your ISP to better one.

BTW, Citadel has 'fetchmail' built in.  You could run Citadel as a local server and configure it to fetch your mail from one or more other servers.  You can also set it to relay outgoing mail through your ISP mail server.  That will get around the port blocks.

Cheers,

Herman

---

