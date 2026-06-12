---
title: "Setting up sendmail on testing server"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by x3graphics on 2009-01-20
So I finally set up my testing server with apache, mysql, and php5 but I want to be able to test php-sendmail function. I have installed sendmail but have no idea how to set it up for a testing server. Any help would be appreciated.

Thanks

---

### Post by cmnorton on 2009-01-22
This is a good question, because it has caused me to look at sendmail
more closely. I am using it in a limited way.

Do you want to route email from this server to your production email
server? Or, do you want people's email clients to use this server as the
smtp server? 

I have experience configuring sendmail so that it relays
email off our Linux servers to our main email server. I have not set up
a sendmail server to be the processor of email for clients.

---

### Post by bsharp on 2009-01-22
Also make sure that your ISP allows mail servers on your network-a couple of years ago I was trying to do the SAME thing, going through conf files, reinstalling, purging my sendmail installation, etc only to learn that I had it configured properly, but my ISP blocked the port!

Disappointing, but at least I know it wasn't due to my own stupidity (except for not checking if it was blocked at the beginning :P).

---

