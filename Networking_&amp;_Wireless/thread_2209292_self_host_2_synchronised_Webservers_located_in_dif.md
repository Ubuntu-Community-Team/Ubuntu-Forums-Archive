---
title: "self host 2 synchronised Webservers located in different states via the internet"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by adamjedgar on 2014-03-05
Hi guys,
not sure exactly how i am supposed to phrase this question, or where to place it in the forums...but here goes...

I have two servers on static ip addresses that are in different states (one in Sydney NSW and one in Brisbane QLD). Both are currently running Ubuntu LAMP webservers.
I would like to link them together via the web so that one may act as a backup webserver for the other in the event of ISP outage or local system/hardware failure. 
In the future, i would like to host wordpress multisites 
I would only like the mirror to backup files that are changed...not entire sites. However, the two systems need to run in sync...even sharing resources in a cloud fashion would be ideal (if that is feasible for a low end tech tragic like myself) 

I was hoping to use free open source platform for this...and i am one who needs things spelled out using examples and in very progressive steps.

Any ideas?

kind regards,
adam

---

### Post by TheFu on 2014-03-06
This isn't the best forum for that question - nothing to do with virtualization.

Don't think "failover" - instead think load balanced so that both system are used all the time, unless one fails. Setup DNS-based load balancers and bi-directional data/DB replication.

There are 50 different ways to accomplish this result with many inputs determining "the best way." How much data change happens per second will be good to know. How much bandwidth is available between the sites? How competent are you at rsync scripting?  Does security matter?  Plus all the different software.

They won't be "linked" through the web. That just isn't done. Data connections to transfer changes on both sides should happen over ssh.

Without extreme details about the setup, nobody qualified can help with "things spelled out using examples." I can't speak for others, but I'm hear to "teach you to fish", not hand you a fish, mainly by giving you things to google to learn on your own.

Or you can find paid help for a few thousand dollars. This is a non-trivial setup.

Don't forget about backups. Bidirectional data replication is not 100% safe. 2 corrupt systems is bad.

---

### Post by bapoumba on 2014-03-06
Moved to Networking.

---

### Post by adamjedgar on 2014-03-06
So to start with simple things,
When someone is browsing my wordpress site how is the url resolved by dns servers when there are for example, multiple ip addresses load sharing the same site?

---

### Post by TheFu on 2014-03-06
> **adamjedgar said:**
> So to start with simple things,
When someone is browsing my wordpress site how is the url resolved by dns servers when there are for example, multiple ip addresses load sharing the same site?

1st we need to understand DNS - [http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System) will explain in more detail than we care. That gets the client to talk to the server ... if HTTP, that will go to the port and web server running wherever the URL specifies. May or may not be port 80.

Once the web server receives the request, it can handle it any many different ways. Most web servers will redirect based on the "name" in the DNS request. So - the web server administrator puts a "name" into the configuration - that is how 2 or 10,000 different HTTP websites can be hosted on the same IP.  HTTPS complicates things. While not impossible, hosting multiple HTTPS websites on a single IP is non-trivial.

For **apache2** the "VirtualHost" of a specific port needs to be a wildcard, but the "ServerName" must be setup. More [details from the horses mouth.]("https://httpd.apache.org/docs/2.2/vhosts/") I don't know how the new apache2.4 does it. Sorry. It is probably the same, but .... 

I use **nginx** (find it to be faster, smaller, easier to secure and it makes a fantastic reverse proxy).  It uses the "server_name" config setting and if running a reverse proxy - the "proxy_pass" setting.

---

### Post by SeijiSensei on 2014-03-06
> **adamjedgar said:**
> So to start with simple things,
When someone is browsing my wordpress site how is the url resolved by dns servers when there are for example, multiple ip addresses load sharing the same site?

That's called "round-robin" DNS; the server gives out one of the addresses randomly for each query.  That works fine if the content is up-to-date on all the servers, but not if they do not stay in sync.

There are methods to accomplish what you want to do, but they are challenging to set up.  First, you should probably look into database replication.  For WordPress sites, where all the content is stored in the database, that's the key to having all the sites stay in sync.  You'll need to read the documentation for the SQL server you are using to determine how it handles replication.

There are also [high-availability]("http://www.linux-ha.org/wiki/Main_Page") methods to have servers monitor each other and take over when one goes down.

---

