---
title: "Nagios Notification"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by hazardfly on 2008-11-21
Hello,

I evaluate at the moment the Network Monitoring Tool "Nagios". It works fine so far. The only problem I have is to configure the notification daemon to send me events and warnings via email. I read many docs and the wiki but didn't got the clou of these two:

- the commands: so you send that from the shell or do you write it into a nagios file or wth?
- I found out that it uses mailx. But I can either send nor receive emails... Is there a simple way to configure that mailx for a newbie like me? Any suggestions? I found out so far that I have to create a .mailrc file. But moreover ... I don't know.

Thanks for your help
hazardfly

---

### Post by hfranco on 2008-12-08
Have you had any luck setting this up?

---

### Post by jonobr on 2008-12-08
Hello


I would like to give you a start, Im not sure if this is useful to you.

You need to be aware that in order to send an email, you need to talk to an SMTP (simple mail transfer protocol) server, or you need to have your own box act as a SMTP server.

Acting as a SMTP server can be problematic if you are not sure what your doing, particular if your box gets hacked.
Your smtp server could be used to send or relay email messages so its generally not advised to do this.

The best way is to use an existing SMTP mail server and send your emails to that.

A program like ssmtp can be used for that, talking with an external SMTP server to send your emails, You can set it up to email files to whomever.
To find out more on SSMTP do a google for "man ssmtp" and it should show you the help files for it.
This program is small and simple.
You can also find resources which will walk you through integrating with things line gmail etc.

If you really need to have your system act as a mail server,
you need to install and configure sendmail which do whats required from a full functional mail system , i.e. sending and recieveing emails.

There should be plenty of information on installing sendmail using synaptic and configuring using threads like this
[http://ubuntuforums.org/showthread.php?t=196112](http://ubuntuforums.org/showthread.php?t=196112)

However, as said, you really need to be careful and know what your doing when installing sendmail.

Good luck

---

