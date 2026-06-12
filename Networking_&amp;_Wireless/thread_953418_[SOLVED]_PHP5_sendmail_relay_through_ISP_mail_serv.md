---
title: "[SOLVED] PHP5 sendmail relay through ISP mail server"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by batfastad on 2008-10-20
Hi everyone
I have an intranet PHP5/MySQL server which is currently windows 2000, but I'm gradually configuring Ubuntu 8.04 Server to take care of this task.

We send out email newsletters using a PHP class called SwiftMailer which works great on our ISPs webspace, but takes a fair old while to send a few thousand.
So on the new Ubuntu box I really want to configure sendmail to relay all mail through our ISP's mail server.

However I've read plenty of posts on here which recommend postfix or exim rather than sendmail for this task. Due to the comparitive ease of configuration.
Is this a correct assumption?

I will only be using the sendmail to send our email newsletters and other email from PHP.
We already have a local Exchange server which handles all our user email data.

What does everyone reckon I should do?
I have sendmail installed and it seems to be working with sending the test emails I have sent out.

But if I switch to Exim/Postfix/another mail server, is there a drop-in replacement that sits in the sendmail path to still allow "sendmail" access?
The most efficient way for sending bulk mail with the SwiftMailer PHP class is to let it interact directly with sendmail on the system.

Any comments/suggestions?

Thanks, B

EDIT: I should have posted this in the Server forum, a mod can move if it's a problem

---

### Post by batfastad on 2008-10-24
Hi everyone

Basically got this solved.
Installed Postfix instead, and added a relay domain and it's working perfectly.
After looking through the headers, seems the mail is being relayed correctly.

There was no extra configuration required to get Postfix working with PHP either, seems to work straight through the existing sendmail binary path given in php.ini

Hope this helps someone out
Thanks, B

---

