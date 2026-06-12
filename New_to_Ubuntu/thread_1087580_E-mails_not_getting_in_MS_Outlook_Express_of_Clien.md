---
title: "E-mails not getting in MS Outlook Express of Clients through SQUID"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by palepups on 2009-03-05
Dear Friends / Moderator

I am a newbie to Ubuntu and Squid.  I have installed Ubuntu on a P-4 3.0 Ghz, 1 GB Ram, 80 GB ATA HDD machine.   Later installed SQUID as per the documentation given in Ubuntu site.

sudo "apt-get ........ squid " at $prompt

squid started.

My end user IE browser network configuration changed as per the configuration of my squid.conf is able to perform browsing through this squid.

But they are not getting mails in their MS outlook Express through my SQUID Box.  What to be done for that ?

I request you please reply as early as possible

Thanks in advance

Regards

PS Prasad
Rajahmundry, AP, INDIA 
Pin - 533105
[email]palepups@gmail.com[/email]

---

### Post by Vishal Agarwal on 2009-03-05
Squid is an internet proxy server not the mail server. Your mail cannot be accessed because of squid configuration. For the mail you have to install the postfix server.

---

### Post by palepups on 2009-03-05
Dear Vishal Agarwal

ThankQ for your immediate favourable reply.

I am having sufficient knowledge in Windows Environment.  How to install & Configure POSTFIX or SENDMAIL in Ubuntu ?   

Earlier we have used WINPROXY in windows environment which allows my users to get their E-Mails and Web Browsing both activities.   Now it's licence period is over.   Hence, now this challange was given to me.

Please advise and do some help to get my users their E-Mails and Browsing through my this UBUNTU Box.

Regards

PS Prasad
Rajahmundry, AP, INDIA
Pin - 533105
[email]palepups@gmail.com[/email]

---

### Post by Vishal Agarwal on 2009-03-05
See this link. I used it to install my server, which worked well  for sending and receiving the mail, but it is not the perfect one.

[The Perfect Server - Ubuntu Intrepid Ibex (Ubuntu 8.10) ]("http://howtoforge.org/perfect-server-ubuntu-8.10")

---

