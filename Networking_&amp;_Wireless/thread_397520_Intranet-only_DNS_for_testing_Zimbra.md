---
title: "Intranet-only DNS for testing Zimbra"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by chris.pappas on 2007-03-30
Hello..

I am trying to test out Zimbra on Ubuntu 6.06 and I am stuck - I have only one external IP address and an email server already running. If worse comes to worse I will get another ext. IP address (and will probably do so in the long run anyways) but for now I would like to test this out.

I have VMware server set up, and two virtual machines. I am not looking for performance, so I am going to run both VMs on my computer at once.

I would like to set up a local testing domain such as "test.foo" so that I can give it an MX record (required for Zimbra) but I would like the testing domain to stay contained within the vm's

I have seen quite a few examples but I just can't seem to figure out where to start. I have installed the LAMP package and bind on my web/dns server, and I am going to reinstall zimbra on the other vm.

Basically I need to figure out how to get this running, so that:
my web/dns server ip: 192.168.1.1
my zimbra server ip: 192.168.1.2

[www.test.foo](www.test.foo) will serve http from 192.168.1.1
ftp.test.foo           "                            "
dns.test.foo will serve dns requests from 192.168.1.1

mail.test.foo will serve email from 192.168.1.2

I may also create a third vm with ubuntu desktop so I can test this out and view web pages on www

can someone point me in the right direction? I am not looking for this network to be accessible from the web.

Thanks!
Chris

---

### Post by Scunizi on 2007-03-30
Your DNS service is outside your network unless you are also running a DNS server.  So when you type in [www.Foo.com](www.Foo.com) the browser automatically goes to the internet and your assigned DNS server to lookup the actual address.  It will bomb unless you have the [www.foo.com](www.foo.com) name registered and pointed at your current IP coming into your router, and most probably on a different port than 80.  Why? 'Cause your ISP will typically block port 80 to keep you from running a server.  

Since you're only concerned about access from your internal network, try just typing in the IP of the VM you're trying to reach.  That should do it.  Now if you are in a browser that is inside of the VM you're trying to reach you'd type http://localhost:"some port number here" and it should pop up.  That's what I'm currently doing while testing Joomla.

---

### Post by Mr. C. on 2007-03-30
Setting up a bind name server is not too difficult.

Review Week 8 Notes, Lab work and Homework here:

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

This will give you a brief overview of setting up an internal name server that is authoritative for your test domain.

MrC

---

